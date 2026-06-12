---
title: "Weird Problem with Live CD's"
date: 2010-10-07
forum: General Help
---

### Post by JonathanDS on 2010-10-07
Today, I decided to install Windows 7 Ultimate on my Ubuntu LT(Toshiba Satellite). I burned an Ubuntu 10.04 Live CD, to repair GRUB after the install, and GParted Live CD 0.6.4-1, to allocate some HDD space to a new partition for Windows. Both .ISO's were burned on Memorex 4.7GB DVD+R's @ 4X.

   I rebooted my system, w/ GParted Live CD in my drive, and booted from it fine. However, immediately after select the Automatic Boot Preference, just after selecting [33] English Key Layout [0] within GParted, I received two "X Server" errors. I retried the boot several times, with identical results, before deciding that the disk was faulty.
   I booted back into my HDD 10.04, and burned a new Disk. The same thing happened when I attempted to boot from the new disk. I finally gave up, and decided to try the partition editor on the Ubuntu Live CD.

   Initially, the Ubuntu Live CD seemed to function properly. The Language Selection pop-up came, and went, followed by the main menu(try ubuntu, install ubuntu, check disk, etc). Unfortunately, none of the menu options functioned properly. When I selected them, I could hear the disk "spin-up" for a moment, but nothing would happen, and the disk would stop spinning. This happened on every option, within the menu.

   At that point, I began to fear that my DVD Drive was failing, so I made a USB Live CD. I used the prescribed method, on the official Ubuntu download page, and successfully made a bootable partition on my 4GB USB 2.0 Memorex Traveldrive. Unfortunately(or fortunately, depending on how you look at it), the USB Live CD had the exact same problem as the DVD Live CD(So I suppose my DVD Drive is fine).

   I was stumped. I decided to try to boot the Windows 7 Ultimate DVD, and it functioned perfectly. I stopped the process just short of formatting my HDD, and had zero issues. Now I was really confused, so I tried to boot a different computer(Acer Netbook w/ W7U) from my USB Live CD, and it had the same problem my Toshiba LT had.

   So, I guess my problem is that, for some reason, my Toshiba Satellite w/ fully updated Ubuntu 10.04 LTS cannot make Live CD's. Anyone have any idea why that would be the case? It used to make them. The last time I used it was about two weeks ago, and it worked fine. I am at a complete loss. The .ISO's I used have always worked before. Any insight would be greatly appreciated.

---

### Post by sikander3786 on 2010-10-07
First of all check the MD5SUM of the downloaded image being used to burn CDs and USB drives. Most probably, it seems corrupt to me.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If it is ok, then boot off an Ubuntu CD and on the screen where you select "Try Ubuntu without making any changes", there is an option to "Check disc for defects". Check it. If a new burn is required, burn the disc at the lowest possible speed.

---

### Post by JonathanDS on 2010-10-07
> **sikander3786 said:**
> First of all check the MD5SUM of the downloaded image being used to burn CDs and USB drives. Most probably, it seems corrupt to me.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If it is ok, then boot off an Ubuntu CD and on the screen where you select "Try Ubuntu without making any changes", there is an option to "Check disc for defects". Check it. If a new burn is required, burn the disc at the lowest possible speed.

[s]I've used the Ubuntu image several times without issue, and I tried two separate versions of GParted with the same result.
The "Check disc for defects" option does not work. When it is selected, the disc begins to spin, but quickly stops without doing anything.
4X is the slowest speed possible, on my drive.[/s]

UPDATE: Actually, it appears that you were right... So why did the new GPL .iso give me problems as well?

---

### Post by sikander3786 on 2010-10-07
I still doubt, it is either the image integrity or the cd/dvd burning software causing the problems. I am unable to figure out anything else. CD, DVD, USB Drive all fail and all on 2 different PCs. As far as I can see, the only thing common is the downloaded image.

---

### Post by JonathanDS on 2010-10-07
> **sikander3786 said:**
> I still doubt, it is either the image integrity or the cd/dvd burning software causing the problems. I am unable to figure out anything else. CD, DVD, USB Drive all fail and all on 2 different PCs. As far as I can see, the only thing common is the downloaded image.

I'll re-download the images and try again. Thanks for the help.

---

### Post by Quackers on 2010-10-07
It could still be a bad burn. I would check the MD5 checksum of the downloaded iso that you already have, as sikander3786 suggested.

---

