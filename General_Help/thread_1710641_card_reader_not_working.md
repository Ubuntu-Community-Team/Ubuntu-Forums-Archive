---
title: "card reader not working"
date: 2011-03-20
forum: General Help
---

### Post by ArbiterOfTruth on 2011-03-20
Good day,

My built-in multi-card reader doesn't seem to be working. I have had at least 3 friends ask me to check something on their cards & all 3 times when I insert the cards into my netbook nothing happens. It didn't work in 10.04 & it still isn't working in 10.10. Is it that I have to enable or activate something in ubuntu to get it going?

I did a search using SD card reader not working & got a cluster&$!& of stuff not relating to the issue so please if there is a good thread i.e. one showing the proper steps to solve the problem that people have replied saying "we did what you said & it worked" please paste the link for me.


Thanks in advance,

---

### Post by tredegar on 2011-03-20
1] Please do a fresh boot, and then _before you have plugged anything in_, run and post the output of this command:

```
cat /proc/scsi/scsi
```

Is your cardreader being seen?

2] What happens if you plug a card into an external USB cardreader, and then plug the cardreader in. Is the card seen?

---

### Post by ArbiterOfTruth on 2011-03-20
> oldtimeveteran@oldtimeveteran-netbook:~$ cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: WDC WD1600BEVT-2 Rev: 01.0
  Type:   Direct-Access                    ANSI  SCSI revision: 05
oldtimeveteran@oldtimeveteran-netbook:~$

That's what I see. Does that help in any way?

Sorry I don't have an external card reader.

Thanks for taking the time,

---

### Post by matt-fender on 2011-03-20
Which netbook are you using Ubuntu 10.10 on?

---

### Post by tredegar on 2011-03-20
From your **cat /proc/scsi/scsi** it looks like your card reader isn't being detected, as only your HDD is listed.

Is your card reader enabled in your BIOS?

You might try putting a card in first and then booting.

Then **cat /proc/scsi/scsi** again.

Any difference?

Please beg, or borrow, an external card-reader, and try that too.

---

### Post by ArbiterOfTruth on 2011-03-20
It's an Acer Aspire One. 


I never even thought about the BIOS. :oops: I will check that ASAP.

Thanks again,

---

### Post by ArbiterOfTruth on 2011-03-21
OK I checked the BIOS & I don't see anything remotely relating to the card reader. Any suggestions?

---

### Post by matt-fender on 2011-03-22
I had an acer aspire one and fixed this issue when i find the fix i will PM it to you!!!

---

### Post by ArbiterOfTruth on 2011-03-22
Thanks!

---

### Post by matt-fender on 2011-03-22
Hey sorry for the late reply, had to work a long shift, this is my thread from a while back when i bought an Acer Aspire One A150 to be precise,

[http://ubuntuforums.org/showthread.php?t=1502972](http://ubuntuforums.org/showthread.php?t=1502972)[B]

Theres a couple of links in there that may help you :)
[/B]

---

### Post by ArbiterOfTruth on 2011-03-23
Hey there, I was looking at the link you sent & one of the suggestions for the problems seems to be editing a command of some sort which I am not familiar with. Before we delve into that however, I had a hunch I decided to investigate.

[IMG]http://i894.photobucket.com/albums/ac143/Tru3b0rn/General/card_repositories.png[/IMG]

I'm wondering if the problem is the driver is not installed for the card reader. Since there are so many which one do I select for installation? Well if that is the problem at all. Just a thought.


Thanks,

---

### Post by tredegar on 2011-03-23
Thanks for the additional information.

I put **card reader** into Synaptic as you did. The packages it pulled up are all to do with "smart cards" [ look like a chipped credit card, often used as 'secure' ID badges ], which are not what you are trying to use. So I don't think the picture you posted is going to help.

Please answer:

1] What, exact,  version of linux are you running on your AAO? "Whatever it came with" or a distro you installed yourself. If the latter, please tell us the exact details of what you have installed.

2] If you put a card in first, then boot, is it visible?

3] Please try putting a nkown to be working card into an _external_ reader and then plugging that in? I know you do not have one, so just borrow one.

---

### Post by ArbiterOfTruth on 2011-03-23
The netbook originally came with Windows 7 Starter which I removed a few minutes after getting it home.
It's now 10.10 netbook edition. I upgraded from 10.04 netbook edition a few days ago. 

I tried that in work & it didn't work.

I will try to see if I can get my hands on one.

Thanks,

---

### Post by matt-fender on 2011-03-24
I rememeber my Acer Aspire One would mount my SD Card if i had it inserted BEFORE i turned it on. XD Cards however were a completely different story, i could never get Ubuntu to read an XD card using my internal reader.

---

