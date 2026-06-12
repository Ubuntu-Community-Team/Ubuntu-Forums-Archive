---
title: "Nautilus showing DUPE share in PLACES?"
date: 2009-11-30
forum: General Help
---

### Post by BassKozz on 2009-11-30
I just upgraded from Jaunty to Karmic, and now in my Places it has one of my Shares listed twice.
My share is setup via /etc/fstab like so:
```
//192.168.1.103/RAID-storage /media/Unicorn-NAS   smbfs  auto,credentials=/root/.credentials_Unicorn-NAS,uid=1000,umask=000,user,exec   0 0
```

Now **Unicorn-NAS** is listed twice:
[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/places-screenshot.png[/IMG]

When I click on one of the shares (top "Unicorn-NAS" in the above screenshot), I get the following:
[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/Screenshot-UntitledWindow.png[/IMG]

But when I click on the other (bottom "Unicorn-NAS" in the above screenshot) it opens up the share (as it should).
So why now (after upgrading to Karmic) do I have a duplicate tab for **Unicorn-NAS**?

---

### Post by BassKozz on 2009-12-01
:bump:

---

### Post by callan79 on 2009-12-02
> **BassKozz said:**
> I just upgraded from Jaunty to Karmic, and now in my Places it has one of my Shares listed twice.
So why now (after upgrading to Karmic) do I have a duplicate tab for **Unicorn-NAS**?

Hi BassKozz,

I have the same problem - I'm running 9.10 64-bit, what are you running?

I have these lines in my fstab, they are two shares on the same NAS I've been using for over 2 years :

```

//192.168.7.2/media /media/media cifs auto,nounix,noserverino,user=username,password=password,uid=root,gid=bogglers,dir_mode=0770,file_mode=0770 0 0
//192.168.7.2/shared /media/shared cifs auto,nounix,noserverino,user=username,password=password,uid=root,gid=bogglers,dir_mode=0770,file_mode=0770 0 0

```

This has always worked just fine (although prior to 9.10 I never needed the 'noserverino' option).

Now on 9.10 I get the two shares showing up twice - one works, the other gives a "cannot mount" error.

Funnily enough, I have a laptop running 9.10 i386, and this problem DOES NOT OCCUR on that computer. The fstab mounts are the same.

Are you running i386 or 64 bit?

Cheers
Callan

---

### Post by BassKozz on 2009-12-02
> **callan79 said:**
> 
Are you running i386 or 64 bit?

64bit...
So this seems to be a 64bit issue... 
Maybe a launchpad ticket is in order?

---

### Post by BassKozz on 2009-12-02
Bug filed: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/491489](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/491489)
And: [https://bugzilla.gnome.org/show_bug.cgi?id=603628](https://bugzilla.gnome.org/show_bug.cgi?id=603628)

---

### Post by BassKozz on 2009-12-14
Just a quick update the bug: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/491489](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/491489)
Has been assigned to Ubuntu Desktop Bugs

---

### Post by gtr33m on 2011-08-16
I realise this is an old post, so there's probably no one following it, but I'm experiencing the exact same problem on natty 11.04 x64, so if the problem has been marked as fixed, it still exists

---

