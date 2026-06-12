---
title: "What's going on with my raid array?"
date: 2011-05-15
forum: General Help
---

### Post by bogoliubov on 2011-05-15
Hello. I have a HTPC set up with three identical disks forming a raid-5 partition ( /home ). There is also a root partition raid-1 formed from 2 of the disks. OS is Ubuntu 10.04 (32 bit).

Now to my problem: when I listen to the computer, it sounds as though the drives are used constantly, even though the load is very low. The sound is not the one you can hear when a disk is about to give up, but rather normal harddrive sound. But constantly and lots of it!

Secondly, in /var/log there are about 8 Gb of logs from the mail daemon. 
Running :
sudo aptitude why procmail
gives me (in swedish):
i   mdadm   Rekommenderar postfix | mail-transport-agent
p   postfix Föreslår      procmail                      

So why do I get so much mail from mdadm? How can I read the mails? Do these mails explain why I have such high disk activity, or are they the cause of the disk activity? Can I configure how mdadm sends mail?

Also, how can I clean out the log files? Just removing them?

The drives seem to function OK. The SMART status seems OK, no errors are reported.

I'd really appreciate any help on this. I worry for my raid array!

---

### Post by The Real Dave on 2011-05-15
I'm not at my Ubuntu computer at the moment, but as far as I recall, the mail is stored at /var/log/mail. You can read it just with a text editor. 

It's probably some sort of automatic report setting in your mdadm.conf, you might want to take a look at that.

As for the logs, you can safely delete them as you would a normal file (rm) but using sudo.

---

### Post by bogoliubov on 2011-05-15
Thanks! How can I see if the mail-daemon is working? One of the largest files in /var/log is mail.warn.1 .
 
I can't find any setting in mdadm.conf about when mail should be sent.

---

### Post by bogoliubov on 2011-05-15
Hmm, it could be related to this: [http://ubuntuforums.org/showthread.php?t=1701258](http://ubuntuforums.org/showthread.php?t=1701258) 

I will try and see what happens...

---

