---
title: "How to burn a virtual disc? Blank cd-rw.iso ?"
date: 2011-10-21
forum: General Help
---

### Post by collisionystm on 2011-10-21
On Windows I found this really great program. It is called Phantom drive. [http://www.phantom-drive.com/en/default.htm](http://www.phantom-drive.com/en/default.htm)

I was looking everywhere for a program on Windows that would let me "burn" to a cd drive that didn't exist. Mainly because I was building a Hackintosh and I needed to burn the extracts of the .dmg to a dvd. Well I don't have a dual layer burner, so I used phantom drive so I could run OSX in a virtual environment. Anyways..

Is there anything like this for Linux?

---

### Post by dcstar on 2011-10-22
> **collisionystm said:**
> On Windows I found this really great program. It is called Phantom drive. [http://www.phantom-drive.com/en/default.htm](http://www.phantom-drive.com/en/default.htm)

I was looking everywhere for a program on Windows that would let me "burn" to a cd drive that didn't exist. Mainly because I was building a Hackintosh and I needed to burn the extracts of the .dmg to a dvd. Well I don't have a dual layer burner, so I used phantom drive so I could run OSX in a virtual environment. Anyways..

Is there anything like this for Linux?

Google is an amazing thing, people should try it one day:

[http://cdemu.sourceforge.net/](http://cdemu.sourceforge.net/)

---

### Post by satanselbow on 2011-10-22
PPA here:

[https://launchpad.net/~cdemu/+archive/ppa](https://launchpad.net/~cdemu/+archive/ppa)

---

### Post by collisionystm on 2011-10-22
> **dcstar said:**
> Google is an amazing thing, people should try it one day:

[http://cdemu.sourceforge.net/](http://cdemu.sourceforge.net/)

I used Google. I rarely ask for help with things like this. Perhaps you should read about what you offered me. IT DOES NOT DO WHAT I AM ASKING.

Thanks anyways

---

### Post by collisionystm on 2011-10-22
Here is the WIKI. [http://en.wikipedia.org/wiki/CDemu](http://en.wikipedia.org/wiki/CDemu)

I need a virtual CD/RW drive. I need to burn an .iso to a virtual cd drive with brasero.

---

### Post by satanselbow on 2011-10-22
You would only need to "burn"  through Brasero if you were after a hard media on physical cd... cdemu mounts a pre-created image which can then be subsequently handled/read by the filesystem...

create ISO with Brasero -> mount image with CDemu

You might want to rephrase your question if that is not want you are after ;)

---

### Post by collisionystm on 2011-10-22
> **satanselbow said:**
> You would only need to "burn"  through Brasero if you were after a hard media on physical cd... cdemu mounts a pre-created image which can then be subsequently handled/read by the filesystem...

create ISO with Brasero -> mount image with CDemu

You might want to rephrase your question if that is not want you are after ;)

Okay... Question rephrase.

I want a virtual cd rom drive that I can "burn" an iso image to. I realize that you usually burn an .iso to a physical media, but I want to burn an .iso to an .iso essentially. 
I am not trying to copy files either. 
I just want a virtual cd drive that Ubuntu will think is a physical drive that holds a blank disc ready to write to.

phantom disc does this. I am just looking for a Linux version.

---

### Post by enkay009 on 2011-10-22
If I understood you correctly, by "burn to a virtual cd drive" you mean you want to access the contents of an ISO?

You can always mount an iso in Linux/UNIX. I don't know if there is any userland tool that lets you do this (CDEmu sounds like an attempt at it). The old school way is this (as root):

```
mkdir -p /mnt/myiso
mount -tiso9660 -oloop /path/to/myiso.iso /mnt/myiso

```In the first step, you're creating the mount point you'll mount the iso to.
In the second step you're mounting the iso to that mount point.

The contents of your iso will be available from /mnt/myiso

When you're done (again as root)...

```
umount /mnt/myiso
rmdir /mnt/myiso
```

---

