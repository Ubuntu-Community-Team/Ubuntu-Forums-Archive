---
title: "Webcam is not working in Skype"
date: 2011-08-12
forum: General Help
---

### Post by Rushyang on 2011-08-12
Hey guys, 

I am having this problem since the day I upgraded ubuntu from 10.04 to 10.10. Couldn't solve it then and now I would like to try again.

>> Webcam is working fine in Cheese Webcam Booth.

But it's not detected in skype. I tried this command 

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```>> I didn't work as last time. Error Messages of it on terminal is as under:

> ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

(<unknown>:2778 ): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:2778 ): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:2778 ): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:2778 ): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:2778 ): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:2778 ): Gtk-WARNING **: Loading IM context type 'ibus' failedIf it helps, 
1) uname -a  
> Linux NattyNarwal 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux2) skype beta Version 2.2.025 is installed.

Please someone help me out.

---

### Post by Dragonbite on 2011-08-12
In my Ubuntu 10.04 installation my webcam worked fine (without the LD_PRELOAD command) until I updated Skype. Now it doesn't work.

In Fedora it works, but only when I use the LD_PRELOAD command.  I am not sure if it is the older version or the newer version at this moment.

Try getting your hands on an older version of Skype and see if that works?

Since mine was working and now isn't and the only thing that really changed was the Skype version, I would try testing that theory out.

---

### Post by Rushyang on 2011-08-12
I get it what you're trying to say. Thanks for suggestion. But I can't find a way to downgrade skype. 
I opened synaptic package manager and there are only 2 versions available. Mine is the oldest and other one is 2.2.0.35-0maverick.

Any way how to do it?

---

### Post by Dragonbite on 2011-08-12
I'll have to see if I have the installer for the older version lying around in one of my computers.

I usually get it from the Skype website. I thought the piece included in the repositories was kinda like a wrapper, or for integrating it with the message center, etc.

My Dropbox and UbuntuOne doesn't have it, but I'm not surprised I haven't been synchronizing them (figured I would download the latest if I needed it).

---

### Post by Rushyang on 2011-08-15
I upgraded to most latest version. Doesn't work on that either

---

### Post by Dragonbite on 2011-08-15
So far, haven't found an old install tarball file yet.  Frustrating.

---

### Post by nanoktom on 2011-10-15
Had the same problem with my very antique Creative Labs webcam (Model PD0040).
Made it work with the following command line:

```
bash -c 'LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype'
```This line is valid for Ubuntu 11.10 (yep, early adopter).

I believe that the path to v4lcompat.so in previous versions of ubuntu was different, but can't check this because I only have 11.10 now.

The error message: "ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored." is caused by an incorrect path to v4lcompat.so and I can easily reproduce it.

I hope this helps!

Cheers

---

### Post by luarwo on 2011-10-16
> **nanoktom said:**
> Had the same problem with my very antique Creative Labs webcam (Model PD0040).
Made it work with the following command line:

```
bash -c 'LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype'
```This line is valid for Ubuntu 11.10 (yep, early adopter).

I believe that the path to v4lcompat.so in previous versions of ubuntu was different, but can't check this because I only have 11.10 now.

The error message: "ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored." is caused by an incorrect path to v4lcompat.so and I can easily reproduce it.

I hope this helps!

Cheers

I upgraded to 11.10, and my Logitech quickcam v11.1 stopped working with skype, this solved it. Great! Cheers

---

### Post by mosquetero on 2012-03-24
Hi everyone, I am having the same problem. If I execute

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

Then it works (throwing a couple of errors in the console). How can I create a script so that everytime I click on Skype it uses this command and so the webcam works?

Thank you

---

### Post by gordintoronto on 2012-03-24
Run Preferences/Main Menu and edit the command.

---

