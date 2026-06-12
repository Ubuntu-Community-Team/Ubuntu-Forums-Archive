---
title: "How do I get ubuntu out of bios"
date: 2009-07-06
forum: General Help
---

### Post by TDS40 on 2009-07-06
Ok, I tried ubuntu and don't like it because I'm a gamer and it doesn't support the cutting edge games.  

So I uninstalled ubuntu and it still comes up as an option when I reboot.  How do I get that out of my computer???

Thanks.

---

### Post by Cheesemill on 2009-07-06
You need to restore the Windows boot loader, just do a search for restore windows mbr and you'll find loads of how-tos.

---

### Post by michy99 on 2009-07-06
You need to restore the mbr with the Windows install disk or recovery disk.

---

### Post by Jesus_Valdez on 2009-07-06
How do you install it and how do you uninstall it?

You need your windows cd/dvd in order to fix your MBR. Put your winows on your cd tray, reboot and initialize from de cd, just before the instalation comes an option to fix your MBR.

---

### Post by TDS40 on 2009-07-06
Wow, talk about instant help.  What a cool forum.

I figured out an easier way to do it.

I just went in to the Boot.ini and delete the ubuntu path and it's no longer an option on boot up.  It just automatically loads Windows now.

My thoughts on ubuntu, after playing around with it for well over an hour.  As on OS I think Ubuntu is the bomb. It's super stable way more stable than windows for sure. Not even the slightest glitch, hiccup, or delay in any application and everything is instant and clean. 

In order for to permanently switch to Ubuntu this is what I would need sorted.

1.  Ubuntu did not see my second hard drive at all (windows has no problem with this, in fact I use the second hard drive to speed up the computer up --- works great).
2.  Ubuntu does not see my Microsoft Word documents ( I have 100's of them I need access to, is there a app for that).
3.  Ubuntu recommended Nvidia display drivers which are way out of date (I think it was v180)  The latest driver (v186.18 ) runs the latest games by improving their performance by 11-45% depending on the game.

So to be honest I'm a little disappointed because ubuntu is the bomb for stability but I can't use it, for reasons explained.

---

### Post by DeMus on 2009-07-06
> **TDS40 said:**
> 

1.  Ubuntu did not see my second hard drive at all (windows has no problem with this, in fact I use the second hard drive to speed up the computer up --- works great).
2.  Ubuntu does not see my Microsoft Word documents ( I have 100's of them I need access to, is there a app for that).
3.  Ubuntu recommended Nvidia display drivers which are way out of date (I think it was v180)  The latest driver (v186.18 ) runs the latest games by improving their performance by 11-45% depending on the game.

So to be honest I'm a little disappointed because ubuntu is the bomb for stability but I can't use it, for reasons explained.

1) How do you mean, Ubuntu does not see your second hard disk? Did you mount it? Apparently not. This is as simple as 2 + 2 = 4. When you don't know it, just ask here, and you get lots of answers from people who want to help you.

2) OpenOffice.org can read and write your office documents, even the 2007 version. No problem here.

3) Sorry, but I run 190.09 already. Okay, Ubuntu does not show it in the Synaptic list, that does not mean it is not there.

So, all in all, your problems can easily be swept from the table. No reason to return to Windows. You really want to do that only to play those games?

---

### Post by TDS40 on 2009-07-06
> **DeMus said:**
> 1) How do you mean, Ubuntu does not see your second hard disk? Did you mount it? Apparently not. This is as simple as 2 + 2 = 4. When you don't know it, just ask here, and you get lots of answers from people who want to help you.

2) OpenOffice.org can read and write your office documents, even the 2007 version. No problem here.

3) Sorry, but I run 190.09 already. Okay, Ubuntu does not show it in the Synaptic list, that does not mean it is not there.

So, all in all, your problems can easily be swept from the table. No reason to return to Windows. You really want to do that only to play those games?

Cool thank you.  I guess I didn't realize the second hard drive needed to be mounted?

Ok, I guess I need to put ubuntu back on the computer and give it another try.  

My reason for trying it to begin with, I got infected with some really bad malware, the kind that keeps re-installing itself after it's deleted.  It took me 4 days before I found the installer program hidden in the registry.  Once I nuked the drop program the problem was cured.  A friend of mine suggested that I try ubuntu and that it's far more secure than windows.  So I decided to give it a try.

ubuntu is so new to me that I just need to spend some time figuring everything out.  thanks again for the comments.

---

### Post by egalvan on 2009-07-06
> **TDS40 said:**
> Wow, talk about instant help.  What a cool forum.

Weclome to Linux, and this forum.
> In order for to permanently switch to Ubuntu this is what I would need sorted.

1.  Ubuntu did not see my second hard drive at all (windows has no problem with this,
 in fact I use the second hard drive to speed up the computer up --- works great).

My install of Jaunty sees both hard drives, NTFS and ext2/ext3 formatted.
You need to go to "Places" to see internal drives, though.
And I also use both drives to spread the swap, although with 8GB of RAM, it's not used :)

> 
2.  Ubuntu does not see my Microsoft Word documents ( I have 100's of them I need access to, is there a app for that).
3.  Ubuntu recommended Nvidia display drivers which are way out of date (I think it was v180)
  The latest driver (v186.18 ) runs the latest games by improving their performance by 11-45% depending on the game.

I can't use it, for reasons explained.

DeMus gave excellent counter-points here, I can't do better.

---

### Post by DeMus on 2009-07-06
> **TDS40 said:**
> Cool thank you.  I guess I didn't realize the second hard drive needed to be mounted?

Ok, I guess I need to put ubuntu back on the computer and give it another try.  

My reason for trying it to begin with, I got infected with some really bad malware, the kind that keeps re-installing itself after it's deleted.  It took me 4 days before I found the installer program hidden in the registry.  Once I nuked the drop program the problem was cured.  A friend of mine suggested that I try ubuntu and that it's far more secure than windows.  So I decided to give it a try.

ubuntu is so new to me that I just need to spend some time figuring everything out.  thanks again for the comments.

Well, you are not the first who thinks Linux = Windows, or Windows = Linux.
Yes, they both are operating systems, that's right, but from there, there are only differences.
You have to learn how Linux, or in this case, Ubuntu, works. It's different, it's new for you. It took you some time to learn how to work with Windows, now take the time to learn Ubuntu.

When you have questions, ask them here. People love to help you. That's why they are here. But don't forget one important thing:
we are all volunteers, loving Ubuntu. We are not professionals, we also don't get paid. We do it to help a person with his/her problem(s). Also to make sure there is one more person using Ubuntu, one more person making the jump towards Linux and away from Windows.

---

