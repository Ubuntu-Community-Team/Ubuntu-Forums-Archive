---
title: "host name change, now sudo wont work"
date: 2006-04-12
forum: General Help
---

### Post by dyoung66 on 2006-04-12
Howdy all,

I have recently changed the host name on my machine, but it has created two entries in the etc/hosts file.

excerpt from etc/hosts:(1st line only)
127.0.0.1 localhost.localdomain localhost littleguy laptoplinux

Normally I can edit this file as root but because sudo is broken I cant edit the file. 
example:
sudoedit etc/hosts
sudoedit: unable to lookup via gethostbyname()

so I then login as root (or go into recovery mode) to fix it, which normally isnt a problem, but I also have the "over-current change on port #" bug(which is known), which constantly floods my screen with:
[####.####] hub 1-1:1.0: over-current change on port 1

I can still type commands but when I go into vi it gets "flooded" with the same message, making it impossible to remove the invalid entry in my etc/hosts file.

Anyone know a workaround or a way to suppress the flooding messages so I can delete the offending hostname?

Any help would be much appreciated.
Cheers

---

### Post by 5-HT on 2006-04-12
Ouch, if it weren't for the flooding error messages, I'd just boot into single-user mode to get the hosts file cleaned up.

Do you have a linux live CD handy (any one would do)?
If you do, then you could boot using the live CD, mount whichever partition contains /etc on your system, and make the quick change to the file.

If you don't have a live CD...
What about booting up into single-user mode, moving the old hosts file to something like /etc/hosts.default, and creating a new one with ```
 echo "127.0.0.1 localhost.localdomain localhost <hostname>" > /etc/hosts 
``` ?

That way you'd still get all the errors, but as long as the commands get run only that one line should make it to your new temp hosts file.
After that you should be able to boot into your account, clear up the original hosts file, and move it back into /etc/hosts.

HTH

---

### Post by dyoung66 on 2006-04-12
Hi 5-HT,

thanks for your help, that solved my problem!
I dont have a cdrom drive(its an old japanese laptop), but I did use that echo trick to build a new hosts file.

I also had to write my hostname to to my etc/hostname file and now everything is working sweet.

Cheers.

---

