---
title: "problem with software center downloading"
date: 2009-11-13
forum: General Help
---

### Post by zeth01 on 2009-11-13
it says "Waiting for other software managers to quit"
this wont go away after hours and re-start
so how do i fix this so i can get the software.  if i download through the terminal i don't get exactly what I want.
i downloaded blender but i cant get the desktop icon for it because i don't know how to since it wasn't an automatic download through the Software Center

any help would be appreciated

---

### Post by ZaHACKieL on 2009-11-13
Have you tried using Synaptic Package Manager? You can find it in the System > Administration menu

---

### Post by Anarci on 2009-11-13
Try starting software-center from a terminal and posting the output here

---

### Post by zeth01 on 2009-11-13
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


thats what i get when trying to open synaptic package manager


ok i ran that and it opens now... ill keep youall updated

---

### Post by zeth01 on 2009-11-13
well im using as i stated nad all is well except that i still can't get the software center to work. oh well

---

### Post by Anarci on 2009-11-14
Seems like an update/upgrade was interrupted and now I assume you ran 
```
sudo dpkg --configure -a
```to fix that. So why is the software center still not working, is it giving another error now?

---

### Post by jcs224 on 2009-12-05
Hi there!  

I am having the exact same problem.  I did the configure thing in the command line as stated above, but that did not work either...could not connect to the sourceforge site or something, connection kept timing out.  I tried the same thing by booting in recovery mode and trying to remove old defective packages...still no luck.  Any fix?  If not...

I might have to switch to Fedora... please don't make me!  Ubuntu 9.10 has been giving me lots of problems...

**UPDATE: ** The configure thing finally worked.  It was seemingly a network problem I was having.

Thanks so much for your help!

---

### Post by ShadenSys on 2010-02-01
im having the same problem. wont let me remove stuff i downloaded, keeps giving me 'waiting for other software managers to close'. went to terminal with the "sudo dpkg --configure -a" command and gets error[FONT=monospace][FONT=Verdana] "dpkg: parse error, in file '/var/lib/dpkg/updates/0002' near line 0: field name '   "

any ideas? im lost here and new to ubuntu. running out of resource room and need to clear up stuff. unwanted programs are my first choice. any others?
[/FONT][/FONT]

---

