---
title: "Partion"
date: 2009-09-15
forum: General Help
---

### Post by jovemac on 2009-09-15
Dear all!

I am new to linux. I recently bought a dell vostro laptop in which ubuntu 8.10 came preinstalled. I am pretty happy with that.  But... my hard disk is of 160GB and its of a single partition. Is it possible to create partitions without disturbing the exisiting installation or need to format and create partitions?

If its possible to create partitions with the exisiting installation, tell me how?

Thanks in advance.

Regards
Jothi vel

---

### Post by P4man on 2009-09-15
Yes its possible, but you need to boot from a cd or usb stick. Not sure if one comes with the Dell, but if not, just download an ubuntu ISO and burn it to cd (or make a bootable stick using system > adminstration > USB startup creator, if that exists already in 8.10, im not 100% sure).

Once booted from the cd or stick, you can open partition editor in system > adminstration > partition editor. Unmount all drives, and swap off the swap partition, then you can resize and move your existing partitions and make new ones.

---

### Post by jovemac on 2009-09-15
Thank you p4man!

I have a CD of 8.10 that came along with my laptop. Will that do if i boot using it?

---

### Post by nikhilk on 2009-09-15
> **jovemac said:**
> I have a CD of 8.10 that came along with my laptop. Will that do if i boot using it?

I believe that should be fine, go ahead and give it a try.

---

### Post by P4man on 2009-09-15
> **jovemac said:**
> Thank you p4man!

I have a CD of 8.10 that came along with my laptop. Will that do if i boot using it?

I dont know if its a regular "live cd", but if you can boot from it and select something like 'try out ubuntu" then you're in business.

---

### Post by jovemac on 2009-09-15
> **P4man said:**
> I dont know if its a regular "live cd", but if you can boot from it and select something like 'try out ubuntu" then you're in business.

Ohmygod!

How to be at home then?

---

### Post by P4man on 2009-09-15
:confused:

---

### Post by jovemac on 2009-09-15
> **P4man said:**
> I dont know if its a regular "live cd", but if you can boot from it and select something like 'try out ubuntu" then you're in business.


If its not a live CD then is it okie?

---

### Post by P4man on 2009-09-15
The opposite, a livecd IS ok. I don't know what Dell ships with their ubuntu laptops, but if they follow the windows tradition then it could be some "wipe entire harddisk and reinstall factory default" cd. Thats not what you want :)

A regular live cd, either downloaded from ubuntu.com or perhaps supplied by Dell should work fine.

---

### Post by jovemac on 2009-09-15
> **P4man said:**
> The opposite, a livecd IS ok. I don't know what Dell ships with their ubuntu laptops, but if they follow the windows tradition then it could be some "wipe entire harddisk and reinstall factory default" cd. Thats not what you want :)

A regular live cd, either downloaded from ubuntu.com or perhaps supplied by Dell should work fine.

I do understand. As alternate, I have already a ordinary CD that has both live and install CD.  After inserting how to proceed?

---

