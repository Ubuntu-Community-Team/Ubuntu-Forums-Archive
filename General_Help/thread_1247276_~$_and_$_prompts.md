---
title: "~$ and /$ prompts"
date: 2009-08-22
forum: General Help
---

### Post by scar1 on 2009-08-22
Hi,

I am a new user of Ubuntu and linux/unix in general, so I consider myself a noob!
Quick question, currently I getting used to navigate my system in terminal, however cannot seem to grasp the concept below

____________________________________________________
**user@linuxsystem:~$ ls**
Application  Desktop    examples.desktop  Pictures  Templates  Videos
Appz         Documents  Music             Public    testdir
[B]user@linuxsystem:~$ cd /
user@linuxsystem:/$ ls[/B]
bin    dev   initrd.img      lib32       media  proc  selinux  tmp  vmlinuz
boot   etc   initrd.img.old  lib64       mnt    root  srv      usr  vmlinuz.old
cdrom  home  lib             lost+found  opt    sbin  sys      var
_____________________________________________________

Why is there a difference when listing files (ls command) at a **~$ **and**/$ **prompts?
what do they signify? 

Thanks in advance for your help.

Thanks
Steve

---

### Post by Rocket2DMn on 2009-08-22
The ~ symbol represents your home directory which is really /home/yourusernamehere
Whenever you use the ~ symbol, it is the same as putting in /home/yourusernamehere.

The / is the root of the filesystem, so when you are at "/" then you are at the highest level of the file system structure.  In *nix, we mount devices somewhere on the filesystem rather than at a drive letter.  So your external flash drive might go to /media/disk when you plug it in, rather than getting assigned a drive letter.

These are directories in the root of the filesystem: (sort of like the C: drive in Windows):
> bin dev initrd.img lib32 media proc selinux tmp vmlinuz
boot etc initrd.img.old lib64 mnt root srv usr vmlinuz.old
cdrom home lib lost+found opt sbin sys var

---

### Post by Post Monkeh on 2009-08-22
~ is basically a shortened form of /home/your-user-name

it is your own home folder where all your own personal files go.


/ is known as root. it is the "top level" of your file system - something like c: in windows, except EVERYTHING is sorted somewhere under / in linux. where in windows you could have a c: and a d: and an e:, in linux, your drives and partitions are all mounted somewhere within the main file system. for instance, where on windows your cd might be d: or e:, on linux, your cd can be found in, for instance, /media/cdrom0)

---

### Post by slakkie on 2009-08-22
/ is the root file system

~ is your $HOME, aka home dir

You could compare it to / being C: and ~ to My Documents on Windows.

Have a look at the following document, where it is explained in detailed.
[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/)

---

### Post by michy99 on 2009-08-22
The prompt is made up of several parts.

First, your username. Then @. Then the name of the computer. Then :

After the : is the directory you are in.

In the first example, you are in ~, which is a shortcut for your home directory.

In the second example, you are in /, which is the root of the whole filesystem. (Not to be confused with /root, which is root's home directory.

After the current directory is either $ (if you are a regular user) or # (if you are root).

---

### Post by scar1 on 2009-08-22
Thanks all for these explanations! 
Much appreciated..

Cheers
Steve

---

