---
title: "Running gvfs-mount as root...is it possible and how?"
date: 2012-02-11
forum: General Help
---

### Post by kcstrom on 2012-02-11
So I've got a nice little script that mounts windows shares from a computer on my home network and hard drive attached to my WIFI router/switch. This works great when I run it manually or WIFI is connected before I login such that my script gets called and works.

However, I would like to have it run whenever my computer actually connects to a network rather than on login. I've spent way too much time today trying everything I could think of (which is probably scan little) to make this work. I've placed a script in /etc/NetworkManager/dispatcher.d. Initially I tried just source'ing my script in, but that failed with a mysterious exit value according to /var/log/syslog. So, eventually, I pretty much copied the contents of the original script into the dispatcher script.

Through some more debugging in my original script, I've found that gvfs-mount doesn't appear to want to work when run as root (using sudo) - which I believe it is when run via the NetworkManager dispatcher. I see this fun error message:

```
Error mounting location: volume doesn't implement mount
```Googling for this incredibly descriptive message doesn't really turn up much useful and there appears to be a severe lack of user documentation for GVfs in general and the only info on gvfs-mount itself is an [OpenSolaris man page]("http://www.unix.com/man-page/OpenSolaris/1/gvfs-mount/") (referred from Fedora's info about Gvfs too).

It's not too surprising there is some snafu since gvfs-mount seems to know to put the mountpoint in my home directory: ~/.gvfs/.

I've tried using su - <my username> -C <the script>, but that didn't seem to help as part of the dispatcher script. When run manually, it asks me for my password and then doesn't like it.

Does anyone have any information on whether or not this can be done? I'm tired of being frustrated about this.

Thanks in advance.

---

### Post by Toz on 2012-02-18
How about trying autofs ([https://help.ubuntu.com/community/Autofs]("https://help.ubuntu.com/community/Autofs"))? This way, the share will only be mounted when you access it (not automatically).

---

### Post by Purkinje on 2012-04-19
If you add the -d switch and specify the device title (such as /dev/sda1), it seems to have a higher success rate than mounting by drive name. Example:

```
gvfs-mount -d /dev/sda1
```

If you don't know the name of the device, go to Disk Utility and select the drive you wish to mount. Under Volumes (not Drive), use what's listed under Device.

I hope that helps!

---

### Post by bab1 on 2012-04-19
Are you sure the host (computer) is connected to the network without you being logged in?  Can you ping this host without some user being logged in?  Nautilus (gvfs) should not mount a network drive without network connectivity.

---

### Post by kcstrom on 2012-04-19
> **Purkinje said:**
> If you add the -d switch and specify the device title (such as /dev/sda1), it seems to have a higher success rate than mounting by drive name. Example:

```
gvfs-mount -d /dev/sda1
```If you don't know the name of the device, go to Disk Utility and select the drive you wish to mount. Under Volumes (not Drive), use what's listed under Device.

I hope that helps!

I don't see what -d is supposed to do from the sparse Solaris man page (link above). When I try it manually, I get:

[CODE]
No volume for device file smb://192.168.2.101/users
[CODE]

I'm guessing that's because it has something to with my device being a network location rather than a physical device file.

---

### Post by kcstrom on 2012-04-19
> **bab1 said:**
> Are you sure the host (computer) is connected to the network without you being logged in?  Can you ping this host without some user being logged in?  Nautilus (gvfs) should not mount a network drive without network connectivity.

Yeah, I'm positive. I can manually run gvfs-mount (or run my script manually) and it works just fine. I want to make it work automatically upon connecting to my home network though.

---

