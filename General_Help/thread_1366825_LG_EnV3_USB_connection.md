---
title: "LG EnV3 USB connection"
date: 2009-12-28
forum: General Help
---

### Post by zonination on 2009-12-28
So I got a nice new LG EnV 3 for Christmas. It comes with a USB charger (it's pretty neat), and for kicks I decided to hook it up to my Ubuntu machine. It has it detected, according to dmesg, and sends it power, but it doesn't do anything beyond that.

I would like to somehow mount this and get some of my pictures off of it. I'm not sure how I go about this, whether or not my first step would be to find some drivers or to input a special loopmount command into terminal.

Let me know what I need to do. Merry Christmas to you all, and I hope your new year's is fantastic!

---

### Post by tjwilli on 2009-12-28
> **zonination said:**
> So I got a nice new LG EnV 3 for Christmas. It comes with a USB charger (it's pretty neat), and for kicks I decided to hook it up to my Ubuntu machine. It has it detected, according to dmesg, and sends it power, but it doesn't do anything beyond that.

I would like to somehow mount this and get some of my pictures off of it. I'm not sure how I go about this, whether or not my first step would be to find some drivers or to input a special loopmount command into terminal.

Let me know what I need to do. Merry Christmas to you all, and I hope your new year's is fantastic!

Try this thread:

[http://ubuntuforums.org/showthread.php?t=1145846&page=2](http://ubuntuforums.org/showthread.php?t=1145846&page=2)

In particular, add

```
 usb-storage option_zero_cd=2
```

to /etc/modules

---

### Post by mdebusk on 2009-12-28
> **zonination said:**
> I would like to somehow mount this and get some of my pictures off of it.

The easiest thing I've found with my "Chocolate 3" is to put a microSD card in it, set the phone to save everything to the card, and get an inexpensive USB card reader.

I *can* connect by cable and by bluetooth, but the card and reader is so simple, and I can take it anywhere.

---

### Post by zonination on 2009-12-29
> **tjwilli said:**
> Try this thread:

[http://ubuntuforums.org/showthread.php?t=1145846&page=2](http://ubuntuforums.org/showthread.php?t=1145846&page=2)

In particular, add

```
 usb-storage option_zero_cd=2
```

to /etc/modules

I tried this and rebooted, but for some reason it doesn't auto-mount it or treat it as storage.

After I added the line to /etc/modules, dmesg became this:
```
[  959.748386] usb 2-1: new full speed USB device using ohci_hcd and address 2
[  959.909094] usb 2-1: config 1 has an invalid interface number: 3 but max is 2
[  959.909107] usb 2-1: config 1 has 4 interfaces, different from the descriptor's value: 3
[  959.915288] usb 2-1: configuration #1 chosen from 1 choice
[  959.917479] cdc_acm 2-1:1.0: ttyACM0: USB ACM device

```

---

### Post by zonination on 2009-12-29
> **mdebusk said:**
> The easiest thing I've found with my "Chocolate 3" is to put a microSD card in it, set the phone to save everything to the card, and get an inexpensive USB card reader.

I *can* connect by cable and by bluetooth, but the card and reader is so simple, and I can take it anywhere.

That's a great idea, but I'm not in the market for an SD card/reader. I figure a simple, straight connection should be all I need instead of buying several accessories to migrate media from point A to point B. However, if things don't go so well here, I might as well.

---

### Post by totalhealth on 2010-01-30
Take a look at 

[http://ubuntuforums.org/showthread.php?t=1240665&highlight=env3](http://ubuntuforums.org/showthread.php?t=1240665&highlight=env3)

You still need the micro-SD card in your ENV3, but you can then connect to your computer through the USB.

---

