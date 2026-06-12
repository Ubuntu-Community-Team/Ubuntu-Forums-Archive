---
title: "No more support for 10.10?"
date: 2011-08-13
forum: General Help
---

### Post by Wuxin on 2011-08-13
I have not found any updates for Ubuntu 10.10 in a few weeks.  Is this because none have been posted or because there is no longer support for this edition of Ubuntu?  I hope that's not the case because I am not yet ready to install 11.04.

---

### Post by CatKiller on 2011-08-13
10.10 is still supported for quite a while yet.

---

### Post by HereInOz on 2011-08-13
Probably the former.  10.10 will be supported until around April next year.  

The one thing I would do is to open the Update Manager, System > Administration > Update Manager, then click on the "Check" button (if you haven't already).  This will update your update list.  

When you do this, check for any errors.  You can also open a terminal and enter
sudo apt-get update

Watch what happens and ensure that the update process runs without error.  Check if there are any updates available.

If there are, enter sudo apt-get upgrade, and see if you get your updates OK.

---

### Post by haqking on 2011-08-13
i had some updates today

---

### Post by raja.genupula on 2011-08-13
the support for LTS desktop 3 years and non-LTS desktop 18 months . so i think 10.10 not completed its journey . you'll get your updates . if they append some updates then you can get them  if they didnt how can you ?  just wait for a while.

---

### Post by Wuxin on 2011-08-15
Thank you very much for the great assistance!  Tell me--does running sudo apt-get update actually install the updates or simply show what's now available?  I ran that and it seemed to actually perform the installation.  Very cool.  Strangely, I am beginning to prefer using the terminal whenever possible instead of the front end stuff.  

I am pleased to know that 10.10 will be supported for the foreseeable future.  In fact, I hope it continues for a good while because I keep hearing mixed reviews about 11.04.  I am very reluctant to install it!  From what I hear it is buggy, many people don't like the Unity format, and it is more cumbersome than what most people associate with Linux.  When I hear a "two thumbs up" for it, I'll go for it.   In the meantime I'm staying with 10.10!

---

### Post by grahammechanical on 2011-08-15
I am using 11.04 and Unity. I upgraded my main installation of Ubuntu about three weeks after release. It is stable and not at all buggy.

I also tested 11.04 from alpha 2 onwards and over time and daily updates it developed into the 11.04 release candidate and was very stable.

Why don't you create another partition of about 12GB and install 11.04 into it to try it out. This is what I am doing with 11.10. In this way I find out for myself the true situation and make my own decisions.

Some recommend only using LTS releases. That means that they will be using 10.04 and will wait until 12.04 for the next LTS release by which time there will be a very big difference between the user experience of 10.04 and the user experience of 12.10. Best to get some experience now of what is to come.

Regards.

---

### Post by Elfy on 2011-08-15
> Tell me--does running sudo apt-get update actually install the updates or simply show what's now available?Just updates the lists - to get any updated software upgraded

```
sudo apt-get upgrade
```

or to do both

```
sudo apt-get update &&sudo apt-get upgrade
```

---

