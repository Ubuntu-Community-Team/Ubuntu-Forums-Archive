---
title: "Grub loads only old kernels"
date: 2010-10-12
forum: General Help
---

### Post by ok_dr on 2010-10-12
Hello all. I've been using Ubuntu for more than a year (just basic simple stuff like surfing the net or the occasional document) and in the last months I've been running into the following problem.
I've been updating regularly to the latest Kernels the last one should be 2.6.32-25. However at start up Grub loads only 2.6.31-19 and below and there's no mentioning of 2.6.32 in grub.cfg while it is present in menu.lst. I tried to update grub with no success.
Any help would be appreciated. :)

---

### Post by ok_dr on 2010-10-15
Wow no answer at all. I didn't expect that. :(

---

### Post by gcndavidmn on 2010-10-15
Are you ok with the terminal?

If so give this a shot:

sudo update-grub

I think that should refresh the various kernels and OSs that GRUB will allow you to select.

---

### Post by oldfred on 2010-10-15
9.10 was 2.6.31
10.04 was 2.6.32

So which version are you running?

Grub version:
grub-install -v
Install:
lsb_release -a

---

### Post by TBABill on 2010-10-15
Did you possibly add a kernel newer than the version you are running? Sounds like you have Karmic running but tried to add Lucid kernels?

---

### Post by ok_dr on 2010-10-15
> **gcndavidmn said:**
> Are you ok with the terminal?

If so give this a shot:

sudo update-grub

I think that should refresh the various kernels and OSs that GRUB will allow you to select.

As I mentioned in my post I already updated grub (through the terminal) with no success.


**@oldfred**

The output of grub-install -v is Grub 0.97
The output of lsb_release -a is:

LSB Version:	core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch:cxx-3.0-ia32:cxx-3.0-noarch:cxx-3.1-ia32:cxx-3.1-noarch:cxx-3.2-ia32:cxx-3.2-noarch:cxx-4.0-ia32:cxx-4.0-noarch:graphics-2.0-ia32:graphics-2.0-noarch:graphics-3.0-ia32:graphics-3.0-noarch:graphics-3.1-ia32:graphics-3.1-noarch:graphics-3.2-ia32:graphics-3.2-noarch:graphics-4.0-ia32:graphics-4.0-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.1 LTS
Release:	10.04
Codename:	lucid

**@TBABill**
It's not like I've tried adding anything really, I just did the upgrade from Karmic to Lucid in May and later ran updates when it was prompted.

It may be that the problem arised after the upgrade, who knows, as it caused no particular problems I might have noticed it only later.

---

### Post by oldfred on 2010-10-15
See if this will re-sync things up.

If command line then use sudo -i to get into sudo mode

#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

sudo update-grub

---

### Post by ok_dr on 2010-10-15
Oldfred by distribution upgrade you mean 10.10? If yes I'd rather not to for the moment, though I plan on upgrading in a couple of weeks.
I tried all the rest, didn't work. Thanks anyway.

---

### Post by oldfred on 2010-10-15
No this is not the command to do an upgrade to a new verison: If you are not getting correct packages  we may need to review your sources list.

#would upgrade you to the latest kernel in the repositories, always run update first:
apt-get dist-upgrade

[http://en.wikipedia.org/wiki/Advanced_Packaging_Tool](http://en.wikipedia.org/wiki/Advanced_Packaging_Tool)
**dist-upgrade**, in addition to performing the function of upgrade,  also intelligently handles changing dependencies with new versions of  packages; apt-get has a "smart" conflict resolution system, and it will  attempt to upgrade the most important packages at the expense of less  important ones if necessary. The /etc/apt/sources.list file contains a list of locations from which to retrieve desired package files.[[12]]("http://en.wikipedia.org/wiki/Advanced_Packaging_Tool#cite_note-11") [aptitude]("http://en.wikipedia.org/wiki/Aptitude_%28program%29") has a smarter dist-upgrade feature called full-upgrade

---

### Post by teward on 2010-10-15
Go into a terminal, run:
```
sudo update-grub
```

That should update grub's list of kernels.

---

### Post by ok_dr on 2010-10-15
Sorry Oldfred I ran those commands but nothing was solved.

**@TrekCaptainUSA**
I already said to have done that when I presented my problem. It was then again suggested by the next poster and I again repeated to have tried that. I don't want to be rude and I welcome your good intentions, but guys please read the posts before replying to them.

---

### Post by drs305 on 2010-10-15
If you would like to just purge grub and reinstall grub2 here is a guide on how to do it. If you are already running Ubuntu from a normal Desktop you only need to accomplish Steps 2-5.

[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")

If this doesn't work or you don't want to use this method, post the info from the boot info script so we can give you further advice:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by ok_dr on 2010-10-16
I ran bootinfo. Attached is the results.txt file

---

### Post by oldfred on 2010-10-16
It looks like you have both grub with its menu updated to the new kernel and grub2 in the MBR and using a menu that is not updated.

You can try editing the grub menu entry to boot the newest kernel. Once booted then run the commands to uninstall grub & grub2 and reinstall just grub per drs305's instructions.

At grub menu press e to edit entry. Change the 31-19 to 32-25

    linux    /boot/vmlinuz-2.6.[COLOR=Red]31-19-[/COLOR]generic-pae root=UUID=7d31d70c-7183-4164-bb0e-128680ef4e23 ro   quiet splash
    initrd    /boot/initrd.img-2.6.[COLOR=Red]31-19[/COLOR]-generic-pae

At the least once booted the sudo update-grub should update grub2's grub.cfg but maybe the issue is it is updating menu.lst, so you can only solve it by uninstalling grub legacy.

---

### Post by drs305 on 2010-10-16
From the RESULTS.txt as *oldfred* noted you have a mixture of Grub legacy and Grub 2. When you boot, are you seeing the old Grub menu, then selecting the Grub 2 option, and then seeing it's menu?

I think that what *oldfred* says to do will get your new kernel booted. 

Once booted, you could also try to update the Grub 2 menu by running this command. It does the same thing as update-grub, but directs the output to a specific file, It might 'force' the update to update the contents of the grub.cfg file. 
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

If it doesn't, you could also add a custom menu entry for the latest kernel in /etc/grub.d/40_custom, but it shouldn't really be needed if Grub 2 updates properly.

Once you do get booted with your new kernel, I'd suggest fully transitioning to Grub 2. As you can see, mixing the two doesn't work extremely well.

Make a copy of the /boot/grub/menu.lst file and put it somewhere else (out of the boot folder). The command to replace Grub with Grub 2 is "sudo upgrade-from-grub-legacy" to allow Grub 2 to fully take over. After running that, I'd try running "sudo update-grub" again and my guess is that Grub 2 will find your new kernels.

Finally speaking of kernels, if you don't want to have dozens of them, one of the easiest ways to remove them (physically and from the Grub menu) is with the GUI app Ubuntu-Tweak. Here is a link with more information on it:
[HOWTO: Remove Older Kernels via GUI]("http://ubuntuforums.org/showthread.php?t=1587462")

---

### Post by ok_dr on 2010-10-16
Well I thought I'd try first simply that "sudo grub-mkconfig -o /boot/grub/grub.cfg" command and it worked, it now shows 2.6.32-25 and 24, so my main problem seems solved. 
Maybe I was better off with the older kernels though :-k cause before booting it spends plenty of time on a black screen with just a couple of lines, it boots alright in the end anyway.
I tried then the command "sudo upgrade-from-grub-legacy" but it said command not found.
Anyway thanks for your help guys. I'll upgrade to Maverick soon, so maybe the prolongation of the boot time won't be an issue then (to leave the place to smth else I guess :tongue:)

---

