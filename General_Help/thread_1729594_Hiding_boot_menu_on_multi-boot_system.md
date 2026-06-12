---
title: "Hiding boot menu on multi-boot system"
date: 2011-04-15
forum: General Help
---

### Post by Yos80 on 2011-04-15
Hi, I have 4 OS's on a publicly used pc.  I want to hide the boot menu on GRUB2 and have it appear only when I press and hold the SHIFT key during boot.  Will changing in /etc/default/grub GRUB_HIDDEN_TIMEOUT to 0 safely accomplish this goal?  Also, what is the command for deleting all of the former kernel upgrades from the boot menu?  Thanks.

---

### Post by Sidewinder1 on 2011-04-15
First Yos80, [I]
Welcome to the Forums!  =D>

[/I]I believe setting to -0- will do what you want; but I'm not absolutely certain as I still use Grub Legacy (and that was the method used) rather than Grub 2.
In answer to your second question the way do it is by using Synaptic Package Mgr, to remove previous kernels. You probably want to retain the current *and one previous kernel* just in case something goes "kerplooie" with the current one.

HTH,
Side

P.S. For more detail and command line options for removing old kernels, please see the thread (found by searching for "removing old kernels with synaptic", in the search bar, above:
[http://ubuntuforums.org/showthread.php?t=1283521&highlight=removing+previous+kernels+synaptic&page=2](http://ubuntuforums.org/showthread.php?t=1283521&highlight=removing+previous+kernels+synaptic&page=2)

---

### Post by Yos80 on 2011-04-15
Thank you for your quick reply and for solving one of my problems.  :-)  However, making the change I mentioned above (and I did update-grub) doesn't work in GRUB2 to hide the menu list.

---

### Post by Dave_L on 2011-04-15
Can you post /etc/default/grub here?  There may be another setting in it that's causing the menu to display.

---

### Post by Sidewinder1 on 2011-04-15
Perhaps you could try using the search bar, above and input search terms:
"Grub 2 hide menu"
I'm reasonable certain there is an easy to do this.
Try this...

[http://ubuntuforums.org/showthread.php?t=1724431&highlight=Grub2+hide+menu](http://ubuntuforums.org/showthread.php?t=1724431&highlight=Grub2+hide+menu)

---

### Post by Yos80 on 2011-04-15
At this time, I don't have internet access (I'm on my phone) but thank you for your willingness to help.

---

### Post by Sidewinder1 on 2011-04-15
You're more than welcome.
When you get a chance, try the above and if the results are not to your satisfaction, post back and I am sure I or someone else will be more than willing to assist you; that's exactly what these forums are for and in my opinion, they accomplish that with immeasurable grace.

Side

---

### Post by Yos80 on 2011-04-15
Thanks Side for pointing me in the right direction. The solution that works for me was to set GRUB_TIMEOUT=1 so that it boots directly into the primary OS without even showing the boot menu. Then when I want to boot into one of the other OS's, I just press and hold the up or down arrow keys during boot up to display the menu. Works for me lol. Thanks guys.

---

### Post by Sidewinder1 on 2011-04-15
Glad to've helped. :D
Please remember to go to "thread tools" above, and mark your thread as "Solved".
Thanx,
Side

---

