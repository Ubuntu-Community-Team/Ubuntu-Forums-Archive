---
title: "Need help :: Last resort :: Aaahhh 11.10"
date: 2011-10-23
forum: General Help
---

### Post by Mao Rune on 2011-10-23
This is going to be a lot to read, but I'm gonna copy paste the last thread I had from another forum where this problem was not resolved.

> **Original post]I posted here last night trying to fix all of my computer problems and some of them were resolved..

Just skipping to the problem here: I had to delete all my partitions and reinstall Windows and Ubuntu. Windows installed fine. Works the same. Ubuntu 11.10 "said" it installed fine and I was stoked.

GRUB boots at start up, Windows boots fine when selected. But when Ubuntu 11.10 is booted, it goes black, runs a punch of lines that are testing things (ie one says "bluetooth connect [OK]" which, I don't even have blue tooth but whatever) and then at the bottom I've got a blinking line and nothing. I left it alone for an hour and it never moved said:**
> https://help.ubuntu.com/[/url]

73 packages can be updated.
6 updates are security updates.

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo-root" for details.

luke@Ike:~$ ~mj

and blinking line cursor after the mj. I don't know which command to run, but I'm on another computer waiting for replies here so I'll be able to do any suggestions in real time without needing to boot.

I had the CD for 11.04, and that CD continually failed to install. So using the trial version booted from the CD, I deleted all the partitions including windows (because Windows was blue screened anyway, so I got an installation disc for Windows 7). After deleting all of the partitions I used someone elses computer to download and create a CD for Ubuntu 11.10. It went through the installation along side windows perfectly, until this.

[QUOTE=2]Here's something else that helps. The screen I get when I boot Ubuntu reads as is:

>* Starting CUPS printing spooler/server
>fsck from util-linux 2.19.1
>/dev/sda6: clean, 153016/3735552 files, 1003223/14937344 >blocks
>*starting configure network device security
>*starting System V initialisation compatibility
>* starting configure network device
etc etc etc all things "starting" with an "[ OK ]" on the far right of the screen aligning with all accept one that says "[fail]" for:
>*stopping automatic crash report generattion

The very last line is:
>*stopping Userspace bootsplash [ OK ][/QUOTE]

THINGS THAT I HAVE TRIED
sudo apt-get upgrade
sudo apt-get install gdm
Completely fresh downloaded ISO for 11.10, burned on new disc, installed using the Replace feature to delete any old Ubuntu files and install a fresh, new system.

All of these have not worked. I still power on the computer, boot's the GRUB and select Ubuntu (btw windows works just fine) and I still get this screen from quote 2.

Hopefully we can get this resolved, guys. I'd really like to get rollin' on this. =\

---

### Post by shadytv on 2011-10-23
ok log in via command line you said you tried "sudo apt-get upgrade" try sudo apt-get update && sudo apt-get upgrade" upgrade just installs current updates available, update refreshes repositories and checks for new updates
what is the output of trying to install gdm? have you tried installing lightdm?
i hope something i said helps, im a bit confused myself :confused:
but hey look on the bright side at least you can get into the system :P

---

