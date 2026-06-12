---
title: "Uninstalled xserver-xorg-video-nv, need to reinstall!"
date: 2009-10-10
forum: General Help
---

### Post by Gunnder on 2009-10-10
I did the ultimate goober move and uninstalled xserver-xorg-video-nv through the synaptic package manager.  How can I re-install this through the command line or from the live cd so my screen/graphics will work again?  

Note: nothing else tampered with, live cd works great, can not boot up in safe mode.  Can boot up so i have command line.

thanks...

---

### Post by rippin on 2009-10-10
> **Gunnder said:**
> I did the ultimate goober move and uninstalled xserver-xorg-video-nv through the synaptic package manager.  How can I re-install this through the command line or from the live cd so my screen/graphics will work again?  

Note: nothing else tampered with, live cd works great, can not boot up in safe mode.  Can boot up so i have command line.

thanks...


sudo apt-get install xserver-xorg-video-nv

---

### Post by Gunnder on 2009-10-10
Thanks for the Help, though I am getting an error message (error 27: unrecognized command), I have access to the grub command line from boot up, what do I need to do to install this from here.  Sorry for being such a retard on this. =)

---

### Post by MaxIBoy on 2009-10-10
The grub command line isn't a way to control Ubuntu, it's a way to control Grub. Grub is a seperate program which lets you choose which Operating System to boot-- you can't control an OS which isn't booted yet.

If you try to boot into Ubuntu, and you get an error message, then after that message try hitting alt+f2 to take you to another [virtual terminal.](http://en.wikipedia.org/wiki/Pseudo_terminal) From there, you can log into your account in full text mode (no graphics) and run the command suggested above.

(Interesting history but not important: It's called a virtual terminal or pseudo terminal, because in the ancient days of history, the terminal was a seperate device from the computer-- when computers themselves got screens and keyboards, a "virtual" terminal was one that didn't exist as a seperate device but was instead "emulated.")

---

### Post by Gunnder on 2009-10-10
Ok, tried this, but got no response.  When I boot into Ubuntu, my screen does not function, just a bunch of lines (been this way since I uninstalled the above! don't ask me why I tried to this!).  Is there another way to boot into the command line?

---

### Post by MaxIBoy on 2009-10-10
As in, your display is glitchy?

If you have set a root password (i.e. if you have ever used "su" instead of "sudo",) you can boot into single-user mode, which can also be called recovery mode or similar. Enter your root password (if there is a menu, you select something like "root console," can't remember the name exactly.) You now have root access to the system-- just fix your problem using that command.

If you have not set a root password, there is still an easy way. Boot from a live CD. Find the name of the mount-point of the partition where Ubuntu is installed (say, for example, /media/disk.) Assuming it's /media/disk, you can then pull up a terminal within the liveCD and type "sudo chroot /media/disk". LiveCDs do not have a password set so you can just hit enter when it asks for one. After that, your live CD is pretending that it is your normal Ubuntu installation (more precisely, it's pretending that your Ubuntu root partition is the liveCD's root partition.) You now have root access to your Ubuntu system, and again you can fix your problem using that command. More information about the chroot command: [http://en.wikipedia.org/wiki/Chroot](http://en.wikipedia.org/wiki/Chroot)


This also demonstrates how frail the security is in ANY operating system if you have access to the physical computer-- insert a liveCD, reboot, and the system is yours. I always set my BIOS to not boot the liveCD by default, and I also have a BIOS password.

---

### Post by Gunnder on 2009-10-10
Thank you very much,  I'm doing this right now and will post my results.  Thanks about the security also,  I have a hd password and a boot password (from bios) set up on my computer.  

Thanks!

---

### Post by Gunnder on 2009-10-11
Ok,
I made it into the root and installed the apt I needed.  Unfortunately this did not help my video problem.  Once I boot up Ubuntu (9.04) The screen is just lines.  It flickers 3 times like it is trying to adjust the graphics or something then just stays with Ubuntu in the middle of the screen smeared across.

I can not figure out what else I can do since I have email and other information that I did not back up yet (like a dummy).  

The only thing I did was to unistall the xserver-xorg-video-nv apt.  

I installed it using the command sudo apt-get install xserver-xorg-video-nv from the root command prompt from the safe boot option.

I've got a bottle of glue ready to go to glue my hair back in once I get this working again! I've just about pulled it all out!

---

### Post by rippin on 2009-10-11
> **Gunnder said:**
> Ok,
I made it into the root and installed the apt I needed.  Unfortunately this did not help my video problem.  Once I boot up Ubuntu (9.04) The screen is just lines.  It flickers 3 times like it is trying to adjust the graphics or something then just stays with Ubuntu in the middle of the screen smeared across.

I can not figure out what else I can do since I have email and other information that I did not back up yet (like a dummy).  

The only thing I did was to unistall the xserver-xorg-video-nv apt.  

I installed it using the command sudo apt-get install xserver-xorg-video-nv from the root command prompt from the safe boot option.

I've got a bottle of glue ready to go to glue my hair back in once I get this working again! I've just about pulled it all out!

No, don't freak. This ain't Windows ... we have more choices than patience. And, when problem solving, patience is a valuable tool!

If there is one, rename or move any /etc/X11/xorg.conf. Should there not be a xorg.conf,  do "apt-get install xorg" as from where/how you did the first attempted repair. If that's borked, boot a liveCD and copy your data to a USB stick or don't format that partition and re-install. BUT, if that partition is all ONE, next install set /home on it's own to avoid that problem. Example (my scheme):

 /dev/sda1            /boot
/dev/sda2            swap
/dev/sda3             /
/dev/sda4            /home

---

### Post by MaxIBoy on 2009-10-11
Agree with above, except that I think reinstalling is cheating.

---

### Post by Gunnder on 2009-10-11
Thanks to all of you!

I am backing up all my old info, and will try the fixes.  If it does not go well I will cheat (re-install but separate things like you said!

This is a huge learning cure from the windows nightmare, but it is fun and Linux/Ubuntu actually makes sense and makes a computer a tool that you can use.

Ubuntu (put very simply) is like a shovel, it is an awesome tool you can use to create/shape the ground you stand on how ever you can dream/imagine.
Windows is just the hole in the ground, one size fits all and if it is not the type of hole you were looking for to build your dream out of they expect you to fit your needs to their ideas.  Hmmm, sounds kinda red army to me.

---

