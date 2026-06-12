---
title: "Aptoncd backup using an usb pen drive"
date: 2010-06-06
forum: General Help
---

### Post by linuxyogi on 2010-06-06
Hi, 

My question is ---------------

Is there a way to create aptoncd back up on a pen drive ?

Meaning when I insert a cd created with aptoncd an autorun dialog box appears asking if I want to start the package manager.

But when I copy those files to a pen drive the above mentioned autorun feature doesn't work.

In short I want my apt cache backup on a pen drive with the autorun feature.

Is this possible ? How?

Please reply.

---

### Post by linuxyogi on 2010-06-09
No one ??? [SIZE="6"]:confused:[/SIZE]

At least tell me a convenient way to share updates between two PCs running Ubuntu.

Actually, my friend's internet connection is very slow.

Downloading updates which are in Kbs upto 5Mb is somewhat possible but when it comes to downloading large files it takes hours.

So he asked me to share the updates from my PC (only the large files) and the small ones he will download himself.

If I copy my entire apt cache it will take a unnecessarily long time and there is also a chance of getting broken packages.

Aptoncd is a solution but a cd/dvd needs to burned every time.
I have tied mounting the iso file but it seems the autorun feature doesn't work.   

Please suggest a method.

---

### Post by jmszr on 2010-06-09
linuxyogi,

This might be what you need: [http://keryxproject.org/](http://keryxproject.org/) .

---

### Post by linuxyogi on 2010-06-11
> **jmszr said:**
> linuxyogi,

This might be what you need: [http://keryxproject.org/](http://keryxproject.org/) .

Thanks for your reply. I will give it a try.

One feature of aptoncd that missed is its ability to restore packages from an iso image -------

Open aptoncd

Tools Menu

Restore files from disc.

I haven't tried it yet (my freind will visit very soon with his laptop) but if this works then that's it.

Thanks again.

---

### Post by plucky on 2010-06-11
Why don't you use AptonCd to create the .iso file and then copy that to the pen drive to transport it to the other computer and restore it straight from the .iso.No need to burn it to CD.

Assuming the pen drive is large enough to take the .iso image file.

Good Luck

---

### Post by linuxyogi on 2010-06-11
> **plucky said:**
> Why don't you use AptonCd to create the .iso file and then copy that to the pen drive to transport it to the other computer and restore it straight from the .iso.No need to burn it to CD.

Assuming the pen drive is large enough to take the .iso image file.

Good Luck

Yes I tried that. It worked. 
Thanks.

---

### Post by enfield on 2010-07-11
That works for me too.

I wonder why aptoncd doesn't handle usb drives more gracefully?  I really shouldn't have to restore an iso file to my cache and then run an upgrade.  What we need is an aptonpendrive application.

---

### Post by linuxyogi on 2010-07-11
> **enfield said:**
> That works for me too.

I wonder why aptoncd doesn't handle usb drives more gracefully?  I really shouldn't have to restore an iso file to my cache and then run an upgrade.  What we need is an aptonpendrive application.

Absolutely. I agree.

---

### Post by Pokkels on 2010-08-20
Using apotoncd to retrieve the files from the iso works all fine and everything, but it only copies the packages from the iso to the cache folder, without actually updating it in the repositories of lets say Synaptic package manager. I would like to open synaptic and click on "mark all upgrades", but can't do that with aptoncd restore.

If you burn the image to a dvd/cd then it automatically updates the repository for you.

Is there another way that I could do this without having to burn the iso to a dvd/cd?

---

### Post by linuxyogi on 2010-08-20
> **Pokkels said:**
> Using apotoncd to retrieve the files from the iso works all fine and everything, but it only copies the packages from the iso to the cache folder, without actually updating it in the repositories of lets say Synaptic package manager. I would like to open synaptic and click on "mark all upgrades", but can't do that with aptoncd restore.

If you burn the image to a dvd/cd then it automatically updates the repository for you.

Is there another way that I could do this without having to burn the iso to a dvd/cd?

Open Update Manager
Click Reload
Now, suppose you find that there are 4 updates which totals to 50 mb, 
Close Update Manager
Open AptonCd, Restore those 4 packages
Reopen Update Manager
You will find that the "50mb" is now 0

---

### Post by e.m.fields on 2010-10-05
hey. I know this thread is marked "solved", assuming that (above) answer was the solution, but: 
**_I think that Keryx is the ticket here, rather than Apt on CD._**

**If you're entirely without internet, and can't get it without (naturally) installing some packages, AptOnCD is as good as useless.**

I am often in a situation where I cannot get internet on a new ubuntu install, because I don't have the right drivers for the wireless cards on my laptops (broadcom - booo!) ... and I love apt-on-cd, and it is *almost* the right solution, but not quite.  

[B]Reasons:
[LIST=1]
[*]You can't "update packages" unless I have an internet connection, or else you have physically burned a CD from your AptOnCD backup.
[*]You don't have an internet connection unless you have ethernet or else appropriate drivers to run the wireless.
[*]You can't install drivers for the wireless without an internet connection.
[*]You're a lot more likely to have an up-to-date Apt-on-CD backup stored as an ISO on a thumbdrive somewhere than to have a handy physical burned CD archive. 
[/LIST][/B]

_So, Keryx seems to be the ticket._ Backup packages to a thumb drive. restore from thumb drive, on a new, blank system, without need for packages already being installed. 

Humble two cents,

---

