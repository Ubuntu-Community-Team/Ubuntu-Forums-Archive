---
title: "The symbol grub_device_open not found"
date: 2010-06-13
forum: General Help
---

### Post by hj_0922 on 2010-06-13
I know I'm not going to have a lot of information, but willing to answer any questions if I can. I'm by no means a Linux guru, however, I am computer literate and I am in IT for a living, so shouldn't need "to much" hand-holding :lolflag:
 
Saturday June 5, completely stable Ubuntu 9.2 system. Shut the system down cleanly and went on vacation for a week. Came home yesterday, booted the system, and it was running very slowly. I see at the bottom the Update Manager was open, and it had several updates available. I'm sorry to say that I did not pay attention to what it was updating. Rebooted system and it immediately goes to a console with the error:
 
GRUB LOADING
error: the symbol 'grub_device_open' not found
grub rescue>
 
I have researched some about the grub rescue console, and it appears there are a lot of commands that do not work, such as ls. A 'set' tells me the following:
 
prefix=(hd0,1)/boot/grub
root=hd0,1
 
I'm at a loss as to where to go from here to get back into Ubuntu. Any help is greatly appreciated.
 
-HJ

---

### Post by bruno9779 on 2010-06-13
I have found some info on this error. It could be because a newer version of grub has been installed and something from the old one is still lingering around

I think that your best bet is booting with live CD and reinstalling grub.

check out this thread: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

At point 13 you have instructions on how to reinstall grub from live CD.

It is the most complete guide to grub2 I have found, I advise you to bookmark it.

---

### Post by hj_0922 on 2010-06-13
I was afraid that would be the answer. Looks pretty straight forward though. Appears I have ran into a roadblock however. The only disk I have is 10.04 (borrowed a 9.x disk from a friend previously).  When it boots and I try to 'Try Ubuntu without Installing', I get a popup message with the title Boot loader, and the message /caspe2/vmlinuz and an OK button. When I hit OK, it's back at the menu.  Thoughts?
 
-HJ

---

### Post by hj_0922 on 2010-06-13
Wow, well actually wow squared. I'm used to stumping the audience on forums when it comes to Windows, but pretty amazed that I've done it on Linux too, I'm pretty new to it.  And the second wow is that there were 13 pages of posts since my post this morning.  Anyone have any ideas on what I've got going on?

---

