---
title: "Laptop KEEPS crashing and showing this weird error message.."
date: 2011-08-08
forum: General Help
---

### Post by _Cathy_ on 2011-08-08
Hi there, 

I am having big problems with my laptop. I use a wubi install of Ubuntu 11.04 atm. 
This happens like 2/3 times a day, basically I will just be doing something normal on the laptop, then suddenly the screen goes black  with white writting - none of which makes sense to me 

This is one of the screens that appears: 
[IMG]http://img685.imageshack.us/img685/5509/dscf3026e.jpg[/IMG]

It stays like that for ages, then I have to restart. Im getting really worried that this is something serious! 

Any advice?? Please!

---

### Post by Rubi1200 on 2011-08-08
The error messages indicate a kernel panic.
[http://en.wikipedia.org/wiki/Kernel_panic#Causes](http://en.wikipedia.org/wiki/Kernel_panic#Causes)

There could be a number of causes of this and tracking it down may not be so easy.

However, to start with here is what you can try working through:

1. post the specifications for the computer, especially RAM and graphics card

2. when did the problem start; after an update, installing a new program or from the beginning?

3. go to System Settings > Log File Viewer and under dmesg and syslog see if there are log entries related to the time/activity that may help us figure this out (post the messages here please).

Thanks.

---

### Post by _Cathy_ on 2011-08-11
> **Rubi1200 said:**
> The error messages indicate a kernel panic.
[http://en.wikipedia.org/wiki/Kernel_panic#Causes](http://en.wikipedia.org/wiki/Kernel_panic#Causes)

There could be a number of causes of this and tracking it down may not be so easy.

However, to start with here is what you can try working through:

1. post the specifications for the computer, especially RAM and graphics card

2. when did the problem start; after an update, installing a new program or from the beginning?

3. go to System Settings > Log File Viewer and under dmesg and syslog see if there are log entries related to the time/activity that may help us figure this out (post the messages here please).

Thanks.

Thanks for the reply 

Here is what you asked for: 

1) Specs: RAM - 3072mb
          Graphics Gard - not sure how to find this? 

2) I THINK it the first time it happened was when I was installing some webcam program from the software centre, I think is was Kamoso. Thats the first time i can remember it happening

3) another problem - none of the entries under dmesg have dates on them. Also, under  syslog, it only has entries for the past few days, and this started about 3/4 weeks ago :/


*edit - This has happened a more since posting - i have a couple more pics of the messages that appear (like in the OP) if they are useful i can upload those too.

---

