---
title: "There is a new version of Grub out now....but why was it not included in 9.10?"
date: 2009-11-22
forum: General Help
---

### Post by Digikid on 2009-11-22
Just curious because in this site here:

[http://grub.enbug.org/](http://grub.enbug.org/)

Grub version 1.97 Beta 4 is old....however the latest version was released before Ubuntu shipped.  Strange.

That said.....how do I install this new version and get my timer back???

---

### Post by fragos on 2009-11-22
It may have been released after the Ubuntu 9.10 package freeze. The purpose of the freeze is to maintain a controlled environment that can be tested before release.

---

### Post by Digikid on 2009-11-23
Possible.  Ok then how do I install this latest version?

---

### Post by Uncle Spellbinder on 2009-11-23
Not to take this thread off track, but out of curiosity, why is everyone calling Grub 1.97 "Grub 2"? I mean, isn't that like calling Firefox 3.5 "Firefox 4"?

---

### Post by wojox on 2009-11-23
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Grub 1.97 is grub2

---

### Post by Uncle Spellbinder on 2009-11-23
> **wojox said:**
> [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Grub 1.97 is grub2

I know. But again. It is 1.97. Just curious why it is being referred to as "2". Just seems odd.

---

### Post by Digikid on 2009-11-24
> **Uncle Spellbinder said:**
> Not to take this thread off track, but out of curiosity, why is everyone calling Grub 1.97 "Grub 2"? I mean, isn't that like calling Firefox 3.5 "Firefox 4"?


I agree.  It is **not** Grub 2.  Quite simply if it does not say 2.0 then it is not.

They are just being lazy and rounding it up.

---

### Post by oldos2er on 2009-11-24
> **Uncle Spellbinder said:**
> I know. But again. It is 1.97. Just curious why it is being referred to as "2". Just seems odd.

 The "2" isn't the version number, it's part of the name of the program, to distinguish it from original grub.

---

### Post by Darael on 2009-11-24
> **oldos2er said:**
> The "2" isn't the version number, it's part of the name of the program, to distinguish it from original grub.
Exactly.  Also for the same reason GRUB 0.9-whatever-it-is is GRUB 1.  AIUI, there will eventually be a GRUB 1.0 and a GRUB 2.0, and they're almost separate projects.  I expect it makes sense to whoever thought up the numbering scheme!
Actually, I think I get the reasoning - it's grub 2 because it's the **2nd** iteration of grub.

Back OT, according to [this]("https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202") help documentation, you can use a timeout with the current version of grub in Ubuntu... and it's usually safer to go with the version of things provided by the distro.  Especially something as essential as the bootloader!

---

### Post by 73ckn797 on 2009-11-24
Point understood but does it really matter?

---

### Post by Darael on 2009-11-24
No - hence why I also tried to pull back ontopic!  *sigh*...

---

### Post by Digikid on 2009-11-24
To me it matters....or else I would not have made the topic.

I did what that article said....still no timer.

---

### Post by fluffman86 on 2009-11-24
Off Topic: [http://en.wikipedia.org/wiki/Software_versioning](http://en.wikipedia.org/wiki/Software_versioning)

Basically, there are a few different ways to number software.

Ubuntu uses date of final release: 9.10 = 2009, the 10th month (October).  Everything before that, i.e., the betas and alphas, are not 9.9, 9.8, etc.  Instead, they are just alpha 1, alpha 2, etc.

KDE uses major/minor releases, starting with point-zero.  So KDE 4.0 breaks away from 3.*, and is no longer backwards compatible.  4.0 is really like beta or alpha software, 4.1 included major bug fixes/new features, and now 4.3.3 is pretty stable.  

Banshee, a few years ago (or less?) was at 0.13.  This was stable, but the devs wanted to add lots of new features.  So they broke compatibility with 0.13, and started working on what would become banshee-1.  0.90 was alpha, 0.99 was beta, 0.99.9 was release candidate, and 1.0 was stable.  1.0.1 included bugfixes.  1.2 included major bugfixes and new features, but was still compatible.  

Wordpress follows numbers directly.  2.6 led to 2.7, even though the Banshee devs would have called it 3.0 because of all the new features and the broken compatibility.  Next will be 2.8.  Then 2.9.

The Linux kernel uses an even/odd system.  2.4 was the previous stable kernel, 2.5 was development which led to 2.6 (which should have been 3.0...sigh...).  Jaunty had 2.6.28, and the devs were working on 2.6.29, which because 2.6.30.  Now we're on 2.6.31, which the Ubuntu devs stabilized, because 2.6.31 had lots of new features over 2.6.30, and 2.6.32 wasn't ready yet.  Right now, there are some kernel hackers working on 2.7, which will eventually become 2.8.

---

### Post by Digikid on 2009-11-25
Grub.  Timer.  Fix.

Please.

---

### Post by Roasted on 2009-11-25
My car was made in March of 2001, but that's all it is - a 2001. Should it be named 03-2001, to signify EXACTLY when it was made?

No.

Why?

Because it just doesn't matter.

---

### Post by philipp2084 on 2009-11-25
**GRUB Timer Fix**

See [https://wiki.ubuntu.com/Grub2]("https://wiki.ubuntu.com/Grub2")

you have to edit /etc/defaults/grub and comment out the following line to get your timer back: 

GRUB_HIDDEN_TIMEOUT=0

---

### Post by Digikid on 2009-11-25
I am still new to Ubuntu /Linux.

"Comment out"?

Got it......but unfortunately it did not work at all.

> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="5"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

---

### Post by seeker5528 on 2009-11-25
> **Uncle Spellbinder said:**
> Not to take this thread off track, but out of curiosity, why is everyone calling Grub 1.97 "Grub 2"? 

Because grub and grub 2 are different programs.

Could also be because they did not think people would get the PUPA connection?

[http://www.nongnu.org/pupa/](http://www.nongnu.org/pupa/)

Later, Seeker

---

### Post by Digikid on 2009-11-26
Anyone have any more ideas on why I have no timer?

---

### Post by phillw on 2009-11-26
> (20:49:42) Phi11W UK: So, there's a new release of Grub .... dare we ?
(20:50:50) drs I haven't.  I don't want to get ahead of the users I'm troubleshooting for at this point.


That's from one of the guys who's written up some of the HowTos for Grub2 that we all use.

His advising caution is good enough for me !!

One of his HowTo's is over here --> [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

That deals with splash images & timers etc.

Regards,

Phill.

---

### Post by blueridgedog on 2009-11-26
> **Digikid said:**
> Anyone have any more ideas on why I have no timer?

At the top of the file it states:

```
# If you change this file, run 'update-grub' afterwards to update
```

Note that should be a sudo command.

Did you do that?

---

### Post by blueridgedog on 2009-11-26
I must admit that I haven't seen the benefit of this upgrade yet.  I really could manage the prior grub and knew it well.  I will hang in there, but I have a strong temptation to go with the flow.  One reason I know it well is having to walk so many people through fixing it, so perhaps we need to move forward to something that one day will not require such effort.

---

### Post by louieb on 2009-11-26
> **blueridgedog said:**
> I must admit that I haven't seen the benefit of this upgrade yet. 

The one that sticks out for me is the os-prober.  Seem to do a much better job of sniffing out other OSes  and setting up grub.conf to boot them.  And adding another OS to the GRUB menu is a lot easier.

---

### Post by Digikid on 2009-11-27
> **blueridgedog said:**
> At the top of the file it states:

```
# If you change this file, run 'update-grub' afterwards to update
```Note that should be a sudo command.

Did you do that?

Yes I did do that....still timerless.

---

### Post by Digikid on 2009-11-29
No one knows eh?  Nuts. :(

---

### Post by Leppie on 2009-11-29
Could you post your /boot/grub/grub.cfg as well?
It might reveal the reason why you don't have the timer.

---

### Post by Digikid on 2009-11-29
> #
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 2459b8b8-432b-40f9-a9c3-5f104741b39b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 2459b8b8-432b-40f9-a9c3-5f104741b39b
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=2459b8b8-432b-40f9-a9c3-5f104741b39b ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 2459b8b8-432b-40f9-a9c3-5f104741b39b
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=2459b8b8-432b-40f9-a9c3-5f104741b39b ro single 
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 2459b8b8-432b-40f9-a9c3-5f104741b39b
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=2459b8b8-432b-40f9-a9c3-5f104741b39b ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 2459b8b8-432b-40f9-a9c3-5f104741b39b
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=2459b8b8-432b-40f9-a9c3-5f104741b39b ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

Ask and it shall be added onto you.  :D

---

### Post by wilee-nilee on 2009-11-29
If you want to control the timer I am assuming the time of grub dwell before booting I think startup manager will control that even without a multi-boot.

---

### Post by fluffman86 on 2009-11-29
I know you're not supposed to edit grub.cfg directly, but it *DOES* work, at least temporarily.  ```
if [ ${recordfail} = 1 ]; then
set timeout=-1
else
set timeout=5
fi
```

negative 1 timeout?  try changing that to set timeout=10 instead.  If it works, then you're missing something in your grub defaults file.

Edit: also try what wilee-nilee said:
sudo apt-get install startupmanager
then go to system > admin > startup-manager

---

### Post by mikewhatever on 2009-11-30
> **Digikid said:**
> No one knows eh?  Nuts. :(

I think it's pretty obvious why you don't have the timer:

```
**GRUB_HIDDEN_TIMEOUT_QUIET=true**
```

and here's the relevant section from grub2 manual:

```

GRUB_HIDDEN_TIMEOUT_QUIET=true

    * true No countdown is displayed. The screen will be blank.
    * false A counter will display on a blank screen for the duration of the GRUB_HIDDEN_TIMEOUT value. 

```

Change true to false, and that should be it, apart from learning to ask question straight and to the point.;)

---

### Post by ptn107 on 2009-11-30
I updated the grub2 packages to the latest 1.97.1 found from the grub website.

UPDATE: I put up a PPA that has working versions for all architectures [2].
```
deb http://ppa.launchpad.net/ptn107/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/ptn107/ppa/ubuntu karmic main
```

---

### Post by Digikid on 2009-11-30
> **fluffman86 said:**
> I know you're not supposed to edit grub.cfg directly, but it *DOES* work, at least temporarily.  ```
if [ ${recordfail} = 1 ]; then
set timeout=-1
else
set timeout=5
fi
```negative 1 timeout?  try changing that to set timeout=10 instead.  If it works, then you're missing something in your grub defaults file.

Edit: also try what wilee-nilee said:
sudo apt-get install startupmanager
then go to system > admin > startup-manager

Startup Manager did not work.   Nice applet though.

> **mikewhatever said:**
> I think it's pretty obvious why you don't have the timer:

```
**GRUB_HIDDEN_TIMEOUT_QUIET=true**
```and here's the relevant section from grub2 manual:

```

GRUB_HIDDEN_TIMEOUT_QUIET=true

    * true No countdown is displayed. The screen will be blank.
    * false A counter will display on a blank screen for the duration of the GRUB_HIDDEN_TIMEOUT value. 

```Change true to false, and that should be it, **apart from learning to ask question straight and to the point.**;)

Now now.  It is not how it is asked that matters.  Besides...I did get straight to the point.  _YOU_ were not reading it correctly.  :P

I tried what you suggested as well.  Same result. :(

---

### Post by Leppie on 2009-11-30
You could try to reinstall grub:
```
$sudo grub-install /dev/sda
```

oh, and there's nothing wrong with this line:
```
GRUB_HIDDEN_TIMEOUT_QUIET=true
```
it's in my grub default file as well, and the menu is working well ;)

---

### Post by Digikid on 2009-11-30
Tried it....same result.

About ready to give it up....maybe it will be fixed by the time that the REAL grub 2 is released ( 2.0 )

---

### Post by Leppie on 2009-11-30
maybe you can try to completely remove (make sure all config files are gone) and re-install grub2?

---

### Post by Digikid on 2009-11-30
I hate to ask you this...but how?  I am a newbie to Linux and am not sure of all the commands as of yet.

---

### Post by fluffman86 on 2009-11-30
Digikid: did you try editing that line I posted earlier in /boot/grub/grub.cfg manually?

---

### Post by Digikid on 2009-11-30
Yes I did....still a no go.

---

### Post by wojox on 2009-11-30
Change to 

```
#GRUB_HIDDEN_TIMEOUT=0
```

Did you comment out the hidden timeout?

---

### Post by Digikid on 2009-12-01
yes

---

