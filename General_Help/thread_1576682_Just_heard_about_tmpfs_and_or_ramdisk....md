---
title: "Just heard about tmpfs and or ramdisk..."
date: 2010-09-17
forum: General Help
---

### Post by Kane Hart on 2010-09-17
Ubuntu Server (64bit) 10.04



Little confused on the 2 I did some googling about to go to work but was wondering if anyone can offer me a solution and if even more possible to give me the exact commands being slightly new to the linux work.



I run a game called Minecraft on the following specs:
Intel Core i7 860 (Quad core w/ HT support)
(four physical cores and four virtual)
8 GB DDR3 1333 Memory
500 GB SATA Hard Drive
5 IP Addresses
6,000 GB (3,000 IN and 3,000 OUT)

My current issue is that Minecraft server is one the most IO intensive applications I have ever used. To the point a SSD would not work even with TRIM because it would just bog down I'm told it will end up slowing down during the writes and ahhh...

The next idea is pay a lot of money to get a Raptor Drive and omg they only sell the 150gigs at my DC? I only use 300mb of space...

**Here is what windows backup of it says when extracted:**
size: 261 MB (274,637,974 bytes)
size on disk: 376 MB (394,903,552 bytes)

Then someone suggested ramdisk or tmpfs and told me it's something like 12,000MB/s is this true??? wth lol..

I know the biggest issue is if you lose power you lose the stuff and that is no issue since I backup every hour anyways. (BTW it takes like 6-7 min to run a backup with the 80k files or so in the folder but when the server is off and fresh restart its like 10seconds lol. Gives you an idea of the usage.


So Minecraft works like this. It generates world as you expand and so yes it could use more space but I heard worst comes to worst it will actually move to swap? Minecraft loads chunks at a time like the 80k files and if someone deletes or adds a block in the game it saves and this is why people just simply exploring and warping the drive just goes overtime.


So would this be a suggested solution? Save me money and I do have a bit of ram extra I was thinking of allocating this 2 gigs to this 4 gigs to java to run minecraft. and keep 2 gigs for the OS no web server and crap runs on my box btw.



If you would be so kind to offer me some commands and maybe a slight information telling that would be great I gotta run to work but I would die to learn more from you guys your experiences and I really hope this solves my problems or I will have to pay a lot of money.

So again please show some example commands <3

---

### Post by xircon on 2010-09-17
Have a look at:

[http://www.cyberciti.biz/faq/howto-create-linux-ram-disk-filesystem/](http://www.cyberciti.biz/faq/howto-create-linux-ram-disk-filesystem/)

---

### Post by Kane Hart on 2010-09-17
> **xircon said:**
> Have a look at:

[http://www.cyberciti.biz/faq/howto-create-linux-ram-disk-filesystem/](http://www.cyberciti.biz/faq/howto-create-linux-ram-disk-filesystem/)

Thanks I will take a look how would one benchmark the speed of it?

---

