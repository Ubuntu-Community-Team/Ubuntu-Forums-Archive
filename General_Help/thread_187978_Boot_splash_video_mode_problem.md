---
title: "Boot splash video mode problem"
date: 2006-06-03
forum: General Help
---

### Post by Terminus on 2006-06-03
Hi, I am a recent convert to Ubuntu (pending my approval of GIMP anyways)
Best distro I have used so far (beating SUSE and FC)!

The only gripe I have (and it's really minor) is with the boot-up splash. I quite like it, but for some reason, it has stopped displaying.

I have a widescreen LCD monitor (Dell 2005FPW), and the boot splash used to display in an odd format (narrower than normal, as opposed to my expected wider-than-normal on a wide-aspect screen). After installing the ATI Fglrx drivers, my monitor says "2. DVI: Mode Cannot Be Displayed" on a black screen during boot-up, and it's rather annoying. The OSD menu suggests it's at a resolution of "NTSC 60hz" which is quite odd.

It might be related to the TV-Out on my video card (Radeon 9800 Pro), but I like using it, since I often watch DVDs and TV shows on my pc, via my TV.

Is there any way to change the resolution of the boot-up sequence?
I am using verbose mode (text-only) right now, but I like the graphical boot-screen better for it's summarized view of the boot process beneath the progress bar.

Or any other solutions you can think of?

Thanks for your help!

---

### Post by Terminus on 2006-06-03
Nobody?

---

### Post by blackjack6.21.91 on 2006-06-03
Wow.. Umm you might want to check and make sure that the boot splash image still exists, and I think there are a number of programs that help you manage the start-up process.  Sorry I can't be more helpful..

---

### Post by traherom on 2006-06-03
Did it just stop or has it never worked on this laptop? It sounds to me like it has just stopped working, in which case I really have no idea beyond blackjack's suggestions. *shrug*

---

### Post by Terminus on 2006-06-03
It was working before, and it's a desktop PC.   I'm pretty sure the image still exists, since I havn't changed anything related to the boot sequence. 
Where would it be stored, however, so I can make sure?

I think the problem is that boot process has started occuring in a strange resolution that my LCD won't display. (NTSC is a TV standard?)

And where can I find a program to manage the boot-up?

---

### Post by givré on 2006-06-03
Try to reinstall grub : 
```
sudo grub-install
```
If it is not working you will probably have to put an option to your kernel line to get it working (for some people adding vga=792 do it work).

But reinstall grub first

---

### Post by Terminus on 2006-06-03
Grub seems to be working fine.. I'm hesitant to mess with boot-related things, since I have an oh-so-delicate-seeming ntfs partition with info i'd really rather not lose.

I came across this [bug]("https://launchpad.net/distros/ubuntu/+source/usplash/+bug/27837"), and people on the wiki seem to suggest using vga=773, or regenerating the initramfs:
```
sudo dpkg-reconfigure linux-image-$(uname -r)
```

I am at work now, but I will try all 4 options when I get home.

---

### Post by Gondar on 2006-06-03
I have the exact same problem with the exact same card. I have noticed that I only get a black screen during boot/shutdown if I have my card connected to the tv. Try booting without it connected and see if it "solves" your problem.

If I boot Windows on my machine with my tv connected I see the Windows boot screen display, but in an odd format aswell. Makes me wonder.... 

I don't have a solution for this, but at least now you know that you are not alone :P I suppose you could remove the splash?

---

### Post by givré on 2006-06-03
I found that post where you could find the different vga option you could have. [http://www.ubuntuforums.org/showthread.php?t=180977](http://www.ubuntuforums.org/showthread.php?t=180977)

---

### Post by jjpertusch on 2006-06-04
as an added comment, I have the exact same setup (monitor and video card using DVI) and i had the same problem.  for kicks I plugged my regular VGA cable  and switched inputs and the splash screen was visible.  I switched back to DVI and the same display error message came up.

so basically, its a problem with DVI.  i haven't tried anything suggested in the thread yet, but at least this helps narrow it down.

---

