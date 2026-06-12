---
title: "Constant hard drive activity - Clean install"
date: 2012-03-30
forum: General Help
---

### Post by MockY on 2012-03-30
I just installed 11.10 Server 64-bit. The only thing I have done is to install SSH and LAMP (which I selected during the Tasksel configuration during th OS install) and applied all available updates.

The activity LED for the hard drives is constantly blinking. iotop does not report anything suspicious, and neither does top. This system in a dual Opteronx2 setup with 12 GB of RAM, and the hard drive is a WD RE4 2TB, so the hardware itself should not be an issu.

What on earth could be causing the HD activity LED to constantly blink?

---

### Post by MockY on 2012-03-30
I did some more testing and installed previous versions of Ubuntu and onlyu installed LAMP and SSH.

With 11.04, I get the same odd hard drive activity. It is constant. Blinking with just less than a second in between.

I then installed 10.04, and the hard drive activities are now normal.

So that leads me to beleive that something in versions after 10.04 causes these hard drives to constantly have activity. As 10.04 is about to "die" next month, this is not really a viable solution.

Any ideas before I have to go to Debian (rather not do that)

---

### Post by winh8r on 2012-03-30
Support for 10.04.4LTS will continue until April 2013 for desktop and until April 2015 for server edition.

Not sure what causes the extra activity on the server edition on the 11.xx releases but I noticed an increase in HDD activity on the desktop releases too. 

I will worry about all that next year though, happy with 10.04 for now and Lubuntu 12.04 as an alternative.

---

### Post by MockY on 2012-03-30
For some reason, I thought the support ended this year. I must have mixed it up with 10.10 Desktop.

Well, I guess 3 more years is long enough for me to go with 10.04.4. I'm now just very curious why it would be impossible to go with later releases. Maybe not impossible, but who know what else is not working properly. Besides, the hard drives will most likely die earlier with such behavior.

---

### Post by MockY on 2012-04-26
I just installed 12.04 64-bit, and I see the exact same behavior. What the heck is going on? Will this never be fixed? If not, then I unfortunately  have to go Debian as my server OS in the future.

---

