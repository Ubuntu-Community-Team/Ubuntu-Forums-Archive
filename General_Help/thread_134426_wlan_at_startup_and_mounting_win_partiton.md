---
title: "wlan at startup and mounting win partiton"
date: 2006-02-21
forum: General Help
---

### Post by SVFUSiON on 2006-02-21
Is there a way I can make ndiswapper modprode automatic at start up? Also, can I mount my windows partiton at startup?
Thanks!

---

### Post by romdos on 2006-02-22
auto starting of scripts can be a little tricky, what you need to do is:
1) create a script that will setup ndiswrapper how you want is and also modprobe it with your favorite text editor.

2) mv the script to /etc/init.d

3) make sure the script is executable by root:
```

romdos@freekbox:~$ chmod 744 /etc/init.d/foo

```

4) run
 
```

romdos@freekbox:~$ update-rc.d foo start 99 2  . 

```

this will insert your script as a startup script into /etc/rcd.2 (ubuntu's default runlevel)

now your script will be run by root everytime you boot

to learn more about this stuff, check out the man pages:
```

man init
man update-rc.d

```

------

now to mount your windows drive on startup, you will need to:

1) create a mount point for it (this can be any directory that you create, a good place for it is in /media/windows
```

romdos@freekbox:~$ sudo mkdir /media/windows

```

2) edit /etc/fstab and create a proper entry (like this):

/dev/hdx /media/windows vfat auto,users,exec,umask=000 0 0

where x is your windows drive and partition #

then
```

romdos@freekbox:~$ sudo mount -a

```
to bring it up

for info on that crazy fstab stuff see:
```

man fstab

```

now everything will start automatically at boot!
Let me know if anything here is too glossed over.

---

### Post by romdos on 2006-02-22
this might make your life a little easier...
i don't use ndiswrapper but read that it you only need to insert drivers into it once.
if this is true it makes modprobing it at every boot as easy as adding ndiswrapper to /etc/modules

```

romdos@freekbox:~$ sudo echo ndiswrapper >> /etc/modules

```

---

