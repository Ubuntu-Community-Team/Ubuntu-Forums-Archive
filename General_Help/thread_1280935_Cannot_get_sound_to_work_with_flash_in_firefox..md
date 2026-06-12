---
title: "Cannot get sound to work with flash in firefox."
date: 2009-10-02
forum: General Help
---

### Post by KodieG on 2009-10-02
First of all, i'm a total linux noobie. Second, I know there are tons of threads about this on here and i've read every single one with no luck. Sound works fine with everything else on ubuntu. But no sound in firefox.

Ubuntu v9.04
Firefox v3.0.14

I've even gone as far as installing Firefox v3.5.3 for Windows using Wine and installed the flash addon and still no sound. Video works fine on everything. Just no sound in firefox.

Can anybody please help me? :confused:

---

### Post by beastrace91 on 2009-10-03
Does sound work for anything in firefox or just not flash? Also which flash player did you install and how did you install it? 32bit Ubuntu or 64bit?

~Jeff

---

### Post by KodieG on 2009-10-05
im not 100% sure but i think it's firefox in general, not just flash. i browsed around to find a site where i could play a sound embedded into a page without flash and found this:

[http://www.javascripter.net/faq/sound/play.htm](http://www.javascripter.net/faq/sound/play.htm)

and couldn't get any sound to play.

i installed flash using the following method:
> $ sudo apt-get install flashplugin-nonfreeim not sure what version or anything but when i try to put the command in now i get the following:
> flashplugin-nonfree is already the newest version.

oh, and im using 32bit.

Thank you for any advice you can give me.

---

### Post by KodieG on 2009-10-13
bump?

---

### Post by easoukenka on 2009-10-13
Is your sound working ok for other applications?  

If so maybe just try another browser like opera for testing. Also try running firefox from terminal with sudo firefox to see if it is a permission problem.   

Found this post which may help
[http://www.linuxquestions.org/questions/linux-software-2/video-but-no-sound-in-firefox-453292/](http://www.linuxquestions.org/questions/linux-software-2/video-but-no-sound-in-firefox-453292/)

---

### Post by easoukenka on 2009-10-13
Is your sound working ok for other applications?  

If so maybe just try another browser like opera for testing. Also try running firefox from terminal with sudo firefox to see if it is a permission problem.   

Found this post which may help
[http://www.linuxquestions.org/questions/linux-software-2/video-but-no-sound-in-firefox-453292/](http://www.linuxquestions.org/questions/linux-software-2/video-but-no-sound-in-firefox-453292/)

---

### Post by KodieG on 2009-10-28
Sorry it took me so long to reply.

Sound is indeed working for any and all other applications.

I downloaded Opera v10.01 and got no sound out of that either.

I've formatted my hard drive and installed ubuntu and everything again still with the same exact problem.

I've even downloaded Firefox v3.5.3 for linux using ubuntuzilla found here: [http://ubuntuzilla.sourceforge.net](http://ubuntuzilla.sourceforge.net) 

and still no luck.

If its any difference, i'm using an after-market sound card instead of the on-board sound card because the on-board one quit working awhile ago when i was still using windows.

Again, any help anyone can give me would be really appreciated.
Thanks.
****

---

### Post by KodieG on 2009-11-01
**Eureka!**

Upgraded to Ubuntu v9.10 and the problem is fixed!

:D

---

