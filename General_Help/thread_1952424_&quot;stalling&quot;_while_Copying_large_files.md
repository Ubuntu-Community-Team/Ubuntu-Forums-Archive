---
title: "&quot;stalling&quot; while Copying large files"
date: 2012-04-04
forum: General Help
---

### Post by AMCjavelin74 on 2012-04-04
I run Ubuntu 11.1 on a system I've had since new back in 2004 running XP.  I rebuilt the system keeping the main HDD and XP in 2009 being on a budget and all, and it was good.  Until fall 2011 when the system went on the fritz.  I managed to get it to boot and saved a lot of my files, even my old IE favorites (I've used firefox since around 2006 though, so I wonder what old sites are in there).  Once my files were safely backed up, I decided to try the linux juice.  So far so good, "growing pains" aside.)

Well, when copying large files from one external HDD to another external HDD the system 'stalls'.  It starts out saying it'll take "5 minutes" or so for example, and about halfway through the progress bar stops and the now "4 minutes" starts counting upward to "10 minutes" and a while later "20 minutes" and the next day... well, you get the point.

I believe all of my external HDDs are still formatted for Windoze, so this may be a factor.  Hopefully I can "empty" my main HDD out and reformat it, "empty" my backup, and reformat that so I have a "Linux friendly" setup.

I found a thread here that didn't help much, it involved copying and pasting into terminal off a link from one of our members who's from Australia.  That didn't help in my case.

Well, I appreciate the help.
Matt

---

### Post by philinux on 2012-04-04
Yes this is an ongoing bug.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/500069](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/500069)

It's getting some more attention now too.

---

### Post by AMCjavelin74 on 2012-04-04
I found this at the link you posted...
*[Brad Figg (brad-figg)]("https://launchpad.net/%7Ebrad-figg")             wrote             on 2012-01-31:               [                 **Test with newer development kernel (3.2.0-12.20)**               ]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/500069/comments/49")*                                             *[ #49]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/500069/comments/49")*                                                               *Thank you for taking the time to file a bug report on this issue.*
 *However, given the number of bugs that the Kernel Team receives  during any development cycle it is impossible for us to review them all.  Therefore, we occasionally resort to using automated bots to request  further testing. This is such a request.*
 *We have noted that there is a newer version of the development kernel  than the one you last tested when this issue was found. Please test  again with the newer kernel and indicate in the bug if this issue still  exists or not.*
 *You can update to the latest development kernel by simply running the following commands in a terminal window:*
 [I]    sudo apt-get update
    sudo apt-get upgrade[/I]
 *If the bug still exists, change the bug status from Incomplete to  Confirmed. If the bug no longer exists, change the bug status from  Incomplete to Fix Released.*
 *If you want this bot to quit automatically requesting kernel tests, add a tag named: bot-stop-nagging.*
 * Thank you for your help, we really do appreciate it.*

              

So, we'll see what happens.  As for the last paragraph in the above post, I wonder if I added a tag named wife-stop-nagging...:p

---

### Post by AMCjavelin74 on 2012-04-04
I tried copying a 1.4GB file (lots of files!) from external HDD 1 to external HDD 2, and after 354mb, it 'stalled'.

Hmmm, so I'm sure it's a known issue from looking at the links, just not a known fix?

---

### Post by AMCjavelin74 on 2012-04-10
Since I'd be busy over Easter weekend, I decided to copy the 80gb hdd (70 of it used) onto my 'archive' (backup) drive.    This was Friday after work.  It's about 60% the way through.:mad:

I wonder how much longer it'll take... anyone ever do this and 'wait it out'?

Will my HDD be faster when it's reformatted in a linux-friendly way (I forget what it's called, but Windoze is not compatible with it)?

---

