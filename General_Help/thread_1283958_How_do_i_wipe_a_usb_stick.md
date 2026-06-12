---
title: "How do i wipe a usb stick?"
date: 2009-10-06
forum: General Help
---

### Post by Jameshardy88 on 2009-10-06
Hi i was recently given a free usb stick at my freshers fair, it contains loads of adverts and promotionl stuff as you would expect. I was wondering how i would go about deleting them so that i could use it as a standard usb stick that i could read and write to as currently i can only view files.

Thanks for any help,

James

---

### Post by minigeek on 2009-10-06
> **Jameshardy88 said:**
> Hi i was recently given a free usb stick at my freshers fair, it contains loads of adverts and promotionl stuff as you would expect. I was wondering how i would go about deleting them so that i could use it as a standard usb stick that i could read and write to as currently i can only view files.

Thanks for any help,

James

Hi

You could use Partition Editor which can be installed via Synaptic Package Manager

or

run the following command in a terminal as root

cd /path/to/usb

rm -fr * 

This will remove all the files on the usb device

---

### Post by Jameshardy88 on 2009-10-06
thankyou =)

---

### Post by Lampi on 2009-10-06
As a security measurement I'd always format a new stick once and entirely just to make sure no potential virus can infiltrate your system. Might be important if you should use the stick on a windows system. You can use gparted for that matter

---

