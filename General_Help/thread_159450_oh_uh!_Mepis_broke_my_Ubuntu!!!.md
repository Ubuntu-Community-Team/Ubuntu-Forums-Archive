---
title: "oh uh! Mepis broke my Ubuntu!!!"
date: 2006-04-12
forum: General Help
---

### Post by Burgresso on 2006-04-12
I am so mad....:twisted: 

Okay, here's what happened. 

I downloaded the live 6.0 Alpha of MEPIS. I didn't like so I removed the CD and restarted the computer.

On restart, it notified me that a bunch of things 'failed'...I was a away for a few moments, so I didn't get to see the details. So I restarted again...

On start up, when checking the root file system, it says I have a root file system with errors. Now it is checking my computer and taking forever.

I've never had luck with Mepis, now it seems like the distro is mad at me.

It's telling me this:

>  
Checking root file system
/ contains a file system with errors, check forced

(talks about a buffer i/o error ; something about block 5281858)

Unexpected inconsistancy; RUN fsck Manually
(i.e., without -a or -p options)

fsck failed. Please repair manually and reboot. Please note that the root file system is currently mounted read-only to remount it read-write:
# mount -n -n remount, rw/

I've looked around and found this thread, among others:
[http://ubuntuforums.org/showthread.php?t=124774](http://ubuntuforums.org/showthread.php?t=124774)

It asks me to fix blocks, but they keep on coming up and asking to fix other blocks and such.

But the thing is, *this hard drive is about 8 months old*...

:twisted: :twisted: 

Okay...please advise:
1. is it fair to blame mepis on this?
2. can I salvage my files? what should I do?

---

### Post by xXx 0wn3d xXx on 2006-04-12
[QUOTE=Burgresso]I am so mad....:twisted: 

Okay, here's what happened. 

I downloaded the live 6.0 Alpha of MEPIS. I didn't like so I removed the CD and restarted the computer.

On restart, it notified me that a bunch of things 'failed'...I was a away for a few moments, so I didn't get to see the details. So I restarted again...

On start up, when checking the root file system, it says I have a root file system with errors. Now it is checking my computer and taking forever.

I've never had luck with Mepis, now it seems like the distro is mad at me.

It's telling me this:



I've looked around and found this thread, among others:
[http://ubuntuforums.org/showthread.php?t=124774](http://ubuntuforums.org/showthread.php?t=124774)

It asks me to fix blocks, but they keep on coming up and asking to fix other blocks and such.

But the thing is, *this hard drive is about 8 months old*...

:twisted: :twisted: 

Okay...please advise:
1. is it fair to blame mepis on this?
2. can I salvage my files? what should I do?[/QUOTE]

Does it cache things on the hdd ? B/c I'm thinking that it puts some stuff on the hdd (caches junk) and then cleans it up and the end of the session. I am almost certain that you will be able to salvage your data. Try reinstalling but no formatting.

---

### Post by dermotti on 2006-04-12
Mepis shouldnt touch your harddrive at all, unless you select install. Im guessing something else happend.

---

### Post by Burgresso on 2006-04-12
Thanks to both responses.

> Try reinstalling but no formatting.

How do I do that? It seems that I have to partition? or Does this not have anthyting to partitioning? :p 

Thanks again

---

### Post by xXx 0wn3d xXx on 2006-04-12
[QUOTE=Burgresso]Thanks to both responses.



How do I do that? It seems that I have to partition? or Does this not have anthyting to partitioning? :p 

Thanks again[/QUOTE]
Well, I'm not sure that this would work but you can insert the install cd and then procede to the partition thing and then go under your old partition and press enter on "Yes Formatt it." After pressing enter it will say, "No don't formatt." Then you can procede with the install. It will keep your home directory and other settings. 

Note: Don't do this until someother people give you suggestions and they don't work.

---

### Post by Burgresso on 2006-04-12
I'm the kind who jumps in...so I tried to reinstall...

The installation screen is red. It says

> The ext3 file system creation in partition #1 of IDE1 master (hda) failed.

Ehr, help?   :) :-k

---

### Post by oblio on 2006-04-13
[QUOTE=dermotti]Mepis shouldnt touch your harddrive at all, unless you select install. Im guessing something else happend.[/QUOTE]

It doesn't touch anything on your HD when one runs the Livecd. HD-partitions aren't even mounted...  The Mepis 6.0 alpha1 testversion did not break anything. 

On the other hand:  If I use a LiveCD (Knoppix / Mepis / whatever) to reformat some existing empty partitions (ext3 to reiserfs), then a later start of an earlier installed (K)ubuntu will stop at the prompt (Ctrl-D get's one going again...) stating that it cannot find the ext3 partitions and the filecheck fails.    
THAT doesn't happen in Mepis, since it verifies the filesystems of existing partitions - instead of assuming it's still the same as before.  Now, can I blame Ubuntu for that?  Of course not.  We are using testversions - all of us.

Regards,  Ko

---

### Post by Sef on 2006-04-13
Did you make a home partition?  If so, then delete and reinstall the other partitions, but leave your home alone.  Your data should be safe.  If you don't have a back up, I would use something like system rescue cd to see if you can back it up before trying to reinstall the os.

---

### Post by Burgresso on 2006-04-13
Thanks for the help. I'll keep ya'll posted.

---

### Post by Burgresso on 2006-04-22
I can't save it. I'm going to have to return my hard drive...thank fully it is under warranty :???:

---

