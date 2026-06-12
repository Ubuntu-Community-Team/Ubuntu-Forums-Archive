---
title: "Problems with HP Officejet J4680 all-in-one"
date: 2011-07-19
forum: General Help
---

### Post by ClientAlive on 2011-07-19
Hi,

I've had this printer working more than once before. I say 'more than once' because I always seem to have some problem with it. Even when it is working I would often get where the job would be delayed a few minutes (and it would tell you when it was held till - which was a few minutes later than what the clock on the computer said).

Now, I can't get it working again. It is a wireless capable printer (and that's how I've been using it all along). Recently my ISP upgraded their system and it required a modem reboot on my part after it was done. I wasn't sure if this could have anything to do with it. So, after I discovered it isn't working, I went to the control panel on the printer and configured the wireless connection again (which it gave output that it connected successfully). I also deleted the instance of that printer in

```
System > Administration > Printing (I'm running Ubuntu 10.04 LTS)
```

and then found it in the list of detected printers under "Network" and installed it again. I hope I didn't just send that test page to my neighbor's printer  :). I did notice that the last two numbers of the ip address for the device was 13 whereas the last two for the printer as it was set up before (before I deleted it in Printing) was 12. Unless the neighbor also has an HP J4680 I'm not seeing that happening.

I also went into

```
Help > Troubleshooting
```

where I was able to select that printer from the list in about step 3. After going "forward" and then telling it to print a test page, the page not printing, and telling it that it didn't work I was given the output of some error log. I've attached that output.

Does anyone know what might be going on?

---

### Post by ClientAlive on 2011-07-19
Nevermind. I'm a total dumbass. I needed to set the date and time on the thing. I'm not sure why that would be the case because it was set before. It did sit unplugged for a couple days though. Maybe that's what happened.

It's working now though. I'd just about bet that, that thing with the printing being delayed by a few minutes (times before) was due to the printer's time being set differently than the computer's.

Should've thought to check that before.

:P

---

