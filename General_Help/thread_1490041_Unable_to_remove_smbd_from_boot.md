---
title: "Unable to remove smbd from boot"
date: 2010-05-21
forum: General Help
---

### Post by snakerdlk on 2010-05-21
I want to disable samba(smbd in lucid) from starting up with the service.

Did not work:
```
#update-rc.d -f smbd remove
```
```
#update-rc.d -f samba remove
```

I tried using *rcconf* but smbd is already disabled...

Did not find any samba/smbd related links in /etc/rc*...

But smbd starts when I boot.

```
#service smbd stop
``` works...

Any suggestions? thanks.

---

### Post by snakerdlk on 2010-05-26
Or is it just me that had this problem, or it is incredible no one commented yet...

Any ideas to help solve the problem would be nice!

---

### Post by snakerdlk on 2010-05-27
Oh well,

I commented the 'start on' stanza in /etc/init/smbd.conf
(and nmbd.conf :D)

apparently the new(?) upstart daemon has this configuration...

---

### Post by oooh on 2010-09-10
is that the only way to unload smbd in bootup ?

isnt it a little crappy ...

is there a cleaner way to do that ??

---

### Post by CharlesA on 2010-09-10
You could stick these two commands in /etc/rc.local.

```
service smbd stop
service nmbd stop
```

Do you just want to stop it from loading on boot, or prevent it from loading at all?

---

### Post by oooh on 2010-09-10
I want to prevent it from loading at bootup

---

### Post by snakerdlk on 2010-09-10
The 'right' thing to do would be to run the update-rc.d command to remove the start up...
But this works for the rc.* start and stop links to /etc/init.d/...

I do not know the difference between this and chkconfig which is usually present in redhat based distros. It seems more elegant but it probably does the same thing.

Since the init daemon is different I don't know the upstart manager for this type.

---

### Post by KeyserSoze93 on 2010-09-10
Try running pstree to see which process is spawning smbd.

You could also install bootchart, to see at what point in the startup process it is being loaded.

---

### Post by snakerdlk on 2010-09-10
The upstart daemon should be the one. Thought I had mentioned but apparently I didnt.

/sbin/init

[http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

---

