---
title: "problem editing grub menu.lst"
date: 2010-04-08
forum: General Help
---

### Post by Rubi1200 on 2010-04-08
I have some obsolete entries on the Grub menu which I would like to remove. Here is the problem: when I run the command to edit the file it says it is loading and then...nothing, just a blank file with no entries. Couldn't find the file with Nautilus either; it says it is there, but even with hidden files showing I cannot see it. What is going on and how do I edit this file?
By the way, on another note, when I popped the LiveCD in to check the Grub entries it tells me no such command found...huh!?
Thanks in advance.

---

### Post by darolu on 2010-04-08
I see in your mini profile you use 9.10; if you made a fresh install of it you have GRUB2.

If you upgraded from 9.04, you have GRUB "1" (legacy).

GRUB legacy uses menu.lst, while GRUB 2 uses a scripts-based system.

If you have GRUB 2 you can "open" the file via CLI with nano, vim or any other text editor, but in reality you would be ***creating*** the file, this is probably why you find a blank one.

Judging from the way you posted your case, I tend to think you do have GRUB2; I do not know of any way to delete the entries (or comment the lines) like we used to do it in GRUB legacy's menu.lst file, what many of us do to eliminate entries we no longer use is to delete the actual kernel images from our /boot, to do it open Synaptic and search for **linux-image** and mark the ones you don't want to be deleted; I recommend leaving one "old" kernel besides the one you are currently using.

---

### Post by Rubi1200 on 2010-04-08
Hi darolu, and thanks for responding. In the meantime I have discovered/realized that I have Grub2, which is why there is no menu.lst and that the files are actually in /etc/grub.d
However, in the thread explaining Grub2, what is new, how to edit/remove entries, I feel a bit out of my depth AND I cannot seem to located the script with the entries I want to remove anyway. There is one for memtest and I think another for recovery mode, but I don't want to delete those. I am looking for the file which has old entries for (shock horror) another distro I had installed and subsequently removed. It still shows up on the boot menu and that is what I wanted to get rid of.
Any ideas?
Thanks

---

### Post by uRock on 2010-04-08
[s]If you want a GUI to help you do this, then you can either use a terminal and run [CODE]sudo apt-get install startupmanager[/CODE or go to Synaptic Package Manager and install startupmanager. This is a great GUI for doing what you want to do.[/s]

Cheers,
Ronnie

---

### Post by uRock on 2010-04-08
> **Rubi1200 said:**
> Hi darolu, and thanks for responding. In the meantime I have discovered/realized that I have Grub2, which is why there is no menu.lst and that the files are actually in /etc/grub.d
However, in the thread explaining Grub2, what is new, how to edit/remove entries, I feel a bit out of my depth AND I cannot seem to located the script with the entries I want to remove anyway. There is one for memtest and I think another for recovery mode, but I don't want to delete those. I am looking for the file which has old entries for (shock horror) another distro I had installed and subsequently removed. It still shows up on the boot menu and that is what I wanted to get rid of.
Any ideas?
Thanks

If you want to remove old kernel entries, go to Synaptic Package Manager and search and remove all three kernel packages for each one you want to remove. It helps to select Status-Installed in the left menu. You will want to keep the ones that you see listed in my screenshot.

---

### Post by darolu on 2010-04-08
Running "sudo update-grub" should 'refresh' your boot-menu entries; run it and see if they disappear.

To see the entries you have run:
```
cat /boot/grub/grub.cfg |grep menuentry
```
Where they are located can be found with:
```
cat /boot/grub/grub.cfg |grep set\ root
```
This information may help you to get rid of the extra entries in your boot menu, your former distro partitions may still be there.

---

### Post by Rubi1200 on 2010-04-08
thanks guys! Will try running this later and post again. currently busy with something else.
Appreciate the advice
:)

---

### Post by Rubi1200 on 2010-04-08
thanks uRock; I removed the entries from Synaptic and everything is fine now - no more obsolete entries.
Nice one!

:)

---

### Post by uRock on 2010-04-08
I am glad I could help. Please don't forget to mark the thread as solved with the "Thread Tools" menu close to the top of the page.

Cheers,
Ronnie

---

