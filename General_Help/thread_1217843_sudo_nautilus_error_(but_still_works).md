---
title: "sudo nautilus error (but still works)"
date: 2009-07-20
forum: General Help
---

### Post by brookie on 2009-07-20
Hello,

I am running Intrepid Ibex with all current updates on two Dell Inspirons. 

I am getting errors on two machines when running sudo nautilus: 

**********
1. error on my inspiron 600m
sudo nautilus
[sudo] password for fontinalis: 
Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus:16323): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

2. inspiron 5150 - inntrepid via external usb
sudo nautilus
[sudo] password for kiki: 
Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus:9032): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


--- Hash table keys for warning below:
--> file:///root

(nautilus:9032): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:9032): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
seahorse nautilus module shutdown
Shutting down nautilus-share extension
*********

Note that sudo nautilus works and I can copy and paste files etc... but I'm a geek and I wanted to troubleshoot the errors and fix them and don't know where to start. 

Let me know if you have any ideas.

Thanks, 
brookie

---

### Post by mc4man on 2009-07-20
They're 'warning's', not errors and of no real consequence. The first one refers to samba, most installs don't have it enabled. (so the warning

The second is just part of a debug, harmless. You'll notice the # of elements equals directories deep you've gone while in nautilus as root plus one.

see here, read down a bit towards end

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/93408](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/93408)

You can also just go Alt+F2, type in gksudo nautilus and never see anything - don't ck. "run in terminal"

Or install nautilus-actions and  set up a nautilus action for the right click context menu - 'open dir as root' (among other useful nautilus actions

---

### Post by brookie on 2009-07-20
Thanks mc4man. I also found another bug related to nautilus share and samba here: 
[https://bugs.launchpad.net/ubuntu/+source/nautilus-share/+bug/225859]("https://bugs.launchpad.net/ubuntu/+source/nautilus-share/+bug/225859")

One suggestion on that link was to remove nautilus-share if samba isn't installed. 

I'll definitely try your right click trick though. Cheers.

---

