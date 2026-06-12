---
title: "can we solve hardware problems with software?"
date: 2009-07-08
forum: General Help
---

### Post by zigga15 on 2009-07-08
Hey all,

I have a really beautiful logitech G7 mouse, I have had it for a few years.

Lately I have been experiencing a problem with the clicking. Roughly 3 times every 10 single clicks. A double click is registered. That is, If I click around every few clicks a double click occurs.

This is even more annoying than it sounds. Clicking Back buttons in a browser makes for some confusing outcomes sometimes.

Anyway, long story short I understand you can easily change the double click speed, which results in you having to click faster in order to create a double click event.

This doesn't fix the problem because the double click is instantaneous, as the error is in the mouse hardware.

Is there a way to slow down the double clicking speed. I.e make it so you have to double click at a humanly possible speed for a double click event to register. And if the double click speed is surpassed a single click is registered.

Any help would be great Thanks.

~ Dan

P.S. Definitely a hardware problem, different computers, windows with setpoint software results in the same issue.

---

### Post by DGortze380 on 2009-07-08
> **zigga15 said:**
> Hey all,

I have a really beautiful logitech G7 mouse, I have had it for a few years.

Lately I have been experiencing a problem with the clicking. Roughly 3 times every 10 single clicks. A double click is registered. That is, If I click around every few clicks a double click occurs.

This is even more annoying than it sounds. Clicking Back buttons in a browser makes for some confusing outcomes sometimes.

Anyway, long story short I understand you can easily change the double click speed, which results in you having to click faster in order to create a double click event.

This doesn't fix the problem because the double click is instantaneous, as the error is in the mouse hardware.

Is there a way to slow down the double clicking speed. I.e make it so you have to double click at a humanly possible speed for a double click event to register. And if the double click speed is surpassed a single click is registered.

Any help would be great Thanks.

~ Dan

P.S. Definitely a hardware problem, different computers, windows with setpoint software results in the same issue.

To the best of my knowledge, those settings only look at the lower bound. ie. You can lower the speed needed to double click, but even when it's bottomed out, you can still double click as fast as you want.

I'm sure it's possible to change that ... not sure how or where to look, or if some programming would be involved. I'd have to do some research.

---

### Post by fouad_jh on 2009-07-08
> **zigga15 said:**
> Hey all,

I have a really beautiful logitech G7 mouse, I have had it for a few years.

Lately I have been experiencing a problem with the clicking. Roughly 3 times every 10 single clicks. A double click is registered. That is, If I click around every few clicks a double click occurs.

This is even more annoying than it sounds. Clicking Back buttons in a browser makes for some confusing outcomes sometimes.

Anyway, long story short I understand you can easily change the double click speed, which results in you having to click faster in order to create a double click event.

This doesn't fix the problem because the double click is instantaneous, as the error is in the mouse hardware.

Is there a way to slow down the double clicking speed. I.e make it so you have to double click at a humanly possible speed for a double click event to register. And if the double click speed is surpassed a single click is registered.

Any help would be great Thanks.

~ Dan

P.S. Definitely a hardware problem, different computers, windows with setpoint software results in the same issue.

I think it's time for a new mouse, as it is mechanical problem most probably so it might develop in the future and so on.

Good luck

---

### Post by XCan on 2009-07-08
I guess in principle it should be possible to write something that would ignore the second click if it comes within some very short time intervall. But to be honest, I too think it's time for a new mouse, that would be much easier and less time consuming.

---

### Post by fouad_jh on 2009-07-08
> **XCan said:**
> I guess in principle it should be possible to write something that would ignore the second click if it comes within some very short time intervall. But to be honest, I too think it's time for a new mouse, that would be much easier and less time consuming.

Well, how do we know it is 2 clicks only? imagine if it is 3 clicks, the system will recognize the first 2 clicks as double click, and the third will be ignored as there is nothing to do (unless by chance there is something) so if we write a code to ignore the second click, we might have to face a third click problem!!!

---

### Post by DGortze380 on 2009-07-08
> **fouad_jh said:**
> Well, how do we know it is 2 clicks only? imagine if it is 3 clicks, the system will recognize the first 2 clicks as double click, and the third will be ignored as there is nothing to do (unless by chance there is something) so if we write a code to ignore the second click, we might have to face a third click problem!!!

Not really. Ignore clicks > 2 within x milliseconds.

---

### Post by fouad_jh on 2009-07-08
> **DGortze380 said:**
> Not really. Ignore clicks > 2 within x milliseconds.

You mean Ignore clicks > 1 within x milliseconds

---

### Post by zigga15 on 2009-07-08
Thanks for all the replies guys.

I am fairly sure it is just two clicks so it is possible. Either way you could define something relating to: if(!Humanly_Possible) then single_click.

I could write something that interposes the mouse polling in linux but the common conception seems to be that it is very time consuming. (I am supposed to be working on a thesis :P)

I was mainly just wondering if there was an easy way. I would have simply opened the mouse and checked for cracked solders or burnt out components but it doesn't have any screws :P

Still under warranty but logitech tells me to go to the vendor, and the vendor tells me to go to logitech. And no one besides me in the whole situation speaks english as a first language - might avoid the frustration, bite the bullet and get a new one.

Thanks again

~ Dan

---

### Post by CatKiller on 2009-07-09
> **zigga15 said:**
> I would have simply opened the mouse and checked for cracked solders or burnt out components but it doesn't have any screws :P

I think they are usually under the pads. You need to lever them up and then stick them back down when you're finished. I'd make sure that I already had a replacement before I tried the repair :)

---

