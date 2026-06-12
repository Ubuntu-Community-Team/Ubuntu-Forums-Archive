---
title: "how to execute commands in script after program is closed"
date: 2012-08-18
forum: General Help
---

### Post by Quazze on 2012-08-18
Hello everyone

I have my music on a different partition, so this means that Banshee Media Player can't play music from my library without me first mounting the partition. So I was thinking of writing a little script that mounts the partition, opens Banshee and remove the partition again after Banshee is closed. Here's what I've got:

```
sudo mkdir /media/A220742420740199
sudo mount /dev/sda2 /media/A220742420740199
banshee
sudo umount /dev/sda2
sudo rmdir /media/A220742420740199
```

Now the problem is, I want to be able to run this as a normal executable. If I run it in the terminal everything works fine. But if I just run, not in the terminal (the way I want it), the partition doesn't get mounted. I guess, but am not sure, that the partition gets unmounted again immediately after Banshee is loaded. How do I get this to happen only after Banshee is closed again?

Thanks for the help
Cheers
Lukas

---

### Post by papibe on 2012-08-18
Hi Quazze.

autofs would be a perfect solution for this situation. Take a look at this [tutorial]("https://help.ubuntu.com/community/Autofs").

Let us know how it goes.
Regards.

---

### Post by LewisTM on 2012-08-18
sudo is meant for terminal only. Try gksudo instead.
The simplest would be to invoke your script with [FONT="Courier New"]gksudo script[/FONT] instead of calling gksudo four times in it.
To execute banshee as yourself (not root) edit the line to look like this:
```
su <yourname> -c banshee
```

So to wrap up:
```
# must be run as superuser
mkdir /media/A220742420740199
mount /dev/sda2 /media/A220742420740199
su <yourname> -c banshee
umount /dev/sda2
rmdir /media/A220742420740199
```
Cheers!

---

### Post by Quazze on 2012-08-20
thanks for the answers

> **papibe said:**
> Hi Quazze.
autofs would be a perfect solution for this situation. Take a look at this [tutorial]("https://help.ubuntu.com/community/Autofs").

From the description it indeed seems what I need, but I don't really seem to understand how it works from this tutorial...

> **LewisTM said:**
> sudo is meant for terminal only. Try gksudo instead.

I might misinterpret this, but I always thought gksudo was for commands running graphical processes?
Also I still then get the problem that, as soon as Banshee is launched, it unmounts the partition immediately after


I also have another question actually. I would want to play my music without having to give my su password. How come if I manually mount the partition I need root permission and when I mount the partition with nautilus I don't?

---

### Post by LewisTM on 2012-08-20
gksudo exists so you can enter the password in a graphical environment. A script run outside of a terminal has not command line prompt to ask for a password so you need gksudo in this case.

Banshee might fork itself in the background on your machine, so that subsequent commands in the script (unmount) will be executed. It doesn't do that on mine but who knows?
To circumvent that you could pause the script and check for the presence of banshee in the running processes every 5 seconds, then resume when it's gone.
```
while pgrep banshee; do sleep 5; done
```

Nautilus uses the gio/gvfs framework to mount partitions. You can use that as well. Here's a new script that might work better and without administrator password:
```
#!/bin/bash
gvfs-mount -d /dev/sda2
banshee
while pgrep banshee; do sleep 5; done
gvfs-mount -u /media/A220742420740199 
```

---

### Post by Quazze on 2012-08-20
nice, this works perfectly

is the ```
#!/bin/bash
``` necessary though? Don't fully understand that....

thanks anyway, learned a lot new too

Cheers
Lukas

---

