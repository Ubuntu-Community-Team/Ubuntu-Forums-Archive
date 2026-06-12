---
title: "sparc64 Sun Ultra 10 Good ISO?"
date: 2006-04-15
forum: General Help
---

### Post by chris_andrew on 2006-04-15
Hi,

I am yet to be able to get past "Booting Linux", with the Dapper images. Can anybody tell me whether they have managed to do an install of Ubuntu (any release), on an Ultra 10.  I am unable to do a netowk/ TFTP install.  I will have to rely on a boot disk and the internet.

Hope this helps.

Many thanks,

Chris.

---

### Post by jworr on 2006-04-15
I could be wrong, but I don't think ubuntu has a binary iso ported to the SPARC architechure.  I know debian does so you might look there.  You could also try compile the source cd for SPARC

---

### Post by chris_andrew on 2006-04-15
jworr,

Thanks for your reply.  I have tried the current Etch release, but this is it's status:

[http://release.debian.org/etch_arch_qualify.html](http://release.debian.org/etch_arch_qualify.html)

Also, Ubuntu do do a release, which currently doesn't seem to work on the Ultra 10:

[http://cdimage.ubuntulinux.org/ports/daily/current/](http://cdimage.ubuntulinux.org/ports/daily/current/)

I was just wondering whether for example, a release/ port of Breezy had been done, that does work.

Many thanks,

Chris.

---

### Post by netztier on 2006-04-25
I've done a successful installation of Ubuntu 6.06 Beta (Dapper Drake) on an Ultra 60. 

I got the CD image from 

[http://cdimage.ubuntu.com/ports/releases/6.06/beta/](http://cdimage.ubuntu.com/ports/releases/6.06/beta/)

Two issues:

[LIST]picking the right X.org driver for the **SUN FFB2+/Creator 3D** card (use sunffb driver), which then would only load after adding
[FONT="Courier New"]"cfb"[/FONT] and [FONT="Courier New"]"cfb32"[/FONT] to the modules section - found that in a wiki describing a Debian Etch install on a Ultra1 [ here ]("http://www.bralug.de/wiki/index.php?title=Debian_Etch_auf_einer_Sun_Ultra_1_Creator") (Text in German)
[/LIST] [LIST]don't use [FONT="Courier New"]"sun"[/FONT] or [FONT="Courier New"]"type 5"[/FONT] in the keyboard section in xorg.conf, stick with "[FONT="Courier New"]pc104/105"[/FONT] and [FONT="Courier New"]"xorg" [/FONT]for the keyboard model and rules. For the mouse, use [FONT="Courier New"]"/dev/input/mice"[/FONT] with [FONT="Courier New"]"ImPS/2"[/FONT] as protocol. [FONT="Courier New"]"/dev/sunmouse"[/FONT] and [FONT="Courier New"]"busmouse"[/FONT] won't work as they used to do with 2.4.x kernels and older xfree86 releases.
[/LIST]

As soon as I'll have the CD-ROM in my Ultra5 (which is technically pretty close to the U10, as far as I know) working properly again, I'll add a post here.

regards

Marc

---

### Post by netztier on 2006-04-28
[QUOTE=netztier][LIST]picking the right X.org driver for the **SUN FFB2+/Creator 3D** card (use sunffb driver), which then would only load after adding [FONT="Courier New"]"cfb"[/FONT] and [FONT="Courier New"]"cfb32"[/FONT] to the modules section - found that in a wiki describing a Debian Etch install on a Ultra1 [ here ]("http://www.bralug.de/wiki/index.php?title=Debian_Etch_auf_einer_Sun_Ultra_1_Creator") (Text in German)[/LIST] [/QUOTE]

Just for the sake of completeness:

The same turned out to be necessary for an Ultra 2 with 2x167Mhz Ultra SPARC I (which gave me other SCSI and initrd.img related headaches, see [this thread]("http://www.ubuntuforums.org/showthread.php?t=166882&highlight=ultra2") ) with a Creator card:

**[FONT="Courier New"]sunffb[/FONT]** as driver and don't forget to load the **cfb** and **cfb32** modules in xorg.conf, and off you go!

regards

Marc

---

### Post by lycurgus69 on 2006-05-05
Hi there. You seem to have good knowledge on getting ubuntu working on sparc ultras. 

I have an ultra 60 3d creator. 2 x 400mhz, 2x 18gb, 1gb ram. 

Here's my saga. I downloaded the iso that you mentioned. My first burn of the iso did not work and bummed out after 59% everytime. I remember reading some previous Debian post about how sparc isos have to be burnt slowly. So I went back and burned the cd at 8x instead of 40x. 

Install works to a point. I can get it all the way to the end and even get a console prompt, but the gui will not start. I attempted your fix of adding the 'cfb' modules to the xorg.conf. 

the problem is that now it appears to try to load GDM, but thats it. It locks and I can't switch to the console to undo whatever breakage I've managed to inflict.

Could you possibly write a slightly more detailed account of how you managed to get gdm to work?

I sincerely appreciate your time and efforts.

best regards.

---

### Post by netztier on 2006-05-05
Hi!

All it basically took was this:

During setup, the installer script prompts twice (yes, twice, I have no clue why, but anyway...) for the driver to use with the video card - for a *Creator* or *Creator 3D*, select **sunffb** there. 

You mal also later edit [FONT="Courier New"]**/etc/X11/xorg.conf**[/FONT] with for example [FONT="Courier New"]sudo nano /etc/X11/xorg.conf[/FONT], to look something like this (only the relevant sections are shown):

```
Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
[COLOR="Red"]        Load    "cfb"
        Load    "cfb32"[/COLOR]
EndSection

Section "Device"
        Identifier      "Sun Creator3D"
[COLOR="Red"]        Driver          "sunffb"[/COLOR]
        Option          "UseFBDev" "true"
EndSection
```

And that was it, as well on a bunch of Ultra 60 with Creator 3D as on an Ultra 2 with a Creator.

To debug further, please boot your system and let gdm's startup fail, then retrieve and attach the filew [FONT="Courier New"]**/var/log/Xorg.0.log**[/FONT] and  [FONT="Courier New"]**/etc/X11/xorg.conf**[/FONT] to a forum posting.

That'll be a bit of reading, but most of the problems can be tracked and nailed down in these two files.

You're saying that you can't revert to text-only console with Alt+F1 or Crtl+Alt+F1? Can you SSH into the machine when it seems locked?


kind regards

Marc

---

### Post by lycurgus69 on 2006-05-06
Awesome! Works like a charm. There was something I had to change down in Screens to make it work , but it works.

Were you able to get sound working at all?

---

### Post by netztier on 2006-05-06
[QUOTE=lycurgus69]Were you able to get sound working at all?[/QUOTE]

Yes, but the chip is not auto-detected. I discovered by chance that there's a few sparc-specific sound modules in /lib/modules/

Try [FONT="Courier New"]**sudo modprobe snd_sun_cs4231**[/FONT] to load the module. When I did this in a GNOME Terminal window, I instantly got a message on screen that new sound hardware had been detected and that it was now ready to be  configured.

To have the module loaded during startup,  you have to manually append a line with [FONT="Courier New"]**snd_sun_cs4231**[/FONT] to [FONT="Courier New"]**/etc/modules**[/FONT]:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
snd-sun-cs4231

```


Since i saw that the Ultra 2 also has the same sound chip, as well as the Ultra 5, I am positive that this will also work on these boxes - have other things to work and nibble on today than my "Ultra Park".

Now all is left is to find out why one of my U60 has gstreamer0.10 installed and why the other seems stuck at gstreamer0.80, and why the newer still won't play MP3s (although libmad0 is installed) ... OGG-files and streams are played, on the other hand.

kind regards

Marc

---

### Post by vorpalblade on 2006-10-05
> **chris_andrew said:**
> Hi,

I am yet to be able to get past "Booting Linux", with the Dapper images. Can anybody tell me whether they have managed to do an install of Ubuntu (any release), on an Ultra 10.  I am unable to do a netowk/ TFTP install.  I will have to rely on a boot disk and the internet.

Hope this helps.

Many thanks,

Chris.

I had a similar problem installing dapper on the Ultra10, and was able to resolve it, via the following method:
at the SILO boot prompt, hit tab to see the boot options. Decide which one you want, and type it at the boot prompt followed by 
append = "video=atyfb:off"
like this:
```

boot: Linux append = "video=atyfb:off"

```
(If Linux is the kernel image you want to boot)
After installation, you will have to go into the silo.conf file and add
this line in the appropriate place, otherwise the same thing will happen after install.


The reason for this is that by default, the dapper install uses the 2.6 kernel, which has some known quirks with the SPARC architecture. with the Ultra10, the BIOS will default to one graphics adaptor, while the linux kernel will default to another (in this case, the onboard ati adapter instead of the rather nice proprietary sun board). The append line simply disables the onboard framebuffer, in favor of the default.

I hope this helps...

Godspeed~

---

### Post by goathens on 2006-10-12
thanks vorpalblade, the frame buffer boot got my dapper sparc install to at least get past the booting linux... line.

problem is that now i get several errors relating to libc.so.6 not existing, leading to failed depmods modprobes, and non-existing files and folders (I apologize, but I am not used to the nitty-gritty of linux).
The first line states that
rtc_init: no PC rtc found
then the rest is all about the lack of libc.so.6

in the end, I am dumped to an unresponsive command line.

I'm also trying to install on an ultra10 (with the creator3d onboard), and have tried using 6.06 desktop for sparc, and 6.10 (today's release) desktop for sparc- and the errors are almost identical.

---

