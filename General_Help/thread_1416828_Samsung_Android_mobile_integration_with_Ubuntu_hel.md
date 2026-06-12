---
title: "Samsung Android mobile integration with Ubuntu help needed."
date: 2010-02-26
forum: General Help
---

### Post by casbahdk on 2010-02-26
I just bought a Samsung i5700 Galaxy Spica (Lite) Android powered mobile and while I am waiting around for the 2.1 update, I am interested in finding out what I can do to sync, backup, etc. my i5700 to Ubuntu. I am particularly interested in what people do about firmware and system updates for Android powered mobiles. Is it possible to do from Ubuntu or do you have to have a Windows system?

Any advice is appreciated as I am a total Android newbie.

I am currently using Linux Mint 7, which is the same as Ubuntu 9.04 (Jaunty Jackalope).

Cheers

---

### Post by ubunterooster on 2010-02-26
Update is likely a .zip file so updating should go well.
make a folder called samsung and copy all files to it, if possible

---

### Post by casbahdk on 2010-02-26
> **ubunterooster said:**
> Update is likely a .zip file so updating should go well.
make a folder called samsung and copy all files to it, if possible

So I just need to connect the mobile with a USB - USB mini cable, the storage disk mounts and I drag the files over?

---

### Post by ubunterooster on 2010-02-26
via USB can you drag ANY files into it? If yes, then you can update.

---

### Post by casbahdk on 2010-02-28
> **ubunterooster said:**
> via USB can you drag ANY files into it? If yes, then you can update.

I assume that this is possible for the micro SD card, but I don't know how to access the file hierarchy of either the mobile or the micro SD. I am still trying to figure out how to turn the mobile into a target USB drive when plugging into a computer. The only other alternative is of course loading the micro SD into a card reader...

---

### Post by ubunterooster on 2010-03-01
Many microSD cards come with an adapter to regular SD. Where I live, microSD-to-USB readers can be gotten inexpensively at Staples.

I'll try posting back when I am more awake if I have more info.

---

### Post by casbahdk on 2010-03-01
> **ubunterooster said:**
> Many microSD cards come with an adapter to regular SD. Where I live, microSD-to-USB readers can be gotten inexpensively at Staples.

I'll try posting back when I am more awake if I have more info.

Thanks. I just got a file manager program called Astro, from the Android Market. The directory structure looks similar to Linux. There is a separate folder called "sdcard". I still have to figure out how to get the mobile to load as a USB drive on my desktop. I assume that if the whole directory structure and not just the micro SD card appears on my desktop, I could use any Linux backup program to backup the system on the mobile.

Interestingly, I have tried switching micro SD cards with my SanDisk Sansa, and the Android default media player didn't do anything. It didn't scan for files on the micro SD card and there were of course no songs listed. It just sat there like a stupid idiot and did nothing.

---

### Post by ubunterooster on 2010-03-01
I assume you can copy files to and from the microSD card using Astro. I'm also assuming you can read the files moved by Astro with Nautilus. If so both updating and backup can be done, though in a roundabout way.

Cameras and some phones don't recognise a card that was stuck in it with prexistent data. My one device requires that all data be stuck in an auto-created folder that it makes the first time it connects to an SD card while another requires formatting by itself. SanDisk's Sansa requires neither method. 
[I just gave my Sansa Fuse away Saturday. It did not give me wanted battery life even with rockbox replacing the firmware. Rockbox (yes it is free) also works on Sansa e250's]

---

### Post by ubunterooster on 2010-03-01
Ubuntu has built-in bluetooth support, but you need to install the "gnome-bluetooth" package via [you guessed it] synaptic. Inside this package is a tool called gnome-obex-server. This app allows you to send files from phone to computer, though not from [as far as I know] computer to phone.
  When the package is installed, hit Alt+F2, and enter "gnome-obex-server". A blue icon will appear in the notification area, and you can now send a file from your phone via bluetooth. [Still not sure how to get files ON to the phone, but it appears bluetooth will be the answer...]

---

### Post by casbahdk on 2010-03-01
The following explains how to connect the mobile to a computer. It also includes a HowTo on how to create and transfer ringtones :) Works fine on Linux Mint 7, but as it is only possible to access the micro SD card, using a card reader works just as well.

[http://www.shoemoney.com/2009/11/11/andriod-driod-mp3-free-ringtones-guid/]("http://www.shoemoney.com/2009/11/11/andriod-driod-mp3-free-ringtones-guid/")

---

### Post by ubunterooster on 2010-03-01
I'm not sure how much this would help but I've found Andriod to have an app for dropbox. You could put the files there with the desktop and pick them up with your phone and vise-versa.

---

### Post by casbahdk on 2010-03-02
> **ubunterooster said:**
> I'm not sure how much this would help but I've found Andriod to have an app for dropbox. You could put the files there with the desktop and pick them up with your phone and vise-versa.

Thanks for the heads up. I already use Dropbox, so it's nice to know that there is a Android version of the app. I guess I will have to wait and see what information we get when the update arrives. Thanks for all of your advice.

---

### Post by casbahdk on 2010-03-03
> **ubunterooster said:**
> I'm not sure how much this would help but I've found Andriod to have an app for dropbox. You could put the files there with the desktop and pick them up with your phone and vise-versa.

I just found a [URL]("http://ars.samsung.com/customer/usa/jsp/faqs/faqs_view_us.jsp?AT_ID=229707&PROD_ID=954&PG_ID=-1&PROD_SUB_ID=0") on the issue. It assumes that the customer is using Win, but it seems that the general idea is to connect the mobile, load the micro SD card on the desktop and transfer the files. In actuality, it would be just as easy to stick the micro SD card in a card reader.

BTW, I think that the reason my i5700 media player didn't react to the micro SD card from my SanDisk Sansa is because all of the files are in .flac format. The mobile doesn't support .flac for some reason. When I put the micro SD card (1 GB) that came with the mobile into the slot, the player detected the .mp3 files I had put on the card immediately.

---

