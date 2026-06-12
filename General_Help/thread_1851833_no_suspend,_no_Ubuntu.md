---
title: "no suspend, no Ubuntu"
date: 2011-09-29
forum: General Help
---

### Post by redFlameStar on 2011-09-29
Hey Guys,
I'd love to switch to ubuntu, hopefully 11.10, but the problem is suspend doesn't work(both 11.04+.10). laptop screen goes blank but the lights still on and fan keeps spinning, plus it doesn't wake up. so please any help would be great!!!!
thanks
PS: I'm a little more than a noob with ubuntu, so if you need info please spell out how to get it.

---

### Post by An Sanct on 2011-09-29
Welcome to the forums!

Well, for suspend to work, you have to have a swap partition double the size of your ram (the default installation option) and it has to be in one piece.

Also your hardware has to be supported (this should be no problem ...)

To check for RAM and swap size, type the command '*free*' in terminal, you can also copy&paste it here, if you need more assistance.

---

### Post by Toz on 2011-09-29
What is the make/model of your computer?

Also, the log file **/var/log/pm-suspend.log** may help identify the problem.

---

### Post by hypertyper on 2011-09-29
This worked for me:
[http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)

My system shutdown half way and came right back up before I ran the script so it was slightly different.

---

### Post by redFlameStar on 2011-10-01
right now i run ubuntu from usb, my computer model is ASUS U50F. everything else works with ubuntu even keyboard function keys. I;ll try running ubuntu in persistent mode to get log file and post a bit later.

---

### Post by Toz on 2011-10-01
Give the suggestion from post #4 a try. There is a report in the comments section of that link that it works for a similar system.

---

### Post by Rasa1111 on 2011-10-01
Running both 11.04, and 11.10

and Suspend works exactly as it should here.
I use suspend more than anything else..
and havent had a problem with it yet. 

hmm

wait,
So you are only running it from a USB?

aka, LiveCD/Live mode?

Some things just dont work properly if the system is not actually installed onto your computer.
That may be the problem.
maybe?

---

### Post by redFlameStar on 2011-10-01
took a little bit to get suspend log but here it is.

---

