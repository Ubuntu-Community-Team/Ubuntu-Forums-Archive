---
title: "repair my Ubuntu installation"
date: 2011-04-20
forum: General Help
---

### Post by joeshmo00 on 2011-04-20
Running 10.04.2 (quite happily I might add) since it came out.  After some hardware issues, I was having a problem viewing my screen (long story that ends in my monitor being the culprit).  I initially thought I would just boot with Knoppix and fix my xorg.conf...didn't help.  I ran a fsck from within Knoppix and let it fix things...seems like that was a bad idea.

At this point, I can log in, but most of my startup items (Gnome indicators ans such) never launch and they take forever to timeout.

My question is, does anyone have any bright ideas on how to "repair" my installation.  I'm thinking of something similar to the Windows "repair" option.

Let me know if you need more gory details of my current situation.

---

### Post by Mark Phelps on 2011-04-20
These days, Windows offers two different kinds of repairs:
1) Startup Repair -- rewrites the boot loader and startup files
2) Repair Installation -- rewrites the Windows system files

Ubuntu has a Recovery Mode that functions similar to Safe Mode in Windows, but I'm not aware of anything like the Repair Installation.

---

### Post by joeshmo00 on 2011-04-20
Right...my bootloader is fine.  I'm thinking of something that would check my system files.  The recovery mode did not seem to help as I had no display once it booted...I didn't check the grub switches, but I assume it boots with some sort of "safe video" mode.

---

### Post by Mark Phelps on 2011-04-21
> **joeshmo00 said:**
> Right...my bootloader is fine.  I'm thinking of something that would check my system files.
I have heard that you can reinstall Ubuntu over itself (choose manual partitioning but do NOT format) and it then functions in the same manner as a Windows Repair Install -- but my Ubuntu system works fine and I have no interest in breaking it in order to test this.  But, if you want to try it out, then make a backup using Clonezilla and try this kind of reinstall.

>   The recovery mode did not seem to help as I had no display once it booted...
No display at all? Or no graphical desktop?  It boots into a command line.  So, if you didn't even get that, don't know what is wrong.

> I didn't check the grub switches, but I assume it boots with some sort of "safe video" mode. It boots into a command line by default.  When you choose a normal restart or enter the command startx, I believe that you doing a normal reboot into your desktop.  I'm not aware of any graphical Safe Mode like in Windows.

---

### Post by dragonfly41 on 2011-04-21
> 
I have heard that you can reinstall Ubuntu over itself (choose manual  partitioning but do NOT format) and it then functions in the same manner  as a Windows Repair Install -- but my Ubuntu system works fine and I  have no interest in breaking it in order to test this.  But, if you want  to try it out, then make a backup using Clonezilla and try this kind of  reinstall.
If it helps to clarify .. I've just in the last hour gone through that process of reinstalling ubuntu .. but not reformatting .. in an effort to get my Internet connection back and curing some glitches in the startup splash.

After this reinstallation .. programs I had installed (jEdit) were gone.   And I still didn't recover Internet connection (I'm posting this via my Vista OS).   Files left on desktop were still there.   The ubuntu install warns which system folders will be scruubed.

I kept all my data (scripts etc.) on a separate NTFS partition so I can access data either in Vista or ubuntu.  And I sync all my Firefox bookmarks through zotero.org (requires zotero plugin).

I guess I'll need to go through a ubuntu reinstall .. with format.

---

### Post by Mark Phelps on 2011-04-22
> **dragonfly41 said:**
> After this reinstallation .. programs I had installed (jEdit) were gone.   And I still didn't recover Internet connection (I'm posting this via my Vista OS).   

OUCH!!!

Well, I guess that the "nondestructive reinstall" method only works for folks that have a separate /home partition, save that off prior to reinstall, and restore it after reinstall.

This "Repair Install" is something I've been championing for YEARS, but it seems Canonical is only interested in eye-candy (Unity desktop) and Cloud Computing -- neither of which are any value to me.

---

