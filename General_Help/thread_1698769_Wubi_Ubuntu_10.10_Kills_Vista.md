---
title: "Wubi Ubuntu 10.10 Kills Vista"
date: 2011-03-02
forum: General Help
---

### Post by PouletEnFeu on 2011-03-02
Hi, I downloaded Ubuntu about a month ago, and have had to do dell factory restore twice in order for windows to also work on the same hard drive ( ubuntu installed in vista). I'm pleased with it, although I need windows working for work and other things I can't do on ubuntu. 
    This morning I turned on pc, selected Vista 64bit SP2, logged into windows, and immediately a error pops up saying I have registry problems or something and should reinstall windows,then immediately logs me out and shuts down the computer. Afterwards I went to the computer repair thing by pressing f8 at startup and chose the dell image restore- i wait a bit and i get an empty error message. I have tried all of the other options also and they have not helped. Basically what I need is How do i get rid of ubuntu and fix vista without having to reinstall it? If no solutions are known, what are some ways I can fix this with uninstalling or whatever need be. Thanks, Pouletenfeu-

Stats:
XPS M1530 4gb ram 500gb SATA HDD nvidia 9600M gt graphics
Ubuntu 10.10 wubi
windows vista 64 bit sp2
:confused:

---

### Post by sanderd17 on 2011-03-03
With reinstalling, it is simple.

Ask a repair disk from dell and install vista from the cd and afterwards ubuntu the normal way (not via wubi).

If you want to do it without reinstall, you need to access windows to fix this. To access Linux you could use a live CD, but MS doesn't give us the option. So I don't know how you could do this.

---

### Post by oliwek on 2011-03-03
Download and burn Ultimate Boot CD, it has all you need to repair boot issues : [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)
;)

edit : **Vista recovery disc** is downloadable from there : [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

just reboot with this disc and choose to repair the boot issue...

the problem with the "official MS repair method" (the easier one) is : you wont have access to ubuntu anymore, so ideally you should repair/edit grub or use another graphical boot manager compatible with both vista and linux. 

What you can do : **restore the windows boot with this vista recovery cd, then boot vista, install EasyBCD** : this software lets you graphically edit your multiboot options from within windows.
download EasyBCD here : [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

there are tutos on the net, for example : [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by Mark Phelps on 2011-03-03
Since you installed Ubuntu via Wubi, the F8 Dell restore SHOULD have worked (you didn't change the partition arrangement).  Don't know why it didn't.

The Vista Recovery CD should repair your Vista boot, but may have to run it as many as three times.  It's not very smart and only finds and repairs one problem at a time.

Also, if you keep having to do a clean restore of your Dell, something basic is wrong with it.  You should contact Dell (if the PC is still under warranty) and see what they will do for you.

P.S. I know the Dell restore DOES work because I recently did that for a client and it restored their PC to its original state.

---

### Post by donkyhotay on 2011-03-03
> **Mark Phelps said:**
> Since you installed Ubuntu via Wubi, the F8 Dell restore SHOULD have worked (you didn't change the partition arrangement).  Don't know why it didn't.


WUBI replaces the default (windows) boot manager with GRUB so that it's possible to boot into linux. Those recovery systems require the original windows boot manager to boot into them since they're basically just a watered down verzion of windows on a seperate partition with no other purpose then repair/reinstallation. You'd have to manually configure GRUB to recognize the recovery partition in order to use it (don't know how myself). Even if you do that the "press F# key for recovery" won't work as you do it through GRUB. It's still there, technically still works, just can't boot into it.

---

