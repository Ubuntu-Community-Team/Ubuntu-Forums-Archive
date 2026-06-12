---
title: "Peculiar upgrade difficulty with 10.4"
date: 2010-05-29
forum: General Help
---

### Post by Coco999 on 2010-05-29
I can't upgrade. I get:

> **Could not calculate the upgrade**

An unresolvable problem occurred while calculating the upgrade:
The package 'skype-common' is marked for removal but it is in the removal blacklist.

This can be caused by:
* Upgrading to a pre-release version of Ubuntu
* Running the current pre-release version of Ubuntu
* Unofficial software packages not provided by Ubuntu

This is most likely a transient problem, please try again later.

I tried again several times in different days and it is the same. I have 10.4 recently updated from my original installation of 9.10. I think it was not a pre-release, I did it automatically from the website and it took a long time. As far as I know, all I have installed is official, except perhaps Skype itself. There seems to be something connected with Skype. But I have exactly the same Skype I had with 9.10, where I updated every few days with no trouble. It is something peculiar in 10.4

What can I do?

---

### Post by wojox on 2010-05-29
Get rid of Skype for the time being.

---

### Post by Spr0k3t on 2010-05-29
Yeah, drop skype and add it back in after the upgrade.

---

### Post by Coco999 on 2010-05-30
This sounds as a brute force solution. It was difficult to install correctly Skype when I did it. If it worked OK with 9.10, why not with 10.4? Please think of something else, if you want to help me.

---

### Post by Spr0k3t on 2010-05-30
Installing skype in 10.04 isn't hard.  You just need to have the correct repos set up.  Read up about the changes over at the wiki.  The only other solution I can offer that doesn't involve removing skype-common, install fresh to a new partition/drive and test the setup there.  Once you are happy with the results you can then go ahead and remove skype-common and do the upgrade.

[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

---

### Post by Coco999 on 2010-05-30
> **Spr0k3t said:**
> Installing skype in 10.04 isn't hard.  You just need to have the correct repos set up.  Read up about the changes over at the wiki.  The only other solution I can offer that doesn't involve removing skype-common, install fresh to a new partition/drive and test the setup there.  Once you are happy with the results you can then go ahead and remove skype-common and do the upgrade.

[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

What is the repos and where do I get it? Where is the wiki? How do I remove completely Skype? If these questions are answered at the url you gave, no need to answer here. But I will study it tomorrow, have not seen it yet. Thank you for your help.

---

### Post by Daminator on 2010-06-04
I had the same problem. If you open Synaptic Package Manager, mark upgrades and run in there, then it all seems to sort it's self out.

Damian

---

### Post by Coco999 on 2010-06-04
> **Daminator said:**
> I had the same problem. If you open Synaptic Package Manager, mark upgrades and run in there, then it all seems to sort it's self out.

Damian

Thank you, Damian. This seems to have solved it nicely. I'll wait for a few days until the next automatic update arrives. If all goes well, I'll mark the thread as solved. Best regards.
Jose

---

