---
title: "monitor shuts down from PC"
date: 2011-09-02
forum: General Help
---

### Post by teodosio on 2011-09-02
Hello  everyone!
 I have  installed, from a year  ago, Ubuntu 10.04 in a AMD PC. Never had any kind of trouble but, since a  couple of months, when  the computer is on and workinging well for about 20 minutes or less, the monitor seems to shut  down from the rest of the system. It goes black, and the monitor  switching button begins to blink as if  the computer had been turned  off. No shutdown  commands from the keyboard work and to shut the  computer I  have to take off the cable from power. Someone  give me a hint on how to solve this? Thanks in advance to everyone.

---

### Post by Topsiho on 2011-09-02
Probably a setting.

I translate from Dutch so the menu names might be somewhat different, but must still be clear to you (I hope :) ) :

Go to System>Preferences>Screensaver>Energy Management

In the tabs you'll find a setting for setting the screen to black after a number of minutes.

Topsiho

---

### Post by teodosio on 2011-09-02
Thanks, Top, I have already done it, turned everything to 'never' but the problem continues. Thanks anyway.      > **Topsiho said:**
> Probably a setting.

I translate from Dutch so the menu names might be somewhat different, but must still be clear to you (I hope :) ) :

Go to System>Preferences>Screensaver>Energy Management

In the tabs you'll find a setting for setting the screen to black after a number of minutes.

Topsiho

---

### Post by Topsiho on 2011-09-02
OK (or not OK :) ).

Then you'll have to think what change did you make to the system, just before the problem manifested itself.

As this was some months ago, that's difficult.

Other thing I think of is hardware. I don't know where you live, but in the Northern hemisphere some months ago the summer began (not in Holland though :( ). It might be a heat problem: is your computer getting too hot?

Also it never hurts to test your memory (not to think of the change you might have made to your system some months ago, but of your computer). Using the LiveCD, letting it run for several passes. If errors are found, you probably have found the culprit. Though a memory defect stops the system usually, not the monitor.

You could also try another monitor.

Enough ideas to keep you busy for a while :)

Have fun :confused:

Topsiho

---

### Post by teodosio on 2011-09-02
Thanks again, dear Topsiho, for your efforts in trying to find out a solution for this. The memory test you asked me to do has resulted in the fact that... I never did any special change in the computer in last months. I installed 10.04 last year and since then I just have been using it with a lot of pleasure and no problems. Now, as for the other ideas you've suggested to me you're much probably right. As a matter of fact, I had even remember of them, but I thought they were too simple to be the cause of the problem. I am talking about the heat. Yes, I live in the northern hemisphere, a bit far south from Holland. I live in Portugal, in the deep Portugal not far from the spannish border. Hot weather begins in June and during this period till now we easily get 37ºC or 38ºC. Moreover, the room where the computer is turned to West and it gets really hot \\:D/specially in the afternoon. We are having fresh days in September, but the wall's houses are still warm... so perhaps the trouble comes from there. I intend to open the CPU box this weekend, clean it from any dust and keep the CPU box openned and then watch what happens. I'll post you the results of cross!:P
Thanks againg for your interest and nice words of encouragement and have a great weekend.

J. Teodósio.


> **Topsiho said:**
> OK (or not OK :) ).

Then you'll have to think what change did you make to the system, just before the problem manifested itself.

As this was some months ago, that's difficult.

Other thing I think of is hardware. I don't know where you live, but in the Northern hemisphere some months ago the summer began (not in Holland though :( ). It might be a heat problem: is your computer getting too hot?

Also it never hurts to test your memory (not to think of the change you might have made to your system some months ago, but of your computer). Using the LiveCD, letting it run for several passes. If errors are found, you probably have found the culprit. Though a memory defect stops the system usually, not the monitor.

You could also try another monitor.

Enough ideas to keep you busy for a while :)

Have fun :confused:

Topsiho

---

### Post by Topsiho on 2011-09-03
OK. I am glad it's not that warm over here though. Over 30 degrees centigrade ... But this might indeed be the cause of the problem. Opening th box and putting a ventilator so it can blow onto the mother board and processor may help.

If Ubuntu has worked well and nothing was changed to it, then it most probably is the hardware.

You could also check whether your hard disk is still OK, using the Disk Utility in System>Management (or something like that).

You could also try using lm-sensors and hddtemp to check the temperatures, of among others the processor, and the hard disk.

Topsiho

---

### Post by teodosio on 2011-09-04
Dear Topsiho:
I was looking for the signed "[SOLVED]" to put in this message subject, but I couldn't find it. Yesterday I've openned the PC box, removed any dust and left it completely opened. Yet, I used it for about 1h30 and the monitor didn't shut down, today it has been connected for about 2 hours (I'm writting this message on it) and everything got back to normal. So I guess you were right and it was the heating that was affecting it. Thanks again! :P
The disk utility says everything is OK, the Imsensirs says: 
"[COLOR=Navy][I]acpitz-virtual-0
Adapter: Virtual device
temp1:       +29.0°C  (crit = +100.0°C)[/I][/COLOR]"
and the Hddtemp says:
[COLOR=Black]"[/COLOR][COLOR=Navy]/dev/sda: WDC WD3200AAKS-00V1A0: 38°C[/COLOR][COLOR=Black]"[/COLOR]
So, I guess I can rest for now from this trouble.
Please have a nice day and believe me I really appreciated you help and will never forget it. THANKS.
J. Teodosio.



> **Topsiho said:**
> OK. I am glad it's not that warm over here though. Over 30 degrees centigrade ... But this might indeed be the cause of the problem. Opening th box and putting a ventilator so it can blow onto the mother board and processor may help.

If Ubuntu has worked well and nothing was changed to it, then it most probably is the hardware.

You could also check whether your hard disk is still OK, using the Disk Utility in System>Management (or something like that).

You could also try using lm-sensors and hddtemp to check the temperatures, of among others the processor, and the hard disk.

Topsiho

---

### Post by Topsiho on 2011-09-04
Great!!

I am really happy that I could have helped someone. You happy - me happy :)

In order to mark this thread as solved, you should have a look at Thread Tools in the upper part of this Forum page. As the original poster I guess you'll find a menu item with which you can mark this thread as solved.

Glad to have been able to help you,

Topsiho

---

### Post by teodosio on 2011-09-04
Eh eh eh right: me happy - you happy. :P 
I've marked the thread as solved.
Hugs from southern Europe.

> **Topsiho said:**
> Great!!

I am really happy that I could have helped someone. You happy - me happy :)

In order to mark this thread as solved, you should have a look at Thread Tools in the upper part of this Forum page. As the original poster I guess you'll find a menu item with which you can mark this thread as solved.

Glad to have been able to help you,

Topsiho

---

