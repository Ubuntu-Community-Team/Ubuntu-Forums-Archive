---
title: "Karmic 64bit - Mounted Drive Keeps Disconnecting"
date: 2010-03-08
forum: General Help
---

### Post by johnathanamber on 2010-03-08
Hello everyone,

About every couple of days, my linuxfiles mount will disconnect.

I notice this because I have created a symbolic link from my user's home folder to this drive. So when I log in, if the drive isn't mounted I get the following errors:

> 
Could not update ICEauthority file
/home/johnathan/.ICEauthority


> 
There is a problem with the configuration server.
(usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)


I keep having to remove the mount folder and then readd it. Then I have to reapply the permissions for it to connect back to those files.

How can I correct this? This only happens to this mount, the others stay connected with no issue.

Also, when I log in and I have this issue... I cannot get out of this or log off unless I shutdown my laptop... is there another way?

I guess I could do an init 3 from the CL...

Thank you and God bless,
Johnathan

---

### Post by myth1914 on 2010-03-08
I don't know that it would necessarily resolve the un-mounting issue, but as a functional work-around, you could try making this an autofs mount rather than persistent.  This way it would attempt to mount the drive whenever it is being accessed.  If the drive has un-mounted, it would re-mount in the background.  While this would cause a very slight delay accessing the directory when mounting, it would provide a simple solution which would survive reboots...

[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

---

### Post by johnathanamber on 2010-03-08
@myth1914,

I am not sure if that would work well or not. It 'sounds' like it would fix the issue... I might give it a try later today.

I'd just like to know what is going on to make it have an issue with a persistant connection.

Thank you and God bless,
Johnathan

---

### Post by johnathanamber on 2010-03-24
I've recently reinstalled Ubuntu karmic. My previous drive I attached to the mount point: /media/files

I've decided to use the following mount point instead: /files

I guess we'll see what happens.

Thank you for your time and God bless,
Johnathan

---

### Post by johnathanamber on 2010-03-31
Reinstalling resulted in the same...

As I've lost this thread... continued another here:
[http://ubuntuforums.org/showthread.php?t=1438781](http://ubuntuforums.org/showthread.php?t=1438781)

---

### Post by johnathanamber on 2010-06-08
Issue has not come back up since upgrading to Lucid Lynx. BTW, I did do a minimalist install... that might have helped.

---

