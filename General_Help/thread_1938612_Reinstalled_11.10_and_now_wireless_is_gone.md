---
title: "Reinstalled 11.10 and now wireless is gone"
date: 2012-03-10
forum: General Help
---

### Post by terceiro on 2012-03-10
I've been successfully running Ubuntu for over a year, but things were starting to slow down. I decided to clean off the HD and reinstall to get rid of the cruft I'd accrued. In retrospect there were probably better ways to accomplish that end, but it's too late now.

I downloaded 11.10 and put it on a USB drive, restarted my laptop, formatted the partition and installed. Everything seems to work just fine, except for networking. I have a wired connection, but wireless is completely borked.

I have the same Broadcom STA proprietary driver installed that I did before. Checking "Additional Drivers" in the System Settings tells me that the driver is activated and currently in use. However, when I click the network menu in the top panel "Wireless Networking" doesn't even appear. Using "Edit Connections..." doesn't detect any wireless networks even though they are active (I'm sitting eighteen inches from the router and other computers see it just fine). 

I feel like an idiot. The hardware is fully operational (Windows still finds the network, demonstrating that the card is still functioning), and the driver is installed. There's tons of help available on getting the driver installed, but I'm past that point. But I have no clue what to do. I've tried installing six times now, hoping that I might stumble across getting it right, but no joy.

I tried Linux Mint, which had the same problem. I tried downloading drivers from Broadcom and building them myself, but that only made the wired connection disappear as well. I'm out of ideas.

Seriously, I'm completely stymied. Help, anyone, please.

The computer is a Dell Inspiron 1501 with 1.5GB of RAM, everything else is stock from the manufacturer. As I mentioned above, I was running 11.10 just fine this morning, but that was just incrementally updated back from probably 9.10 or 10.04.

---

### Post by terceiro on 2012-03-10
I'm not quite willing to admit that I'm an idiot, but I did solve this myself. Here's the solution:

1. Remove the proprietary driver that is installed by Ubuntu. I don't know if the restart is necessary, but I did.

2. Install the b43 driver ("sudo apt-get install firmware-b43-installer")

3. Voila. Now it works. 

Sheesh. If only I'd figured that out seven hours ago.

On the upside, everything is running much faster than it did yesterday. On the downside, I wasted and day and still need to reinstall all my files, etc.

---

### Post by Dcduo on 2012-05-04
Made an account to reply to this. Had the very same problem of the inbuilt wireless not working. Had done some more searching and NOWHERE answered even remotely as simple as this (atleast to me as a linux newbie).

Thanks a lot!

---

