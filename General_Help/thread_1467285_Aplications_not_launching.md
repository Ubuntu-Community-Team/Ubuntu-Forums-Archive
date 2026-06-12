---
title: "Aplications not launching"
date: 2010-04-30
forum: General Help
---

### Post by Irishbmx on 2010-04-30
Ok so not sure what I did to cause this.
I am using ubuntu 9.10 32 bit fresh install on xfx 8200 mb.
The problem is Allot of the applications just won't launch like pulsaudio device chooser, network manager ect.

I'll try and give a rundown of everything I've done.
Edited grub for the pci=nomsi thing and changed the root=uui thing to root=sda1, I installed eve online and teamspeak 3 had some problems with eve so I ubdated the kernal to [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc3-karmic/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc3-karmic/) did the first one first then the second one.
Had problems with audio on ts3 so I fallowd the tutorial and punched in some codes in the terminal don't remember exactly wich ones but I had this problem before that, looks like eve still doesn't launch unless I disable the network though wich I can't do because network manager isn't launching ><
oh I also activated one of the restricted nvidia drivers the one that said recommended.

Any Ideas on what I did wrong or how to go about working out the kinks with my sound/the eve online thing the sound seems to work fine for everything exept ts3 sometimes the sounds just doesn't work on it other times it gets real choppy.
Also being able to launch the system applications would be nice lol.
I have 3 HD's on this bored and 1 disk drive 2 HD's are sata 1 is my primary the other is storage the 3rd is IDE and has my windows xp on it.

---

### Post by Irishbmx on 2010-04-30
Ok I got eve working now fallowing a walkthru on the eve forums but pulsaudio device chooser and netwrok manager still will not launch.

---

### Post by Irishbmx on 2010-04-30
Still trying to figure this out.
Bold pink is what I edited/added I added the pci=nomsi and changed the root= from the uui or whatever it's called to that to get my hd to boot did I do this wrong or could this be why pulsaudio device chooser and allot of the other system tools are not working?
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **[COLOR="Magenta"]pci=nomsi[/COLOR]**"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "**[COLOR="Magenta"]root=/dev/sda1[/COLOR]**" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

---

### Post by 3rdalbum on 2010-04-30
padevchooser and nm-applet will appear in the notification area when you run them.

Also, I'd highly advise not to run any commands unless you know what they actually do or what the result is meant to accomplish. In terms of audio, you now have a non-stock system and nobody, not even yourself, knows how it differs from the norm.

---

### Post by Irishbmx on 2010-04-30
> **3rdalbum said:**
> padevchooser and nm-applet will appear in the notification area when you run them.

Also, I'd highly advise not to run any commands unless you know what they actually do or what the result is meant to accomplish. In terms of audio, you now have a non-stock system and nobody, not even yourself, knows how it differs from the norm.

ok well crap now I feel retarded ... I accidentally removed that from my bar ><
Thanx a bunch :)
Yea I plan on being very careful but I also plan on doing all the dangerous stuff before I get all set up so if need be I can just start with a fresh install no harm done.

---

