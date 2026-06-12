---
title: "no ubuntu in dual boot"
date: 2010-01-25
forum: General Help
---

### Post by cu19 on 2010-01-25
I have not used the ubuntu OS on this computer for several months becasue ubuntu would not load.  But now i want to try and get ubuntu to work.  I am not sure what all I had tried at that time.  When the system starts it gives me the option to load Windows (XP) or ubuntu.  But when I select ubuntu a screen comes up that says, "Windows could not start because the following file is missing or corrupt: <Windows root>\system32\hal.dll.  Please re-install a copy of the above file."  I did reinstall the Windows XP but that did not fix anything.  I started with ubuntu 8.04 LTS when I first installed ubuntu which did work for quite a few months before i got my failure.  I am running Windows XP service pack 2.  When I choose Windows it starts without any problems.
Any advice that you can give this novice would be appreciated.
Thanks!

---

### Post by hemimaniac on 2010-01-25
If you reinstalled XP it more then likely wrote over the grub instillation, my advice (since you mentioned you were running 8.04) is the following

boot to a ubuntu (8.04/8.10 live cd
open a terminal
sudo grub

 then when in the grub terminal ( denoted by the grub> prefix )

find /boot.grub/stage1
root (hd*,*)   ( *,* will be the numbers returned from the previous command)
setup (hd*)
quit

then sudo grub-update ( or is it update-grub)

sudo reboot

---

### Post by cu19 on 2010-01-25
I ran ubuntu from the live cd I used for installation.  While ii was looking for the terminal icon I noticed the partition icon. I started that since I remembered I had done that during setup.  It came up with a "note indicator" in the NTFS section.  It told me to run "chkdsk /f" a couple of times to fix some problem.  I opened a terminal and after entering the find it came back with "could not find file". So I am doing doing the chkdsk now, and will try the find after that is complete. 
Maybe I am doing something else wrong, when I started ubuntu I used the "try without install" option.  I hope that was correct.

---

### Post by cu19 on 2010-01-25
I finished doing the chkdsk and when I run ubuntu there are no warning flags.  But I failed to mention that when in the partition program, this is what I have - 1) /dev/sda1, fat16. 2) /dev/sda2, ntfs, with "boot" flag. 3) unallocated.  I am wondering if my previous trails a few months ago messed things up.  I would like to be able to install the latest unbuntu in the "unallocated" section I think but I am not sure how to do that.
And again I am trying to give you all the correct information that will help you with my problem.
I really do appreciate your help, and thanks.

---

### Post by hemimaniac on 2010-01-26
OK, now i'm kinda lost, if ubuntu is already installed, my last post will have you up and running in a snap :-k

---

### Post by cu19 on 2010-01-26
After reading your reply I am thinking that I must have deleted ubuntu when I attempted to fix it.  If that is the case then I am guessing I should do a new install with the latest ubuntu.  The last time I used a helper program to install (forget name).
How do I make sure it gets installed in the unallocated section of my hard drive?
Thanks for your help and patience.

---

### Post by hemimaniac on 2010-01-26
This i believe [this]("http://www.psychocats.net/ubuntu/installing") will be more then adequate to help you out.

---

### Post by cu19 on 2010-01-26
Thank you very much for helping me, I now have ubuntu up and running.  And seems to be working great.
I hate to ask you again for help but I do have another question.  I still have the "unallocated" section on my hard drive.  How can I change it so that I am using the rest of the hard drive?  
Again thanks for your help, really appreciated.
If you think I should start a new post just let me know.

---

### Post by hhlp on 2010-01-26
install gparted you can find in synaptic

---

### Post by cu19 on 2010-01-26
I have Gparted loaded and opened and can see the unallocated section.  Now I am not sure what to do.  Do I make it a new one?  And what type partition?  And do I make it a Primary partition or an Extended partition.  I think that is all I need to know but may request additional help.
Thanks to all helping an old man learn new tricks.

---

### Post by hemimaniac on 2010-01-26
Go [here]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/") , and you may want to book mark that home page, there is a fountain of information there with rather in depth walk through s

---

