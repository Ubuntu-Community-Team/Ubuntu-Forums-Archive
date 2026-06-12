---
title: "kubuntu dapper wont boot correctly"
date: 2006-04-27
forum: General Help
---

### Post by Gorgazm on 2006-04-27
Ive got it working on my computer but when my cousin tried loading it onto his computer witht he same disk, the installation went smoothly. He boot sup, selects the version from the loader (still shows his xp/2k as wella s the recovery mode and memory test). When it is highlighted and you hit enter, it loads normally, showing the kubuntu logo, a progress bar, and the things being checked underneath. after that it flashes some command prompt and then shows a black screen with the kubuntu logo and a progress bar but nothing happens after that. any ideas? asus p4s800-mx mobo, p4 2.0ghz oc'd to 2.4, 768mb ram (512 and 256), maxtor harddrives (60 gig master/primary and 80 gig slave/secondary, which kubuntu and windows are installed on. wondows boots, kubuntu dapper does not.

---

### Post by Gijith on 2006-04-27
I ran into the same thing (is this a common bug?). What video card are you using? For whatever reason, my problem was fixed by ctrl+alt+F1 at that screen, logging in at the prompt, and then:

```
 sudo apt-get install nvidia-glx
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable
```

Hopefully, that will work for you.

If this is a common bug, it's a pretty major one!

---

### Post by Gorgazm on 2006-04-27
i'll try that in a second, but currently it's running on an agp radeon 9550 256mb with omega drivers (atleast through windows, which software overclocked the gpu slightly)

---

### Post by Gorgazm on 2006-04-27
well, the alt+control+f1 did get me into the login screen, but after that i have no idea what to do. any script to have it boot into the desktop from that point? fex the possible issue with my graphics card? could it have something to do with my wireless network pci card? should i try hooking up the monitor to the onboard graphics port as opposed to the card? (I'd say try another card but I dont have any on me here, they're all being used or being borrowed)

---

### Post by Gorgazm on 2006-04-28
1. ffxi money is gil, not isk
2. that doesnt help me at all, whatsoever
3. you should be banned for coming into a technical support forum and trying to become a rpg money maker
4. Learn english, it nice that you tried, but its not so nice that you were taught by a monkey
5. i still need help... I'm not too good with any kind of scripting so I basically have no idea whatsoever of wat to do in command promt after I log in.

---

### Post by Gijith on 2006-04-28
what happened when you tried what I posted?

---

### Post by Gorgazm on 2006-04-28
basically the splash screen went away, the login came up (a command line login, not a graphical one) which then kicked me into command prompt, at which point i didn't know what to do so I rebooted into winxp and came here

(im going to try using the onboard graphics driver, it seems that it may be the cause of this particular problem somehow)

---

### Post by Gijith on 2006-04-28
you logged in and typed in those lines I posted?

---

### Post by jecos on 2006-04-29
This is just an issue with the installer not setting the correct display driver to allow it to login to the desktop (dapper is still Beta).

You need to install the ati drivers **Not the Nvidia drivers!**

when you are in a command prompt (like) login .  login 
and type
if you have an intel cpu
**"sudo apt-get install xorg-driver-fglrx linux-686"**
or if you have an amd cpu
**"sudo apt-get install xorg-driver-fglrx linux-k7"**
then type 
**"sudo aticonfig --initial"**
and
[B]"sudo aticonfig --ovt=Xv"
[/B]
now reboot

---

### Post by Gorgazm on 2006-05-04
well i just got the ubuntu and that worked, im kinda not in the mood to do command prompt to make it boot, i kinda just wanted a load and use distro for my internet applications (and to make use of some usb devices that windows doesnt seem to like)

---

