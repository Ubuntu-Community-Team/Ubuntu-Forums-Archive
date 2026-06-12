---
title: "No Plymouth Boot screen after upgrade to 11.04"
date: 2011-04-29
forum: General Help
---

### Post by timgood on 2011-04-29
Following upgrade, I get no bootscreen on startup, just a black screen. On shutdown, I get the regular Plymouth screen.

Using NVidia proprietary drivers. Any idea on how I can get Plymouth back to normal?

---

### Post by FokkerCharlie on 2011-04-29
I'm also seeing this.  There was a workaround for 10.10, but I'm not at all sure that it still works.  I also thought that it had been fixed before Natty was released, see:

[http://ubuntuforums.org/showthread.php?p=10665319](http://ubuntuforums.org/showthread.php?p=10665319)

However, I still have an ugly boot sequence!

---

### Post by legendryrdx on 2011-04-29
I am also facing the same problem :(

---

### Post by ibootindos on 2011-04-29
I alos did the upgrade, now when I try to boot up it just says 

plymouth main process (53) killed by segv signal. 

and below that it reads

plymouth-splash main process (175) terminated with status 2. 

what the fudge batman?

---

### Post by legendryrdx on 2011-04-30
Apart from the above problem.
My PC is taking 10-15 secs for logging in.
Are you guys also facing similar problem ?

---

### Post by NoNameWill on 2011-04-30
The boot screen is black and a little slow to get to login in. When I shutdown I get Plymouth not mounted. It also shows root logged in.

---

### Post by Naglfar.90 on 2011-04-30
> **timgood said:**
> Following upgrade, I get no bootscreen on startup, just a black screen. On shutdown, I get the regular Plymouth screen.

Using NVidia proprietary drivers. Any idea on how I can get Plymouth back to normal?

I was having a black screen, and then a flash of plymouth at the end of the startup.

Fixed it doing:

```
sudo -s
echo FRAMEBUFFER=y >>/etc/initramfs-tools/conf.d/splash
update-initramfs -u
```
[http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html)


But may be your problem is different since you don't see plymouth at all.

---

### Post by timgood on 2011-04-30
> **Naglfar.90 said:**
> I was having a black screen, and then a flash of plymouth at the end of the startup.

Fixed it doing:

```
sudo -s
echo FRAMEBUFFER=y >>/etc/initramfs-tools/conf.d/splash
update-initramfs -u
```
[http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html)


But may be your problem is different since you don't see plymouth at all.

Indeed - I have tried this and also all the online solutions for fixing ugly boot. But I have a brief flash of purple and then a black screen, nothing more. Funny that shutdown seems to work OK.

I'm also experiencing some problems with random freezing of the Launcher and System Tray which is fixed by a restart. Conky works OK though. Weird. I might bite the bullet and go for a complete new install and see if that changes anything.

---

### Post by daxino on 2011-04-30
> **timgood said:**
> Following upgrade, I get no bootscreen on startup, just a black screen. On shutdown, I get the regular Plymouth screen.

Using NVidia proprietary drivers. Any idea on how I can get Plymouth back to normal?

I solved the problem in my case using the "StartUp-Manager" application i found in the "Software Center". First i suggest to undo all the stuff done with this

[http://ubuntuguide.net/ubuntu-10-10-fix-the-screen-messed-up-at-start-up-and-shutdown](http://ubuntuguide.net/ubuntu-10-10-fix-the-screen-messed-up-at-start-up-and-shutdown)

Then find your current resolution and color-depth (in my case 1024x768 - 24bit). Open "StartUp-Manager" and set in "Boot options" the right resolution and color depth. Select the option "Show boot splash" and deselect "Show text during boot". Under "Arvanced" I have the setting 640x480 for the Bootloader. However this option seems to be not-working in my case. To get a 640x480 boot-loader screen i have to uncomment the line

[COLOR=red]GRUB_GFXMODE=640x480

[/COLOR]In the preceeding guide.

:D

P.S. My Nvidia GeForce Go 7400 was blacklisted for using Unity interface. In solved this problem following this
[http://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity](http://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity)

P.P.S. Sorry for my bad english-speaking!

---

### Post by timgood on 2011-04-30
Many thanks for this! Worked for me.

---

### Post by tom957 on 2011-04-30
> **daxino said:**
> I solved the problem in my case using the "StartUp-Manager" application i found in the "Software Center". First i suggest to undo all the stuff done with this

[http://ubuntuguide.net/ubuntu-10-10-fix-the-screen-messed-up-at-start-up-and-shutdown](http://ubuntuguide.net/ubuntu-10-10-fix-the-screen-messed-up-at-start-up-and-shutdown)

Then find your current resolution and color-depth (in my case 1024x768 - 24bit). Open "StartUp-Manager" and set in "Boot options" the right resolution and color depth. Select the option "Show boot splash" and deselect "Show text during boot". Under "Arvanced" I have the setting 640x480 for the Bootloader. However this option seems to be not-working in my case. To get a 640x480 boot-loader screen i have to uncomment the line

[COLOR=red]GRUB_GFXMODE=640x480

[/COLOR]In the preceeding guide.

:D

P.S. My Nvidia GeForce Go 7400 was blacklisted for using Unity interface. In solved this problem following this
[http://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity](http://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity)

P.P.S. Sorry for my bad english-speaking!

That worked for me too. Your English is great BTW. Thanks!

---

### Post by legendryrdx on 2011-05-01
Works for me as well :)

---

### Post by piotrekkr on 2011-05-01
I have same problem with no bootsplash but only a blue screen until login screen. I've yesterday upgraded to 11.04. In 10.10 I had some issues with 1920x1200 resolution but fixed them. But I can't fix them in 11.04.I've tried [this]("http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/") solution but no effect.

What to do if I don't have correct resolution listed in startup manager. My native resolution is 1900x1200 (it worked in 10.10 after changing some config settings). I have only:

```

1600x1200
1280x1024
1024x768
800x600
640x480

```

I've noticed that startup manager ads "vga=xxx" to /etc/default/grub and updates it. But there is no vga mode for 19200x1200x24 :(

Maby I should do same thing I did in 10.10. That time i found [this]("http://www.sucka.net/2010/03/nvidia-drivers-ubuntu-10-04-lucid-lynx/") solution to work. But as I found out that gfxpayload is depreciated...

Thx for help.

Sorry for my  poor english.

//EDIT
[This]("http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/") solution actually works but my GRUB was adding strange kernel param on boot:
```
vt.handoff=7
```

It was in /etc/grub.d/10_linux  around line 67.

```

for word in $GRUB_CMDLINE_LINUX_DEFAULT; do
  if [ "$word" = splash ]; then
    GRUB_CMDLINE_LINUX_DEFAULT="$GRUB_CMDLINE_LINUX_DEFAULT vt.handoff=7"
  fi
done

```

and I changed it like that:

```

for word in $GRUB_CMDLINE_LINUX_DEFAULT; do
  if [ "$word" = splash ]; then
    GRUB_CMDLINE_LINUX_DEFAULT="$GRUB_CMDLINE_LINUX_DEFAULT"
  fi
done

```
It works now.

---

### Post by Dominator008 on 2011-05-01
> **piotrekkr said:**
> I have same problem with no bootsplash but only a blue screen until login screen. I've yesterday upgraded to 11.04. In 10.10 I had some issues with 1920x1200 resolution but fixed them. But I can't fix them in 11.04.I've tried [this]("http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/") solution but no effect.

What to do if I don't have correct resolution listed in startup manager. My native resolution is 1900x1200 (it worked in 10.10 after changing some config settings). I have only:

```

1600x1200
1280x1024
1024x768
800x600
640x480

```I've noticed that startup manager ads "vga=xxx" to /etc/default/grub and updates it. But there is no vga mode for 19200x1200x24 :(

Maby I should do same thing I did in 10.10. That time i found [this]("http://www.sucka.net/2010/03/nvidia-drivers-ubuntu-10-04-lucid-lynx/") solution to work. But as I found out that gfxpayload is depreciated...

Thx for help.

Sorry for my  poor english.

//EDIT
[This]("http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/") solution actually works but my GRUB was adding strange kernel param on boot:
```
vt.handoff=7
```It was in /etc/grub.d/10_linux  around line 67.

```

for word in $GRUB_CMDLINE_LINUX_DEFAULT; do
  if [ "$word" = splash ]; then
    GRUB_CMDLINE_LINUX_DEFAULT="$GRUB_CMDLINE_LINUX_DEFAULT vt.handoff=7"
  fi
done

```and I changed it like that:

```

for word in $GRUB_CMDLINE_LINUX_DEFAULT; do
  if [ "$word" = splash ]; then
    GRUB_CMDLINE_LINUX_DEFAULT="$GRUB_CMDLINE_LINUX_DEFAULT"
  fi
done

```It works now.

That "vt.handoff=7" thing IS the culprit. I just kept the settings from 10.04 and 10.10 following [this]("http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/") solution, deleted the "vt.handoff=7" from /etc/grub.d/10_linux, did a "sudo update-grub2", and my hi-resolution boot splash is back! Thanks piotrekkr!

---

### Post by Oldster on 2011-05-10
Thanks piotrekkr! Worked for me as well.

---

### Post by jemofthewest on 2011-05-12
Thanks!  As a side note, plymouth manager might be better instead of startup manager... so happy to finally get this working :-)

---

