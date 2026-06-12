---
title: "SOS! GRUB loads shell and not menu! SOS!!!"
date: 2009-11-03
forum: General Help
---

### Post by gnomeout on 2009-11-03
OK so I have 9.10 installed and it has been running fine ever since the beta was released, this included a working install of "grub1.97beta4"

recently my grub has just stopped working. now instead of a nice menu where I can select between ubuntu and windows I get a "minimal" grub shell and I cant boot anything!!!


the screen just shows
"sh:grub>"

when I tried to do "find /boot/grub/stage1" the find function was not available.

I then tried booting a live cd and running "sudo grub"
and then "find /boot/grub/stage1" and this time it returns "Error 15: File not found"

so I am stuck now. 

Grub super boot cd also could not fix this problem, although it did install LILO and now my windows boots automatically(no menu to select linux though). 


SO I need to either fix grub, and remove LILO, or get LILO working for my linux partitions..

Please help, this is urgent as I need to get this computer running for my work. 

kthxbye

---

### Post by ranch hand on 2009-11-03
You need to rescue grub from a LiveCD.

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

You should look at the link in my sig.  There is some good info there and a lot of links to in depth info.

---

### Post by donaldt on 2009-11-04
what do I do with error 21 that won't go away?  I have repeatedly used a live CD to get access and run sudo grub.  Find /boot/grub/stage1 brings up hd1,4   This has never changed.  I then do the root    setup    and   quit.  I get the message "Succeeded".

When I re-boot I still get <GRUB loading, please wait...error 21>

What am I missing?

I upgraded my 9.04 to 9.10, but still have the legacy grub.  I checked  (-v) and it verified this.  I'm in never never land and can't get out...

Thanks

donaldt

---

### Post by ranch hand on 2009-11-04
> **donaldt said:**
> what do I do with error 21 that won't go away?  I have repeatedly used a live CD to get access and run sudo grub.  Find /boot/grub/stage1 brings up hd1,4   This has never changed.  I then do the root    setup    and   quit.  I get the message "Succeeded".

When I re-boot I still get <GRUB loading, please wait...error 21>

What am I missing?

I upgraded my 9.04 to 9.10, but still have the legacy grub.  I checked  (-v) and it verified this.  I'm in never never land and can't get out...

Thanks

donaldt
And people ask why I don't like upgrading.

There are LOT of changes between 9.04 and 9.10.  Grub is one of them.  On the upgrade you stayed with grub-legacy.  You also have a lot of grub2 on there and grub has probably confused itself.

Your best bet is to go back in and remove grub and grub-common and then reinstall them (clean start) and run the command you did before to set it up.  Those commands need to be run from the LiveCD not chrooted into your  installed system.

---

### Post by gnomeout on 2009-11-04
that sounds like a very different error, perhaps you should google further, I feel like ive seen it elsewhere.

---

### Post by gnomeout on 2009-11-04
> **ranch hand said:**
> You need to rescue grub from a LiveCD.

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

You should look at the link in my sig.  There is some good info there and a lot of links to in depth info.

this sounds promising since it seems to be doing more than the basic steps, one question though. Will it also remove this LILO?

---

### Post by ranch hand on 2009-11-04
I do not think that it will but you could do a more complete chroot and do that.  I have no idea why you would have that on your box.  Neat.

The only purpose of that set of directions is to rescue grub2 when it has been hosed in some way.

Be a lot easier to get rid on lilo when you get back into your OS.

---

### Post by gnomeout on 2009-11-04
> **ranch hand said:**
> I do not think that it will but you could do a more complete chroot and do that.  I have no idea why you would have that on your box.  Neat.

The only purpose of that set of directions is to rescue grub2 when it has been hosed in some way.

Be a lot easier to get rid on lilo when you get back into your OS.

Yeah I followed your instructions, worked like a charm, LILO appears to have disappeard, which is good enough for me, I am going to hope that the "grub-install" overwrites the master boot record entirely, which would thoroughly remove LILO. either way it works now. 

only I have a new issue, in that something is causing my computer to have serious difficulty loading, which in turn destroys grub all over again. 

elaboration:
when my computer goes to log in(automatically) my desktop never loads and the screen stays black usually except the mouse, which i can move. 
I then try crtl+alt+backspace to restart X. What happens next is interesting.

first the mouse disappears, as it normally would when one presses that key combination, but then the screen stays black for a long time, and then it goes back to the ubuntu loading screen, the one with the logo and the loading bar that is before login even loads! I have no idea how it goes back to this. anyway sometimes it will actually come back to my login screen and i can even login, but not much else. And usually it doesnt even get there. when I inevitably restart, my grub is broken again.

one possible solution seems to be to rename my home folder. This causes a new default folder to load and it seems to login smoothly. This is a major bummer though. but so far it seems my only solution is to do this, and then hopefully copy back most of my hidden config files. 

my only recent activity is that yesterday I installed Avant window navigator(AWN). But this seemed to work fine and my computer restarted with ease several times after this though. although it wasnt till this morning that it tried booting with it starting on login(before i had manually started it) this resulted in some strange taskbar behaviour(didnt load my session manager). 2 restarts later grub was broken. although im definitely not 100% convinced this is the entire issue.


**UPDATE**
I have tried this approach and after copying all of the essential program folders, such as .mozilla, .kde, .gconf, etc.... this was done in batches, and it slowed significantly after the second batch and didnt make it past the third. At no point did AWN come into play, so that cant be it. a more serious issue is brewing i feel.

---

### Post by ranch hand on 2009-11-04
You better start a new thread  on this problem.  It sounds very strange to me.

---

### Post by sparvik on 2009-11-04
HHD Self Test?

---

### Post by donaldt on 2009-11-04
> **ranch hand said:**
> And people ask why I don't like upgrading.

There are LOT of changes between 9.04 and 9.10.  Grub is one of them.  On the upgrade you stayed with grub-legacy.  You also have a lot of grub2 on there and grub has probably confused itself.

Your best bet is to go back in and remove grub and grub-common and then reinstall them (clean start) and run the command you did before to set it up.  Those commands need to be run from the LiveCD not chrooted into your  installed system.

Thank you for the advice.  I'm sorry, but I will need some hand holding to accomplish what you suggest.  I have no Ubuntu support locally here in NM.  I'm comfortable in terminal, but don't know how to remove grub and re-install.

Any help will be appreciated.

donaldt

---

### Post by ranch hand on 2009-11-04
Well, I think we can do this.  How ever, I have been a member of these forums all of 4-5 months longer than you have.  I am a noob.

I believe I know how to do this but never have.  So it will be a bit before I start you on this.  I am going to install 9.04 on my test platform and do it first to make sure I do not hose things.

This will require the use of the command -rm and that can really screw things.  I want to make sure that I understand all I know before inflicting it on you.

I will be back in a while.

---

### Post by ranch hand on 2009-11-04
Well, that went as slick as grass through a goose.

Boot to your LiveCD and pull up gparted (may be listed ans partition editor).

Label your / partition.  It is just easier if you do this.  Label it something short (3 to five letters).

Pull up the terminal and, in order, one at a time;
```

sudo mkdir /mnt/karmic
sudo mount /dev/sdb1 /mnt/karmic/
sudo mount -o bind /proc /mnt/karmic/proc
sudo mount -o bind /dev /mnt/karmic/dev
sudo mount -o bind /dev/pts /mnt/karmic/dev/pts
sudo mount -o bind /sys /mnt/karmic/sys
sudo cp /etc/resolv.conf /mnt/karmic/etc/resolve.conf
sudo chroot /mnt/karmic /bin/bash
sudo dhclient wlan0(or eth0) 


```You need to replace "karmic" with what you labeled you / partition.  In the second command you also need to replace the "sda5" with the correct partition for your box.


You also need to edit the last line to reflect how you connect to the net.

You should now have a root terminal with an internet connection.

Do, in this order;
```

apt-get update
apt-get remove grub grub-common grub-pc
apt-get install grub grub-common

```That last command will install grub-legacy.  If you want grub2 (I would, I like it a bunch) change the "grub" to "grub-pc".
One advantage to installing grub2 is that it will set itself up and be ready to boot when you are finished with those commands.

There is a group of commands for leaving chroot.  From the LiveCD I ignore them and just drop the terminal and reboot.

---

### Post by gnomeout on 2009-11-04
> **sparvik said:**
> HHD Self Test?
not too sure how to run exactly what youre talking about, but i have run e2fsck and it has found errors, but fixed them(and re-ran error free) and my issues persist.

i might start a new thread, but i think its just gotten to the point where i am just going to clean install and be done with it.

on a side note, the fast-user-switch-applet seems to be causing some of my home loading issues. computer now boots regularly but super super slow to load, but got mildly faster when i got rid of this applet which kept producing an error.

---

### Post by ranch hand on 2009-11-04
I think this is fixable but I think a clean install, at least of this version, is a good idea anyway.

Back up your data and save it for your new 9.10.

---

### Post by donaldt on 2009-11-05
Ranch Hand,

Thanks for the effort.  I was not able to solve the problem.  Grub error 21 was prior to the boot sequence.  I could not regain Vista, even using a repair disk, for the same reason.  Error 21 (I'm guessing?) must have infected the registry in Vista.

I took the portable computer to the local "windows" repair store.  They tried everything they could do, but were unable to get to a boot capability.  The solution will be to copy the hard drive and then re-load Vista.  I have a back-up, so will recover most of my programs.  Loss of use, plus a few hundred dollars, is the fallout from this adventure.

Question, however, is can I afford to continue to fool with Ubuntu if it is going to destroy my portable (used in my business)?  Even using an external hard drive did not prevent Ubuntu from eventually killing the computer.  I guess it was my fault for upgrading from 9.04 to 9.10 so soon.  But when Canonical announces a new release is ready, can we believe it is really ready for prime time?  It doesn't seem so.

I still have the 9.10 system on the same external hard drive and may try to access it through a small Fujitsu (sunlight readable) note book I use for FAA approach charts in the cockpit of my aircraft.  If it gets contaminated, I can take the time to re-load and restore it myself.

My plan would be to reload the 9.04 iteration (which worked good for 8 months) and wait for any upgrade until wiser heads than mine report it is safe.  Any other ideas or suggestions (anyone??) would be welcome.

Thanks to all,

donaldt

---

### Post by ranch hand on 2009-11-05
If 9.04 works I would use it.

I would not be fooling around with a box I use for navigation.

---

### Post by ST3ALTHPSYCH0 on 2009-11-05
@ Donaldt
[This](http://prdownload.berlios.de/supergrub/super_grub_disk_0.9799.iso) would have at least allowed you to repair your Windows MBR. Sorry I didn't see this sooner.

---

