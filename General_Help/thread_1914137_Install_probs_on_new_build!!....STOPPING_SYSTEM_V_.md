---
title: "Install probs on new build!!....STOPPING SYSTEM V RUNLEVEL COMPATIBILITY"
date: 2012-01-23
forum: General Help
---

### Post by tonewheelkev on 2012-01-23
Used CD to install 11.10 (64 bit) on a new build.....got message that install was successful, and to restart!

Nightmare started there....boot up halts, and "STOPPING SYSTEM V RUNLEVEL COMPATIBILITY" is as far as I can get before freezing.

Am really stuck here, and require some serious 'nurse-maiding'....!!

---

### Post by varunendra on 2012-01-24
See if this thread can help you ([s]post #16[/s] post #12 and next ones): [http://ubuntuforums.org/showthread.php?p=11344874&postcount=12](http://ubuntuforums.org/showthread.php?p=11344874&postcount=12) [COLOR=DarkRed](EDIT: modified link to point to post **#12** by *effenberg0x0*)[/COLOR]

To install the *"lightdm-gtk-greeter"* or *"unity-greeter"* package suggested there, you can either follow the earlier posts to manually start X, or by booting into recovery mode > drop to root shell.

---

### Post by tonewheelkev on 2012-01-24
Can boot ONLY from live CD....and changes made cannot be saved.....

Once again....and from the very beginning please....HELP!!!! :KS

---

### Post by QIII on 2012-01-24
Can you give us some specs on your machine?

---

### Post by varunendra on 2012-01-25
> **tonewheelkev said:**
> Once again....and from the very beginning..
When you power on your computer:

[LIST]
[*]press and hold "Shift" key. This should bring up the grub menu.
[*]Choose the 2nd option (recovery mode), and press enter
[*]After some scrolling text messages, you will get the 'Recovery menu'. Choose "remount" option (to remount partitions with read/write permission)
[*]Press 'Enter' when prompted to get the similar menu again
[*]Choose the last option this time (root --> drop to root shell prompt)
[/LIST]
Now at the root shell prompt (command-prompt that ends with '**#**'), enter this command:
```
apt-get install unity-greeter
```then follow the installation prompts and answer yes/no as and if required.

[To see the effect of installed packages, you will have to restart in normal mode. If you see no improvement, you can also try other commands, suggested in the thread I linked in my earlier post, at the same root-prompt (by restarting into recovery mode again).]


**[[COLOR=Red]!!Caution!!: [/COLOR]Use the root shell carefully as entering harmful commands there can permanently damage the installed OS without warning!]**

---

### Post by tonewheelkev on 2012-01-25
Hi Varunendra...and thanks!

Didn't help....I'm afraid.

In the earlier post that you mention, it seems to me that nothing seemed to help...
...perhaps I'll read it again

And some specs for QIII....

Intel i3-2120 3.3GHZ
ASUS P8Z68-V LX
8GB 1330 PNY
Zotac GT-430

........!!?

---

### Post by varunendra on 2012-01-26
> **tonewheelkev said:**
> Didn't help....I'm afraid.

In the earlier post that you mention, it seems to me that nothing seemed to help...
...perhaps I'll read it again
I am not familiar with such problems or their causes, but after a second look at the thread I linked to, it seems like you may have to follow the post #12 first, afterwards post #16 or others. Please do so if you already haven't and tell us if it makes any difference or not.
*(I am editing my first post to modify the link to point to post #12 in the thread anyway, as it seems to me a pre-requisite to subsequent solutions)*.

---

