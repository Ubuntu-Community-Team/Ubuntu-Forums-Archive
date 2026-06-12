---
title: "Update Manager - greyed-out objects"
date: 2010-07-23
forum: General Help
---

### Post by bloodorange on 2010-07-23
I've just installed the latest (today's) updates to Lucid.  However, after Update Manager had finished, there were three items still left under "Recommended Updates", but these items are greyed-out.  Running Update Manager again doesn't sort it out, and updating from a terminal doesn't sort it out.

Does anyone know why this has happened?

I've recorded a short video to show Update Manager and the "failed" update, which you can see here: [http://dl.dropbox.com/u/1098200/out.ogv](http://dl.dropbox.com/u/1098200/out.ogv)

---

### Post by cookiepuss on 2010-07-23
I'm having the same issue with the same updates. I have just updated Firefox and other packages while the three for new Linux headers remain grayed out.

I got a message from/in Update Manager instructing me that Dropbox must be started. I started Dropbox and attempted the update again but with same results.

I ran Synaptic's "fix broken packages" command and it replied that dependency issues had been resolved.

Ran update manager again and still same results. I wonder if Dropbox is lacking a needed package for the kernel update?

I'll keep looking...

---

### Post by j7%&lt;RmUg on 2010-07-23
Well, this (if its what im thinking it is) is an easy fix, in the terminal type:
```

sudo apt-get dist-upgrade

```

Try that.

---

### Post by cookiepuss on 2010-07-23
@nisshh thanks for the suggestion. Here is the result:

kevin@wopr:$ sudo apt-get dist-upgrade
[sudo] password for kevin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
kevin@wopr:$ 

It's seems a dependency can't be satisfied? Perhaps nautilus-dropbox is the culprit?

@bloodorange are you running Dropbox as well?

---

### Post by mc4man on 2010-07-23
See here and be patient..
[http://ubuntuforums.org/showthread.php?p=9627247#post9627247](http://ubuntuforums.org/showthread.php?p=9627247#post9627247)

---

### Post by bloodorange on 2010-07-23
Thanks for your replies.  It looks like we just need to wait, then, as mc4man and his link has pointed out.

No problem.

Cheers

---

### Post by vanquishedangel on 2010-07-24
I just updated to the Linux headers right off the site and then the updates installed and were no longer grayed out hope this works for the rest of ya


[http://www.ramoonus.nl/2010/05/linux-kernel-2-6-34-installation-guide-for-ubuntu-linux-10-04/](http://www.ramoonus.nl/2010/05/linux-kernel-2-6-34-installation-guide-for-ubuntu-linux-10-04/)

btw running ubuntu 10.04 Lucid

---

### Post by ivan-wells on 2010-07-24
Same problem last night. Just used update manager before writing this message today and there are more updates, none were greyed out and all installed as normal. Would appear that just wait is the right approach for most as no other action was necessary for me.

---

### Post by vanquishedangel on 2010-07-24
> **vanquishedangel said:**
> I just updated to the Linux headers right off the site and then the updates installed and were no longer grayed out hope this works for the rest of ya

[http://www.ramoonus.nl/2010/05/linux-kernel-2-6-34-installation-guide-for-ubuntu-linux-10-04/](http://www.ramoonus.nl/2010/05/linux-kernel-2-6-34-installation-guide-for-ubuntu-linux-10-04/)

 ignore this post lol it worked but messed up my ati drivers, but they seemed to work fine also games wouldnt play because of it sorry. if you followed it and had issues, "sudo aptitude purge" the files and then run "sudo update-grub"

---

### Post by bloodorange on 2010-07-24
> **ivan-wells said:**
> Same problem last night. Just used update manager before writing this message today and there are more updates, none were greyed out and all installed as normal. Would appear that just wait is the right approach for most as no other action was necessary for me.

Yep, mine's cleared-up now, too.  I should've been more patient.  I'll sleep better tonight now!:)

---

### Post by dcstar on 2010-07-24
Repositories that are not set up correctly can advertise updates as available that they have not actually downloaded as yet. They should be set up to only advertise a list of new updates after they have actually downloaded all of those updates.

Basically waiting for the repository to catch up will eventually solve the problem - and selecting a non-default repository can help as they are usually far less loaded that the main ones that most users never bother to change from.

---

