---
title: "near-complete hardware upgrade - need to reinstall?"
date: 2012-03-26
forum: General Help
---

### Post by kurja on 2012-03-26
I'm about to upgrade most of my hardware, but I'm keeping the hard drives that I have now, so the question is - do I need to reinstall Ubuntu? Or could ubuntu work with the new motherboard etc? Both old and new hardware configurations would use ati gpu's, default drivers are in use. If I just try and find out what happens, is there something I should know beforehand, or are there precautions I should take?

---

### Post by Bobhuber on 2012-03-26
> **kurja said:**
> I'm about to upgrade most of my hardware, but I'm keeping the hard drives that I have now, so the question is - do I need to reinstall Ubuntu? Or could ubuntu work with the new motherboard etc? Both old and new hardware configurations would use ati gpu's, default drivers are in use. If I just try and find out what happens, is there something I should know beforehand, or are there precautions I should take?
Nope should work just fine.

---

### Post by imachavel on 2012-03-26
should work just fine. Linux isn't like windows xp where drivers don't exist for the network or other on fresh installation and you need to transfer that driver with a usb device. It will be like anything else, you need codecs and plug ins installed, and for acceleration you might need to do a 

sudo apt-get install update or manually find drivers online, and at the same time possibly download them manually if you want video acceleration(not great with ubuntu which still uses opengl api library)

Consult this:

[http://www.techdrivein.com/2011/10/15-things-i-did-after-installing-new.html](http://www.techdrivein.com/2011/10/15-things-i-did-after-installing-new.html)

---

### Post by QIII on 2012-03-26
Disable/remove all third party drivers prior to shutting down for the last time.  Backup everything.

It is a persistent myth that this "just works".  I have had it work most of the time, but I have also had it fail.

Take care.  Do backups.

---

### Post by philinux on 2012-03-26
> **QIII said:**
> Disable/remove all third party drivers prior to shutting down for the last time.  Backup everything.

It is a persistent myth that this "just works".  I have had it work most of the time, but I have also had it fail.

Take care.  Do backups.

Very good advice +1.

---

### Post by kurja on 2012-03-26
Both great news and sound advice - thanks, people.

---

### Post by kurja on 2012-03-27
yup, it worked.

---

