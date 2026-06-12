---
title: "How can I remove the &quot;Windows Network&quot; link from nautilus network area?"
date: 2011-01-09
forum: General Help
---

### Post by darthpenguin on 2011-01-09
Hi all

I recently installed a second router in my home to expand my network. I am now unable to browse Windows shares on my network. This is not a big deal because I don't actually use Windows anywhere on my network (the shares where samba shares on various linux boxes). I can just share files via sftp so I just removed all samba packages on all my machines via apt-get. I still see the "Windows Network" icon when I browse to Places -> Network. I don't use it and would like to get rid of it, how can I do that?

Also when I browse to Places -> Network the window can sometimes take 30 sec - 1 min to open. Why so slow? any ideas? thank you.

---

### Post by nickytheknife on 2011-03-02
> **darthpenguin said:**
> Hi all

I recently installed a second router in my home to expand my network. I am now unable to browse Windows shares on my network. This is not a big deal because I don't actually use Windows anywhere on my network (the shares where samba shares on various linux boxes). I can just share files via sftp so I just removed all samba packages on all my machines via apt-get. I still see the "Windows Network" icon when I browse to Places -> Network. I don't use it and would like to get rid of it, how can I do that?

Also when I browse to Places -> Network the window can sometimes take 30 sec - 1 min to open. Why so slow? any ideas? thank you.


Any news on this ?

---

### Post by goscuter1 on 2011-03-18
> **nickytheknife said:**
> Any news on this ?

Any news on this? 

I have the same issue... :confused:

---

### Post by goscuter1 on 2011-03-25
I'm new to these forums, but is it concerning that no one seems to know? 

I have a Windows network showing, and no Samba (which I thought would be the cause of it?)


> ~$ sudo apt-get remove samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package samba is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I wish I could figure out what's going on here ;(

---

### Post by darthpenguin on 2011-03-25
Nice to know I'm not alone in this. I removed samba too but the "Windows Network" icon is still there. If anyone has any ideas please let us know. thanks.

---

### Post by goscuter1 on 2011-03-25
It would be, indeed... :confused: 

I'm starting to think this might be more serious than a mere peculiarity. I have samba folders installed. But when I try to remove samba, it says I never had it?

I disabled the onboard LAN controller in my BIOS, then ran netstat. With no network connection at all (icon had X over it), my netstat is showing CONNECTED streams pages and pages long. Screenshot for verification: [http://i.imgur.com/hjz9Y.png](http://i.imgur.com/hjz9Y.png)

I'm running zenmap now (after I re-enabled LAN) - yeah I think there's some problems here. Have you encountered anything beyond the ordinary connection-wise (aside from the unexplainable Windows Network showing, and the lag)?

---

