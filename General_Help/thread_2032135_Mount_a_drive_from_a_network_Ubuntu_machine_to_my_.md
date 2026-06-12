---
title: "Mount a drive from a network Ubuntu machine to my Ubuntu laptop."
date: 2012-07-23
forum: General Help
---

### Post by Matt Pellegrini on 2012-07-23
I have a desktop ubuntu 12.04 machine with the drive (partition) /dev/sda6 which is full of media.

I'd like to mount this drive to my laptop. The IP (static) of the desktop is 192.168.0.77

I've tried mount //192.168.0.77/dev/sda6  /mnt/   but this doesn't work, is there an easy way to do this?

Thanks,
Matt

---

### Post by SlugSlug on 2012-07-23
install ssh server on desktop

on lappy use nautilus and in one of them menus at top of screen is connect to server


select ssh server and fill in username etc

then 'bookmark'  it for later use :)

maybe then look at ssh keys so you don't need to keep typing in the password

---

### Post by Matt Pellegrini on 2012-07-23
Already have keys set up for this, I've been crash coursing this the past few days.

Thanks a lot,  works great, knew there had to be a simple solution.

---

