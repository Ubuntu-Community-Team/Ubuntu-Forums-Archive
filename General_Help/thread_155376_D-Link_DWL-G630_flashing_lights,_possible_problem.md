---
title: "D-Link DWL-G630 flashing lights, possible problem?"
date: 2006-04-04
forum: General Help
---

### Post by PapaWiskas on 2006-04-04
Just wondering about the flashing lights on my card.

On my wifes XP laptop the LINK light is solid and the ACT light flashes.  
Her same card in my Ubuntu laptop shows up as wlan0, and I have a solid Link light and blinking ACT light.

Now I got the same model card, from a different seller, but this card in my Ubuntu shows up as ath0, which I wasnt expecting since the one that my wife uses shows up as wlan0, and both of my lights flash simulataneously.  I am typing this wirelessly right now, so my question is, is something wrong, am I hurting the card, or is this blinking normal?

Everything appears normal, but I am by no means an expert.  I just dont want to fry something.

---

### Post by Shay Stephens on 2006-04-05
I have the DWL-G650 on breezy and it shows up as ath0 and both lights blink on and off at the same time too.  Everything seems to be working fine for me.

I just wish I could get this to work in the dapper partition I have, but it won't show up in the networking window.

---

### Post by PapaWiskas on 2006-04-05
seems like I read a post somewhere about your problem.  I was going to get the 650 but opted for the 630 since I am not an adept Linux user.

YET....:twisted: 

In fact I know I read something about that issue of yours, I might go looking to see if I can find it.

---

### Post by Shay Stephens on 2006-04-05
Hmm, I have the 630 in a box somewhere.  I will try it just to see if anything changes.

[QUOTE=PapaWiskas]seems like I read a post somewhere about your problem.  I was going to get the 650 but opted for the 630 since I am not an adept Linux user.

YET....:twisted: 

In fact I know I read something about that issue of yours, I might go looking to see if I can find it.[/QUOTE]

---

### Post by Shay Stephens on 2006-04-05
[QUOTE=Shay Stephens]Hmm, I have the 630 in a box somewhere.  I will try it just to see if anything changes.[/QUOTE]

Using the 630 in dapper didn't change anything.

---

### Post by PapaWiskas on 2006-04-05
Hey Shay Stephens,

You didn't happen to try this page did you, because it is the page I used to help determine which card I bought for Breezy.  Also, keep in mind Dapper is far from being done yet, I would imagine that by final release it will work.  But you might want to notify someone, one of the developing staff and let them know about your issue.

Anyway here is the link, I hope it helps. If you are not sure how to do ndiswrapper, just search around, there are tons of threads about it.

[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)

Good luck bra!  Peace

---

### Post by Shay Stephens on 2006-04-05
[QUOTE=PapaWiskas]Hey Shay Stephens,

You didn't happen to try this page did you, because it is the page I used to help determine which card I bought for Breezy.  Also, keep in mind Dapper is far from being done yet, I would imagine that by final release it will work.  But you might want to notify someone, one of the developing staff and let them know about your issue.

Anyway here is the link, I hope it helps. If you are not sure how to do ndiswrapper, just search around, there are tons of threads about it.

[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)

Good luck bra!  Peace[/QUOTE]

It looks like there is no driver associated with the card.  So that is why it shows up in the device manager but not the networking window.  I will try looking around for a driver.  Thank you for the info link.

---

