---
title: "Resolution Warning on Grub"
date: 2012-04-02
forum: General Help
---

### Post by TurtleKing on 2012-04-02
Last thing I did: Downloading a game on Steam using Wine yesterday.

Problem: Today tried to boot into Ubuntu, and kept getting "Error kernel deprecated...gfxresolution...set it to 1920x1080"

It wouldn't let me boot despite me restarting 2 times. I decided to Google the error on windows, and read a couple of suggestions. However, when I restarted again it booted normally.

I use Startup-Manger & Grub for booting purposes. I noticed in Startup-Manager that the highest resolution listed is 1600x1200.

Is there anyway of adding the 1920x1080? I don't want to experience that booting error again.:(

---

### Post by Paddy Landau on 2012-04-02
I had been led to believe that Startup Manager was defunct for the more recent versions of Ubuntu. Have you found that it does anything for your system (11.10)?

---

### Post by TurtleKing on 2012-04-02
> **Paddy Landau said:**
> I had been led to believe that Startup Manager was defunct for the more recent versions of Ubuntu. Have you found that it does anything for your system (11.10)?

To be honest no. I installed it to make Grub "prettier", but I never got around to doing it. Also, I think I installed it to changed the resolution (don't remember anymore).

---

### Post by oldfred on 2012-04-02
You may need to manually edit /etc/default/grub, but resolution you set must be supported by your system or else it will not work. 

vga=xxx is a deprecated boot option
Use this with your monitor size in /etc/default/grub:
GRUB_GFXMODE=1024x768
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993)
"VGA Deprecated" Message on Boot
[http://ubuntuforums.org/showthread.php?t=1453524](http://ubuntuforums.org/showthread.php?t=1453524)

VGA conversions:
[http://wiki.archlinux.org/index.php/Gensplash](http://wiki.archlinux.org/index.php/Gensplash)
[http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes](http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes)

---

### Post by TurtleKing on 2012-04-05
I'm sorry can you be a little more detailed? I just changed the following line in etc/default/grub:
[PHP]#GRUB_GFXMODE=1920x1080[/PHP]
And it still doesn't work. :(

---

### Post by oldfred on 2012-04-05
If it still has the # then it still is just a comment. Remove the  # and then run this to update grub.cfg

```
sudo update-grub
```

---

### Post by TurtleKing on 2012-04-06
Resolution still has not changed. I even tried your recommended resolution to no avail.
Here is the entire grub file:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1024x768

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```
If it helps, I did re-install Ubuntu a couple of days after getting this warning (had too much unnecessary software).

---

### Post by oldfred on 2012-04-06
[COLOR=#000000][COLOR=#FF8000][COLOR=Black]Does your system support video mode 1920x1080 when booting. 
That may not be the same as what you system supports  once your video drive  kicks in  on Ubuntu loading.

[/COLOR][/COLOR][/COLOR]

---

### Post by TurtleKing on 2012-04-07
> **oldfred said:**
> [COLOR=#000000][COLOR=#FF8000][COLOR=Black]Does your system support video mode 1920x1080 when booting. 
That may not be the same as what you system supports  once your video drive  kicks in  on Ubuntu loading.

[/COLOR][/COLOR][/COLOR]

How would you figure out if it's supported?

---

### Post by oldfred on 2012-04-07
As the grub file says use  vbeinfo.

I just rebooted and at the grub menu pressed cntl-C to get to a grub command line.
My vbeinfo showed a lot of choices. In my 10.10 I am using a default of 640x480 but it does show my monitor preferred of 1280x1024. I notice that 12.04 is using the 1280x1024 as default and for me that is very small print. Old eyes do not work well anymore.

---

### Post by TurtleKing on 2012-04-07
According to grub 'vbeinfo' 1920x1080 is not supported (not listed).:(
So I went ahead with the previous 1600x1200, updated grub, and now it is running the chosen resolution.

Well at least, I didn't have to install a 3rd-party software just to change it. Thanks for the help.:)

---

