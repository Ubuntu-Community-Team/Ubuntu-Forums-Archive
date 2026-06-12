---
title: "Help: unable to boot toshiba running karmic"
date: 2010-02-25
forum: General Help
---

### Post by rohan1 on 2010-02-25
Hi

Have been using Karmic kaola for a few months on my toshiba tecra laptop..as of yesterday unable to boot up..all I get is a black screen on start up with no further activity..no bios menu etc..the led lights up for the power source and occasionally lights up on the hard drive which seems to make some noise as if trying to function...did connect it up to an external monitor which displayed the start up toshiba logo but then came up with the message error: "invalid enviroment block" unable to load default boot entries...am wondering if 
1. there is a fault with the grub set up?
2. Something more serious as my laptop screen refuses to function?
3. Will I be able to retrieve my hard drive data using ubuntu live cd connected to an external monitor?

Would appreciate any help!

Thanks, Rohan

---

### Post by NefariousNobo on 2010-02-25
Okay, so the first thing you need to verify for certain is whether the error occurred while the bootloader was in control or while the BIOS was in control. Can you boot from any alternate devices (Ubuntu LiveCD?)?

---

### Post by rohan1 on 2010-02-25
> **NefariousNobo said:**
> Okay, so the first thing you need to verify for certain is whether the error occurred while the bootloader was in control or while the BIOS was in control. Can you boot from any alternate devices (Ubuntu LiveCD?)?

Hi

Tried booting from a live cd but the same response occurs i:e Black screen...will try and connect it to an external monitor at work tomorrow to see if I can boot from a live cd

Rohan

---

### Post by rohan1 on 2010-02-25
With the ext monitor, I was able to see the toshiba start up logo followed by the option to enter bios set up before I received the error

---

### Post by NefariousNobo on 2010-02-25
Well (obviously) there is a problem with your monitor, in addition to whatever other problems you may have ;)

Now, at least, I can tell you fairly certainly that any data is probably recoverable, unless the "invalid environment block" referred to HD corruption. At any rate, the first thing you want to do is to try to see *more* where the problem is. I recommend checking the hard drive with the LiveCD (i.e. Can it be mounted, can the files on it be read, possibly an HD integrity test would not go amiss). If the HD partition appears to be more or less healthy, then the next step will be to restore grub (probably). I'm hoping someone else shows up here with a better solution than the ones I'm thinking of, but this *should* work.

Hope this helps...

---

### Post by rohan1 on 2010-02-25
connected laptop to an external monitor..booted from a livecd..display showed toshiba logo followed by the Mandriva linux booting process (forgotten that I had installed mandriva sometime ago)..quickly shut it down as I remember it was not a Livecd and did not want to erase my hard drive...will download a livecd and try again..unfortunately only have access to an ext monitor on tuesday..also, the laptop screen still does not show up anything when not connected to the external monitor..will provide updates on the problem on tuesday..am hoping the laptop has not packed in as would prefer to continue using linux

Appreciate all the help so far....

---

### Post by rohan1 on 2010-03-01
Okay...tried booting laptop using LiveCd connected to an externalmonitor..Display showed toshiba logo with bios setup options...then followed by the LiveCd loading up...selected ' try ubuntu without making any changes to computer...ubuntu logo displayed with horizontal line showing status of loading process...when the status line fills up to the right a few minutes later display shows streaks of coloured lines at the top of the screen and a black background and no further activity...also the LiveCd seems to stop as well...tried booting twice but no success..need to mention that when connected to an ext monitor at the beginning I get several vertical bands of red or green lines...Any advice on the above issue would be appreciated..

Thanks

---

### Post by rohan1 on 2010-03-02
anyone with suggestions :(

---

