---
title: "booting without  cd or usb"
date: 2010-06-07
forum: General Help
---

### Post by NaTeY` on 2010-06-07
can I boot xubuntu without burning a cd, because I don't have any cds, nor can my desktop burn any cds or anything, so can I boot it without having a cd or usb?

---

### Post by Smart Viking on 2010-06-07
I'm pretty sure it is possible to boot from an usb hard drive the same way you do with usb flash drive, other than that i don't know. :)

---

### Post by Jakiejake on 2010-06-07
> **Smart Viking said:**
> I'm pretty sure it is possible to boot from an usb hard drive the same way you do with usb flash drive, other than that i don't know. :)

But does he have a hard drive???
CD's Are like $14 AUD A Packet
Just go buy some!
DVD's work too!

---

### Post by NaTeY` on 2010-06-07
I think I can extract the .iso with winrar into the same folder, and run wubi.exe

---

### Post by NaTeY` on 2010-06-07
> **Jakiejake said:**
> But does he have a hard drive???
CD's Are like $14 AUD A Packet
Just go buy some!
DVD's work too!
i dont have a burner, it's reallllllllyyy outdated.....

and I have some dvd+r's, nothing worked...

---

### Post by Jakiejake on 2010-06-07
> **NaTeY` said:**
> i dont have a burner, it's reallllllllyyy outdated.....

and I have some dvd+r's, nothing worked...

How many PC's do you have

---

### Post by NaTeY` on 2010-06-07
I have one pc, I'm trying to put xubuntu on my laptop

---

### Post by Jakiejake on 2010-06-07
> **NaTeY` said:**
> I have one pc, I'm trying to put xubuntu on my laptop

Could you buy a usb
Otherwise you could order a CD from Ubuntu Shipit or buy a cd or usb from someone else

---

### Post by NaTeY` on 2010-06-07
I don't have any money, nor do any of my friends have cd's or usb's.

---

### Post by Jakiejake on 2010-06-07
> **NaTeY` said:**
> I don't have any money, nor do any of my friends have cd's or usb's.

Oh Come On
Try This [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/) It's Free I've done it before!

---

### Post by Jakiejake on 2010-06-07
What country are you in?
Someone could send you one

---

### Post by XubuRoxMySox on 2010-06-07
Just to politely correct a small error: Xubuntu is not available from ShipIt, as Ubuntu and Kubuntu are. Xubuntu is an independent project, and Canonical does not provide free CDs for Xubuntu. The project had to find it's own separate provider. Fortunately they did! Free Xubuntu CDs [here]("http://on-disk.com/product_info.php/products_id/866") (for USA) and [here]("http://on-disk.com/product_info.php/products_id/872") (for the rest of the world).

As for the OP, there's always wubi I suppose.

Enjoying my Xubuntu,
Robin

---

### Post by Smart Viking on 2010-06-07
> **Jakiejake said:**
> What country are you in?
Someone could send you one

True! If the OP wants to, i can burn you a xubuntu cd, and send it in the mail(it will be much faster than shipit). :)

---

### Post by john newbuntu on 2010-06-07
You can boot straight from a partition on your HDD that grub could get to.  I am assuming that you have grub2 set up already.  Download the xubuntu iso file to some place on your hard disk drive(say, to a directory called /ISO).  Add a stanza like this to /etc/grub.d/40_custom file:

```
menuentry "Xubuntu - poor mans liveCD" {
     loopback loop (hd0,5)/ISO/xubuntu-10.0.4-desktop-i386.iso
     linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ISO/xubuntu-10.0.4-desktop-i386.iso file=(loop)/preseed/ubuntu.seed quiet splash bootkbd=sg --
     initrd (loop)/casper/initrd.lz
}

```
Make appropriate changes above to the /ISO path, device path(hd0, 5) and the .iso filename.  Then run "sudo update-grub".  Reboot.  When the grub menu shows up, choose "Xubuntu-poor mans..".
I have gotten Ubuntu and a few other distros to boot this way with some changes to the parameters but haven't tried booting xubuntu.

---

### Post by NaTeY` on 2010-06-07
how long does it take to get to my house?

---

### Post by Jakiejake on 2010-06-08
> **NaTeY` said:**
> how long does it take to get to my house?

What country are you in?

---

### Post by Jakiejake on 2010-06-08
> **dixiedancer said:**
> Just to politely correct a small error: Xubuntu is not available from ShipIt, as Ubuntu and Kubuntu are. Xubuntu is an independent project, and Canonical does not provide free CDs for Xubuntu. The project had to find it's own separate provider. Fortunately they did! Free Xubuntu CDs [here]("http://on-disk.com/product_info.php/products_id/866") (for USA) and [here]("http://on-disk.com/product_info.php/products_id/872") (for the rest of the world).

As for the OP, there's always wubi I suppose.

Enjoying my Xubuntu,
Robin

I suppose your right
Nice links!
I personally think... Whats wrong with Ubuntu
It can be suited to lower specs ):P

---

### Post by phr33k-dc on 2010-06-08
Do a netboot!!!!!!!!!!!!!!1

---

