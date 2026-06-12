---
title: "Screen session problem"
date: 2012-07-13
forum: General Help
---

### Post by serhancan on 2012-07-13
Hello,

I connect to my beagleboard by using screen from my Ubuntu PC:

screen /dev/ttyUSB1 115200

and when I connect to my beagleboard I open the dev/ttyO1 by screen in the same terminal display. Now, I want to close only the last screen connection. But I cannot. When I close the screen session with ctrl+a d, it does not only close the last screen connection to ttyO1, it also closes the connection to the ttyUSB1,beagleboard. (There is only one window. Therefore I cannot use anything like ctrl+a w.) 

I want to be able to close the last screen session and go back to root@beagleboard rather than root@Ubuntu

What can I do?

ps: I tried to connect to beaglebone with picocom and then connect to ttyO1 with screen. But nothing changed.

---

### Post by Cheesehead on 2012-07-13
I don't think you can do this in screen.

If I recall correctly, it's not designed to run nested sessions. It will run nested sessions (that's what you are doing), but only the top-level session is detachable or multiplexable.

That's also why screen gives you no indication of which level in a nested structure it is currently in.

---

### Post by serhancan on 2012-07-15
> **Cheesehead said:**
> I don't think you can do this in screen.

If I recall correctly, it's not designed to run nested sessions. It will run nested sessions (that's what you are doing), but only the top-level session is detachable or multiplexable.

That's also why screen gives you no indication of which level in a nested structure it is currently in.

So what should I use rather than screen? Any suggestions?

---

