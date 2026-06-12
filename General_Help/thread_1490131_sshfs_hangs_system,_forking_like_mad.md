---
title: "sshfs hangs system, forking like mad"
date: 2010-05-21
forum: General Help
---

### Post by cacycleworks on 2010-05-21
Hey Everyone,

This problem started a few days ago (probably with an update) and I was running 9.10. I just did a fresh install of 10.04 and it's still happening. (I did keep /home in case that makes a difference)

When I sshfs mount a filesystem in our workplace, once I hit enter, there is an insane amount of new sshfs processes forked. They run continuously until the system runs out of memory/cpu/whatever and it just stops. If you catch it within 10 or so seconds and ctrl-c, you can kill it before death to system.

Any ideas?? I'm pretty baffled with this one.

Oh, and I've been sshfs-ing from 3 servers everyday for about 3 years. 2 are on the LAN and #3 is our website in canada.

ssh and scp work great.

Thanks in advance,
Chris

---

### Post by tgalati4 on 2010-05-21
Sounds like a recursive-mounting issue.  Did you add any FUSE directory mounts recently?  Check all of your directories in your home folder.  That would persist across distros.

So perhaps you mounted a local directory in your home folder to the server that also had a folder linked back to your local machine.  That might cause a recursive FUSE process as it tries to create the mount-within-a-mount.  Sort of like a video camera in a mirror.

All it takes is one directory for this to occur.  Check your /etc/fstab as well.

---

### Post by cacycleworks on 2010-05-26
@tgalati4 : Thanks for your great reply! 

My fstab is generic and only has proc, swap, /home, and /. I've been doing the sshfs thing for a while and have a few times gone back and checked that there are no recursive connections.

The latest hack I did was to use "Connect to Server..." under the Places menu. This mounts the remote filesystems under ~/.gvfs  So to get the usual mounts on my home dir, I basically did this:
```

~$ rmdir raid
~$ ln -s .gvfs/sftp\ on\ raid/raid raid

```

So while this operates, it is hideously slower than sshfs was. A ls on our live website takes 10 seconds, where it would be 1 or 2 before. Pretty much everytime I reboot, I would manually run my sshfs...
```

~$ sshfs webdev:/var/www dev
~$ sshfs raid:/raid raid
~$ sshfs user@our.webhost.in.canada.com: live
Password for user:

```

And then I'll use Geany to edit files "everywhere".

In researching this, it seems there is a fuse / gvfs-fuse-daemon problem. :( This [bugzilla talks about things]("https://bugzilla.redhat.com/show_bug.cgi?id=493565") to do, but when I killed the gvfs daemon, my mouse stopped working. :P I have a keybinding to launch a terminal and use cli to shutdown.

This is pretty annoying, since it broke my workflow.
and the googling goes on...

---

### Post by cacycleworks on 2010-05-26
OMG I fail.

So I have a ~/bin folder. A **long** time ago, I tried to be slick and make a script called sshfs ... in it were the sshfs mounts I normally type be hand. I recall it not working, so I just forgot it and left it there. :P 

I did a```
$ strace sshfs .... 
``` then it spewed out something like /home/username/bin/sshfs, which I promptly realized was wrong. Went there and mv'd the file. So I run sshfs command and it says /home/username/bin/sshfs not found. (that will probably go away when I log in again ... in a few weeks) Running /usr/bin/sshfs totally worked fine.

I am assuming there was some kind of subtle change in gnome or ubuntu that has to do with priority of the $PATH, which suddenly borked my setup. So, yes, it probably was recursion, however, it was my sh script calling itself recursively and had nothing to do with FUSE or gvfs.

That sh script has been there about 6 months, too. :confused:

Aw well, back to work for me... :)

---

