---
title: "klik"
date: 2006-03-02
forum: General Help
---

### Post by tikal26 on 2006-03-02
I want to try some pacakages from klik but can't find it int eh repos aby one tryed klick in kubuntu before and if so did you had to use the source.Or how do you delete or upgrade programs. I mean I would like to install the xarax-lates but I would like to know how to delete it or upgrade it as they add more klik pakages

---

### Post by ltmon on 2006-03-03
You might try reading [http://klik.atekon.de](http://klik.atekon.de).

Klik packages are _very_ different from normal packages.  In short the package is the program.  Delete it by deleting the file.  Upgrade it by deleting the file and getting a new one.  It's a more manual process.

L.

---

### Post by towsonu2003 on 2006-03-03
[http://klik.atekon.de/wiki/index.php/Troubleshooting#I_get_.22Xdialog:_command_not_found.22](http://klik.atekon.de/wiki/index.php/Troubleshooting#I_get_.22Xdialog:_command_not_found.22)

---

### Post by tikal26 on 2006-03-06
thanks

---

### Post by gingermark on 2006-03-07
Hey,

I had a go with Klik, but I got an error relating to zAppRun.

I read on the Klik site that Klik needs to be run with root priviledges the first time. But I read on these forums that running as a regular user is fine. These seem a little conflicting.

Does anyone have any advice on this? I wasn't planning to use Klik much, so am not too woried I can't get to work, but it seems a good way to get updated versions of apps that may not be backported between Kubuntu releases.

---

### Post by towsonu2003 on 2006-03-07
[QUOTE=gingermark]
I had a go with Klik, but I got an error relating to zAppRun.
[/QUOTE]
what was the error?

---

### Post by gingermark on 2006-03-07
Yeah, sorry. I got the error several times downloading Firefox 1.5, but I've just tried it again (so I could post the exact error) and it's now worked!

I guess if I get the problem again I'll post the exact error.

---

### Post by gingermark on 2006-03-07
"/home/gingermark/.zAppRun: line 132: /tmp/app/1/wrapper: No such file or directory" was the error. Seems to be an intermittant one, as it came trying to run Firefox 1.5 which worked earlier....

EDIT: Also got the error "Unable to mount /tmp/app/1" before that. That was where I thought the root privs were needed. Dunno why it worked before though.

---

### Post by ltmon on 2006-03-07
I had to install with root privileges to get it working.  

It's because the installer needs to modify the file /etc/fstab, which is not writable by regular users.

The conflicting information comes from the fact that on more modern systems (incl. Dapper I think) Klik can use the FUSE kernel module for this task instead.

L.

---

### Post by towsonu2003 on 2006-03-07
yea, I got your second error myself, than I just quit trying. maybe the klik forum people can help? don't know...

edit: you mean install with root privileges or run with root privileges? I installed and it asked for the root pass and changed fstab. my error was due to klik not mounting loop device bc apparently ubuntu needs root to mount loop stuff (same with qemu, regardless of fstab options)

---

### Post by adamkane on 2006-03-14
klik installation requires zenity, dialog, and xdialog:
```

sudo apt-get install zenity dialog zdialog

```

---

