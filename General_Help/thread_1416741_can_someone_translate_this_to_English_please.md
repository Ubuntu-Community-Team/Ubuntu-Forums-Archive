---
title: "can someone translate this to English please?"
date: 2010-02-26
forum: General Help
---

### Post by petedes5 on 2010-02-26
Quick install
=============

1) You must have full configured source for the Linux kernel which you
   want to use for the ALSA drivers. Note that ALSA drivers are part
   of the kernel, so there is necessary to resolve all symbol dependencies
   between the used kernel and ALSA driver code. Partly installed kernels
   (for example from distributor makers) can be unuseable for this action.

2) You must turn on sound support (soundcore module).

3) Run './configure' script.

 * General Options
   If you do not want ISA PnP support, use --with-isapnp=no switch.
   If you do not want sequencer support, use --with-sequencer=no switch.
   If you do not want OSS/Free emulation, use --with-oss=no switch.
   If you have udev or devfs and want to use more than eight cards, use
   --enable-dynamic-minors switch.
   If you want to turn on debug mode, use --with-debug=full switch.
   If you want to debug soundcard detection, try --with-debug=detect switch.

 * Kernel Source Tree
   On 2.4/2.6 kernels, the location of the kernel source tree is
   parsed automatilly from the running kernel.
   If it's not in the standard place, specify the path via
   --with-kernel=<kernel_directory>. 
   On 2.6 kernels, the build directory has to be given via
   --with-build=<kernel_build_dir> option additionally, too.

 * Drivers to Compile
   The card drivers to be compiled can be selected via --with-cards option.
   Pass the card driver name without "snd-" prefix.  To specify
   multiple drivers, list names with comma (,).
   Passing "all" will compile all possible drivers (and this is the
   default choice).
   Some drivers have compile options.  They can be passed via
   --with-card-options option.  Multiple options can be passed with comma,
   too.  The default is "all".
   For available cards and options, see ./configure --help.

   Note that you have to specify all items you want to enable unless
   you pass "all".  Or, pass "all" and additionally "NAME=n".  This will
   enable all but the ones that with =n suffix.  See examples below.

 * Example
      ./configure --with-debug=full
          Enable debug option "full"

      ./configure --with-cards=sb16,emu10k1 --with-card-options=sb16-csp
          Build for cards sb16 and emu10k1 drivers and enable sb16-csp
          option.  But all other card options are *disabled*.

      ./configure --with-cards=all,hda-intel=n
          Build drivers except for hda-intel.

4) Run 'make'.

5) Run 'make install' as root.
   If you have already a system with ALSA init script, you should install
   just only modules via 'make install-modules' so that the existing init
   script won't be replaced.

6) Run the './snddevices' script to create new sound devices in /dev directory.
   Skip this step, if you have already /dev/snd/* files, or if you're
   using a DEVFS or udev.

7) Edit your kernel module config (either /etc/modprobe.conf or
   /etc/modules.conf, depending on the kernel version). If you are not
   sure, what to do, you may try the alsaconf script available in
   the alsa-utils package.

8) Run 'modprobe snd-xxxx' where xxxx is the name of your card.
   Note: All ALSA ISA drivers support ISA PnP natively, so you don't need
         isapnptools any more.  Don't use both together.  It will
         conflict.  For disabling the ALSA ISA PnP support, specify
         --with-isapnp=no configure switch.

You can also look at the utils/alsasound file. This script is designed for
the RedHat distribution, but it can be used with other distributions which
use System V style rc init scripts.

Note: All mixer channels are muted by default. You must use a native
      or OSS mixer program to unmute appropriate channels (for example a
      mixer from the alsa-utils package).

Note: This document notices the /etc/modules.conf file. Many current
      distributions uses the old /etc/conf.modules file. Both names are
      valid.

---

### Post by johngreth on 2010-02-26
What is this supposed to do?

---

### Post by nothingspecial on 2010-02-26
If you don`t know what that means, I suggest you post the exact nature of your sound problem, your sound card and what you have done so far in attempting to fix it.

Doing that could make it a lot, lot worse if you make a mistake.

---

### Post by petedes5 on 2010-02-26
My problem lies with my external speakers that I am plugging in through my headphone jack. somewhere along the lines in trying everything possible to fix the problem, I deleted my alsamixer driver.


anyways.... I just reinstalled ubuntu and still have the same [original] problem with my external speakers,


speakers work fine and i had windows 7 before ubuntu on this computer and the external speakers were working fine.

I think the problem lies with ubuntu mis-communicating with my soundcard.

---

### Post by sgosnell on 2010-02-27
That is in English.  But there is no need to compile ALSA drivers, you can get them in a .deb file.

---

### Post by Mark Phelps on 2010-02-27
It IS english -- technical jargon, to be sure -- but english nonetheless.

Compiling source is quite possibly the most difficult and technically challenging thing for a new Ubuntu person to do -- and runs the risk of making your system worse, not better.

Not insulting you ... just telling you that the path you have chosen is a very difficult one, and should you decide to go down it, you will have a LOT to learn.

As others have suggested, describe the problem you have, and perhaps we can help you solve it without you having to go down this path ...

---

### Post by johngreth on 2010-02-27
> **Mark Phelps said:**
> Compiling source is quite possibly the most difficult and technically challenging thing for a new Ubuntu person to do -- and runs the risk of making your system worse, not better.
I can attest to that. I tried recompiling the kernel to get rid of ipv6 in Ubuntu 9.04 and it took several tries, each time crashing my computer. When I finally got it to not crash, it still didn't get rid of ipv6. Moral is, if you can avoid compiling from source, don't. There's usually a much easier way or a patch in the making.

---

### Post by gordintoronto on 2010-02-27
> **petedes5 said:**
> My problem lies with my external speakers that I am plugging in through my headphone jack...

speakers work fine and i had windows 7 before ubuntu on this computer and the external speakers were working fine.

I think the problem lies with ubuntu mis-communicating with my soundcard.

I assume your problem is that you expect sound from the speakers and you aren't getting any. (It might be helpful if you would say, "I expected X but got Y.")

What do you see in Preferences/Sound? Are you running Karmic? Have you opened Volume Control and checked that nothing is muted? What sound card do you have? (Run Accessories/terminal and enter the command lspci, one line of the output should describe your sound card.)

---

### Post by petedes5 on 2010-02-28
> **gordintoronto said:**
> I assume your problem is that you expect sound from the speakers and you aren't getting any. (It might be helpful if you would say, "I expected X but got Y.")

What do you see in Preferences/Sound? Are you running Karmic? Have you opened Volume Control and checked that nothing is muted? What sound card do you have? (Run Accessories/terminal and enter the command lspci, one line of the output should describe your sound card.)

In preferences/sound: 

Sound Playback: autodetect

Sound Capture: ALSA

Device: HDA Intel (Alsa MIxer)

Sound Card: 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller

Everything is unmuted and I have played with muting and unmuting to no avail.

I'm not familiar with Karmic ???

---

### Post by petedes5 on 2010-03-01
i have 9.04

---

### Post by gordintoronto on 2010-03-01
Have you tried changing "Sound Playback" to ALSA?

---

### Post by petedes5 on 2010-03-02
yes, i have and nothing  


: (

---

### Post by nothingspecial on 2010-03-02
[[COLOR="Magenta"]This[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1140667") thread could fix your problem.```


gksudo gedit /etc/modprobe.d/alsa-base.conf
```

Then try all of the options listed in the thread.

Might be an idea to ```
sudo cp /etc/modprobe.d/alsa-base.conf ~/alsa-base.bak
```

first, just incase.

That just makes a backup of the file you`re editing.

---

### Post by petedes5 on 2010-03-02
I think this thread will fix my problem but what does this mean; can someone explain this to an extreme beginner?

 [SIZE=3]put following lines on /etc/modprobe.d/alsa-base.conf
[/SIZE]  	[SIZE=3]Code:[/SIZE]
 	[SIZE=3]options snd-hda-intel model=hp-m4 enable=1 index=0
options snd-hda-intel enable_msi=1[/SIZE]

---

### Post by petedes5 on 2010-03-02
thread was on to something but it all failed, still doesn't work

---

### Post by nothingspecial on 2010-03-02
What, exactly, did you try?

---

### Post by petedes5 on 2010-03-02
i found this thread:

[http://ubuntuforums.org/showthread.php?p=7574382#post7574382](http://ubuntuforums.org/showthread.php?p=7574382#post7574382)

and that's my computer and I know all i need to do now is update my alsa drivers

but that is very difficult for me as i don't understand any ubuntu lingo

[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

^ I download the attached file and all it is , is a readable document and I don't know how to install!

what a mess!

---

### Post by sgosnell on 2010-03-02
A script is the equivalent of a batch file in DOS.  If you don't remember DOS, well, you're probably way, way behind the power curve for computer literacy, but you can catch up.

Navigate to the script in Nautilus, right-click on it, and select Properties.  Go to the Permissions tab, and click the box that says "Allow executing file as a program".  This makes the script executable, and you can do the same thing in a terminal by typing "chmod +x filename", where filename is the name of the file.  You can also use chmod by using numbers, where different numbers set different bits, but you don't have to know that right now.  There are many ways to do most things in Linux, and you're probably more used to a GUI, coming from Windows, so use Nautilus, and check the box.  Then just double-click on the file, and a dialog will ask what you want to do.  Choose the option to run it in a terminal, and it will run, and you can see the results.  This is the same thing as running a batch file in a command window in Windows, but most people don't even know how to do that.  They have to have someone write and compile a complete program, even for simple tasks.  The script you downloaded should do that.  I haven't read it, so I'm making an assumption that it will do what you think it will.

---

