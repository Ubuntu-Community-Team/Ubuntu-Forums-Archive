---
title: "Google Earth not starting"
date: 2010-12-24
forum: General Help
---

### Post by DJYoshaBYD on 2010-12-24
i found that after i installed Google Earth on a freshly downloaded and installed copy of ubuntu 10.04 (fully updated), that google earth would not start, indicating that it could not find one of its bin files..

I discovered this online, and it fixed the problem right off the batt

```
sudo apt-get install lsb-core
```

hope this helps someone else out

---

### Post by DJYoshaBYD on 2010-12-25
just bumping this one more time before it gets buried in the forum.. haha..

---

### Post by Syed75 on 2010-12-25
> **DJYoshaBYD said:**
> i found that after i installed Google Earth on a freshly downloaded and installed copy of ubuntu 10.04 (fully updated), that google earth would not start, indicating that it could not find one of its bin files..

I discovered this online, and it fixed the problem right off the batt

```
sudo apt-get install lsb-core
```

hope this helps someone else out

THANK YOU! I had the same problem! Though this worked like a charm.

---

### Post by dcstar on 2010-12-25
> **DJYoshaBYD said:**
> just bumping this one more time before it gets buried in the forum.. haha..

Well don't.

This "issue" has been covered in multiple threads already well before you posted your solution. It is also solved by the direct .deb download now available from the Google Earth site.

Stop wasting forum space because you didn't bother to search for the existing posts on the issue.

---

### Post by Syed75 on 2010-12-25
> **dcstar said:**
> Well don't.

This "issue" has been covered in multiple threads already well before you posted your solution. It is also solved by the direct .deb download now available from the Google Earth site.

Stop wasting forum space because you didn't bother to search for the existing posts on the issue.

It has? I never knew!:eek:

---

### Post by drewster1829 on 2010-12-31
> **dcstar said:**
> Well don't.

This "issue" has been covered in multiple threads already well before you posted your solution. It is also solved by the direct .deb download now available from the Google Earth site.

Stop wasting forum space because you didn't bother to search for the existing posts on the issue.

I downloaded the deb directly off of Google Earth's site (AMD64) and installed it, and it doesn't have lsb-core as a dependency. I had the same problem with this deb.  This thread was linked to from another thread with the same problem. :p

Oh, and thank you, DJYoshaBYD.  Your thread was helpful to me. :)

---

### Post by Kalimol on 2010-12-31
Yeah, I just experienced the same problem with the most current .deb. Of course, it would be just as easy to find the solution whether or not the thread was bumped. I mean, for my part at least, I just Google search a few key words, and I assume that's the most common strategy....

---

### Post by DSimm626 on 2010-12-31
I had this issue with Google Earth too. Thank you for the resolution.

I just searched these forums and this thread showed up first :p

---

### Post by VietCanada on 2010-12-31
I appreciate it as well. I never knew Google Earth worked on Linux. Now I have it installed. I installed the recommended fix first just in case.

This forum can a terrific place to discover things I can do with Ubuntu.

---

### Post by gschoper on 2011-01-01
Post helped me as well. TY.

---

### Post by summerinmaine on 2011-01-02
Same here.  Worked perfect for this Ubuntu n00b!=D>

---

### Post by summerinmaine on 2011-01-02
> **dcstar said:**
> It is also solved by the direct .deb download now available from the Google Earth site.

Not for me running 10.04.  Just did the download 15 minutes ago, and it required the fix.

---

### Post by 2541 on 2011-01-03
Very helpful! Thank you, DJYoshaBYD.

---

### Post by wightghost on 2011-01-03
This worked for me too. Thank you!

---

### Post by ian.xerl on 2011-01-07
> **dcstar said:**
> Well don't.

This "issue" has been covered in multiple threads already well before you posted your solution. It is also solved by the direct .deb download now available from the Google Earth site.

I use Kubuntu 10.10 and I installed the .deb package from google's website, but anyhow Google Earth would just not start up.

DJYoshaBYD's solution solved the problem. THANKS a lot !!

---

### Post by llanitedave on 2011-01-07
I'll add my voice.  I did the 64 bit .deb download, and got no response after installation.  I searched and found this thread, and now it works fine!

So consider this a bump -- but it's not really necessary if all anyone does is search "google earth" on the Ubuntu Forums.  It'll be found.

---

### Post by jahLux on 2011-01-08
> **DJYoshaBYD said:**
> i found that after i installed Google Earth on a freshly downloaded and installed copy of ubuntu 10.04 (fully updated), that google earth would not start, indicating that it could not find one of its bin files..

I discovered this online, and it fixed the problem right off the batt

```
sudo apt-get install lsb-core
```

hope this helps someone else out

Thanks a million - Just saved me a a whole bunch of time and frustration . . . .Works as advertised !!

---

### Post by RogerDavis on 2011-01-08
Mine starts and works ok, but the icon is now a white page.  

Any ideas?

---

### Post by Qazulight on 2011-01-08
After trying everything else. Twice.

This code worked. Don't do away with it yet.

sudo apt-get install lsb-core

Now if my search for a way to get my plantroincs usb headset to work is a productive.....

Cheers
Qazulight

---

### Post by hte333 on 2011-01-12
I had this same issue. Thanks a lot!!

---

### Post by ToniMe on 2011-02-10
This helped me, too. Thanks  a lot.

---

### Post by okkie on 2011-02-13
as usual I will have a same but different problem,lsb-core will not install.
See attached photo of error.

---

### Post by smgendler on 2011-02-13
DJYoshaBYD, thank you for "wasting" forum space.  This fix worked for me, too.  Can you tell me why this fix works?  I'm still new to linux, and the thought process may be helpful in the future.  I did search and this thread is the first that popped up with a bunch of replies, so I've learned that much about getting solutions, but I'm looking for an explanation that's a touch technical.  I also wonder why the package from Google works for some and not others?

---

### Post by wstrong714 on 2011-02-15
> **DJYoshaBYD said:**
> i found that after i installed Google Earth on a freshly downloaded and installed copy of ubuntu 10.04 (fully updated), that google earth would not start, indicating that it could not find one of its bin files..

I discovered this online, and it fixed the problem right off the batt

```
sudo apt-get install lsb-core
```hope this helps someone else out

This fix worked for me, Thank you very much!!

---

### Post by okkie on 2011-02-16
I once again attach a screenshot of the error trying to install lib-core.Please look at it.

---

### Post by okkie on 2011-02-16
I meen lsb-core

---

### Post by junaid_572 on 2012-02-20
sudo apt-get install lsb-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lsb-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

And my google earth (latest from website is not starting) :( :'( tell me what to do

---

### Post by scooper77515 on 2012-02-20
Junaid, same problem here. Newest version of Google Earth won't load for me, either. It appears to install correctly, but when I hit the launch button, nothing. No hard drive light, no suggestion that it is even trying to load anything at all.

---

