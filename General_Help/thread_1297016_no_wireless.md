---
title: "no wireless???"
date: 2009-10-21
forum: General Help
---

### Post by cmscott2 on 2009-10-21
Hello, i recently moved to a place with wireless internet. for some reason i can not connect to the internet. I was able to connect with a wired connection at  my old place. How can I check to see if I have a wireless card? What is ubuntu can not read the card? when i open the side of my computer what should i look for if i want to check for a wireless card?

I miss the internet :( and the only way to get online is at work which is what i am doing now......

please helP!!!

---

### Post by ColdFFF on 2009-10-21
AFAIK most wireless network adapter cards have an external aeriel. You would see this on the back of your computer with the rest of the PCI cards (sound card, graphics card etc.). I doubt very much a wireless adapter will be built into the motherboard.

Alternative to a wireless card, you can buy wireless usb dongles.

For ease of use I would suggest buying a wireless dongle, which will be much easier to transfer between computers if/when you get a new one.

---

### Post by NightwishFan on 2009-10-21
Perhaps my post in the other thread should be merged, or this thread merged back.

[http://ubuntuforums.org/showthread.php?t=1296196&page=3](http://ubuntuforums.org/showthread.php?t=1296196&page=3)


I would advise you check if you actually have a wireless adapter before we proceed. How do you connect to the wireless? If there is a router local, I am sure you could use a wire.

---

### Post by jward3010 on 2009-10-21
The best way to tell if you gave a wireless card is running the following command in the terminal:
```
sudo lshw -C network
```
Copy it and paste it back here if possible.

---

### Post by cmscott2 on 2009-10-21
will this work on ubuntu?

**D-Link Wireless G USB 2.0 Adapter 802.11g, 54Mbps**

---

### Post by NightwishFan on 2009-10-21
A poster said that that device worked immediately with no tweaking on Ubuntu.


When you get back to your home machine could you do the following?

I would like to see the whole LSHW output, to see if the driver is loaded. Could you run this command and post the text file here. It will be on the desktop.
```
sudo lshw > Desktop/hardware.txt
```


Also post the output of this command when you can as well.
```
sudo iwconfig
```

---

### Post by cmscott2 on 2009-10-21
ok i will do that tonight and let you know tomorrow, thank you! :)

---

### Post by cmscott2 on 2009-10-22
here is what I have done so far. 

Please see attachment

I hope this helps

---

### Post by jward3010 on 2009-10-22
Is there any reason you can't put that stuff into a post. 

In some cases you got a few commands wrong and thats why they printed out there usage options as opposed to actual data needed.

Post those commands again within (code)info(/code) tags (Just change the normal brackets to square ones). Makes everything visible and easy to read.

I'm currently on my Windows7 laptop and have no Office (Open or Microsoft) installed yet, hence can't read the doc.

---

