---
title: "computer wont load please help"
date: 2011-03-10
forum: General Help
---

### Post by SE7EN-LOCSTA on 2011-03-10
ive done it now somehow. everything has been working a-ok until today. upon starting my computer, ubuntu 10.10 goes to a cursor '|' and does nothing. it wont let me type, no mouse, nothing, just a black screen with a little cursor in the top left hand. 

i disabled my 2nd hardrive and esata external, tried to load an older kernel, same result. i also tried to boot into windows 7, and it does the little starting windows and winsymbol, but never loads. 

my cd drive is unusable, so i use usb to install (but the image is on my secondary harddrive, so i cant access it to try a windows fix, and for ubuntu as well) i am on my girlfriends computer now, where i cant use my hd (hers is ide, mine is sata) and it would take weeks to download a new image. 

i have noticed no memorable events as far as things not working until today. the only thing i can think of that is different is not shutting down properly. i had loaded up xubuntu-- i was showing it to someone else, i normally use gnome-ubuntu---, and logout only removed panel, left cairodock running and never logged out. being froze like that, i had to manually power down. 

i do understand that this can damage information on the hard drive, but grub works fine, and windows 7 starts to load, it shows loading windows and the little symbol shows animation or whatever 'glowing effect' its supposed to. also, my windows partition was not mounted at all when i powered down, so i assume that the data on there shouldnt be affected? my computer is less than a year old, and my primary harddrive is maybe a few weeks old, so i dont think thats the issue either.

any ideas?

---

### Post by SE7EN-LOCSTA on 2011-03-10
quick update.. after it starting to go to the pre-login screen, light blue 'kubuntu 10.10' (i dont know why it does that when ububuntu standard is my default) it crashed the computer, but upon a restart, it loaded (taking much longer than normal). i would like to leave this thread open however, see if anyone knows as to the cause of my problem, or if i might have some other problems that, while it is starting fine now, may be something deeper that i need to fix before it does something irreversible.

---

### Post by coffee412 on 2011-03-10
> **SE7EN-LOCSTA said:**
> quick update.. after it starting to go to the pre-login screen, light blue 'kubuntu 10.10' (i dont know why it does that when ububuntu standard is my default) it crashed the computer, but upon a restart, it loaded (taking much longer than normal). i would like to leave this thread open however, see if anyone knows as to the cause of my problem, or if i might have some other problems that, while it is starting fine now, may be something deeper that i need to fix before it does something irreversible.

First off Sorry your having a problem. They can be very frustrating.

Tell me, After you boot to a cursor can you hit your <alt> 2 keys and get a login? If you can I would look at a possible video problem. But you can also get to the logs which are going to tell you what happened. Specificaly /var/log/messages file. 

coffee

---

### Post by garvinrick4 on 2011-03-10
You have a lot of newer hardware there, why optical not working? Did you build yourself?
I would look into drivers first.

---

### Post by SE7EN-LOCSTA on 2011-03-10
@coffee. when the problem was occuring, it was not registering keypresses, i dont know if there is certain ones that go thru when others dont, but i tried alt + all the f buttons, and some other random stuff i pushed. 

i have went through the log files, and it might as well be written in mandarin for as much sense as i could make of the non-basic stuff. it is quite large though for the time in question. if i need to show that, is there a special way i can do so, or just put a big text-wall on these forums?

i had also neglected to mention before, that before disabling the 2nd harddrive it was registering in bios as some gibberish, like z**********z*******z or something. after disabling it, it returned to normal after a few restarts, and seems to be functioning normally now that i am able to login.

@garvinrick. perhaps 'unusable' was the wrong choice of wording to use for my optical drive. the cd drive itself is perfectly fine as far as i know. i am 1 sata cord short for it, after buying a new harddrive recently. i also have an electrical wiring issue in my residence, where i am not getting enough power to my computer. i decided to leave that, and some in-tower lighting unplugged to try to get the most amount of power to the other components. 

i dont believe the new parts and whatnot would be the issue, as it has been running solid for several weeks since the last hardware change. 

thanks guys, and let me know if my var/logs are needed and the proper way to post them. :)

---

