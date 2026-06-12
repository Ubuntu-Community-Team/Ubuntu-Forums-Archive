---
title: "Netbook: suggestions for offloading file system to external drive"
date: 2010-06-22
forum: General Help
---

### Post by cheshirekow on 2010-06-22
I have a netbook... I like it. A lot. I'm constantly surprised by how functional it is. I use it mostly for browsing the internet, reading email, and reading PDFs. However, I also use it to do a little hacking when I'm on the airplane or a long car ride, to punch out some updates to LaTeX, watch a movie, listen to some music, etc, etc. 

So the 20GB (actually 4GB + 16GB) solid state drive has become prohibitive, and I picked up a portable USB hard drive for use here. So I'm wondering what is the best way to distribute the file system among these three drives. I will obviously store large media on the portable drive, such as:

Portable Drive:
/home/[me]/Collections/music
/home/[me]/Collections/movies

etc, or else use SD cards (which is what I do now). But what else can I offload onto the hard drive? I would like the netbook to still function without the external harddrive, but maybe just not be able to do some of the rarer activities... like compile code, or latex, or run inkscape or gimp. I.e. It should still be able to run firefox, alpine, evince, vlc and probably a few more things that don't come to mind immediately. My idea is that if I need to do something "quick" or "fun" I can pop open the netbook and do it... but if I'm going to be sitting down somewhere for a while, I can plug the external hard drive in, and then get some real work done.

I don't know the file system well enough, but is it possible to offload all the library headers without offloading all the shared libraries? Is it possible to change where packages are installed when using synaptic? If so, can I "move" a package that is already installed? Should I mount certain paths of the file system on the external drive, or should I create a parallel file system on the external drive and then just add them all to the path environment variable?

Please help! I'm ignorant :(.

P.S. I'm currently using xubuntu 9.10, but this question I think is sufficiently general that it shouldn't matter.

---

### Post by cheshirekow on 2010-06-26
I may have almost found a solution to this problem, but I'm having a little trouble testing it out and I lack the knowledge to complete the solution. My idea is to use a combination of unionfs-fuse and schroot. 

0. second drive mounted to media/two
1. create a fakeroot directory, something like /fakeroot
2. use unionfs to union bin, etc, home, lib, opt, usr, var from / and /media/two into /fakeroot
3. create symbolic links to everything else, i.e. media, mount, proc, sys, et. cetera
4. schroot into /fakeroot

Then the system apparent to the current user will be a union of the file system on the main drive and on the unioned external drive.

So here are the things I don't know: 

1. I can't seem to get schroot to work outside of using debootstrap to create a chroot of an entire distribution. I keep getting 

```

user@host:~/test$ schroot -c union -d .
W: Shell ‘/bin/bash’ not available: /bin/bash: Failed to stat file: No such file or directory
W: Falling back to shell ‘/bin/sh’
E: Failed to execute “/bin/sh”: No such file or directory

```

This is the block from /etc/schroot/schroot.conf

```

[union]
description=Symlinked and Unioned FS
directory=/home/user/
users=user
groups=user
root-groups=root
root-users=root

```

I can't find good documentation on what should really be in this file, every schroot info page I find on google only uses it with debootstrap, and I got that to work so I can't tell what I'm doing wrong. (note, "user" is a place holder for my actual user name).


2. Is it possible to change the configuration for a local user so that he logs in with the desktop and everything running from inside the schroot? How do I create / configure a user to login in this manner?

---

### Post by colorlessprism on 2010-06-26
You could try Remastersys. It allows you to create an installable LiveCD of your current setup. Its not entirely what you are looking for but i think it is a simpler solution for you.

[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

a guide I made can be found here:
[http://ubuntuforums.org/showthread.php?t=1514043](http://ubuntuforums.org/showthread.php?t=1514043)

---

### Post by cheshirekow on 2010-06-26
Thanks for the suggestion, I will look into it.

---

### Post by cheshirekow on 2010-06-26
Upate: 

Ok. Things seem to have worked out so far. This is my fstab:

```

unionfs-fuse#/mnt/slow/bin=RW:/bin=RO   /chroot/bin     fuse    cow,allow_other     0   0
/boot           /chroot/boot        none    bind            0       0
/cdrom          /chroot/cdrom       none    bind            0       0
/dev            /chroot/dev         none    bind            0       0
unionfs-fuse#/mnt/slow/etc=RW:/etc=RO   /chroot/etc     fuse    cow,allow_other     0   0
unionfs-fuse#/mnt/slow/home=RW:/home=RO /chroot/home    fuse    cow,allow_other     0   0
unionfs-fuse#/mnt/slow/lib=RW:/lib=RO   /chroot/lib     fuse    cow,allow_other     0   0
/lost+found     /chroot/lost+found  none    bind            0       0
/media          /chroot/media       none    bind            0       0
/mnt            /chroot/mnt         none    bind            0       0
unionfs-fuse#/mnt/slow/opt=RW:/opt=RO   /chroot/opt     fuse    cow,allow_other     0   0
/proc           /chroot/proc        none    bind            0       0
/root           /chroot/root        none    bind            0       0
unionfs-fuse#/mnt/slow/sbin=RW:/sbin=RO /chroot/sbin    fuse    cow,allow_other     0   0
/selinux        /chroot/selinux     none    bind            0       0
/srv            /chroot/srv         none    bind            0       0
/sys            /chroot/sys         none    bind            0       0
/tmp            /chroot/tmp         none    bind            0       0
unionfs-fuse#/mnt/slow/usr=RW:/usr=RO   /chroot/usr     fuse    cow,allow_other     0   0
unionfs-fuse#/mnt/slow/var=RW:/var=RO   /chroot/var     fuse    cow,allow_other     0   0

```

And here's my schroot.conf

```

[union]
description=Ubuntu hardy
directory=/chroot
priority=3
users=user
groups=user
root-groups=root

```

I can chroot into the unioned file system with the following

```

dchroot -c union

```

And things look pretty good. The only thing left is: is there a way to edit the local user login so that when I log in on the machine the system is rooted at /chroot instead of at /? There has to be a way to dchroot the user right?

---

### Post by cheshirekow on 2010-06-27
So I've played around some more. I can start a graphics application from within the chroot if I start an Xserver 

```

user@host:~$ Xnest -ac : 1

``` 

and then exporting the following when I log to the chroot

```

user@host:~$ dchroot -c testunion
user@host:~$ export DISPLAY=localhost:1
user@host:~$ firefox

``` 

Works as expected. Starting Xnest opens a new xwindow and starting firefox in the chroot starts firefox in that new x window. It's my understanding I can also start a desktop manaager in the Xnest. Now what I really want to do is get the *main login* to occur in the chroot. I think what this means is that I want gdm to do something different. So here's my new question(s):

How do I configure gdm to log the user into the chroot?
How do I configure the XServer so that xfce can run inside the chroot?
How do I run a xfce session inside the chroot?

---

