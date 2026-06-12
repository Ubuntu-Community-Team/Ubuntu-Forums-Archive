---
title: "Hibernate doesn't work"
date: 2006-05-28
forum: General Help
---

### Post by ahaslam on 2006-05-28
Hi,

I have done an on-line upgrade from Breezy to Dapper.
The hibernate option on the log out screen used to work quite well and very reliably.
Now that I'm using Dapper it doesn't work at all. It shuts down but upon reboot I'm greeted with a pin-striped screen and a locked system. I am am on a laptop and often rely upon this to work properly, can anyone help?

Many thanks,
Tony.

---

### Post by l.tambiah on 2006-05-28
[quote=Anthony Haslam]Hi,

I have done an on-line upgrade from Breezy to Dapper.
The hibernate option on the log out screen used to work quite well and very reliably.
Now that I'm using Dapper it doesn't work at all. It shuts down but upon reboot I'm greeted with a pin-striped screen and a locked system. I am am on a laptop and often rely upon this to work properly, can anyone help?

Many thanks,
Tony.[/quote] 
I have the same issue, on my IBM Thinkpad R50e, Hibernate did work in Breezy. It would be nice to get the Hibernate to work, not so fussed about suspend though.

I think the patch will get addressed, we just have to  be patient, I have added to the bug report with other Hibernate issues people are having. If no patch is provided then I'm sure there will be hacks to make it work. Besides just because we are having issues doesn't mean everyone is having problems. 

I'm going to start looking into this issue more deeply myself tommorrow to try and make sense as to why it is failing.

If you really need Hibernate to work at this current time just revert back to Breezy, Breezy still has 12 Months of life left and really is still a great Distro.

I'll miss Breezy.....

---

### Post by stojan on 2006-05-28
[QUOTE=Anthony Haslam]Hi,

I have done an on-line upgrade from Breezy to Dapper.
The hibernate option on the log out screen used to work quite well and very reliably.
Now that I'm using Dapper it doesn't work at all. It shuts down but upon reboot I'm greeted with a pin-striped screen and a locked system. I am am on a laptop and often rely upon this to work properly, can anyone help?

Many thanks,
Tony.[/QUOTE]

Yeaah, I've the same problem on my HP Omnibook 6000...
It looks on global problem :)
When I try to hibernate my system, It goes down, but when I try to wake it up, it will not turn up backlight on display, so I can't see anything :-D

It'll be nice to use this feature...

---

### Post by dsquared on 2006-06-04
I have this same problem too, but on my desktop -- MSI KM3M-V motherboard with a Sempron processor. I'm using Dapper.

This is quite frustrating. Hibernate worked flawlessly in Breezy.

---

### Post by l.tambiah on 2006-06-04
[quote=dsquared]I have this same problem too, but on my desktop -- MSI KM3M-V motherboard with a Sempron processor. I'm using Dapper.

This is quite frustrating. Hibernate worked flawlessly in Breezy.[/quote]

It is nice to have a everything work, I agree, but it is only a minor bug, and on a Desktop there is little need for the function anyway. As software is updated things change and unfortunateley what worked for you and me before has became broken. However it does work fine on other hardware, I can confirm that the hibernate works on my desktop, and works fine on many others. 

Dapper is not even a week old yet so give it time and someone out there will have a fix, a great thing is that we can fix things if issues are occur. This is the case with my laptop my "suspend" didnt work so after a bit of research I found a hack to make it work. It now works flawsly.

May I suggest you may want to go to launchpad and have a look around for bugs simular to that of yours, you may consider adding a bug report specific to your hardware.

On all Dapper is fantastic, im very impressed and the Ubuntu team have done a great job.

---

