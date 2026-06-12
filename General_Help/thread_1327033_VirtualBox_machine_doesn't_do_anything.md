---
title: "VirtualBox machine doesn't do anything"
date: 2009-11-15
forum: General Help
---

### Post by oospill on 2009-11-15
hello, I just installed virtualbox .. even with a walkthrough on a webpage.  I swear I did everything right.  I set up a new machine with 1024MB RAM, and a 20GB space of harddrive.  I set it to boot from the CDROM first.  with a windows XP disk in the drive, I started the virtual machine.  it just sits there, blank screen.  the CD spins up for a few seconds and then stops.

anyone have any ideas?

---

### Post by MaxIBoy on 2009-11-15
How does the CD/DVD ROM dialog look? It should be set to "host CD/DVD drive" if you want to use the drive in your actual computer (and if you have more than one drive, you need to pick the right one.) See screenshot...


If you want to use an ISO select that option and then the file (but of course you don't have an ISO for Windows, right? ;))

---

### Post by nikgare on 2009-11-15
Whcih walkthrough on which webpage?

---

### Post by oospill on 2009-11-15
well.. I'm 99.9% sure I got the cdrom setup just fine.  when I 'start' my virtual machine, the little (you know) black screen pops up, and the CDROM starts spinning, making me think it's about to say "Press any key to boot from CD-ROM..." .. but alas, after about 20 seconds the cdrom powers down and my VM just sits there.

ARGH!

[hey you make it sound bad to have ISO's.] [jk]

maxiboy: what theme are you using?  that looks pretty slick!!

---

### Post by oospill on 2009-11-15
nik gar: which walkthrough .. lemme see.. [http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html](http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html)

---

### Post by steveneddy on 2009-11-15
> **oospill said:**
> hello, I just installed virtualbox .. even with a walkthrough on a webpage.  I swear I did everything right.  I set up a new machine with 1024MB RAM, and a 20GB space of harddrive.  I set it to boot from the CDROM first.  with a windows XP disk in the drive, I started the virtual machine.  it just sits there, blank screen.  the CD spins up for a few seconds and then stops.

anyone have any ideas?

How much RAM is actually installed on the PC that you are running the VM on?

You must use much less RAM on the VM than the actual PC has installed. If you have 1 GB RAM on the machine, tel the VM to run on 256 mb RAM. If you have 2 GB RAM, try bumping the VM ram down to 768.

Make sure that under Settings that you have the CD/DVD drive to mount for the VM.

Is the Windows CD you are trying to boot a good CD?

---

### Post by steveneddy on 2009-11-15
> **oospill said:**
> 

maxiboy: what theme are you using?  that looks pretty slick!!

Looks like 

[SlicknesS_black]("http://gnome-look.org/content/show.php/Slickness+Black?content=73210")

Everyone has DLed it because of the geeky Linux girl on You Tube.

[http://www.youtube.com/watch?v=gl-tmGfQrzs](http://www.youtube.com/watch?v=gl-tmGfQrzs)

---

### Post by oospill on 2009-11-15
well, I've got 3GB RAM on this laptop..  I enabled virtual machines in the BIOS, and I enabled root and myself in the virtualbox user group.

yes, the Windows cd is good.. it tries to boot when I start up my laptop.  but it doesn't do anything but spin when I try to 'bootup' my virtual machine.

I'm gonna go ahead and try to find a different windows disk..

thanks to all for any input.

---

### Post by nikgare on 2009-11-15
Did you tell your virtual machine to boot from the cd?

---

### Post by steveneddy on 2009-11-15
> **oospill said:**
> well, I've got 3GB RAM on this laptop..  I enabled virtual machines in the BIOS, and I enabled root and myself in the virtualbox user group.

yes, the Windows cd is good.. it tries to boot when I start up my laptop.  but it doesn't do anything but spin when I try to 'bootup' my virtual machine.

I'm gonna go ahead and try to find a different windows disk..

thanks to all for any input.

OK - did you make sure that the CD drive was mounted? - see my first post on this thread and attached pic.

---

### Post by oospill on 2009-11-15
well, I got it working.  I had tried using the version found in synaptic.  SO, I uninstalled that, and installed the .DEB for my version of Ubuntu found on the virtualbox website.

I set everything up the same..  but now it works.  weird.

I love to hate it when that happens.

ah well.

goodnite!

---

### Post by MaxIBoy on 2009-11-15
Run this command:
```
lsmod | grep vbox
```

The results should be roughly similar to this:
```
~$lsmod | grep vbox
vboxnetadp             77184  0 
vboxnetflt             83665  0 
vboxdrv               118920  1 vboxnetflt

```

Those are the virtualbox kernel modules, and Vbox will do nothing if one of these is missing. (I doubt that's the problem though, usually there's actually an error message if one is missing.)


Things to try:

[LIST=1]
[*]Boot the VM with a Linux CD instead.
[*]Boot the VM from a Linux ISO.
[/LIST]



> **steveneddy said:**
> Looks like 

[SlicknesS_black]("http://gnome-look.org/content/show.php/Slickness+Black?content=73210")

Everyone has DLed it because of the geeky Linux girl on You Tube.

[http://www.youtube.com/watch?v=gl-tmGfQrzs](http://www.youtube.com/watch?v=gl-tmGfQrzs)
Damn good guess! I had just installed Debian about four months ago, and I was looking for a dark theme on gnome-look. Saw it, installed it, been happy with it since. Although I've been thinking about going back to playbill...

---

### Post by tipiglen on 2009-12-05
I'm having similar problems.  

I'm trying to get either an xp or preferably a karmic guest set up on a karmic host.  I've tried the appropriate VirtualBox from the website, which gave the problem noted:

Everything goes fine in setting up 512Mb 'base memory' (2G onboard)
dynamic virtual hd, etc.

I then get it to mount the karmic iso from my host hd (as a floppy image), and it no longer says "no bootable medium", says "running" and just sits there....

Same behaviour with the virtualbox-ose from synaptic....

Of course, I don't have a windoze iso, but I do have the 'recovery' file stashed in the 'PE' parttition as supplied with the netbook.

Any ideas or suggestions welcome.

Thanks in advance
ed

---

### Post by rturner on 2009-12-05
I don't know if this is the problem, but I have vbox set up from synaptic and I always point the boot disk to cdrom, not floppy.  If the iso is on my hd, that's where I point to as "cdrom".  I change it to the actual cdrom location if I need that.  When you mouse over the little cd image at the bottom of vbox, it shows the path of what you're using.  I set up mint8 and a windows7 rc that way.  One uses a path to the iso, the other uses my actual cdrom drive.

---

### Post by tipiglen on 2009-12-05
That seems to have sorted it.  Thanks.

The virtual 'full screen' ain't too big, and I get a warning that I should change to a 32bit colour display, but there doesn't seem to be anywhere to do that within unr...

Seems to work fine with firefox so far.

---

