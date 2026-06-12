---
title: "cannot upgrade virtualbox"
date: 2011-08-24
forum: General Help
---

### Post by qwertyjjj on 2011-08-24
I have not been able to upgrade VirtualBox for a while now.
I get the attached error - any ideas on how t resolve it?

---

### Post by qwertyjjj on 2011-08-25
any ideas?

---

### Post by Azdour on 2011-08-25
Hi,

How are you downloading the latest version?

I also believe things in /tmp get wiped after a reboot.

---

### Post by qwertyjjj on 2011-08-25
> **Azdour said:**
> Hi,

How are you downloading the latest version?

I also believe things in /tmp get wiped after a reboot.

No reboot.
When I load VB it says there is a new download. I click that and it asks to run it with the software manager, it then updates and then fails.

---

### Post by qwertyjjj on 2011-08-28
must be a bug in VB?

---

### Post by YesWeCan on 2011-08-28
Try downloading from [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Dont forget the Extensions Pack [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by haqking on 2011-08-28
It depends on the version you are upgrading from, i used to get that error.

I remove my current install, download the .deb and do a fresh install, dont remove your settings though.

And all should be good.

---

### Post by coldraven on 2011-08-28
If you are trying to upgrade from vers. 3x to vers. 4x then before you do anything else... **Export your VM!**
I think they changed something because I could not get my VM to load in the new version. I had to re-install the old version and export, then import it back into the new one.
After exporting use Synaptic to remove the old version. Select "Remove" but **not** "Completly Remove".
The Export does not take a long time even though it will say two hours it will only take about 15 minutes.
At least you will have a backup in case things go wrong.
Download the latest version directly from the VirtualBox web-site.

---

### Post by CharlesA on 2011-08-28
> **coldraven said:**
> If you are trying to upgrade from vers. 3x to vers. 4x then before you do anything else... **Export your VM!**
I think they changed something because I could not get my VM to load in the new version. I had to re-install the old version and export, then import it back into the new one.
After exporting use Synaptic to remove the old version. Select "Remove" but **not** "Completly Remove".
The Export does not take a long time even though it will say two hours it will only take about 15 minutes.
At least you will have a backup in case things go wrong.
Download the latest version directly from the VirtualBox web-site.

+1. I was able to upgrade to 4x from 3.2 without any problems but exporting your VMs before making any drastic changes is always a good idea. Just keep in mind that snapshots aren't saved during export.

---

### Post by qwertyjjj on 2011-08-29
Strange, now VB says it is the latest version even though it errored on the update.

---

### Post by CharlesA on 2011-08-29
> **qwertyjjj said:**
> Strange, now VB says it is the latest version even though it errored on the update.
What does the about box say?

---

### Post by qwertyjjj on 2011-08-29
> **CharlesA said:**
> What does the about box say?

v 4.0.12

---

### Post by haqking on 2011-08-29
> **qwertyjjj said:**
> v 4.0.12

4.1 is available

---

