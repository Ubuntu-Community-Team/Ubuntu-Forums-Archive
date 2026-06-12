---
title: "HP Mini 210-1021eg driver"
date: 2010-10-22
forum: General Help
---

### Post by nearlymagicman on 2010-10-22
I want to install Ubuntu on my netbook, but HP doesn't provide any drivers so i asked @ Laptops but nobody answered me so i hope that anybody here will be able to give me some advise. I don't want to install Ubuntu without any knowledge about drivers and so on.


Thanks for your help,


nearlymagicman

---

### Post by Hippytaff on 2010-10-22
Ubuntu has good support for most hardware now with the exception of a few things. What drivers/hardware are you worried about?

---

### Post by nearlymagicman on 2010-10-22
Well,

i am not a real pro in the driver-topic, but i guess i will need a driver for my graphic chip, for my motherboard, and for my wlan/lan adapter, for my soundchip and most likely for my touchpad (multitouch).(I already read that there is no perfect driver for the touchpad.)

That were about all drivers i needed for my Home-PC.

---

### Post by Hippytaff on 2010-10-22
Well, it's faily likely that there are native drivers for these (which form part of the kernel) the best thign to do is try ubuntu from live cd and if everything works then install it. If not investigate :-)

---

### Post by nearlymagicman on 2010-10-22
ok thanks, i will do that :)

One last question, is it necessary to install the Ubuntu-netbook-mix or can i just install the normal one i use on my home PC?

---

### Post by Hippytaff on 2010-10-22
The netbook-mix is designed with netbooks if mind, so screen resolution for example is taylord for small screens etc. But as far as I know the standard ubuntu will work, but might be a bit heavy on resouces depending on the specs of the netbook. So it might be worth doing a bit of research
 
[http://en.wikipedia.org/wiki/Ubuntu_Netbook_Remix](http://en.wikipedia.org/wiki/Ubuntu_Netbook_Remix)

---

### Post by nearlymagicman on 2010-10-22
Well, my netbook can handle Windos7 so it schould be able to handle Ubuntu :P
I will test the live-cd (usb)


Well it seems to work but my touchpad doesn't respond i have to use an usb mouse.

---

### Post by arubislander on 2010-10-22
Ubuntu Desktop Edition is sure to work with the available resources. I installed it on my Acer Aspire One with no probs. But always check with a live edtition first.

---

### Post by Hippytaff on 2010-10-22
> **nearlymagicman said:**
> Well, my netbook can handle Windos7 so it schould be able to handle Ubuntu :P
I will test the live-cd (usb)
 
 
Well it seems to work but my touchpad doesn't respond i have to use an usb mouse.
 
If you happy using a mouse great (i prefer using a mouse to the touchpad) but it also means you've got something to fix, which is fun :-) if your that way inclined :-)

---

### Post by nearlymagicman on 2010-10-22
Well, i now tested the ubuntu-live and all works perfectly just my WLAN doesn't work :), so if you could give me a hand here i wont bother you anymore ;).

Details: I want to use my home-WLAN but Ubuntu doesn't see it, which is quite fascinating because it does see a bunch of other which belong to the neighbors. The second quite interesting part is that when i switch to windows i can connect without any problems (and yes i does see it as well).
Any clues what might cause that behavior?
My only guess is that the adapter broadcasts on a false Channel, but i aint sure about that. I entered  "sudo iwlist chan" and the output is:
```
lo     no frequency information
eth0   no frequency information
eth1   14 channels in total; available frequencies :
       //bunch of frequencies
       current channel 1
```
So i guess my adapter broadcasts on channel 1, but my router does on channel 6 (I am sure about that part).
But when i tried to "fix" it with "iwconfig eth1 channel 6" and then i check the channels again, it is still on the same on (Channel 1).
Well, i do have a second guess but this one seems even more unrealistic than the first one, it might be possible that my adapter isn't strong enough to get the signal, even though there are just like 2 1/2 Walls between. But this scenario is really unlikely because my netbook is getting so much other signals.

thank you for your fast and helpful help :)

---

### Post by Hippytaff on 2010-10-22
What does
```

lshw -c network 

```
show

---

### Post by nearlymagicman on 2010-10-22
Is there smth special you are interested in? Like i said, my netbook is without internet, and it is alot i would have to copy.

If it helps, like if there was a similar incident, there are EVERY other WLANConnection i ever saw in my Windows list, just not my XD. I don't know but maybe there are some weird possibilities to configuration a adapter in a way he won't recognize the closest one.

---

### Post by Hippytaff on 2010-10-22
As much network info as possible...if it turns out its about changing the  broadcast chanell I can't help...but it might be worth cheking 'hidden networks' in network manager. Also probably worth starting a new thread so others can chip in :-)

---

### Post by nearlymagicman on 2010-10-22
i will do that then thx :)

---

