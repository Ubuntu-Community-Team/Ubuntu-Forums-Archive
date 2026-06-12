---
title: "unclean shutdown every time i boot or reboot"
date: 2010-03-09
forum: General Help
---

### Post by anupam128 on 2010-03-09
I am on Ubuntu 9.04. Every time i boot or reboot i get the "Unclean Shutdown" message and it checks /dev/sda1 i.e where my / is. It is really irritating as it takes a lot of time every time i boot.

After the disk check it continues booting as usual and there is no reboot again.
I did a manual fsck but nothing special happens.

I have a Dell Inspiron 1520 and have Windows 7 also (if that helps).

---

### Post by dcstar on 2010-03-09
> **anupam128 said:**
> I am on Ubuntu 9.04. Every time i boot or reboot i get the "Unclean Shutdown" message and it checks /dev/sda1 i.e where my / is. It is really irritating as it takes a lot of time every time i boot.

After the disk check it continues booting as usual and there is no reboot again.
I did a manual fsck but nothing special happens.

I have a Dell Inspiron 1520 and have Windows 7 also (if that helps).

When your system shuts down Linux it is supposed to cleanly unmount the partitions and reset the "unclean" flags, for some reason this is not happening on your system.

Do you see any messages when you shutdown/reboot?

You may also want to look at the syslog file to see if there are any messages from the shutdown sequence.

---

### Post by anupam128 on 2010-03-10
> **dcstar said:**
> When your system shuts down Linux it is supposed to cleanly unmount the partitions and reset the "unclean" flags, for some reason this is not happening on your system.

Do you see any messages when you shutdown/reboot?

You may also want to look at the syslog file to see if there are any messages from the shutdown sequence.
Thanks for your reply dcstar.
I do not see any messages.
Yeah, i understand that is is something about the flags not getting set properly.
I have attached syslog in txt format as i could not get anything useful out of it.

---

### Post by anupam128 on 2010-03-21
Bump

---

### Post by pjalegria on 2010-05-22
i have the same problem with home on SD card... any fix?

---

### Post by nbo10 on 2010-05-22
When grub starts press esc, and boot into a recovery mode. Run fsk on the problem partition.

---

### Post by anupam128 on 2010-05-23
I did the fsck by going in recovery mode. But it did nothing.

---

### Post by pjalegria on 2010-05-23
The problem is on shutdown, i have the message "unmount home is busy", and then on start up i have "unclean shutdown" at home partition

---

