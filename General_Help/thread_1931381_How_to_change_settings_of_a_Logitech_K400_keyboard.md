---
title: "How to change settings of a Logitech K400 keyboard?"
date: 2012-02-25
forum: General Help
---

### Post by Teh Lurv on 2012-02-25
Hey everyone,

I recently picked up the Logitech K400 wireless keyboard/trackpad to allow me to use my netbook with Ubuntu while it is hooked up to my TV. The keyboard works fine with Ubuntu (no unused keys, trackpad works, etc) but there is no way to change the settings of either the keyboard or trackpad. I would like to, at the very least, turn off tap-to-click and up the CPI of the trackpad.

Does anyone know if there any utilities or drivers to control this device?

---

### Post by Mark Phelps on 2012-02-25
If there's nothing under Mouse and Touchpad under System Settings, then you're out of luck.

In Windows, Logitech setting are often handled by the Logitech software -- which won't install or run under Linux.

---

### Post by Guinioul on 2012-02-29
hello [Teh Lurv]("http://ubuntuforums.org/member.php?u=903089") :

I plan to buy this keyboard for my htpc . 

But i got one question :
Is the multitouch of the touchpad natively working on ubuntu ? 
I mean : scolling with two fingers .


Thanks by advance .

---

### Post by Teh Lurv on 2012-03-01
> **Guinioul said:**
> hello [Teh Lurv]("http://ubuntuforums.org/member.php?u=903089") :

I plan to buy this keyboard for my htpc . 

But i got one question :
Is the multitouch of the touchpad natively working on ubuntu ? 
I mean : scolling with two fingers .


Thanks by advance .

I can confirm that vertical and horizontal scrolling works with Ubuntu. I've only used my the two finger scrolling, so I can't confirm if any other multi-touch gestures work.

The scrolling has become my new pet-peeve with this keyboard. By default it uses two finger scrolling, however edge scrolling would've been a more natural fit with this keyboard, as the layout encourages you to hold it like a controller and manipulate the trackpad with your thumb.

But don't let that discourage you from buying it. It is overall a pretty good keyboard for the price.

---

### Post by Guinioul on 2012-03-02
Hello [Teh Lurv]("http://ubuntuforums.org/member.php?u=903089")
 
 Thanks for your answer :smile:
 
 Finaly I found another great wireless keyboard with multitouch features, rapoo E9080 :
[IMG]http://www.journaldugeek.com/files/2011/10/Rapoo-E9080-Wireless-Ultra-Slim-Keyboard-with-Touchpad.jpg[/IMG]

It is not bluetooth so it might be same protocol as other wireless products and finaly I think i will buy this one instead of the k400 cause the multitouch should be supported (I hope) .

a big thanks again :-)

---

### Post by wump on 2012-08-05
I just bought the Rapoo E9080 and it works well in Ubuntu. All the gestures are supported (single finger tap left button, two finger tap right button, two-finger vertical scrolling, and two-finger swiping left/right for forward/back). No horizontal scrolling is supported by this device.

However, it does not appear to be possible to get raw multitouch event data (not even in Windows) to implement custom gestures (zooming, rotating, and other fun). The device simply shows up as a HID keyboard and mouse. I'm not sure whether this is problematic for you, but it was a bit of a disappointment for me.

---

### Post by Guinioul on 2012-08-06
Hello Wump,

thanks for your answer .

I finally bought the k400, it support two finger swipe for horizontal and vertical scrolling but no more gestures .

as your rapoo it is not real raw multitouch events (but the keyboard and the touchpad do the job) . 

Can you tel us more about the numeric keypad ? does it work ? Is it practical ?

thanks .

---

### Post by wump on 2012-08-11
It works OK. By sliding at the bottom of the keypad you can switch between keypad and mouse. This works reliably, though it's easy to forget what mode you are in. There is no visual indication of this on the keyboard, they say due to power concerns, and AFAIK there is also no software event that notifies the host of the mode. 

Also I find that using the keypad in keyboard mode is a bit tricky, as there is no tactile feedback of the key positions. This makes it easy to fat-finger :-) For light keypad usage it's good enough.

Horizontal scrolling doesn't work because it interprets the horizontal swipe as key 8 and 9 (forward and back). HID capabilities do report the horizontal wheel but it simply never sends events.

All in all it is a good keyboard for a media PC and internet surfing.

---

### Post by flea74 on 2012-12-09
Just found answer to k400 r tap to click problem here [http://forums.logitech.com/t5/Keyboards-and-Keyboard-Mice/Disable-logitech-K400-mouse-click-tap-to-click/td-p/737830](http://forums.logitech.com/t5/Keyboards-and-Keyboard-Mice/Disable-logitech-K400-mouse-click-tap-to-click/td-p/737830)

Simple answer without going to page.
"Hold down the blue function key and the left trackpad key simultaneously.


No software required, OS is irrelevant."

---

