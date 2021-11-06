# rasPBX_Docker
This is a complete port of RasPBX (Asterisk for raspberry pi.)

**How this image was created:**

Download the image from official website: http://www.raspberry-asterisk.org/downloads/

```
$ mkdir rootfs raspbxfdisk -l -u=sectors /home/pi/raspbx-10-10-2020.img
$ mount -o loop,offset=272630784 /home/pi/raspbx-10-10-2020.img /rootfs
```
Then, 

```
$ cp -a /rootfs/. /raspbx/
$ nano /raspbx/run/startup.sh
$ chmod +x /run/*
$ tar -C raspbx -c . | docker import - raspbx 
```

This image is now can be used as a base image or independently using **"docker run --name=raspbx -it --privileged --restart unless-stopped raspbx bash"**. Also, adding --cmd=/run/startup.sh will keep the container running without the bash.
