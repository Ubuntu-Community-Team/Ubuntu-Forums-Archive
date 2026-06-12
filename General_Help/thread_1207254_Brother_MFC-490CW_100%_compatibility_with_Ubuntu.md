---
title: "Brother MFC-490CW: 100% compatibility with Ubuntu?"
date: 2009-07-08
forum: General Help
---

### Post by tominto on 2009-07-08
Hello.  I'm thinking of replacing my 10 year old canon printer, that just bit the dust, with a Brother MFC-490CW. It's a multifunction printer that prints, scans, faxes and has wifi.  This will work with my current setup using Windows XP, but I'm wondering if this will be 100% compatible with Ubuntu??  Not using Ubuntu at the moment because the drive that I had it installed on died but hope to get going again with Ubuntu soon.

Thanks
Tom

---

### Post by Shazaam on 2009-07-08
I have a 420CN that works flawlessly. Install the Brother drivers through Synaptic. Once installed enter this in Firefox to get to the cups admin page...
```
http://127.0.0.1:631/
```

---

### Post by chriskin on 2009-07-08
my experience with printers on ubuntu says that they work ok, but the wifi is a rare thing to find

i also believe that not many people in the next hours will get to see this post AND have the exact same printer, so it would be best for you to google it

---

### Post by HermanAB on 2009-07-08
If you have bought it already, then, well, good luck...  It may work, it may work partially...  My experience with Brother is that they do not really know how to write printer drivers and I have had nothing but trouble.

If you want to be sure that your printer will work, buy an HP.

---

### Post by whitehousea on 2009-07-08
I have the same printer you speak of and I am having trouble installing the drivers myself, however I am a linux newbie and that is playing  a large portion in my existing problems.  Did you have any luck with any of this yet ?

---

### Post by dylbud on 2009-07-12
I have the same printer. I originally set it up using Windows XP, which was of course easy. I use a wireless router, so the "connection" goes computer-->router-->printer. So, when I boot Ubuntu, the printer is already available on the network (Although I still needed to download a driver in order to use it).

If you are just using Ubuntu, I would suggest going into the menu on the printer and try going through some of the wireless network configurations, including what I think is a wireless setup function. From there you should be able to generate or view an access code that you would then use to access the printer from your computer using Ubuntu's wireless network tools.

I didn't do it that way, so that is just a hunch. But I think the key is getting the information that you need out of the printer, and then configuring ubuntu with that info.

By the way, I while I got the printer to work, I haven't figured how to use the scanner function. Using the XSane scanner application does not work, because it does not detect any attached devices.  If anyone figures that out, please let me know.

---

### Post by tominto on 2009-07-15
Thanks for the replies everyone.  I went ahead and bought the printer because I was able to get a good deal on it, hoping for the best.  I'm glad I did because after a bit of tinkering I got it to work (at least the printer and scanner work for me...haven't tested the wifi, network printing or the fax).

So if anyone wants to get this working, this is what I did:

Downloaded the printer driver, and scanner driver/scankey tool from the brother linux site at: [http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html)
The .deb files install themselves automtically.

The printer worked fine, but when I tried to open xsane for the scanner I got an I/O error.  

The solution for this is also on the brother website here: [http://solutions.brother.com/linux/en_us/instruction_scn1c.html](http://solutions.brother.com/linux/en_us/instruction_scn1c.html)

which involves changing the MODE number in /lib/udev/rules.d/50-udev-default.rules from "0664" to "0666", save the file and presto!!

---

### Post by alekese on 2009-08-21
For any newbies to Ubuntu (like me) who are still frustrated, let me make it even simpler:

1. Go to Brother's Linux [Download page for MFC-490CW]("http://solutions.brother.com/linux/en_us/download_prn.html#MFC-490CW").
2. Download _both_ of the "deb" format drivers (one is big, one is tiny)
3. Double-click on each file once it's downloaded (either from the download manager or - more than likely - on your desktop) to install it.
4. Go to System>Administration>Printing and the printer configuration utility comes up.
5. Find MFC490CW (if it's not there, make sure you've downloaded and run _both_ deb files - beyond that I have no idea what you might have done differently than me) and right-click properties on the icon for this printer.
6. MFC490CW is installed but probably not set up as a wireless network printer yet.  If the "Device URI" doesn't say something like: "socket://192.168.1.100:9100" (but possibly with different numbers?) then click the "change" button to the right of it.  It will search for printers.
7. In the new window that pops up, click on the triangle next to "Network Printers".  The MFC-490CW should be listed (assuming you have one, it's turned on, and it's within wireless range).  Select it.  Hit the "Apply" button.
8. Back at the printer configuration window, hit "Print Test Page".  You should be done.

---

### Post by atomicben on 2009-08-24
PERFECT Instructions [alekese]("http://ubuntuforums.org/member.php?u=897947") I just installed Jaunty and I'm printing to my 490CW.  Now I'm going to tackle the scanning deal but hey, I'm almost there.

---

### Post by atomicben on 2009-08-24
1

---

### Post by Chicanob12 on 2009-09-08
> **tominto said:**
> Thanks for the replies everyone.  I went ahead and bought the printer because I was able to get a good deal on it, hoping for the best.  I'm glad I did because after a bit of tinkering I got it to work (at least the printer and scanner work for me...haven't tested the wifi, network printing or the fax).

So if anyone wants to get this working, this is what I did:

Downloaded the printer driver, and scanner driver/scankey tool from the brother linux site at: [http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html)
The .deb files install themselves automtically.

The printer worked fine, but when I tried to open xsane for the scanner I got an I/O error.  

The solution for this is also on the brother website here: [http://solutions.brother.com/linux/en_us/instruction_scn1c.html](http://solutions.brother.com/linux/en_us/instruction_scn1c.html)

which involves changing the MODE number in /lib/udev/rules.d/50-udev-default.rules from "0664" to "0666", save the file and presto!!


How did you get the permission to save the changes? it tells me 
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

HELP!!!!

________________________________________
SOLVED-----I figured it out

---

