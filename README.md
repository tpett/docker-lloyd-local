# docker-lloyd-local
*[Lloyd's Coffee House](http://en.wikipedia.org/wiki/Lloyd%27s_Coffee_House)
was the first marine insurance company.*

This tools backups Docker [volume containers](http://docs.docker.io/en/latest/use/working_with_volumes/#creating-and-mounting-a-data-volume-container)
and stores them in a local directory.

To use it, run:

    $ docker run -v /var/run/docker.sock:/docker.sock \
             -v /var/lib/docker/vfs/dir:/var/lib/docker/vfs/dir \
             tpett/docker-lloyd
             container-a container-b container-c...

This will run [docker-backup](https://github.com/discordianfish/docker-backup),
gzip a tarball named after the container and put it in `BACKUP_DIR`
(default "/backup").

See the original project [docker-lloyd](https://github.com/discordianfish/docker-lloyd) if you would like to upload your files to S3.

See [docker-backup](https://github.com/discordianfish/docker-backup) on
how to restore a backup.

The Dockerfile passes command line options to docker-backup by setting the OPTS
environment variable. If you need to override/change those, you can set it on
the command line:

    $ docker run -e OPTS="-addr=/foo/docker.sock" ...
