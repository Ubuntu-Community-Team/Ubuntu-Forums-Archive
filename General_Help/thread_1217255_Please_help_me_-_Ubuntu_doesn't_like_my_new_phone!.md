---
title: "Please help me - Ubuntu doesn't like my new phone!"
date: 2009-07-19
forum: General Help
---

### Post by Thanh-BKK on 2009-07-19
Hello.

Today i bought a new mobile phone, came home - and found that my Ubuntu doesn't like it. USB cable, that is. The phone is a Samsung L700, it uses the same cable as my boyfriend's Samsung U900 and my other Samsung S259. 

Ths S259 immediately pops up as an external drive, it's memory card that is, and the U900 asks first if i want "Mass Storage", "PC-Studio" or "Media Player". Selecting "Mass Storgae" does the same - i.e. the memory card is mounted as an external drive.

The new L700 has the same options as the U900, however selecting "Mass Storage" does - nothing on the computer, and on the phone the icon for memory card disappears. So instead of that memory card being mounted in the computer it is being UNmounted in the phone (and after disconnecting the cable i have to restart the phone or remove and re-insert the card to make it work again).

Now what can i do to make my Ubuntu play ball nicely and do what it is supposed to do - mount that memory card as with any other phone..? 

And nope, it's not the phone's fault - tested on my boyfriend's laptop with Windoze and there it works as it should. 

And on Ubuntu, issuing a "lsusb" tells me that a device "Samsung Elctronics" is indeed connected, so the computer knows it's there, just doesn't work with it. 

Ubuntu here is still my trusty Hardy 8.04.2, kernel 2.6.24-24 generic. 

Appreciate any help - many thanks in advance :)

Kind regards.....

Thanh

---

### Post by 3rdalbum on 2009-07-19
This could be related to the bug in Hardy that stopped certain MP3 players from mounting. Hardy tries to be a little too clever and attempts to mount the devices as MTP, but fails.

You will probably need to manually mount the device, from the command-line.

---

### Post by khelben1979 on 2009-07-19
Does the mobile phone support bluetooth?

---

### Post by abhilashm86 on 2009-07-19
> **Thanh-BKK said:**
> Hello.

Today i bought a new mobile phone, came home - and found that my Ubuntu doesn't like it. USB cable, that is. The phone is a Samsung L700, it uses the same cable as my boyfriend's Samsung U900 and my other Samsung S259. 

Ths S259 immediately pops up as an external drive, it's memory card that is, and the U900 asks first if i want "Mass Storage", "PC-Studio" or "Media Player". Selecting "Mass Storgae" does the same - i.e. the memory card is mounted as an external drive.

The new L700 has the same options as the U900, however selecting "Mass Storage" does - nothing on the computer, and on the phone the icon for memory card disappears. So instead of that memory card being mounted in the computer it is being UNmounted in the phone (and after disconnecting the cable i have to restart the phone or remove and re-insert the card to make it work again).

Now what can i do to make my Ubuntu play ball nicely and do what it is supposed to do - mount that memory card as with any other phone..? 

And nope, it's not the phone's fault - tested on my boyfriend's laptop with Windoze and there it works as it should. 

And on Ubuntu, issuing a "lsusb" tells me that a device "Samsung Elctronics" is indeed connected, so the computer knows it's there, just doesn't work with it. 

Ubuntu here is still my trusty Hardy 8.04.2, kernel 2.6.24-24 generic. 

Appreciate any help - many thanks in advance :)

Kind regards.....

Thanh
oh i'd also same problem, i used wine to run .exe form cd they gave from samsung, it din't help:(
if you have memory card, then ubuntu will recognise...........

---

### Post by Thanh-BKK on 2009-07-19
Hello.

Thanks for all replies, i will address accordingly.

@3rdalbum
My mp3-player (a Philips) works as pretty much every other phone that i tried so far - plug in the cable and rather immediately a new external (USB) drive is mounted. However this phone simply does nothing, instead it's memory card disappears INSIDE THE PHONE as if unmounted there. Which is weird. 

How would i mount it from the command line? I don't have a mount point. Maybe it helps to say that if i select "Media Player" from the phone's menu, F-Spot comes up and properly imports respectively displays the PHOTOS inside the phone (and the memory card!), but ONLY photos - and no possibility to open the drive where they are on, just the actual photos. F-Spot detects the phone as a camera and ignores videos, mp3 and other content. 

@khelben1979
Yes, it has Bluetooth and no problems whatsoever transferring files back and forth between the computer and the phone that way. However it is, as Bluetooth is by nature, rather slow for larger files such as mp3 or videos. I prefer to use the data cable for it's convenience - plug-and-play supposedly, except for THIS phone. I have an internal memory-card reader in the computer, too, which also works flawlessly. But, see above - the cable is supposed to be for that purpose :)

@abhilashm86
On Samsung's CD is the PC Studio or what that's called, and modem drivers. I don't need that, to modify pictures i use Gimp, to create and edit videos i use WinFF/FFmpeg and to transfer data, well, i would use the cable and the "Mass Storage" mode as with all the other phones - if it would work with this one. 

Yes, there is a memory card inside the phone but Ubuntu does NOT work with it, unlike any other Samsung i have so far tried (i have several own Samsung phones and my boyfriend has one, too, two of that "collection" even use the very same data cable as this one). With some other phones (Sony-Ericsson, Huawei, TWZ) and my Pghilips mp3-player it works as well, as soon as the respective cable is plugged in the computer the device comes up as a drive and i can copy/paste or drag/drop files around.

This Samsung L700 is the first phone i personally tried on this Ubuntu where it does NOT work that way.

I will now fire up my second computer which runs Jaunty and see if it works THERE. Will report again.

Kind regards.....

Thanh

---

### Post by Thanh-BKK on 2009-07-19
Hello again.

On Jaunty it works as it should!!

So clearly a bug (?) in Hardy. 

Kind regards.....

Thanh

---

