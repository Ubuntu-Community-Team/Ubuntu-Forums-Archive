---
title: "Brasero Doesn't Burn Discs"
date: 2010-03-21
forum: General Help
---

### Post by Unanimated on 2010-03-21
I'm having an issue with Brasero. I just bought a huge stack of CD-Rs (all blank), but Brasero doesn't see them when I put them in to my CD-R drive. I know they work, though, because when I download and install GnomeBaker, the discs burn just fine. I would just use GnomeBaker, but on my computer, it's an extremely unstable and frustrating piece of software, and Brasero has always been good in my experience. But, why won't Brasero work with these CDs?

Note: It's always worked fine with other CD-Rs.

---

### Post by 98cwitr on 2010-03-21
k3b > *

sudo apt-get install k3b

this is all.

---

### Post by zeroseven0183 on 2010-03-21
Hi! In what process are you stuck when trying to burn CDs? I experience also a problem (I think it's a bug) last week when burning Data using Brasero. It was stuck on creating checksum and would not proceed burning. I noticed in Nautilus that the previous CD I inserted is still (strangely) mounted. After unmounting that, the burning process continued.

---

### Post by Miljet on 2010-03-21
> sudo apt-get install k3b

This is an all too often recommendation for disk burn problems. But not everyone, myself included, wants to install a ton of KDE dependencies just to run that one application. Any time you recommend installing k3b, you should also note that it is not a Gnome application.

Just my 2 cents worth.

---

### Post by Unanimated on 2010-03-21
> **zeroseven0183 said:**
> Hi! In what process are you stuck when trying to burn CDs? I experience also a problem (I think it's a bug) last week when burning Data using Brasero. It was stuck on creating checksum and would not proceed burning. I noticed in Nautilus that the previous CD I inserted is still (strangely) mounted. After unmounting that, the burning process continued.
I can go as far into Brasero as I want, but when I click 'Burn' and it brings up the dialog and asks which drive I want to use, I pick the burner drive and it tells me to insert a CD. I eject and put the CD back in, and the it says to use a compatible CD. I'm not totally sure why that one CD isn't compatible when all the other burner programs offered in the repos accept it, but whatever...

---

### Post by soryu on 2010-03-21
Switch over to serpentine cd creator.

---

### Post by ch3mi0n on 2010-11-05
> **Unanimated said:**
> I can go as far into Brasero as I want, but when I click 'Burn' and it brings up the dialog and asks which drive I want to use, I pick the burner drive and it tells me to insert a CD. I eject and put the CD back in, and the it says to use a compatible CD. I'm not totally sure why that one CD isn't compatible when all the other burner programs offered in the repos accept it, but whatever...

If you haven't already figured it out, it's probably because your drive does not support CD-R. Make sure you have a CD-R compatible burner, as opposed to CD+R or other. The plus (+) and minus (-) are not interchangeable unless you have a CD+/-RW burner.

If this is not the problem, please disregard. :)

---

### Post by ch3mi0n on 2010-11-05
> **zeroseven0183 said:**
> Hi! In what process are you stuck when trying to burn CDs? I experience also a problem (I think it's a bug) last week when burning Data using Brasero. It was stuck on creating checksum and would not proceed burning. I noticed in Nautilus that the previous CD I inserted is still (strangely) mounted. After unmounting that, the burning process continued.

Thank you for posting this. I found this thread while researching my issue with Brasero (Ubuntu 10.10) and it turns out that was exactly the problem I was having, too. I'm not sure if the problem is actually Nautilus; I haven't looked into it yet. It could be a problem with automount(?), but unmounting the (previous) disc definitely made Brasero continue with the burning process.

---

### Post by Quackers on 2010-11-05
I found that once a cd/dvd is mounted by the system I have to use the right-click and eject option. If I just open the drive and take the media out the system still seems to think the drive is occupied with the disc I just took out.

---

### Post by cottfcfan on 2010-11-05
I've had problems with all Linux native Cd burners, so I tried Nero Linux 4.
 It costs a nominal amount, but i've had no poor burns and the quality is A1.
 You also get a 30 day free trial. Never used anything else since.

---

### Post by coldraven on 2010-11-05
I have never got Brasero to burn anything successfully! I don't know why it's packaged with Ubuntu :(
Just install K3b instead :)

---

### Post by ussndmac on 2010-11-05
My experience is opposite the OP.

Brasero has never worked for me on several different machines.

Gnomebaker, on the other hand, has just worked every time.

I've never tried K3b, based on this thread I'm gonna check it out.

---

