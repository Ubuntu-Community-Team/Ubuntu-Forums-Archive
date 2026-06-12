---
title: "Can't update/install a program"
date: 2009-07-19
forum: General Help
---

### Post by Martin Neshev on 2009-07-19
Hey guys, I'm new here and I don't know if this is the place for this thread but whatever :P
soo when I try to install a program or update my ubuntu to 9.04 this thing shows up 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


Soo what do I do? lol


And I've got 1 more question...
I've got 80 GB of music and 90% of it is locked! link for screenshot>  [http://store.picbg.net/pubpic/1A/86/3dfbecbbc58b1a86.png](http://store.picbg.net/pubpic/1A/86/3dfbecbbc58b1a86.png)

how do I fix this also?

I'm sorry for the dumb questions, for wasting your time and for my bad english.

Love you all linux users :D 

martin neshev

PS> I'm using linux ubuntu 8.10 (intrepid)

---

### Post by 3rdalbum on 2009-07-19
Go to a terminal and run the command that it suggests, but you need to run it as root by putting the word "sudo" before it:

```
sudo dpkg --configure -a
```

That usually happens when you interrupt an install or upgrade; or if you try and install a package that is incompatible with your version of Ubuntu.

----

If those folders are locked, it usually means that they were created by root - this includes copying them from another disk using a file browser that you have started as root.

Just open a root file browser:

```
gksudo nautilus
```

Select the "locked" folders, right-click and click Properties, then go to Permissions and change the owner to your username (or set Read/Write permission to everyone). And next time try and use your normal user account wherever possible, and only elevate to root if you absolutely need to.

---

### Post by Martin Neshev on 2009-07-19
I tried this and..  




neshev@neshev-desktop:~$ sudo dpkg --configure -a
[sudo] password for neshev: 
Setting up libc6 (2.8~20080505-0ubuntu9) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Aborted
dpkg: subprocess post-installation script returned error exit status 134
neshev@neshev-desktop:~$





EDIT:

where do I type this code? :oops:

---

### Post by jimmyhacker on 2009-07-19
its a fatal bug,not your fault.now you must re-install,probably.report bug in launchpad and install 8.10 or 8.04.

---

### Post by Martin Neshev on 2009-07-19
damn it ;d
so I'll have to delete my whole hard disc when re-installing?  is there a way to save my music? (without usb memory, disc etc etc)

---

