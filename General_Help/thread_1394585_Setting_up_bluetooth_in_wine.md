---
title: "Setting up bluetooth in wine"
date: 2010-01-30
forum: General Help
---

### Post by wmerrell on 2010-01-30
I am running Ubuntu 8.04 and the bluetooth works ok. I can see, connect, and upload to and download from my phone. The phone's manufacturer's sync program runs under windows, so I installed it in wine, and it runs, but I can't get the bluetooth to work under the wine installation.

The problem is the sync program wants a bluetooth DUN port, and is not finding one. I have set up a rfcomm port and ln linked it to com1: under wine's dosdevices folder. If I echo an at command to com1:, the command is successfully sent to the phone, but the sync program does not see any DUN ports.

How do I set up the DUN port so that the program in wine will find it?

Thanks,
-- Will

---

### Post by theozzlives on 2010-01-30
> **wmerrell said:**
> I am running Ubuntu 8.04 and the bluetooth works ok. I can see, connect, and upload to and download from my phone. The phone's manufacturer's sync program runs under windows, so I installed it in wine, and it runs, but I can't get the bluetooth to work under the wine installation.

The problem is the sync program wants a bluetooth DUN port, and is not finding one. I have set up a rfcomm port and ln linked it to com1: under wine's dosdevices folder. If I echo an at command to com1:, the command is successfully sent to the phone, but the sync program does not see any DUN ports.

How do I set up the DUN port so that the program in wine will find it?

Thanks,
-- Will

why not use Blueman, it works fine with my BlueTooth

---

### Post by wmerrell on 2010-01-30
Thanks for the speedy reply. Blueman is better than the default, but my problem is that the phone does not support much functionality via simple bluetooth. I cannot edit the address book or contacts or much else. They have a sync program that does (or claims to) all of that, but I can't get it to connect.

So I'm left with my original question, how do I set up a DUN port under wine so that the sync program will find it?

Thanks,
-- Will

---

### Post by sgosnell on 2010-01-30
[This thread](http://ubuntuforums.org/showthread.php?t=700657) claims to have a solution, but the link to ubuntology.com doesn't work.  Maybe some of it might help you, or at least give you some ideas.

---

### Post by wmerrell on 2010-01-30
Thanks for your reply.

> This thread claims to have a solution, but the link to ubuntology.com doesn't work. Maybe some of it might help you, or at least give you some ideas.

Unfortunately, I have already found that thread and I got at far as I have with it. (the ubuntology.com link does not lead to a working site)

It looks like I have a com1: port, but my sync program does not find what its looking for so I still need to know what a bluetooth DUN port is and how to create one inside of wine.

Thanks for any help anyone can offer,
--Will

---

### Post by wmerrell on 2010-01-31
bump

---

