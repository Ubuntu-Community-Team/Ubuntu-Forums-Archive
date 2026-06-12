---
title: "Ubuntu working, but Desktop is not?"
date: 2010-03-05
forum: General Help
---

### Post by jewels. on 2010-03-05
The partition I was using for / ran out of space. (It was because of a backup program - so I deleted the mess of files that filled up the drive, and continued on.)  The lack of space on the drive cause a "corruption" or "problem" to occur with the GNOME desktop.  

When I reboot the computer, GRUB loads, when the default option is selected, the white ubuntu symbol appears,
then the words UBUNTU with a spotlight below them appear,
then the desktop login screen appears but looks blue-ish colored.
An error message in the top right corner says:

**[COLOR="RoyalBlue"]The configuration defaults for gnome power manager have not been installed correctly.[/COLOR]**

If I try to login at this blue-ish screen, it just keeps returning me to this blue-ish screen with the same error message.  
The Ubuntu OS seems to be working, because I can CTRL-ALT-F1 to a command line, and perform normal operations correctly.

After reading some forums, I came to the conclusion that the power manager is probably not the entire problem, and if I fixed just the power-manager, I would get the desktop back, but not correctly.
So, I tried to **[COLOR="SeaGreen"]"apt-get --reinstall install ubuntu-desktop"[/COLOR]**
but that still did not fix the problem.

If I return back out to the GRUB options, and select recovery mode, I attempted to select dpkg (from the Recovery Menu) to repair all broken packages, and in the middle of this process, the following error came up:

**[COLOR="DarkOrchid"]grub probe: error: cannot find a grub device for /dev/sdc1  Check your device.map[/COLOR]**

So, perhaps there is an error with the grub.cfg file.  But I hate to go any further because I'm not sure if this is the right direction to go.  If I select grub (from the Recovery Menu) to Update the grub bootloader, this same error message also appears.  I'm wondering if the /etc/fstab file has some issue with it, but I don't entirely know.  Can someone walk me through what to do next.

FYI, I'm familiar with UNIX from university classes years ago.  And I messed with Debian about five years ago.  I've been running Karmic Kaola now for a few months. So I'm familiar with Linux, but rusty.  It's all been coming back to me slowly.  I should be able to run commands if you ask me to, and to paste output here.  What do you suggest for my next step?  (I'm tryin to avoid having to re-install the entire ubuntu OS if I can avoid it.)

Thanks in advance! ~jewels.

---

### Post by jewels. on 2010-03-05
bump?

---

### Post by jewels. on 2010-03-05
Hmmm.... i think i'm finding the problem....
i *thought* that i had removed files to make more space on the drive, but apparently i had not.... so i'm now removing files, and we'll see what happens....

its amazing how awful the system runs when it has no space!  LOL

---

### Post by jewels. on 2010-03-05
Yep!  That fixed it!  The problem was no space on /

So, my original problem was (as quoted):
> **jewels. said:**
> The partition I was using for / ran out of space. (It was because of a backup program - so I deleted the mess of files that filled up the drive, and continued on.)  The lack of space on the drive cause a "corruption" or "problem" to occur with the GNOME desktop.  

When I reboot the computer, GRUB loads, when the default option is selected, the white ubuntu symbol appears,
then the words UBUNTU with a spotlight below them appear,
then the desktop login screen appears but looks blue-ish colored.
An error message in the top right corner says:

**[COLOR="RoyalBlue"]The configuration defaults for gnome power manager have not been installed correctly.[/COLOR]**

If I try to login at this blue-ish screen, it just keeps returning me to this blue-ish screen with the same error message.  
The Ubuntu OS seems to be working, because I can CTRL-ALT-F1 to a command line, and perform normal operations correctly.

So, I dropped to the command line and deleted the files that filled up all the space.  (They were created by a BackInTime backup program).  I didn't know that the program put all those files in a folder under the / directory.  (I wanted the files to go somewhere else.)

After I deleted the files, I ran these commands, just to be sure my problems would be fixed:

$sudo apt-get remove ubuntu-desktop
$sudo apt-get install ubuntu-desktop

Then, I rebooted the computer into recovery mode, and selected dpkg (from the Recovery Menu) to repair all broken packages.
Just for good measure, I selected grub (from the Recovery Menu) to Update the grub bootloader.
No problems anywhere.
I rebooted again, and WHHHAAAA LAAAAA!  My desktop has returned to normal!  Woohoo!!
Thanks for reading this everyone!  I hope it helps someone else in the future.  
LESSON: Do not let / run out of room! :D
Have a great day!

---

### Post by tom4everitt on 2010-03-06
Ok, good to know that its actually fixable by removing some files! Thanks for sharing. 

You'd probably want to use

apt-get remove --purge ubuntu-desktop
apt-get install ubuntu-desktop

since that would also fix any broken settings. Now it worked anyway but :)

---

### Post by JamezQ on 2010-03-06
Hey this seems like my [problem]("http://ubuntuforums.org/showthread.php?t=1421258") so I am very happy you fixed it and it worked so well, my problem seems to be also caused by a backup program.

However I have a problem, when I try to remove backup, the folder that takes up so much space, it says Permission denied.

What do I do to show the computer who is boss?

---

### Post by tom4everitt on 2010-03-06
You do the same command, but put sudo first :)

So 

rm -r <folder>, becomes
sudo rm -r <folder>
(or sudo rm -rf <folder> if it gives you a lot of tedious questions).

If its not that easy you might need to get yourself full permsissions:
sudo chmod -R 777 <folder>

and then do rm again.

---

