---
title: "Installed XP, not able to launch linux"
date: 2009-12-25
forum: General Help
---

### Post by Cinemarxism on 2009-12-25
Hi. First of all, I have Linux Mint. But it's similar enough to ubuntu, so I hope it's okay for me to seek help on this board (LM-boards aren't that active, sadly).

So I just finished installing Windows XP. Already have Linux Mint installed, and used [this]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1") guide. I saved my grub-file (if that's what it's called, its the "menu.lst"-file) on a memory stick, so luckily I still have those settings at hand.

I found out grub is not installed ("The program 'grub' is currently not installed.  You can install it by typing:
sudo apt-get install grub"). I do the install, then "sudo grub".

Alright, this works, so I proceed to enter (following the guide blindly, heh) the following: 

> - root (hd0,0)
- setup (hd0)Get an error 17 after the last line.

Then I proceed with the following command: "find /boot/grub/stage1". This gives me the following: "(hd0,1)".

So I proceed with the following entries:

> - root (hd0,1)
- setup (hd0)This works. No error or anything. Relieved, I reboot my computer, and to my joy I get the grub-menu. I pick Linux Mint. But now I get to a black screen with a Grub Error 17.

I reboot with the LiveCD, only to find that grub is once again not installed (though that could be because its a LiveCD, I dont know). I try the same thing again, although I dont have much faith in a positive result. And the result is the same, error 17.

Tried to do the "sudo grub" - "root (hd0, 1) and then "setup (hd1)"

Once again, no errors in terminal. However, when trying to run Mint the result were the same.

Here's the exact error-message:

> 
root (hd0,0)
  Filesystem type unknown, partition type 0x7
kernel   /boot/vmlinuz-2.6.24-19-generic root=/dev/sda1 ro quiet splash

Error 17: Cannot mount selected partition

Press any key to continue. . .Any input/help would be greatly appreciated. Thanks in advance!

---

### Post by User3k on 2009-12-25
Ubuntu 9.10 uses grub 2. If I type that in the command line then it also tells me that grub is not installed though I know grub 2 is.

This link might help you.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by dcstar on 2009-12-25
> **Cinemarxism said:**
> 
..........
This works. No error or anything. Relieved, I reboot my computer, and to my joy I get the grub-menu. I pick Linux Mint. But now I get to a black screen with a Grub Error 17.
..........
Any input/help would be greatly appreciated. Thanks in advance!

There are already many posts in the forums on Grub Error 17, search them out.

---

### Post by -=hazard=- on 2009-12-25
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by MaxIBoy on 2009-12-25
If it still uses menu.lst, you still use Grub 1 (Grub 2 doesn't use that file anymore.)


Which partition and hard drive is Linux Mint on? (hd0,0) = first hard drive, first partition. (hd0,1) = first hard drive, second partition. (hd5,2) = sixth hard drive, third partition.

---

### Post by Cinemarxism on 2009-12-26
Thanks for all the help.

I've tried the method [suggested here](http://ubuntuforums.org/showthread.php?t=1014708). It does not work. Or, it kind of works - I get to the GRUB-menu, but as soon as I pick Linux Mint I get the GRUB error 17.

What I find weird is that while all guides suggest that you type "sudo grub" in the terminal (in the LiveCD) this always results in a "GRUB not installed". So I then proceed to install grub with the suggested command. Then I do "sudo grub", get into grub-mode, then "find /boot/grub/stage1" which gives me hd (0,1).

I follow with "root (hd0,1)" then setup (hd 0).

As I said, this gives me the GRUB-menu when rebooting, but picing Linux Mint results in grub error 17.

But by doing "sudo fdisk -l" I get the following disc info:

>  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         973     7815591    7  HPFS/NTFS
/dev/sda2             974       18704   142424257+  83  Linux
/dev/sda3           18705       19457     6048472+   5  Extended
/dev/sda5           18705       19457     6048441   82  Linux swap / Solaris

So Linux is on sda2. Does this mean I should type something else after "root" or is it irrelevant?

Again, thanks a lot.

---

