---
title: "login screen cursor"
date: 2012-04-21
forum: General Help
---

### Post by Thegoldendog777 on 2012-04-21
Hi all
Just installed ubuntu 12.04 lts beta 2,everything seems fine bar one error..
When i come to the login screen,the mouse cursor does'nt move properly,its jerky and sometimes theres no response at all.So if say i logout and then want to shut down its extemely difficult to manovoure the cursor to the top right of the screen so i can select the shutdown option.
But whilst actually in a live session the cursor is fine...its just on the login screen where the problem is..
cheers for any help
D

---

### Post by ryn.cor21 on 2012-04-29
I also have the same problem in the full release of Ubuntu 12.04. You may want to have a look at this:
[https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/945749](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/945749) It is a confirmed bug. One thing that I notice is that the person in the bug description, as well as I, are using the default onboard Radeon Graphics Drivers. I will seek a new graphics card driver and let you know how it goes.

EDIT:

I am pleased to say that an installation of the correct driver fixed the problem.
[http://support.amd.com/us/Pages/AMDSupportHub.aspx](http://support.amd.com/us/Pages/AMDSupportHub.aspx)

Please go to the above website and select your graphics card from the list in the top Right corner.

By the way, this is what I did to get the driver:

Component Category: Motherboard/Chipset
Product Line: Integrated Radeon HD Series
Product Model: Radeon HD 4200 Series
Operating System: Linux86_64

(just in case you have the same graphics card)

If you need help installing the driver please let me know.

---

### Post by Thegoldendog777 on 2012-05-02
Thanks mate for the info,
Think i might have a problem though,my graphics card is a ati radion x1200 and it doesn't seem to be listed.
Cheers for any help

---

### Post by ccornchip on 2012-06-15
Hello, and thanks for the link. It mostly works.

`lspci -v` told me "...[Radeon X1200 Series]..." so I downloaded it, chmodded it, and sudo-ran it. It looks like all is good, but then I get:

```

Error: ./default_policy.sh does not support version
default:v2:x86_64:lib::none:3.2.0-25-generic; make sure that the version is being correctly set by --iscurrentdistro

```

What does this mean? Google translate doesn't do linux to English yet ;P

---

