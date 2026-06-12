---
title: "How to you install a driver for a new sound card?"
date: 2010-03-08
forum: General Help
---

### Post by harryliddic on 2010-03-08
I bought a new sound card for 9.10 and it said it was linux compatible, the mini_DVD produced the following

```
Archive:  /media/SBT-SP6C/SBT-SP6C/PCI-8738-081002-8.17.30(FULL-LO-01)/Setup.exe
[/media/SBT-SP6C/SBT-SP6C/PCI-8738-081002-8.17.30(FULL-LO-01)/Setup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /media/SBT-SP6C/SBT-SP6C/PCI-8738-081002-8.17.30(FULL-LO-01)/Setup.exe or
          /media/SBT-SP6C/SBT-SP6C/PCI-8738-081002-8.17.30(FULL-LO-01)/Setup.exe.zip, and cannot find /media/SBT-SP6C/SBT-SP6C/PCI-8738-081002-8.17.30(FULL-LO-01)/Setup.exe.ZIP, period.

``` 

the water is beginning to move faster and I don't have a paddle. or a clue.

---

### Post by phidia on 2010-03-08
Please provide the specs of your sound card or go [here]("http://ubuntuforums.org/showthread.php?t=205449") and use the guide there.

---

### Post by harryliddic on 2010-03-08
thank you for your response. I went to the site you quoted and ran a few of the commands here is an example


```
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
	Subsystem: nVidia Corporation Device 0091
	Flags: 66MHz, medium devsel, IRQ 3
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Expansion ROM at fe000000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel modules: nvidiafb, rivafb

02:08.0 USB Controller: NEC Corporation USB (rev 43) (prog-if 10)
	Subsystem: NEC Corporation USB
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at ff1ff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

02:08.1 USB Controller: NEC Corporation USB (rev 43) (prog-if 10)
	Subsystem: NEC Corporation USB
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at ff1fe000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

02:08.2 USB Controller: NEC Corporation USB 2.0 (rev 04) (prog-if 20)
	Subsystem: NEC Corporation USB 2.0
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at ff1fdc00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

02:09.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
	Subsystem: C-Media Electronics Inc CM8738
	Flags: bus master, stepping, medium devsel, latency 191, IRQ 11
	I/O ports at 7f00 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: C-Media PCI
	Kernel modules: snd-cmipci

02:0b.0 Ethernet controller: Lite-On Communications Inc LNE100TX (rev 20)
	Subsystem: Kingston Technologies Device f002
	Flags: bus master, medium devsel, latency 64, IRQ 3
	I/O ports at e800 [size=256]
	Memory at ff1fd800 (32-bit, non-prefetchable) [size=256]
	Expansion ROM at 50000000 [disabled] [size=256K]
	Kernel driver in use: tulip
	Kernel modules: tulip

harry@harry-desktop:~$ 

```



the specs on the sound card box are
> 16 bit full duplex CODEC
Legacy audio SB pro compatilbe
ai pin standard Dual Game/MIDI port
supports direct sound 3D
6-ch 16-bit DAC,32-bit PCI bus master, PCI12.2 compliant

The mic on my Dragon Dictating progam seems to work out the speakers, that is probably a jack in the wrong hole elsewise everything is still mute. I have loaded every driver in the repos. any ideas?

---

### Post by phidia on 2010-03-08
> **harryliddic said:**
> thank you for your response. I went to the site you quoted and ran a few of the commands here is an example


```
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
	Subsystem: nVidia Corporation Device 0091
	Flags: 66MHz, medium devsel, IRQ 3
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Expansion ROM at fe000000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel modules: nvidiafb, rivafb

02:08.0 USB Controller: NEC Corporation USB (rev 43) (prog-if 10)
	Subsystem: NEC Corporation USB
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at ff1ff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

02:08.1 USB Controller: NEC Corporation USB (rev 43) (prog-if 10)
	Subsystem: NEC Corporation USB
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at ff1fe000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

02:08.2 USB Controller: NEC Corporation USB 2.0 (rev 04) (prog-if 20)
	Subsystem: NEC Corporation USB 2.0
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at ff1fdc00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

02:09.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
	Subsystem: C-Media Electronics Inc CM8738
	Flags: bus master, stepping, medium devsel, latency 191, IRQ 11
	I/O ports at 7f00 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: C-Media PCI
	Kernel modules: snd-cmipci

02:0b.0 Ethernet controller: Lite-On Communications Inc LNE100TX (rev 20)
	Subsystem: Kingston Technologies Device f002
	Flags: bus master, medium devsel, latency 64, IRQ 3
	I/O ports at e800 [size=256]
	Memory at ff1fd800 (32-bit, non-prefetchable) [size=256]
	Expansion ROM at 50000000 [disabled] [size=256K]
	Kernel driver in use: tulip
	Kernel modules: tulip

harry@harry-desktop:~$ 

```



the specs on the sound card box are


The mic on my Dragon Dictating progam seems to work out the speakers, that is probably a jack in the wrong hole elsewise everything is still mute. I have loaded every driver in the repos. any ideas?

What shows in the Devices tab, from the System>Preferences>Sound menu?
You can test your sound there too. Installing many drivers is probably not that helpful-try opening the terminal and entering alsactl -i then go through the setup from there.

---

### Post by harryliddic on 2010-03-08
It needed an argument

```
harry@harry-desktop:~$ alsactl -i
alsactl: option requires an argument -- 'i'
Usage: alsactl <options> command

Available global options:
  -h,--help        this help
  -d,--debug       debug mode
  -v,--version     print version of this program

Available state options:
  -f,--file #      configuration file (default /var/lib/alsa/asound.state)
  -F,--force       try to restore the matching controls as much as possible
                   (default mode)
  -g,--ignore      ignore 'No soundcards found' error
  -P,--pedantic    do not restore mismatching controls (old default)
  -I,--no-init-fallback
                   don't initialize even if restore fails
  -r,--runstate #  save restore and init state to this file (only errors)
                   default settings is 'no file set'
  -R,--remove      remove runstate file at first, otherwise append errors

Available init options:
  -E,--env #=#	   set environment variable for init phase (NAME=VALUE)
  -i,--initfile #  main configuation file for init phase (default /usr/share/alsa/init/00main)


Available commands:
  store   <card #> save current driver setup for one or each soundcards
                   to configuration file
  restore <card #> load current driver setup for one or each soundcards
                   from configuration file
  init	  <card #> initialize driver to a default state
  names   <card #> dump information about all the known present (sub-)devices
                   into configuration file (DEPRECATED)
harry@harry-desktop:~$ 
harry@harry-desktop:~$ 
harry@harry-desktop:~$ alsactl -l
alsactl: invalid option -- 'l'
Usage: alsactl <options> command

Available global options:
  -h,--help        this help
  -d,--debug       debug mode
  -v,--version     print version of this program

Available state options:
  -f,--file #      configuration file (default /var/lib/alsa/asound.state)
  -F,--force       try to restore the matching controls as much as possible
                   (default mode)
  -g,--ignore      ignore 'No soundcards found' error
  -P,--pedantic    do not restore mismatching controls (old default)
  -I,--no-init-fallback
                   don't initialize even if restore fails
  -r,--runstate #  save restore and init state to this file (only errors)
                   default settings is 'no file set'
  -R,--remove      remove runstate file at first, otherwise append errors

Available init options:
  -E,--env #=#	   set environment variable for init phase (NAME=VALUE)
  -i,--initfile #  main configuation file for init phase (default /usr/share/alsa/init/00main)


Available commands:
  store   <card #> save current driver setup for one or each soundcards
                   to configuration file
  restore <card #> load current driver setup for one or each soundcards
                   from configuration file
  init	  <card #> initialize driver to a default state
  names   <card #> dump information about all the known present (sub-)devices
                   into configuration file (DEPRECATED)
harry@harry-desktop:~$ 

```

It appears  that the driver is CM8738 with I believe is the driver for my old and thought to be dead card,

---

### Post by phidia on 2010-03-08
From the link I provided previously: 

> (3) Check to see if the ALSA driver for your sound card exists. Go to [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) and search for your sound card (chipset) manufacturer in the dropdown box. You'll be given a matrix of the sound cards made by the manufacturer. Try to match the chipset you found in step 2 with the driver(green hyperlink text).

    * Success - You will have found the driver for your soundcard's chipset.

    *
      Failure - You will have not found the driver for your soundcard chipset. (at the moment I cannot help you, but stay tuned!)

(4) Now go back to the shell and type
Code:

sudo modprobe snd-

Now, press the TAB key BEFORE pressing the ENTER key to see a list of modules. Try to find the module that matches the driver you found in step 3.


For example, my driver is a via82xx so I would type, sudo modprobe snd-via82xx.

    *
      Success
          o
            A success here means that your soundcard was installed, but it was not being loaded. Now you have loaded it for the current session.
          o
            To load it for all sessions (you will probably want to do this) you will have to edit /etc/modules (I think this is the file, I'll check once I get to my Dapper PC).
          o
            Type this into the shell
            Code:

             sudo nano /etc/modules

          o
            Add only the name of the module to be loaded at the end of the file. In my case, the via82xx module gave me sound so I added "snd-via82xx" to the end of the file.(iii) Make sure that you have all channels unmuted in alsamixer
          o
            See the alsamixer section
          o
            Play media using your favorite media player. Set your audio engine to alsa. In some cases, you have to configure your audio engine within another (media engine) like in Kaffiene in Kubuntu. If you hear sound, hurray!
          o
            One final step. Go onto Saving Sound Settings

    * Failure -You have two options

    * Move on to Getting the ALSA drivers from a *fresh* kernel. This step is easier and is recommended to users who might have been tinkering with their sound settings and want to revert back to the way it was just after installing Ubuntu (without reinstalling Ubuntu of course )

    *
      Move on to ALSA driver Compilation, if you have not done so already. If you have, please post a new thread with your problem.


Getting the ALSA drivers from a *fresh* kernel

Sometimes, sound might be configured correctly, but for some reason or another (tinkering) it stops working. One way to go back to the old setup is to reinstall Ubuntu. However, this step is actually quite unnecessary since you are reinstalling everything because of one thing.

A faster way, is to just remove the problematic packages and reinstall them cleanly.

(1) Remove these packages
Code:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils


(2) Reinstall those same packages
Code:

sudo apt-get install linux-sound-base alsa-base alsa-utils



See if those commands will get your sound drivers/modules loaded and sound working for you.

---

### Post by harryliddic on 2010-03-09
I emailed you a post by mistake sorry I think it when to Ubuntu. What is said and what I left out was that I took the new card out because it was not on the list and replaced it with the old(supposedly dead) card and was fool with some commands use suggested and suddenly Tom Petty can blasting through the speakers I should have stayed in Preferences>Sound and see what went right but I immediately turn it down and went to Kino to see if my video had sound, it didn't nor did various CD-players or video editor but I definitely feel that it is in the input because the input section of Preferences>Sound had no device in the lower half,

---

### Post by phidia on 2010-03-09
> **harryliddic said:**
> I emailed you a post by mistake sorry I think it when to Ubuntu. What is said and what I left out was that I took the new card out because it was not on the list and replaced it with the old(supposedly dead) card and was fool with some commands use suggested and suddenly Tom Petty can blasting through the speakers I should have stayed in Preferences>Sound and see what went right but I immediately turn it down and went to Kino to see if my video had sound, it didn't nor did various CD-players or video editor but I definitely feel that it is in the input because the input section of Preferences>Sound had no device in the lower half,

I'm not sure if your sound problem is related but often when one application is using sound it prevents other apps from using sound too-that can be changed but you would need to refer to the guide I linked here or see [community docs]("https://help.ubuntu.com/") on sound.

---

### Post by harryliddic on 2010-03-09
your "here" link didn't work could you re-send. Secondly, has the change from /dev/dvd
had any effect on Ubuntu  programs particularly legacy programs like kino. I know I had to use /dev/sr1 to get the video ripped. if so is there a work-around for this.This I do know I have typed more CLI than all my years in Ubuntu. By the way what is the CLI for fstab?

---

### Post by phidia on 2010-03-09
By "here" I meant the previously supplied link to the sticky sound guide.

---

