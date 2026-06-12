---
title: "Ubuntu keeps freezing completely"
date: 2009-10-03
forum: General Help
---

### Post by azurfire on 2009-10-03
Ubuntu keeps freezing on my desktop computer. It locks up completely - the mouse stops moving, I can't use Ctrl-Alt-F1, etc. I have to restart it with the power button.

-It just froze 4 times in the past 10 minutes (though usually it does not freeze this frequently)
-Sometimes it happens when I log in, before I even see the desktop
-Nothing appears in kern.log
-Current temperatures are CPU:44 Celsius, GPU:71 Celsius
-The last time it froze, I was only running Terminal, GEdit, and Firefox
-This is a fresh install, that was done with WUBI. (note that I have previously had it installed without WUBI, and still had the freezing problem)

-Some stats:
Release 9.04 (jaunty)
Linux ubuntu 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux
GNOME 2.26.1

Memory: 3.2 GB
Processor: Intel Core 2 CPU 6420 @ 2.13GHz
GPU: Nvidia GeForce 8600 GTS

So does anyone know what may be causing this? Is there any additional information I could provide that would help?

Thanks.

---

### Post by user333 on 2009-10-03
I was going to say get a better graphics card, but you have the same one as me! And you have no lack of memo

---

### Post by scragar on 2009-10-03
You'll find logs in /var/log
If you could copy say the last 20 lines or so of each of these to pastebin it would help: kernel.log1 errors.log1 Xorg.0.log.old
Alternatively run this:
```
sudo tail /var/log/{kernel.log1,errors.log1,Xorg.0.log.old}
```
And copy the output to pastebin. [http://pastebin.com/](http://pastebin.com/)

---

### Post by azurfire on 2009-10-03
kernel.log1 and errors.log1 do not seem to exist in /var/log/.

So here is the entire Xorg.0.log.old:
[http://pastebin.com/m73d116c4](http://pastebin.com/m73d116c4)

I might have restarted since the most recent freeze (can't remember), if that affects anything.

---

### Post by moster on 2009-10-03
I would check my computer for hardware errors first, then look further.

Insert Ubuntu startup cd and in startup menu select "check my computer" or similar I do not remember exactly. It will run some test in loop and you leave it alone for about 30 min or so. 5 minute will not do it. If there is no errors.

If there is no errors consider upgrading kernel.

---

### Post by scragar on 2009-10-03
Interesting, from what I've read it might be releated to how you log on, could you try something for me, reboot and press escape to show the grub menu if it isn't there by default, press **e** to edit the ubuntu line, **e** again on the line that starts *kernel*, at the end insert a space and 3, then press enter followed by **b** to boot.
Log in on the command line, then type```
startx
```To load the gui like normal.

I would be interested to see if that stops the crashes or not.

---

### Post by 2roombas on 2009-10-03
> **azurfire said:**
> Ubuntu keeps freezing on my desktop computer. It locks up completely - the mouse stops moving, I can't use Ctrl-Alt-F1, etc. I have to restart it with the power button.

-Some stats:
Release 9.04 (jaunty)
Linux ubuntu 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux
GNOME 2.26.1

Memory: 3.2 GB
Processor: Intel Core 2 CPU 6420 @ 2.13GHz
GPU: Nvidia GeForce 8600 GTS

So does anyone know what may be causing this? Is there any additional information I could provide that would help?

Thanks.

I've been having the very same problem all morning here. It froze about 8 times in the last half hour. Not fun! It only freezes when I use Firefox though. I used Kmymoney for almost an hour today with no problem.

I upgraded to the beta Karmic last night on my desktop (the comp with that the freeze problem). I had no trouble using it last night but after a synaptic update this morning it now keeps freezing.  My desktop is an old Dimension 2350 tho, so I'm thinking maybe that Firefox 3.5 just doesn't play nice with those old dinosaur comps. :(

---

### Post by azurfire on 2009-10-03
@scragar
So I pressed escape after selecting Ubuntu from the Windows boot loader, and I got the GRUB screen. So at the top is "Ubuntu 9.01, Kernel 2.6.28-15-generic". So I press 'e', and I get another screen, where I select "kernel /boot/vmlinuz-2.6.28-15-generic ..." and press 'e'. So then I get another screen where I place ' 3' at the end of the line so it looks like "<D86A8DAE9 loop=/ubuntu/diskcs/root.disk ro quiet splash 3", and then I press enter and boot it.

So it boots, and I get to the login screen, and that didn't look any different (was it supposed to?) You said log in to the command line, so I was thinking that maybe I needed to set session to 'Failsafe Terminal'? So I started to move my mouse to select 'Failsafe Terminal', and then it froze. -_-;

@2roombas
Except firefox can't be my problem, because sometimes it crashes before it even finishes loading the desktop, and it just crashed before I started to login.

@moster
Maybe later I can go burn a disc and do the hardware check

---

### Post by scragar on 2009-10-03
> **azurfire said:**
> @scragar
So I pressed escape after selecting Ubuntu from the Windows boot loader, and I got the GRUB screen. So at the top is "Ubuntu 9.01, Kernel 2.6.28-15-generic". So I press 'e', and I get another screen, where I select "kernel /boot/vmlinuz-2.6.28-15-generic ..." and press 'e'. So then I get another screen where I place ' 3' at the end of the line so it looks like "<D86A8DAE9 loop=/ubuntu/diskcs/root.disk ro quiet splash 3", and then I press enter and boot it.

So it boots, and I get to the login screen, and that didn't look any different (was it supposed to?) You said log in to the command line, so I was thinking that maybe I needed to set session to 'Failsafe Terminal'? So I started to move my mouse to select 'Failsafe Terminal', and then it froze. -_-;

It's not a failsafe at all, it's just the terminal, one of the more common causes of the problem you reported was with GDM crashing, it's possible to start your desktop without GDM by logging in on the command line, I figured it was worth a try since it's only a temporary change, all settings go back to normal when you reboot(graphical log in).
Actually, it was supposed to look different though, like this:
[http://crazytoon.com/wp-content/uploads/2008/04/centos_default_login_prompt-300x74.png](http://crazytoon.com/wp-content/uploads/2008/04/centos_default_login_prompt-300x74.png)
Although obviously it talks about ubuntu rather than CentOS.

---

### Post by azurfire on 2009-10-03
'Failsafe Terminal' is just what I see when I select 'Change Session' or whatever. So since it crashed before I even logged in, that means that GDM crashing is not the problem?

[EDIT]
Nope, I didn't see that when I tried. Did I not edit it correctly? I just saw the normal login screen, with the large Ubuntu logo.

---

### Post by azurfire on 2009-10-03
@moster
So I'm guessing you were talking about memtest? I just ran that and it didn't find any problems.

Any other ideas?

Thanks.

---

### Post by moster on 2009-10-04
> **azurfire said:**
> @moster
So I'm guessing you were talking about memtest? I just ran that and it didn't find any problems.

Any other ideas?

Thanks.

Try installing newer kernel. If you decide to do that here is how.

This is last one 2.6.31. It worth a try because lot of people have problems with jaunty. Uninstall vga drivers before this, after, you will have to manually install new one.

1. download and install this: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.1/linux-headers-2.6.31-02063101_2.6.31-02063101_all.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.1/linux-headers-2.6.31-02063101_2.6.31-02063101_all.deb")

2. then this: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.1/linux-headers-2.6.31-02063101-generic_2.6.31-02063101_i386.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.1/linux-headers-2.6.31-02063101-generic_2.6.31-02063101_i386.deb")

3. then this: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.1/linux-image-2.6.31-02063101-generic_2.6.31-02063101_i386.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.1/linux-image-2.6.31-02063101-generic_2.6.31-02063101_i386.deb")

4. Done! restart and select new kernel at startup. 

5. Install nvidia vga drivers by adding repos, complete guide is **[HERE]("http://webupd8.blogspot.com/2009/08/how-to-install-nvidia-190xx-drivers-in.html")**.

---

### Post by azurfire on 2009-10-04
@moster
Thanks, that seems to have fixed it.

---

