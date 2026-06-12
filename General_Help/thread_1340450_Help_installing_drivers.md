---
title: "Help installing drivers"
date: 2009-11-28
forum: General Help
---

### Post by Iron Calves on 2009-11-28
I have an ati radeon x1650pro and for some reason I can't get Ubuntu to install it. I've tried using terminal and apt-get install. Nothing I can find works. I downloaded the .run file from ATI and I can't figure out how to use it... any help?

---

### Post by coffee on 2009-11-28
Have you tried the built in app under 
System -
         Administration -
                          Hardware Drivers
This has worked for me (I am running on NVIDIA though).

You could also check out Envy-ng @ [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html"), I have not used this for 9.10 but it always worked for me in the past and it is stated to install ATI drivers.

I would suggest moving to NVIDIA graphics, there is much better support for them on Linux.

coffee

---

### Post by Iron Calves on 2009-11-28
Yes, I've tried both of those and neither of them worked. I checked ATIs website and it said this card was supported. Thanks though. Maybe i'll just try to find a cheap Nvidia since cyber monday is coming up.

---

### Post by kellemes on 2009-11-28
The ATI driver from AMD (fglrx) will not work for your card!
You'll need the opensource driver, and in my experience it works just fine with the x1650pro.

And as far as I know they are installed by default..

---

### Post by Iron Calves on 2009-11-28
I believe it was an open source that I downloaded from ATI... EnyNG is saying 

ATI- 8.660-Oubuntu4 Not Compatible- Not Recommended 

When I run Hardware Drivers from system it tells me 

" No proprietary drivers are in use on this system"

None are listed to install either. 

Any ideas? Thanks for the help.

---

### Post by Iron Calves on 2009-11-28
These help at all?

---

### Post by Iron Calves on 2009-11-28
:confused::confused::confused: 
Anyone?

---

### Post by Iron Calves on 2009-11-28
bump

---

### Post by kellemes on 2009-11-29
> **Iron Calves said:**
> I believe it was an open source that I downloaded from ATI... EnyNG is saying 

ATI- 8.660-Oubuntu4 Not Compatible- Not Recommended 

When I run Hardware Drivers from system it tells me 

" No proprietary drivers are in use on this system"

None are listed to install either. 

Any ideas? Thanks for the help.

The open source driver is not coming from AMD.
The proprietary driver (as you can download from AMD) will not work with your card!
Envy will not install the opensource driver and so should not be used on your system!

Like I said.. the open source driver should be installed by default.
What's not working with your card?

Currently I'm not using Ubuntu so can't guide you into troubleshooting but maybe the following link helps..
[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

I have used this exact same card for years using the open source driver with fine performance..

---

### Post by GnubbyaBush on 2009-11-29
Well i guess theres a couple ways of going about this. You could google it, search the ati site for linux pacakges debian files ect. I would take the softpedia route. Sign up for softpedia (its free) and then you can use their linux section. then search for the specific linux drivers there, sometimes they have drivers.

---

### Post by Iron Calves on 2009-11-29
> **kellemes said:**
> The open source driver is not coming from AMD.
The proprietary driver (as you can download from AMD) will not work with your card!
Envy will not install the opensource driver and so should not be used on your system!

Like I said.. the open source driver should be installed by default.
What's not working with your card?

Currently I'm not using Ubuntu so can't guide you into troubleshooting but maybe the following link helps..
[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

I have used this exact same card for years using the open source driver with fine performance..

I can not enable visual effects and the screen flickers at times. I had Ubuntu... I think it was 9.04 on this computer before but uninstalled it and the card worked fine then... So i'm pretty confused on that. Thanks for the help though.

---

### Post by Iron Calves on 2009-11-29
Ok, I have the driver from softpedia but I honestly have no idea how to install this... I've really only been using linux for about a week. Any advice on how to do this?

---

