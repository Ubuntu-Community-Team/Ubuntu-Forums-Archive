---
title: "Is Ubuntu bad to prepare for Linux+ LPIC-1 exam? (Poll)"
date: 2011-02-22
forum: General Help
---

### Post by abo_shreek11 on 2011-02-22
Hi,
I decided in last October to learn Linux and get certified as well. I downloaded courses from Testout, learnkey and CBT Nuggets. I found in the tutorials that Ubuntu is away different than other Linux distributions. Most of the configuration files have different names and locations than other distribution. I like Ubuntu and it has a tremendous how-to articles on the Internet. But I don't want to fail the exam because of this. I am wondering if I should switch to Fedora or Suse until I get certified?

Kindly share your opinion with me.

---

### Post by Mariane on 2011-02-22
I don't know about Suze but with Fedora even some command words are different. Instead of "apt-get" I had to type "yum" or something like that, I've forgotten what. 

If you are considering getting professional about it I think you should know Ubuntu, because it's the most widely used, and also the others. Closely read anything you can find about this exam, in particular last years question, and set up a dual boot of the OS you need practice with. 

Mariane

---

### Post by matt_symes on 2011-02-22
Hi

Dual or multi boot.

Kind regards

---

### Post by mastablasta on 2011-02-22
or try Debian on which Ubuntu is based. They just released new stable version. It's used a lot in Linux servers due to stability.

---

### Post by 3rdalbum on 2011-02-22
The exams should be based around a particular distribution. If they are based on SLED/SLES, you could try OpenSUSE. If they are based around Red Hat Enterprise, you could try CentOS.

---

### Post by aeiah on 2011-02-22
> **mastablasta said:**
> or try Debian on which Ubuntu is based. They just released new stable version. It's used a lot in Linux servers due to stability.

whilst i agree that debian is used a lot, this isnt going to be very useful. since ubuntu is based on debian, any underlying differences between ubuntu and other major distros will be the same as between debian and other major distros.

basically red hat and novell are the most popular enterprise linux companies. both SLED (suse linux enterprise) and RHEL (redhat) are RPM based distros, and so most accreditation will focus on that way of doing things. there are probably fairly large differences between the way suse does things and the way redhat do too, so really i advise you check out CentOS, the free community version of RHEL.

---

### Post by 3Miro on 2011-02-22
In my experience Ubuntu tutorials are written fro people with very little skills not just in Linux, but computers in general. If you are one of those people, this is wonderful, but if you want delve deeper into the realm of the OS, go for something more "advanced".

I learned a lot about how Linux works from the Arch Linux HowTo pages. I think Arch is better for learning thins (better than Fedora/CentoOS, Suse or really any of the rest). If you want to learn, Arch is accessible enough yet challenging enough.

Set a dual boot with Ubuntu and Arch (or possibly add Fedora to the mix). Also, get Virtual Box and try several distribution at once.

---

### Post by srs5694 on 2011-02-22
It's been over a year since I last took the Linux+/LPIC-1 exams, but my recollection is that there's some Red Hat bias in them; there are a few questions that assume Red Hat's way of handling runlevels and X, for instance. (I might be thinking of the older Linux+ exam, though; the newer exam is based on LPIC-1.) SUSE is more similar to Red Hat in this respect than either is to Ubuntu (or Debian, which is the basis of Ubuntu, not the other way around as one poster claimed). Fedora, of course, is the freely-available version of Red Hat.

That said, the LPIC-1 exam is officially distribution-neutral, and it does explicitly cover *both* the RPM and Debian package systems. Thus, you're well advised to learn using both an RPM-based and a Debian-based distribution. The suggestion of using VirtualBox to install multiple distributions is a good one. Personally, I recommend Debian and either Fedora or OpenSUSE, if you're going to limit yourself to just two distributions. Ubuntu adds a lot of "eye candy" to Debian, but the Linux+/LPIC-1 exams don't cover these GUI tools, so at best the differences between Debian and Ubuntu will be irrelevant, and at worst they'll be a distraction. I wouldn't bother with Arch; as far as I can tell, it's a bit too much of a niche distribution. Also, IIRC it uses its own package management system, so it won't help you to learn either the RPM or Debian systems covered by the exams.

Oh, and FWIW, I'm the author of the [Linux+ Study Guide,](http://search.barnesandnoble.com/CompTIA-Linux-Study-Guide/Roderick-W-Smith/e/9780470888452/?itm=7&USRI=linux%2b) which is a slightly updated version of the [LPIC-1 Study Guide.](http://search.barnesandnoble.com/Lpic-1/Roderick-W-Smith/e/9780470404836/?itm=3&USRI=lpic) I mention this just to point out that I know a thing or two about the exams -- although I wasn't involved in their development and don't have privileged access to their contents.

---

### Post by abo_shreek11 on 2011-02-24
> **srs5694 said:**
> It's been over a year since I last took the Linux+/LPIC-1 exams, but my recollection is that there's some Red Hat bias in them; there are a few questions that assume Red Hat's way of handling runlevels and X, for instance. (I might be thinking of the older Linux+ exam, though; the newer exam is based on LPIC-1.) SUSE is more similar to Red Hat in this respect than either is to Ubuntu (or Debian, which is the basis of Ubuntu, not the other way around as one poster claimed). Fedora, of course, is the freely-available version of Red Hat.

That said, the LPIC-1 exam is officially distribution-neutral, and it does explicitly cover *both* the RPM and Debian package systems. Thus, you're well advised to learn using both an RPM-based and a Debian-based distribution. The suggestion of using VirtualBox to install multiple distributions is a good one. Personally, I recommend Debian and either Fedora or OpenSUSE, if you're going to limit yourself to just two distributions. Ubuntu adds a lot of "eye candy" to Debian, but the Linux+/LPIC-1 exams don't cover these GUI tools, so at best the differences between Debian and Ubuntu will be irrelevant, and at worst they'll be a distraction. I wouldn't bother with Arch; as far as I can tell, it's a bit too much of a niche distribution. Also, IIRC it uses its own package management system, so it won't help you to learn either the RPM or Debian systems covered by the exams.

Oh, and FWIW, I'm the author of the [Linux+ Study Guide,]("http://search.barnesandnoble.com/CompTIA-Linux-Study-Guide/Roderick-W-Smith/e/9780470888452/?itm=7&USRI=linux%2b") which is a slightly updated version of the [LPIC-1 Study Guide.]("http://search.barnesandnoble.com/Lpic-1/Roderick-W-Smith/e/9780470404836/?itm=3&USRI=lpic") I mention this just to point out that I know a thing or two about the exams -- although I wasn't involved in their development and don't have privileged access to their contents.

Thank You Mr. Smith,
I decided to dual boot Ubuntu and Fedora whilst most of the CBTs (Computer Based Training) I have tech Fedora and Suse. By the way, I already bought your book. 

Thank You.

---

