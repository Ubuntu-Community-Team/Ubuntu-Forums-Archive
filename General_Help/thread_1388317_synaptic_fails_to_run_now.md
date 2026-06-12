---
title: "synaptic fails to run now"
date: 2010-01-23
forum: General Help
---

### Post by jerome schatten on 2010-01-23
Ubuntu 9.10. System has been running fine for months. Today, tried to run Synaptic and get the following error:  **'Failed to run /usr/bin/synaptic as root - unable to copy the user's Xauthorization file**'

Where invoking synaptic used to ask me for my password, it now gives the above error message.

What I did today was change grub so that I boot to the command line instead of the gui. That worked fine and I can invoke the gui with **startx** as a normal user. 

sudo apt-get works OK from the command line. Can you help me fix this?  

Thanks,
jerome

---

### Post by Tanker Bob on 2010-01-23
Does:

gksu --description /usr/share/applications/synaptic.desktop /usr/sbin/synaptic

work from the terminal? Or simply gksu /usr/sbin/synaptic? Or the Ubuntu Software Center?

---

### Post by jerome schatten on 2010-01-23
> **Tanker Bob said:**
> Does:

gksu --description /usr/share/applications/synaptic.desktop /usr/sbin/synaptic

work from the terminal? Or simply gksu /usr/sbin/synaptic? Or the Ubuntu Software Center?

Here's the terminal output:

[B]orange@orange:~$ gksu --description /usr/share/applications/synaptic.desktop /usr/sbin/synaptic
Error copying '/home/orange/.Xauthority' to '/tmp/libgksu-A2KgZV': Permission denied

orange@orange:~$ gksu /usr/sbin/synaptic
Error copying '/home/orange/.Xauthority' to '/tmp/libgksu-hyG6Dz': Permission denied

[/B]I'm not sure what you mean by the Ubuntu Software Center?

Thanks,
jerome

---

### Post by Tanker Bob on 2010-01-23
> **jerome schatten said:**
> I'm not sure what you mean by the Ubuntu Software Center?

Thanks,
jerome

From the menu, Applications -> Ubuntu Software Center. That's assuming that you're running karmic.

Your error sounds like either you don't have write privileges to /tmp/ or read privileges to /home/orange/.Xauthority . Have you checked their permissions? gksu should give you root access. What happens if you just type gksu in the terminal? You should get a "run program" dialog, from which you should be able to select or type a program and select what user you wish to run it as.

---

### Post by jerome schatten on 2010-01-23
> **Tanker Bob said:**
> From the menu, Applications -> Ubuntu Software Center. That's assuming that you're running karmic.

Your error sounds like either you don't have write privileges to /tmp/ or read privileges to /home/orange/.Xauthority . Have you checked their permissions? gksu should give you root access. What happens if you just type gksu in the terminal? You should get a "run program" dialog, from which you should be able to select or type a program and select what user you wish to run it as.

Yep... running karmic

Running gksu in the terminal with root as user and synaptic, returns exactly the same error as in my initial post. Root has RW priv's for .Xauthority but it is a file of zero bytes.

Here's what /tmp looks like:

orange@orange:~$ cd /tmp
orange@orange:/tmp$ ls -la
total 80
drwxrwxrwt 18 root   root   4096 2010-01-22 21:42 .
drwxr-xr-x 22 root   root   4096 2010-01-08 20:25 ..
drwx------  2 orange orange 4096 2010-01-22 20:52 .esd-1000
drwx------  2 orange orange 4096 2010-01-22 21:31 .exchange-orange
drwxrwxrwt  2 root   root   4096 2010-01-22 20:52 .ICE-unix
drwx------  2 orange orange 4096 2010-01-22 20:52 keyring-GZqgSo
drwx------  2 orange orange 4096 2010-01-22 21:24 libgksu-A2KgZV
drwx------  2 orange orange 4096 2010-01-22 21:22 libgksu-c9wL3b
drwx------  2 orange orange 4096 2010-01-22 21:42 libgksu-ccwq7K
drwx------  2 orange orange 4096 2010-01-22 21:24 libgksu-hyG6Dz
drwx------  2 orange orange 4096 2010-01-22 21:21 libgksu-iRCBsc
drwx------  2 orange orange 4096 2010-01-22 20:52 libgksu-ycR1r5
drwx------  2 orange orange 4096 2010-01-22 21:42 orbit-orange
drwx------  2 root   root   4096 2010-01-22 21:41 orbit-root
drwx------  2 orange orange 4096 2010-01-22 20:52 pulse-p2DtJAnaHFjb
-rw-------  1 orange orange   51 2010-01-22 20:52 serverauth.hdbMrS2By6
drwx------  2 orange orange 4096 2010-01-22 20:52 ssh-mUvGRn1752
drwx------  2 orange orange 4096 2010-01-22 20:52 virtual-orange.m9HCi6
-r--r--r--  1 root   root     11 2010-01-22 20:52 .X0-lock
drwxrwxrwt  2 root   root   4096 2010-01-22 20:52 .X11-unix
orange@orange:/tmp$ 

Thanks for sticking with this...
jerome

---

### Post by Tanker Bob on 2010-01-23
I know this is a dumb question, but is your gui up and running while you're doing this? gksu and Synaptic must be run in the gui.

---

### Post by jerome schatten on 2010-01-23
> **Tanker Bob said:**
> I know this is a dumb question, but is your gui up and running while you're doing this? gksu and Synaptic must be run in the gui.

Not a dumb question at all... but the answer is yes, it's running. Here's what the Xaurthority files in my home directory look like. Are yours zero bytes?

[...]

-rw-------  1 root   root          0 2010-01-20 22:22 .Xauthority
-rw-------  2 orange orange        0 2010-01-22 20:52 .Xauthority-c
-rw-------  2 orange orange        0 2010-01-22 20:52 .Xauthority-l
drwxr-xr-x  2 orange orange     4096 2009-12-04 09:24 .xine
-rw-r--r--  1 orange orange      573 2010-01-13 08:44 .xscreensaver-getimage.cache
-rw-------  1 orange orange    42966 2010-01-22 20:54 .xsession-errors
-rw-------  1 orange orange     7694 2010-01-22 10:24 .xsession-errors.old
orange@orange:~$ 

j.

---

### Post by jerome schatten on 2010-01-23
Just thinking... do you think it's worthwhile putting the system back the way it was: re-editing /etc/default/grub  and running  update-grub to see if the problem goes away?
j.

---

### Post by Tanker Bob on 2010-01-23
I don't have any .Xauthority files in my home directory. Can you run any programs in the gui, like gedit or firefox? I'm starting to wonder if your system is preventing Xserver from opening new objects as if you don't have permissions for the Xserver.

---

### Post by Tanker Bob on 2010-01-23
> **jerome schatten said:**
> Just thinking... do you think it's worthwhile putting the system back the way it was: re-editing /etc/default/grub  and running  update-grub to see if the problem goes away?
j.

Yes. At least your system may work correctly again until you figure out what's going on. What switches are set on the kernel in grub?

---

### Post by king smith on 2010-01-23
I tried running it, but this popped,
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."
what do i need to do? not really sure what this means

---

### Post by jerome schatten on 2010-01-23
I'm beginning to see the problem: I fired up my laptop which also has 9.10 on it, and it doesn't have any Xauthority files either. My bet is that something else has to occur other than changing from
...
GRUB_CMDLINE_LINUX_T='quiet splash'  to 'quiet splash text'.

Some updating of Authorities or stuff I know nothing about. I'll change it back and see what happens.

j.

---

### Post by Tanker Bob on 2010-01-23
That switch may be a general inhibitor of some key gui functions. I've never used it, but there's probably a reference on the net somewhere.

---

### Post by jerome schatten on 2010-01-23
Oh yeah... how do I determine the kernel switches that are set in grub?  Sorry for being so thick, but this probably would have come a bit easier if I was a bit younger -- I'm 72.
j.

---

### Post by lisati on 2010-01-23
> **king smith said:**
> I tried running it, but this popped,
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."
what do i need to do? not really sure what this means

Hijacking threads isn't recommended.
From the terminal:
```
sudo dpkg --configure -a
```

---

### Post by jerome schatten on 2010-01-23
Ah... I see what you mean by kernel switches... here they are:
orange@orange:/etc/default$ cat grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
orange@orange:/etc/default$ 

OK... I'm gonna change it back and at least things should be back to normal. I'll let you know. Thanks for all your help; I learned a bunch, and I'll see what google has to say about that switch.
j.

---

### Post by Tanker Bob on 2010-01-23
> **jerome schatten said:**
> Oh yeah... how do I determine the kernel switches that are set in grub?  Sorry for being so thick, but this probably would have come a bit easier if I was a bit younger -- I'm 72.
j.

There are lines in your menu.lst file that look something like this:

kernel	/boot/vmlinuz-2.6.31-17-generic root=/dev/md0 ro quiet splash 

The first parameter after the kernel image location and name is the root partition - /dev/md0 in this case. Everything after that are the loading switches for the kernel. The kernel is originally compiled with all sorts of switches with which we don't usually play, but some may be set with the kernel command on boot.

I don't think age has anything to do with it. I'm not a teen geek either. When one delves into kernel switches during boot, one enters a rarefied atmosphere.

---

### Post by Tanker Bob on 2010-01-23
Yep, you have it. In your grub file, your default kernel switches are set by this line:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text"

I don't know what "text" does.

---

### Post by jerome schatten on 2010-01-23
OK... back to the way it was, and synaptic works again.  Now I'm back to where I started, looking for a way to boot to the command line and still be able to access the gui with all functions working. Thanks again for your good guidance!
jerome

---

### Post by Tanker Bob on 2010-01-23
You're welcome. I'm glad that you're back to even. I found the kernel manual. The chapter on kernel command line options is in a [pdf here](http://www.kernel.org/pub/linux/kernel/people/gregkh/lkn/lkn_pdf/ch09.pdf). The parameter "text" does not appear in the list. Having in as a default can't be good given that absence.

It was a pleasure working with you. I learned something tonight as well. Almost 2 AM here and time to quit!

jerome - see my next post.

---

### Post by Tanker Bob on 2010-01-23
> **jerome schatten said:**
> Now I'm back to where I started, looking for a way to boot to the command line and still be able to access the gui with all functions working. 

jerome - just boot the recovery mode for your desired kernel in the grub menu on start up. That will give you a text interface from which you can startx and all will work fine. When you end your gui session, you'll be back in the shell. You can make that the default situation in menu.lst if you want by changing the "default 0" line in menu.lst near the top to "default 1" w/o the quotes. 

I was so focused on the presented issue that I forgot your original objective! Sorry...

---

### Post by jerome schatten on 2010-01-23
Thanks Bob for your suggestion about the recovery mode -- that works for me!

I got into this text interface mess working on a project for a friend of mine who has been blind from birth.  I'm trying to make a system with ubuntu in text mode; a screen reader; and a text mode email client.  Been playing with Orca, but I'm afraid tis a work in progress.  Disappointing results.

Hard to believe that over 25 years ago my little Mac+ had a superb screen reader that would have probably worked fine. Technology doth not always march forward methinks! 

Thanks again for all your help...
jerome

---

