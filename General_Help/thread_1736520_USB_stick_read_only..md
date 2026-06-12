---
title: "USB stick read only."
date: 2011-04-22
forum: General Help
---

### Post by Swedish Berserk on 2011-04-22
Hello everyone. My USB stick has transformed itself to read only in Ubuntu 10.04 and Windows 7. When i put it in the old Windows XP computer i get read write permissions. 

What can be the problem here? I dont have a switch on my USB stick so it cant be that. I have tried checking it for errors in Windows 7 but it couldnt fix it. Some of the files has weird names and some folders is corrupted. I have used this USB stick many times without problems so i dont know what i did wrong..... 

How can i solve this? Do i have to reformat it? I just want my USB stick back. 

Sorry for my bad english and hope you can help me.

---

### Post by Blasphemist on 2011-04-22
You may have inadvertently changed the type of partition on the drive. Look at this for restoring it to a FAT32 type partition.
[http://www.pendrivelinux.com/restoring-your-usb-key-partition/#more-230](http://www.pendrivelinux.com/restoring-your-usb-key-partition/#more-230)

---

### Post by Swedish Berserk on 2011-04-22
> **Blasphemist said:**
> You may have inadvertently changed the type of partition on the drive. Look at this for restoring it to a FAT32 type partition.
[http://www.pendrivelinux.com/restoring-your-usb-key-partition/#more-230](http://www.pendrivelinux.com/restoring-your-usb-key-partition/#more-230)

Thanks for your fast reply Jim or Blasphemist. :P My USB stick is already FAT32. I think its corrupted..... Should i follow your guide? 

Its so weird because it worked perfectly all the time. Until i plugged it into Windows XP. Maybe i forgot to do a secure removal? I usually dont forget that.

---

### Post by Blasphemist on 2011-04-22
I understand, who knows what happened. Yes, do follow the guide and you should get good to go.

---

### Post by Swedish Berserk on 2011-04-22
> **Blasphemist said:**
> I understand, who knows what happened. Yes, do follow the guide and you should get good to go.

I tried following the guide. But it took me to a chinese website! It said something like website not available with the help of Google Translate. Anyway i used Windows 7 format tool. And i formated to FAT32 again and now its working. I lost 2mb when doing this format from 7.46GB to 7.44GB but thats to be expected. 

See how long it works now. Fortunate i have all those files on my laptop so i didnt lose anything. 

Thanks for your help Blasphemist. :)

---

### Post by jetole on 2011-12-30
> **Swedish Berserk said:**
> I lost 2mb when doing this format from 7.46GB to 7.44GB

Just thought I would give you a heads up on this. .02 GB is not 2 megabytes. It's 20 megabytes.

Once upon a time gigabyte meant 1024 megabytes when it was referred to as having a binary unit. This meant 1 gigabyte was 1024 megabytes which was 1024 kilobytes which was 1024 bytes. .02 gigabytes used to mean 20.48 megabytes, 20971.52 kilobytes or 21474837 bytes and RAM size is actually still measured with a binary unit but storage space is not. It is almost entirely accepted by the industry that storage is a SI unit meaning 1 gigabyte is 1000 megabytes which is 1000 kilobytes which is 1000 bytes. IEEE, NIST and several other top standards agencies have proposed standards to define the meaning of gigabyte, megabyte, kilobyte, etc to be SI unit and since then it has otherwise been accepted in the industry that this is now how they are referred to. New terms have been created to refer to the binary unit as gibibyte, mebibyte, kibibyte, etc. These are abbreviated as GiB, MiB and KiB but RAM is still sold as either gigabytes or GB but uses the binary unit of measurement. In my opinion I think this whole SI unit for storage capacity on a computer was the wrong decision since computers are binary by design and nature but doesn't matter. Seems the decision has been made.

Anyways, long story short, if you want to know how many megabytes .02 gigabytes is, just multiply .02 * 1000

---

