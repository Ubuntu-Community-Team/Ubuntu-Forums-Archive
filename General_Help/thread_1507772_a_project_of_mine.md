---
title: "a project of mine"
date: 2010-06-12
forum: General Help
---

### Post by kmaster228 on 2010-06-12
hello, i have been wanting to do this project for a while now, i want to hook an ubuntu powered computer to some wheels and a webcam, and make a sort of a remote controlled super car, i was hoping to control it remotely using like ssh or something, i know this is far fetched but let me start of simply, it there and way to get ubuntu to recognize motors or senors and use them?

---

### Post by Yarui on 2010-06-12
Practicality aside, this would require knowledge on several different things.  You would need some experience not only in programming but also circuitry and probably a little bit on mechanical engineering.  This almost definitely falls in the realm of robotics. If you are looking to make your computer give information to a circuit you should probably do some research on USB technology.  Serial ports would probably work too.  I don't have the slightest idea which of the two would be easier, though.

It would probably be much more practical to make some sort of remote controlled device that does not contain an entire PC, but instead uses microchips and circuits designed to do specifically what you want the device to do.  If you want it to send some information to your PC, there are countless ways to achieve that.

If you really want to do something like this, you should probably start by learning as much as you can about circuitry.  If you are a beginner you will probably want to start by buying a bread board and some components and designing some simple circuits.  Start out by making a circuit that lights an LED, after that figure out how to make the LED blink, then try adding a switch that will turn the led on and off.  Just keep trying to make new things and you can work your way towards more complex projects.  You can buy kits that come with components and a project booklet.  For $50 you can get one from thinkgeek that comes with 130 parts.  It looks like a worthwhile purchase.

[http://www.thinkgeek.com/gadgets/electronic/b80b/](http://www.thinkgeek.com/gadgets/electronic/b80b/)

---

### Post by kmaster228 on 2010-06-12
i know it wud be hard, but i was thinking sumthing like the lego control systems, i doubt it wud be like that in ubuntu, but the main thing is how to get ubuntu to reconize and use motors and senors

---

### Post by shiri_prgmr on 2010-06-12
There are many ways to accomplish what you mentioned. At it's simplest a serial port can be made to control motors. However, since you want to control multiple motors, it would be advisable to run ubuntu embedded on a custom board. This would allow it to handle multiple I/O ports. Servos would need to be controlled using PWM or some such technique.

You can do ssh via bluetooth/wifi. But, ssh would be the least of your issues.

If your are still in school, would suggest you start off with assembling kits first for experience. You know: small scale prototypes.

---

### Post by kmaster228 on 2010-06-12
ok yea i know ssh wud be the least of my worries lol :P ok yes i am still in school and advice on which assembling kits i can start with and tutorials on how to use them?

---

### Post by Yarui on 2010-06-12
I just updated my previous post.  It has a link to a starter kit for circuitry, which is what I would recommend if you want to really understand what you are doing.  You can get project kits that are just a board and a schematic, but you would probably learn more from something that allows you to be creative.

---

### Post by shiri_prgmr on 2010-06-12
See what Google says. IIT Mumbai or someone associated with them used to give courses for hobbyist and/or kids. Check if they can help.

---

### Post by chayzer on 2010-06-12
Oddly enough I considered something like this to mess with my dogs. Have you checked out arduino for a cheap i/o interface through usb?

---

### Post by shiri_prgmr on 2010-06-12
OK. Here is the link: [http://www.thinklabs.in/]("http://www.thinklabs.in/")

For general info, google: robotics for beginners

---

