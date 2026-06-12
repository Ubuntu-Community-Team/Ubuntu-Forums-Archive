---
title: "Best way to backup whole partition like Norton Ghost does"
date: 2011-08-15
forum: General Help
---

### Post by vanjadjurdjevic on 2011-08-15
I decided to make an Ubuntu distro upgrade but I want to backup to prevent data loss and to have a working backup which I can restore any time if my system crashes or something like that.
So I'm looking for a solution on this, I want to backup the whole partition (userdata, ubuntu system files) and move that backup to external hdd and restore it whenever i want to.
Avoid posting thing like use search because i DID USE SEARCH and i found no solution for my problem. Help would be apriciated.

---

### Post by haqking on 2011-08-15
> **vanjadjurdjevic said:**
> I decided to make an Ubuntu distro upgrade but I want to backup to prevent data loss and to have a working backup which I can restore any time if my system crashes or something like that.
So I'm looking for a solution on this, I want to backup the whole partition (userdata, ubuntu system files) and move that backup to external hdd and restore it whenever i want to.
Avoid posting thing like use search because i DID USE SEARCH and i found no solution for my problem. Help would be apriciated.
 
clonezilla

[www.clonezilla.org](www.clonezilla.org)

---

### Post by Vishal Agarwal on 2011-08-15
The tar and dd are the backup tools to take backup in Linux system. The dd can copy the HDD sector wise while the tan can handle the directories backup well.

---

### Post by vanjadjurdjevic on 2011-08-15
> **haqking said:**
> clonezilla

[www.clonezilla.org]("http://www.clonezilla.org")

I'm trying this right now so I'll keep you posted about my exp. with it :) thanks for the rapid reply

---

### Post by varunendra on 2011-08-15
> **haqking said:**
> clonezilla

[www.clonezilla.org]("http://www.clonezilla.org")
+1

Besides, you may wish to try [Remastersys]("http://www.geekconnection.org/remastersys/") if the installation size is not very huge and can be fitted on a DVD after shrinking. Typically, a 5-6 GB installation (without user-data in the /home directory) gets shrinked to approx. 2-3 GB by remastersys. The brighter side of remastersys in contrast to clonezilla is that you can use the DVD (iso) it creates as a live DVD.

---

### Post by vanjadjurdjevic on 2011-08-15
Thanks to everyone ! 
I solved my problem with CloneZilla but not easily. First I was trying to set up live usb device which always ended with a boot error ("Boot error", "The device is not bootable please put in a floppy" or something like that, "no operating system", and so on) and after dozens of failed solutions I decided to stick to DVD (which i hate) and i burned it and made an iso backup luckily.

Remastersys:
I tried this before clonezilla and I was disappointed with its iso size segment (cuz my os is larger then standard iso size even without home folder) so i gave up on that but it's an excellent program though.

---

### Post by varunendra on 2011-08-15
> **vanjadjurdjevic said:**
> I solved my problem with CloneZilla but not easily. First I was trying to set up live usb device which always ended with a boot error ("Boot error", "The device is not bootable please put in a floppy" or something like that, "no operating system", and so on) and after dozens of failed solutions I decided to stick to DVD (which i hate) and i burned it and made an iso backup luckily.
Yeah, creating a live usb sometimes gives a lot of headache. While there are several possible reasons and respective solutions, most of such problems seem to get solved either by using unetbootin, or by replacing the USB key itself with a different brand/model.

As for over-sized installation, you may use disk-usage analyzer in super-user mode (**gksu baobab**) to determine if there are things that can be safely removed to reduce the size. Some common things that can be removed are cached deb packages (sudo apt-get clean), installed packages that are no more required (sudo apt-get autoremove) and virtual machines if any.

Anyway, now that you got your problem solved, I think you should mark it as such. Hope the experience gets better for you next time :)

---

### Post by vanjadjurdjevic on 2011-08-16
Hey I figured it out, the problem with usb. After switching 3 usb i finally realized that the motherboard on my acer 5315 aspire is not very supportive about booting from usb so thats it :) Thanks for ur help. I'm starting to think that this forum is amazing :]

---

### Post by walt.smith1960 on 2011-08-16
> **vanjadjurdjevic said:**
> Hey I figured it out, the problem with usb. After switching 3 usb i finally realized that the motherboard on my acer 5315 aspire is not very supportive about booting from usb so thats it :) Thanks for ur help. I'm starting to think that this forum is amazing :]

I don't know if your problem is the same as mine.  I created live USB sticks that would boot in two machines but not in my desktop -- Homebrew with Gigabyte MB w/ Award Modular BIOS. I thought I had to be doing something wrong or the MoBo was defective. My problem was that with my particular BIOS, the USB stick had to be formatted with Windows in order to boot.  I read that, tried it and it worked like a charm.  My MoBo reads and writes USB sticks perfectly with factory or GParted FAT32 formatting but wouldn't boot.  To boot requires formatting with Windows.

---

### Post by vanjadjurdjevic on 2011-08-17
> **walt.smith1960 said:**
> I don't know if your problem is the same as mine.  I created live USB sticks that would boot in two machines but not in my desktop -- Homebrew with Gigabyte MB w/ Award Modular BIOS. I thought I had to be doing something wrong or the MoBo was defective. My problem was that with my particular BIOS, the USB stick had to be formatted with Windows in order to boot.  I read that, tried it and it worked like a charm.  My MoBo reads and writes USB sticks perfectly with factory or GParted FAT32 formatting but wouldn't boot.  To boot requires formatting with Windows.

Exactly! I remembered that Acronys boot up script on my usb worked perfectly on this laptop, but linux formated flash wouldn't. That is MB problem definitely. Thanks for your info :KS

---

