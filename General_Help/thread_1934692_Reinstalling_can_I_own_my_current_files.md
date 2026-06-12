---
title: "Reinstalling: can I own my current files?"
date: 2012-03-02
forum: General Help
---

### Post by Xero Xenith on 2012-03-02
**Situation**:
I have a problem with my install of Ubuntu. Several problems, actually. It looks like a helluva lot of junk has built up in my settings and who knows where else! :p

Basically what I want to do is reinstall. The problem is, I have 1.2 TB of files that belong to me. I'm pretty sure the junk is all the stuff in my Home folder (~5GB), which is separate from the useful stuff I file away nicely in my /home/data (~1.5 TB) folder.

**Questions**:
Let's say I deleted my /home/*user* folder (so my user doesn't exist) and reinstalled Ubuntu with the same username in the same /home/ partition. _Would I be automatically be the owner of my old files in /home/data since I have the same name?_

What if I did this for the release of Precise - would it work then?

**Apology**:
Sorry, I know this has probably been asked a million times, but I did search and I got nicely lost in a sea of permissions and chmod and everything else ever :)

---

### Post by papibe on 2012-03-02
Hi Xero Xenith.

Probably yes, but maybe not.

I've done similar reinstallations like that, and it usually works fine. In a few occasions though, the installation process didn't set the typical 1000 uid for the basic user, but 1001.

In any case, that is not really a problem since the new user will belong to the admin group, and he'll be able to change the owner if necessary.

For instance:
```
sudo chown -R newuser:newuser /home/data
```
Hope it helps, and tell us how it goes.
Regards.

---

### Post by Xero Xenith on 2012-03-03
Ah, so the first user on any install should automatically get the same ID? That's very useful! Thank you :)

On a side note, would you happen to know any way to get a list of all packages installed that you installed yourself (from repos or from files; everything installed that's not on the default install?). I always find myself struggling to find exactly what I had installed.

I might wait until Precise; may as well do it properly! Then I'll have everything fresh for the first time since, oh, Jaunty? :P

---

### Post by snowpine on 2012-03-03
Before you go through aaaaallllll that trouble, try creating a new user. If the new user works OK then your hypothesis may be correct, that hidden settings in your /home folder are causing the difficulties.

My experience confirms papibe's, that if you have the same user name and ID, you will have no problems with ownership of the files. (And of course you have a full backup, right?)

---

### Post by nothingspecial on 2012-03-03
To develop the idea further each subsequent user you create will get the next uid 1001, 1002, 1003

If you have multiple users, add each new user in the correct order.

---

### Post by Xero Xenith on 2012-03-04
Thanks a lot guys! Yes, I've made a new user and it seems to run fine. I'll be trying this for sure :)

But one thing that still seems not to work is deep file searching. I thought Unity had a full filesystem index/search dealie built in - so even if I haven't opened or used a file, it can still find it. This doesn't seem to work. Is this how it should be?

If so, is there a way to get full, quick, indexed file search in Ubuntu? Something built in to Unity would be neat. (If the answer's non-trivial I'm happy to make a new thread! :P)

EDIT: A bit of research says this should be available with "updatedb" as a backend?

---

