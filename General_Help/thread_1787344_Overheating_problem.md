---
title: "Overheating problem"
date: 2011-06-21
forum: General Help
---

### Post by Mr Nemo on 2011-06-21
I bought a new Hp Pavillion DV6T. For the most part, everything worked right out of the box with ubuntu, but the computer seems to be heating up really quickly for no reason whatsoever even if i'm not doing anything intensive. Does anyone have any ideas as to why this is happening. The fan always seems to be running at full blast. I logged onto windows for a minute to see if there was any difference in heating between the two OSs and windows seems to run much cooler and much more quiet.

On a side note i'm thinking of returning the HP and buying a dell XPS 15. I hear they are more compatible with ubuntu and are better built. If anyone has any laptop suggestions i'd appreciate it.

HP Pavillion DV6t
ATI Radeon 6570  1 GB graphics card
Intel I7 2.0GHZ quad

---

### Post by wgarcia on 2011-06-21
Do you know if it is the CPU fan or the graphics card fan? If it is the latter, maybe using a different graphic controller may help.

---

### Post by lavinog on 2011-06-21
Have you installed the restricted graphics driver for the ATI video yet?

The issue is very likely to be the graphics driver.  The opensource ATI driver is usually a little behind when it comes to power management.

do a search for jockey in the application search dialog...it should pull up the additional drivers application (assuming you are using Natty)
This should show if you are using the proprietary ATI/FGLRX driver...enable it if you are not.

---

### Post by Mr Nemo on 2011-06-21
Truthfully i'm not really sure. Now that you said it i'm gonna assume its the graphics card fan.

I wouldn't know how to change the controller though.

---

### Post by Mr Nemo on 2011-06-21
enabling it now. I did have this driver enabled at one point, but it restricted me from using almost any compiz function, including my much beloved cube, so i disabled it. Ill let you know if it changes the heating issue.

Also when i try to open catalyst i get an error message that says either the api driver is not installed or not functioning properly

---

### Post by wildmanne39 on 2011-06-21
> **Mr Nemo said:**
> I bought a new Hp Pavillion DV6T. For the most part, everything worked right out of the box with ubuntu, but the computer seems to be heating up really quickly for no reason whatsoever even if i'm not doing anything intensive. Does anyone have any ideas as to why this is happening. The fan always seems to be running at full blast. I logged onto windows for a minute to see if there was any difference in heating between the two OSs and windows seems to run much cooler and much more quiet.

On a side note i'm thinking of returning the HP and buying a dell XPS 15. I hear they are more compatible with ubuntu and are better built. If anyone has any laptop suggestions i'd appreciate it.

HP Pavillion DV6t
ATI Radeon 6570  1 GB graphics card
Intel I7 2.0GHZ quad
Hi, I have had a dell and an hp laptop and both of them worked  equally well. There is nothing wrong with hp laptops, the only thing I do not like is hp does not give a windows disk, so it made it hard for me to put windows in virtualbox on ubuntu. I used a chilling pad with my laptop it only got warm when running virtualbox, and I set it to power on demand for my cpu, because if you have it set to performance then it will run a lot hotter,when you are not even using the extra cpu most of the time anyway.

---

### Post by mitk0o0o0 on 2011-06-21
This is definately cause of the graphics card (the loud fan) i had this too at the beginning when i installed ubuntu, i had to download some nvidia driver and it cooled off, also now i don't have any heat problems when playing games or doing other stuff.

---

### Post by beew on 2011-06-21
> **Mr Nemo said:**
> .

On a side note i'm thinking of returning the HP and buying a dell XPS 15. I hear they are more compatible with ubuntu and are better built. If anyone has any laptop suggestions i'd appreciate it.



Don't buy the dell XPS 15, it doesn't work in Linux because of Optimus. There are some successes in bringing Linux support to Optimus but the technology still seems early in its development. Just wonder where do you hear that it is more compatible with Ubuntu???


[https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee)

---

### Post by hawthornso23 on 2011-06-21
Natty runs cooler than maverick is my experience. I'm not seeing that `load balancing tick' issue any more, and my battery is lasting longer. I'm using the classic desktop since like you I love the cube. Natty with the classic desktop is a good distro. Natty with unity is ...

---

### Post by nrundy on 2011-06-21
> **Mr Nemo said:**
> I bought a new Hp Pavillion DV6T. For the most part, everything worked right out of the box with ubuntu, but the computer seems to be heating up really quickly for no reason whatsoever even if i'm not doing anything intensive. Does anyone have any ideas as to why this is happening. The fan always seems to be running at full blast. I logged onto windows for a minute to see if there was any difference in heating between the two OSs and windows seems to run much cooler and much more quiet.

On a side note i'm thinking of returning the HP and buying a dell XPS 15. I hear they are more compatible with ubuntu and are better built. If anyone has any laptop suggestions i'd appreciate it.

HP Pavillion DV6t
ATI Radeon 6570  1 GB graphics card
Intel I7 2.0GHZ quad

Mr. Nemo. Presently there is a power regression bug that is making linux run very hot. Nonetheless, in general over the last several years linux is running a lot hotter than Windows. If you want a cool, quiet, long-lasting battery laptop you have no choice but to use Windows 7 or Mac OS at the moment.

Hopefully this will change soon. But the developers have to get the heat down and so far they haven't made it a priority.

---

### Post by Mr Nemo on 2011-06-21
So Beew..

Is bumblebee a fix for the optimus problem?

EDIT: sorry Beew I didnt read your whole post... Thanks for the input

---

### Post by beew on 2011-06-22
> **Mr Nemo said:**
> So Beew..

Is bumblebee a fix for the optimus problem?

EDIT: sorry Beew I didnt read your whole post... Thanks for the input

Check its website, it is impressive but it is still very early. If I have an Optimus laptop already I will definitely use it, it is the best option for now and it would help the project by reporting bugs and giving feedbacks, but I wouldn't go buy  a new laptop knowing that it has Optimus counting on bumblebee to work, it is not at this stage yet based on all the posts from its website.

---

