---
title: "Firefox freezes"
date: 2010-12-02
forum: General Help
---

### Post by rapattack1 on 2010-12-02
Hi the last couple of weeks i think every now and then firefox(3.6.12) freezes. Nothing in particular is happening. I am not using too many pages or doing anything like scanning or anything that would slow down the system. The freezes range from 0-3 per session roughly. I usually close firefox and just start up again. Any reason for this as it is getting annoying ? :0)

---

### Post by scooby359 on 2010-12-11
Can I piggy back this thread as I'm having the same problem. Past couple of weeks my Firefox has kept having trouble either freezing for no apparent reason while I'm surfing, and at the moment, I can't even load it up - soon as the firefox window appears, it greys out and freezes.

Not sure what to check to fix this, any ideas?

---

### Post by sikander3786 on 2010-12-11
It might be some extension/add-on causing the problems.

Kill any running instance of firefox.

Applications > Accessories > Terminal:
```
ps axjf | grep firefox
```

And start in safe mode.

```
firefox -safe-mode
```

Is it usable now?

---

### Post by rapattack1 on 2010-12-11
The thing is though that all the browsers are doing the same thing. Opera and Google Chrome. Do i do that command while the browser is open or not? Sorry not very good with commands yet. Basic ones and thats all :0)

scooby359-yep my browser is not doing the same thing but who knows whatever i try might work for you. Did you try the fix?

---

### Post by sikander3786 on 2010-12-12
> **rapattack1 said:**
> The thing is though that all the browsers are doing the same thing. Opera and Google Chrome. Do i do that command while the browser is open or not? Sorry not very good with commands yet. Basic ones and thats all :0)

scooby359-yep my browser is not doing the same thing but who knows whatever i try might work for you. Did you try the fix?
I all the browsers are encountering the problem, it might be a bad plugin, flash or java.

In your Firefox browser's address bar, type

```
about:plugins
```

And see which java and flash plugins are there. You can try removing and re-installing them. Or if it is flash, you can try flash-aid.

[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/) 

And the commands in the above post need to be done while firefox is not running. Try it in safe mode as mentioned above.

---

### Post by rapattack1 on 2010-12-12
Yep i think i mentioned somewhere that flash was in this. I don't remember now because i have posted on a few forums and this is the first time someone answered me :0)

OK i see that there are lots of versions of java installed after i put that whatever in the address bar, OK am using flash-aid. Will report back when it has done it's work;)

---

### Post by rapattack1 on 2010-12-12
:p:D:P
Oh i think that did it. Had over 24 hours and nooooooo freezes....very happy! Thanks sikander3786....your a gem :0)

---

### Post by rapattack1 on 2010-12-13
Damnit it started again.

---

### Post by rapattack1 on 2010-12-15
Well got sick of many problems not being resolved so went up to Ubuntu 10. I had used it on another machine recently and things worked better so here i am. The first boot was fine of the new install but the 2nd one was terrible with firefox freezing heaps so i opened the box and stuck a fan at it then rebooted. Now everything seems good. What could this be. I know the weather is hot but i have seen this machine work through hotter than this ???

And skype was still running ok like in Ubuntu 9 so this is odd

---

### Post by sikander3786 on 2010-12-15
So you think it is an heating issue? At least it sounds like that.

You can check if the heatsink on processor didn't run loose. Or even if the fans are spinning or not. Or it might be a chip on the motherboard that is heating.

Keep on testing it in a cooler environment and see if you still get problems or not. You might also be able to check the current temperatures under Bios menu when you feel it is causing some problems.

---

### Post by rapattack1 on 2010-12-15
Yep it is definately heat. I woke up today and booted up....same problem. Shut things down and put the room fan on and now it works. I can see the fan on the cpu working and the two case fans. Can't see the one in the psu while it is on because where the case is positioned. Will look further later as there seems to be a thunder storm brewing. I recently replaced the board and it was only the second or third time i ever put a cpu in a socket and all that. I followed a detail youtube video on how to spread the paste on properly.
Will check the bios later....thanks :0)

---

### Post by rapattack1 on 2011-04-30
Had to get rid of this machine. Maybe faulty motherboard

---

