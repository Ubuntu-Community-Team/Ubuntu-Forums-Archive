---
title: "Thunderbird can't delete messages, says another user is using the folder"
date: 2011-09-14
forum: General Help
---

### Post by dirtyvicar on 2011-09-14
Hi. I have been having a problem for a few days trying to delete e-mail in Thunderbird. If I click the delete button, or hit the delete key for a message in any folder, I get the response:

The operation failed because an other operation is using the folder. Please wait for that operation to finish and then try again.

There is only one copy of Thunderbird running, so nothing else is using the folder. I tried rebooting, shutting down Thunderbird for a while, still can't delete messages.

Running Ubuntu 10.04 LTS, Thunderbird 3.1.13.

I searched around, and saw recommendations about rebooting or shutting down Thunderbird for a while. Didn't help. 

At one point I found a thread that discussed locks. I found a lock in my .thunderbird/4u229wim.default directory:

-r--r--r-- 1 mdc mdc       1 2011-09-12 09:34 lock -> 192.168.1.7:+1927

The lock is 2 days old at this point. My IP address isn't 192.168.1.7 any more (I've rebooted since then). It looks like the name of the lock is the IP address:+<first octet|last octet>

I am able to delete mail by dragging to the Trash under the 'Local Folders' hierarchy, but that's inconvenient...

Is there anyway to release the lock? Or is there any other way around this?

Thanks!

---

### Post by SeijiSensei on 2011-09-15
> **dirtyvicar said:**
> Is there anyway to release the lock?

```
rm -f lock
```

Use 'ls -la' to list the directory as well.  Firefox uses a .parentlock file as well that doesn't appear in ordinary directory listings because it's a "hidden" (starts with a dot) file.  I don't think that's true for Thunderbird, but it doesn't hurt to check.

Both programs occasionally leave stale locks when the program or system crashes.  It used to be especially annoying with Firefox and left a lot of people wondering why they couldn't launch the program after logging back in.  It seems like Mozilla has done a pretty good job of cleaning these up in more recent releases, but stale locks still occur from time to time.

---

### Post by Azdour on 2011-09-15
Hi,

Just to confirm that Thunderbird has both a lock and .parentlock file.

But I'm not sure if this is your issue. In the past when my Thunderbird has closed without releasing the locks, I cannot re-open Thunderbird at all until I remove them.

I believe that sometimes the .msf files can become corrupted. There should be a repair option when you right click on a folder and choose properties - this may or may not work. I strongly suggest you make a back-up of your profile/emails before you do this though...

---

### Post by omegaomega on 2011-09-30
Hi, dirtyvicar,
 
I have just had the same message while trying to delete e-mails.  I tried several [COLOR=black][FONT=Verdana]offered [/FONT][/COLOR]solutions without success.  Finally, I discovered that several files in the mail directory had mysteriously been flagged as read-only.  I cleared the read-only flags, and that solved my problem.  I hope that your solution can be as simple.
 
Cheers,
Randy

---

### Post by 01000111 on 2011-11-03
Just ran into this problem myself.  The solution that worked for me:

- right click on the folder
- click properties
- click repair folder

try to delete the message again.  Problem solved!

Thunderbird 3.1.15 on Xubuntu 11.04

G

---

