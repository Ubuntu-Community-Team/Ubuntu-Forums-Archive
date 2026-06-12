---
title: "no ctrl alt f1 ubuntu 10.04"
date: 2010-05-03
forum: General Help
---

### Post by BrockStrongo on 2010-05-03
I don't know if anyone else has experienced this, but, after resume from suspend I have no GUI or maybe no GDM , anyway there is nowhere to punch in my login information. I tried ctrl alt f1 to get to a shell and was presented with a flashing cursor and no login option. Ctrl alt f7 brought me back to a login screen, I was able to login, but all my settings had reverted back to the default setup. ie; buttons on left. 
This doesn't happen all the time.

---

### Post by BrockStrongo on 2010-05-09
anyone else had this issue. I am strongly thinking of moving back to karmic.

---

### Post by mynk on 2010-05-12
I am unable to do this either but an additional input -

This works on a desktop machine for me but not on my laptop - Thinkpad T400 (lenovo).

Hope this helps. Would like to see this fixed soon.

thanks,
Mayank

---

### Post by MJalbert on 2010-05-19
Same problem here: Sony Vaio Z520N. Yesterday I've installed it Ubuntu 10.04 then update everything (except video card) and it worked. I've reinstalled Linux today without updating anything and the Ctrl-Alt-F1 does'nt work anymore. My guess would be to update Ubuntu using the "automated updater", reboot, then try again. I will do that tonight.

---

### Post by ahso4271 on 2010-05-22
so any luck?

---

### Post by aliasad20 on 2010-05-28
Hi Guys, 

I also have the same problem. And without this alt+ctrl+F1 - if any hang ups occur - we have to force reboot the system. That's why alt+ctrl+F1 is really essential.

I am using HP Pavilion -DV4 - 2112TX

Thanks 
aliasad20

---

### Post by gherardo on 2010-06-03
It seems that the whole interplay between gdm and virtual terminals is buggy. I have related problems in normal use (no suspend/hibernate).

Hitting Ctrl-Alt-F1 does the right thing, virtual terminal 1 opens in text mode. But then it's impossible to come back to graphical session (virtual terminal 7); it opens the text terminal, complains about

```

(process 348): GLib-WARNING **: getpwuid_r() failed due to unknown user id (0)
                                                                              Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox

```  
followed by some restarting (MTA, sensors... why? They should not depend on the graphical session) marked as [OK], and finally it dies on "Checking Battery". 

I also tried suspend after having read your posts, works fine, back to graphic session; while hibernate breaks the graphic session (Same messages as above).

Lucid Lynx (64bit) downoladed and installed yesterday, not yet updated, toshiba satellite pro U500.

G.







Only way out, Ctrl-Alt_F1 (back to terminal 1) and issue a "restartt gdm".

---

### Post by siloko on 2010-06-16
I'm getting the same thing. CTRL-ALT-F1 takes me to the terminal as expected but then no way to get back to the Desktop. Occasionally CTRL-ALT-F7 starts a NEW Gnome session but with complaints that it can't read user files and screen defs and leaves me with a VGA system. Only solution is a reboot. So have terminals been superseded in 10.04??

---

### Post by raviolli on 2010-06-24
Hi all,  I'm getting the same problem when I press ctrl+alt f1 the only thing that happens if my mouse disappears and nothing works, I can still see my desktop.

To get back to working conditions I press ctrl + alt + f7

---

### Post by manifesto666 on 2010-06-28
Hi,

I got this solution that works for me (asus u30jc).
This is likely to be a pb with you FB resolution.
I give a short explanation how to fix :

apt-get install hwinfo
hwinfo --framebuffer
-> choose the resolution that fit your screen best.
-> take the corresponding vga number from here -> [http://www.pendrivelinux.com/vga-boot-modes-to-set-screen-resolution/](http://www.pendrivelinux.com/vga-boot-modes-to-set-screen-resolution/)

vi /etc/default/grub.cfg and change the variable like that with your vga number (mine is 792)  :
GRUB_CMDLINE_LINUX_DEFAULT="splash vga=792"
Then 
update-grub (this willcreate a new /boot/grub/grub.cfg)
Finally create the file /etc/initramfs-tools/conf.d/splash with the following line :
FRAMEBUFFER=y

save and reboot.
Mine was ok after that.

Hope this helps.

Original post is in french : [http://blog.rom1v.com/2010/05/splash-screen-ubuntu-lucid-lynx-10-04-et-pilote-nvidia-proprietaire/](http://blog.rom1v.com/2010/05/splash-screen-ubuntu-lucid-lynx-10-04-et-pilote-nvidia-proprietaire/)
Report to my blog in french also : [http://systemx.nosuke.org/index.php/post/2010/06/28/Correction-de-affichage-de-boot-et-ctrlaltF1-(tty)-sous-(K)ubunut-10.04](http://systemx.nosuke.org/index.php/post/2010/06/28/Correction-de-affichage-de-boot-et-ctrlaltF1-(tty)-sous-(K)ubunut-10.04)

---

### Post by Jose Catre-Vandis on 2010-07-03
No virtual terminals at all for me on Xubuntu 10.04. The only time I can see a login breifly is if I CTRL+ALT +1 as soon as the login in screen comes up, but then it disappears after about 10 seconds. Using the proprietory nvidia driver. VT's work fine on my karmic installation on the same PC. Tried the fix above, no change. When I try to switch to a vt I first get a black screen, then a blank screen (monitor back light working)

For me, definitely something to do with the nvidia driver. I replaced "nvidia" with "vesa" in the Driver section of my xorg.conf and rebooted. VT's worked as expected. None of the fixes found other than in this thread seem to make any difference. 

I tried [this]("http://ubuntuforums.org/showpost.php?p=9228983&postcount=69") too

here also stuff from dmesg showing uvesafb failing
```
[    2.869424] uvesafb: NVIDIA Corporation, MCP79 Board - mcp7a-e8, Chip Rev   , OEM: NVIDIA, VBE v3.0
[    2.885610] uvesafb: protected mode interface info at c000:cbc0
[    2.885621] uvesafb: pmi: set display start = c00ccc23, set palette = c00ccc7e
[    2.885627] uvesafb: pmi: ports = 3b4 3b5 3ba 3c0 3c1 3c4 3c5 3c6 3c7 3c8 3c9 3cc 3ce 3cf 3d0 3d1 3d2 3d3 3d4 3d5 3da 
[    2.949245] uvesafb: VBIOS/hardware doesn't support DDC transfers
[    2.949252] uvesafb: no monitor limits have been set, default refresh rate will be used
[    2.949480] uvesafb: scrolling: ypan using protected mode interface, yres_virtual=1911
[    2.949490] uvesafb: cannot reserve video memory at 0xf7000000
[    2.949524] uvesafb: probe of uvesafb.0 failed with error -5
```

So how to fix?

Hardware:
Asus EB-1012 eeebox with ION graphics
HANNSG HH241 24" 1920x1080 monitor
"current" nvidia driver from Hardware Drivers

---

### Post by Jose Catre-Vandis on 2010-07-11
bump - anyone any ideas how to fix?

---

### Post by afrodeity on 2010-08-13
I haven't been able to ctrl-alt-F7 back to X/GUI since upgrading to LUCID. Intially after the upgrade I was told to use sudo gdm service start, but this no longer working if I log into any one of the f1-six terminals.

---

### Post by isti37 on 2010-08-17
[http://crunchbanglinux.org/forums/topic/8883/how-to-fix-tty16-ctrlaltfx-terminals-if-they-are-not-working/](http://crunchbanglinux.org/forums/topic/8883/how-to-fix-tty16-ctrlaltfx-terminals-if-they-are-not-working/)

If someone still has problems.

---

### Post by jan.peciva on 2010-10-02
One quick solution that worked for me: The problem disappeared after installing Radeon binary drivers on my laptop (Dell Studio 1558 ). For newbies: Go to Start -> Applications -> System -> Hardware drivers

John

---

### Post by acsmckenzie on 2012-01-31
Just a simple thought, but on a lot of laptop keyboards, the Function Keys F1, F2 ... require that you press the Fn key.  So the full combination is Ctrl Alt Fn +F1.  That's four keys to hold down, not three.

---

### Post by pcardout on 2012-02-03
Manifesto666 had some helpful advice.  I have spent a few hours
solving this problem for myself and investigating the good (and not
so good) advice out on the net.  I am using *Oneiric Ocelot* and I posted on *linuxquestions.org* about what worked for me (and how to figure it out for you.)

In short ... you do some simple magic with your */boot/grub/grub.cfg*
and your virtual terminals all come back!

Here's the whole story:
[http://www.linuxquestions.org/questions/linux-general-1/ctrl-alt-f1-%3D-black-blank-screen-385376/#post4593178](http://www.linuxquestions.org/questions/linux-general-1/ctrl-alt-f1-%3D-black-blank-screen-385376/#post4593178)

---

### Post by oldos2er on 2012-02-03
And with that we will let this old thread go back to sleep. Closed.

---

