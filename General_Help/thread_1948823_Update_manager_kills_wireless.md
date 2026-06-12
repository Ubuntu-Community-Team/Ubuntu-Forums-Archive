---
title: "Update manager kills wireless?"
date: 2012-03-28
forum: General Help
---

### Post by Spewed on 2012-03-28
I ran an update through update manager. Just a standard run of the mill update, and of course as always with Linux nothing can just go smoothly, NOTHING. I restart the machine, and now suddenly my Wireless network adapter no longer works? This is absolutely senseless, makes no sense to me. It was an ENORMOUS pain in my *** to even get the wireless network card working in the first place, now I run a simple update and it no longer works? What gives, Ubuntu? Seriously.. What gives? 

Now, all the fixes I'm trying for it are to no avail. I tried running through the same procedure that I used with Ndiswrapper to get it working in the first place, and of course modprobe hangs and does absolutely nothing.

---

### Post by Spewed on 2012-03-29
I see what the problem is. It downgraded my version of Ndiswrapper from version 1.57 back to version 1.56. Why the hell would that happen? 

Last time I tried to even upgrade to 1.57 from 1.56 it wasn't even possible. I tried removing Ndiswrapper completely and reinstalling it and that didn't work. The only thing that worked was a fresh install of Ubuntu. 

Why? How can I successfully COMPLETELY remove Ndiswrapper from my system and install 1.57??

---

### Post by Spewed on 2012-03-29
Okay, I installed Ndiswrapper 1.57 without a hitch this time. Now.. When I try "modprobe ndiswrapper" it hangs.. Like always. How can I get around this?

---

