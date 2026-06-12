---
title: "ubuntu installation CD"
date: 2010-11-16
forum: General Help
---

### Post by jsvidyad on 2010-11-16
Hello,

   I have a question regarding ubuntu installation. When I burn the ubuntu installation iso file to a CD-R, does it close the CD-R disc at the end(i.e. prevent writing more data to disc) or can I append more data to the disc in another session?

---

### Post by papibe on 2010-11-16
The Ubuntu installation CD is an image, so it is supposed to be burn using the "Burn Image" (or similar) option in your CD/DVD burning software. That option close the disk for more data.

Some people get confused and instead burning an image, burn a data disk, and include the ISO file as a file. That won't let you use the CD for installation because it isn't going to boot properly.

Did that help?

---

### Post by pricetech on 2010-11-16
Brasero offers you an option to leave the disk open after the burn, but I honestly don't know if that would work or not.

I used to tinker around with a program called Ultra ISO under windows that allowed me to open an ISO and make changes to it.

I suspect there's a way to do that under Linux, but I've never looked into it.  I'd pursue that angle though if it was me.

Have fun with it.

---

### Post by jsvidyad on 2010-11-16
OK. Thanks. I just wanted to make sure that nothing can add its own code to a ubuntu installation CD once the iso image had been burned to a CD-R. I used the option to burn an image to CD. So, I guess that means that the CD-R is closed to further attempts to write to it and nothing can append its stuff to the installation CD-R.

  Once again, thanks for letting me know.

---

### Post by jsvidyad on 2010-11-16
Hello,

  My question was whether after I burn the ubuntu LiveCD iso image to a CD-R to create an installation disc, some virus or other malware can infect the installation disc by adding code to the already burnt CD-R. Is this possible? I used the LiveCD(on a CD-R) on a computer which has a boot-sector virus and I was wondering if my LiveCD could have become infected. Can you write more than once to a CD-R? Does the ubuntuiso image close the CD-R to further data addition once it is burnt to a CD-R?


Please let me know.

---

### Post by krismatth3 on 2010-11-16
In general, no, the boot CD would not be affected. If you're really paranoid about it, compare the output of

```

sha256sum /dev/mycd
sha256sum orginal_iso_image.iso

```

---

### Post by jroa on 2010-11-17
I don't think that CD-R is capable of having changes made to it, even if you want to do so.  But, I might be wrong.

---

### Post by jsvidyad on 2010-11-17
Hello,

  Can someone help me with this?

---

### Post by Slim Odds on 2010-11-17
Finalizing the disk is up to you. There is no reason not to do it, but it is an option based on the program that you use to burn the disk. Most will finalize by default.

Also note that the Ubuntu install CD's are totally full. They pack absolutely as much as they possibly can onto it. As a matter of fact, the disk will not even burn to a "standard" 650MB disk. It requires a 700MB disk.

What platform and program are you burning the disk with?

---

### Post by jsvidyad on 2010-11-17
The CD-R disk was burnt in 2009. It is ubuntu 9.10 LiveCD. I just want to know if the disc can become infected if I use it on an infected system. I am worried that malware can add its own code to the disc.

---

### Post by jsvidyad on 2010-11-17
I believe I used GnomeBaker to do it.

---

### Post by jsvidyad on 2010-11-17
or it could have been nautilus burn

---

### Post by cgroza on 2010-11-17
No malware can get in a CD-R closed or not closed as this requires code to access the CD-ROM drivers and nobody bothers to do that, unless you write it yourself.

---

