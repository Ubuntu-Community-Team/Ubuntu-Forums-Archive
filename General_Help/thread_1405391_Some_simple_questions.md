---
title: "Some simple questions"
date: 2010-02-12
forum: General Help
---

### Post by munitor on 2010-02-12
Trying to do a few simple things and though I've searched quite a bit, the answers I've found seem so cumbersome that I figure I must be wrong. So looking for some expert advice on the simple way to do things.

1. Make a disk image of my 9.10 system (formatted ext3, btw) on my Syology CS407 NAS so I can do a bare metal restore. Why is this a couple of clicks on my Mac and Windows boxes, but so far not easy on Jaunty? Did I miss something?

2. Drivers. Why can't I just have an automatic wrapper for Windows drivers so I can use any printer or scanner, or a simple point and click driver install for native drivers? I have my ethernet connected Brother MFC-7820N, and the Samsung CLP-315 that runs off my CS407 installed and working on my Jaunty, but it was way more work than expected. What is the easy, automatic or point and click way to install drivers?

3. Graphics drivers. I have decent cards in my big boxes, Nvidia GTX 200 series. But when I get kernel updates, I have to uninstall and reinstall the graphics driver. Is there an easy way to keep this working?

4. Is there one flavor of linux distro that has a really consistent standard for user interface? I like to be able move things around, but do like my menus to be consistent (and do I ever hate the MS ribbon!). I've really only tried Ubuntu.

Linux installs have come a long, long way from the old days, and are such a point and click operation that I just wonder what I'm doing wrong. Someone is bound to have sorted these things.

Thanks

---

### Post by tgalati4 on 2010-02-12
3.  If you are using the proprietary nvidia drivers, then yes, you will have to reinstall the drivers with each kernel upgrade.  Nvidia drivers are binary "blobs" and are not open source.  To work properly, they need to be hooked into the kernel.  Every time you upgrade the kernel, you need to rehook the proprietary drivers to the kernel.

4.  For a standard user interface, you have a choice of desktop environments:  GNOME, KDE, XFCE, Fluxbox, etc.  When you stick with GNOME for instance, it will have a nearly-consistent interface, regardless of what distro you are running.

The fact that all linux destop environments are heavily customizable means that each installation will look and feel different--even though they may all be using GNOME.

There was a distro called Linspire (formerly known as Lindows) that tried to create a consistent (and more Windows-like) environment.

Combine the some 26K packages available means that certain applications won't look consistent in your chosen environment.  For instance you can run KDE applicaitions in GNOME (such as k3b), but they don't pick up the GNOME color scheme.

Linux Mint is a distro that has a more-consistent theme, but as soon as you start to customize it and add applications, your system will look more disorganized.

If you want consistency, then try the Mac OS X.

---

### Post by jken146 on 2010-02-12
Backups:
[https://help.ubuntu.com/9.10/serverguide/C/backups.html](https://help.ubuntu.com/9.10/serverguide/C/backups.html)
[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

---

### Post by gordintoronto on 2010-02-12
1. Remastersys.

2. I've installed a networked Brother laser by point-and-click, but I don't remember the details.  Somewhere, I found a "printers" program.

3.  I installed the nVidia driver through Administration/Hardware Drivers, and I have never had to do anything when a new kernel arrived.  (This is exactly the opposite of what Tgalati4 said above...)

4.  When there are thousands of *volunteer* programmers developing software, it's no wonder they don't all follow the same user interface standards.  I happen to like GIMP and Cinelerra, but many people think they have horrid user interfaces.

---

### Post by munitor on 2010-02-13
Thanks for the answers. The ubuntu user community is always helpful.

WRT the nvidia drivers, I use the ones from nvidia rather than the ones that are packaged by ubuntu because I had some weird problems with the packaged ones (they were too old), so that's where the binary blob comes in. I suppose I'll just have to script automatic uninstall/reinstall if it becomes too much of a hassle. I wonder if now that Win 7 has started to get a bit more like linux (you don't want the Microsoft maintained drivers for nvidia cards, either) then system suppliers will handle all the upgrades for their machines, the way we are seeing netbooks that run linux handle things. That would definitely work for laptop makers, but be a stretch for desktop machines where users sometimes upgrade video cards (but little else).

Bacula, Remastersys, Partimage, are things I've looked at/tried and weren't very friendly. I tried a newer version of Clonezilla today and it seems to have worked okay and was fairly easy to use. Still could have used a simple point and click interface for newbies, though. Most of the folks I'd like to suggest linux for wouldn't know an IP address from a street address, but can point and click through a network map to the folder where they want to store disk images.

Indeed OS X is the gold standard for UI nazis, though it has it's own baggage. I had my first mac in 1985 and was astonished that in 2010 it still acts like all monitors are 9" and driven by a pocket calculator. I have to admit, though, that I installed cinelerra and uninstalled it fairly quickly - didn't like the interface. Maybe I'm too picky.

For myself, I think I'll stick to gnome apps, but maybe I'll muck around with Mint and see if that is a good choice for newbies. 

Thanks again for the advice.

---

### Post by LoneWolfJack on 2010-02-13
#2

a) because most drivers aren't open source, so we can't adapt them
b) because that "wrapper" would basically mean re-implementing windows on linux... the wine guys have been working on that for what... 15 or 20 years?

---

### Post by colobix on 2010-02-13
1. Remastersys is the answer my friend.
This thing works like a charm and you can take both distro or private iso backups of your system. The private backup includes your home folder.
This program makes a live/installation cd for you automaticly.
[http://scumbox.com/ubuntu/remastersys_2.0-5_all.deb](http://scumbox.com/ubuntu/remastersys_2.0-5_all.deb)

---

### Post by munitor on 2010-02-13
> **colobix said:**
> 1. Remastersys is the answer...

except, according to the remastersys site, it skips proprietary packages like nvidia drivers. I want bare metal backup to previous state. If I'm not mistaken, the current version supports grub2.

---

### Post by munitor on 2010-02-13
> **LoneWolfJack said:**
> #2

a) because most drivers aren't open source, so we can't adapt them
b) because that "wrapper" would basically mean re-implementing windows on linux... the wine guys have been working on that for what... 15 or 20 years?

a) If I understand it right, they do get packaged and supported as third party proprietary. I thought those did automatic updating for kernel changes, but not sure. The fact that it often runs several versions behind the current version on nvidia's site is the problem I ran into, because the "stable" one was v173, whilst nvidia's was v190 and actually worked correctly with my cards.
b) I hear you. But why is installing a driver on linux such a pain sometimes, even if you have a hardware vendor supplied linux driver? MS Windows does a great job managing this. 

Seems to me it's about time for a standardised, newbie friendly approach. System vendors can manage internal hardware driver updates in a newbie friendly fashion, but they can't manage the peripherals users hook to their systems.

---

### Post by jken146 on 2010-02-13
Well, you *could* always tarball the whole file system and save it somewhere separate. Then restoring it is as simple as unpacking the archive over the top of whatever's there. (see the link to the serverguide I posted above)

---

### Post by munitor on 2010-02-14
> **jken146 said:**
> Then restoring it is as simple as unpacking the archive over the top of whatever's there.
If I'm not mistaken, I'd still need to partition, format and set mount points before unpacking the tarball, which isn't quite bare metal but close.

I'm going to try the tarball as a back up to clonezilla, and test my clonezilla restore to see if it works as advertised (it claimed to be saving mbr and everything else!).

On printer installs, not much joy there unless the peripheral is really common. I don't see an automated ndiswrapper version of that any time soon.

On the nvidia binary driver front, that should be scriptable so that a new kernel does an uninstall/reinstall. I'm willing to try that.

WRT user interface standards, I'll give up on that. If MS can foist the Fluent interface on the world's businesses and not go down in flames, I suppose anything is possible and permitted.

---

### Post by tgalati4 on 2010-02-14
I can do a Mint install in 20 minutes.  It would take longer to do a bare-metal restore.  Therefore, I only backup my /home directories.  If the OS gets trashed (which is rare in linux) then I simply reload it from scratch and copy over the /home directory.

If you come from a Windows background, you tend to want to do a complete backup because reinstalling Windows and all of the applications can be a pain and very time consuming.

In linux, you acquire a different mindset.  All of your data is in open formats and any linux distro can open your files.  No need to load a bunch of proprietary applications to get access to your data.

---

