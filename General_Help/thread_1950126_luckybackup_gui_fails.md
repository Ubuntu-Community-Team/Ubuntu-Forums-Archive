---
title: "luckybackup gui fails"
date: 2012-03-31
forum: General Help
---

### Post by F35 on 2012-03-31
LuckyBackup 0.4.6-1 is loaded on oneiric ubuntu 11.10.  Don't know what version I had a month ago, but I do know that the gui would start.  Now, I get an hourglass for a minute then nothing.  If I use LuckyBackup SuperUser, the gui starts as expected.

Anyone know how to fix, or do you know how to obtain a previous version to try?

---

### Post by dino99 on 2012-03-31
Now Ubuntu have made a better choice: deja-dup

Déjà Dup is a simple backup tool. It hides the complexity of backing up the
Right Way (encrypted, off-site, and regular) and uses duplicity as the
backend.

Features:
 * Support for local, remote, or cloud backup locations, such as Amazon S3,
   Rackspace Cloud Files, and Ubuntu One
 * Securely encrypts and compresses your data
 * Incrementally backs up, letting you restore from any particular backup
 * Schedules regular backups
 * Integrates well into your GNOME desktop

---

### Post by F35 on 2012-03-31
I loaded luckybackup 0.4.7-1.  No change.  

In theory, it appears I should be able to go to a terminal and load luckybackup at the prompt.  However, I get an error:  Segmentation Fault.  Looks like that has been an issue through older versions of luckybackup.  

Any thoughts?

---

### Post by F35 on 2012-03-31
Dino99,

I may switch.  I had invested some time getting luckybackup to run and was satisfied it was working till now.  Disappointing.  Still hoping someone has a quickfix so that I don't have to switch.

---

### Post by jerrrys on 2012-03-31
Im running 12o4 and after reading your post i installed lucky (0.4.6-1), and seems to work fine (non sudo).

I wonder if some configuration files have been left over.  Have you tried to purge it?

[https://help.ubuntu.com/community/AptGet/Howto#Removal_commands](https://help.ubuntu.com/community/AptGet/Howto#Removal_commands)

---

### Post by F35 on 2012-04-03
I did the following:

apt-get remove luckybackup

and 

apt-get purge luckybackup

Then I reloaded luckybackup

apt-get install luckybackup
Still behaving the same.  Luckybackup is not starting the gui, but luckybackup super user works.

Still getting the "segmentation fault".

Just as a reminder, luckybackup was working on this machine about  a month ago, so my assumption is that some automatic update changed the machine impacting the luckybackup.

What seems strange is that luckybackup super user still seems to work fine.

Thanks for the tip jerrys, I had not tried purge...it was a good idea.

Other ideas?

---

### Post by F35 on 2012-04-03
I found this:  [http://aplawrence.com/Unixart/segmentation_fault.html](http://aplawrence.com/Unixart/segmentation_fault.html)

The point of that link is that hardware is typically an issue for segmentation fault.  

That is another good idea, since I just recently plugged in an external usb drive to the machine having the problem.  So, haven't had time to check this idea out, yet.  But the timing if plugging in the external hard drive and the failure of luckybackup may be more than coincidence.

---

### Post by F35 on 2012-04-05
Turns out that removing the external hard drive did not make a  difference to luckybackup, even after rebooting and removing and purging  and re-installing again.  So, this issue is not yet solved.

---

### Post by colin.p on 2012-04-06
Unfortunately, I do not have a solution for the problem you are having in Lucky Backup. However, I myself am a total believer in "redundancy"  and have two or more programs that will do the same thing. So I run Lucky Backup, Deja Dup, as well as Back in Time for my backup strategies.
If one stops working, I have at least another program and its corresponding backup to fall back on.

Forgot to add, I do the backups to three different drives, as well as two different computers. I'd also backup to an "offsite" location if I had a real high-speed connection, not this crappy Xplornet wireless "dialup" connection(I refuse to call it high-speed).

---

### Post by Zill on 2012-04-06
F35:  luckyBackup saves its settings in a hidden (dot) directory within your home directory.  If this is corrupted then this *could* cause your problem, particularly as the superuser profile works OK.

I would try generating a new "clean" settings directory to see if the "new" version works OK.  To do this, I suggest you simply rename the old one which will then mean that a new directory will be created when you run luckyBackup again.  Note that you can always revert to the old version by reversing the command in 3) below.

1)  Close luckyBackup
2)  Open a terminal (Ctrl-Alt-t)
3)  Paste the following code into the terminal...
```
mv ~/.luckyBackup ~/.luckyBackup_old
```
4)  Open luckyBackup
5)  Reconfigure all your settings as required
6)  Establish if luckyBackup is working OK

---

### Post by F35 on 2012-04-08
Zill, I declare this issue solved.  Before I followed the steps recommended by Zill, I followed the remove, purge, and re-install steps jerrys provided.  Looking now at what jerrys said, I think he was suggesting what Zill spelled out for me.  

Anyway, thanks.

As for colin.p, while your methods might seem like overkill to some, I concur with the spirit of your thought.  I am sure this is important to you as well, even though you didn't mention it...on top of having reliable backups in many forms, it is important to me to be able to go back in time to prior versions.

Thanks for everyone's input in solving my problem.

---

### Post by Zill on 2012-04-08
F35:  I am pleased you have resolved the problem.  Please now use the "Thread Tools" link at the top to mark the thread as "Solved" - only you as the original poster can do this. ;-)

---

