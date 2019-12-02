jdownloader 2 headless for arm64 board 

Clone from https://github.com/PlusMinus0/headless-jd2-docker

**RUN**

```
sudo docker run \
  --name jdownloader2 \
  -e EMAIL=<your email> -e PASSWORD=<your-password> 
  -p 3129:3129 \
  -v /.config/jd2:/opt/JDownloader/cfg  \
  -v $HOME/Downloads:/opt/JDownloader/Downloads \
  --restart unless-stopped \
  skywirex/jdownloader-2:<tagname>
```

`<tagname>` see https://hub.docker.com/r/skywirex/jdownloader-2/tags

**BUILD** 

```
docker build -t skywirex/jdownloader-2:debian-arm64-v20191202 .
```

If you don't want to specify your credentials on the command line, remove them from the command above (`-e EMAIL=... -e PASSWORD=...`) 
and add them manually to the file`<config-dir>/org.jdownloader.api.myjdownloader.MyJDownloaderSettings.json` as in

```
{ "email" : "your email", "password" : "your-password" }
```
    
# Optional environment variables

Environment Variable | Description
---------------------|------------
EMAIL                | The MyJDownloader account e-mail. Is written automatically to config-file, if set.
PASSWORD             | The MyJDownloader account password. Is written automatically to config-file, if set.
UID                  | Specifies the UID the daemon should run as. All created files will be owned by this UID. Defaults to 1000.
GID                  | Specifies the GID for all created files. This only works in combination with the UID. Defaults to 100 for users.

Not setting `UID` / `GID` will default to `1000`:`100`.


More info at [skywirex.com](https://skywirex.com/)
