---
title: "Ubuntu 10.10 freezes randomly on Dell Inspiron 1501"
date: 2011-02-12
forum: General Help
---

### Post by mahman on 2011-02-12
Hi All,
I freshly installed Ubuntu 10.10 on a Dell Inspiron 1501. I am using the full disk. The system freezes randomly and doesn't respond anymore. The only thing I can do is a physical reboot. I tried to reinstall it a couple of times but I end up with the same problem. The system freezes anytime and with any program but mostly when  Update Manager is running and when copying from a USB drive or taring few gigs of data.

Any idea how to fix this??

Thanks

---

### Post by cogier on 2011-02-12
I have a Dell laptop that used to freeze now and again and I found that certain Compiz settings were to blame.

If you have not made any changes try running without Compiz by going to **System>Preferences>Appearance** clicking on the **Visual effects** tab and selecting **None**.

If after a period of use the computer does not freeze and you would like to use better graphics go to **Applications>Ubuntu software centre**, enter **compiz** in the search box and install the **Advanced Desktop Effects Settings**.

You can then turn off each setting until the offender is located.

---

### Post by samacaster on 2011-02-12
GD! Dell 1501!!!! BS! I',m so tired of these OEM manufacturers , especially Dell. So Linux unfriendly!

---

### Post by mahman on 2011-02-12
> **cogier said:**
> I have a Dell laptop that used to freeze now and again and I found that certain Compiz settings were to blame.

If you have not made any changes try running without Compiz by going to **System>Preferences>Appearance** clicking on the **Visual effects** tab and selecting **None**.

If after a period of use the computer does not freeze and you would like to use better graphics go to **Applications>Ubuntu software centre**, enter **compiz** in the search box and install the **Advanced Desktop Effects Settings**.

You can then turn off each setting until the offender is located.
I forgot to mention that all visual effects are disabled. The freezing still happens randomly.

---

### Post by Nuxer-India on 2011-02-12
The same problem annoyed me on my Acer Aspire 5542G with Ubuntu 10.10. I solved this problem by disabling bluetooth service.

---

### Post by mahman on 2011-02-12
> **Nuxer-India said:**
> The same problem annoyed me on my Acer Aspire 5542G with Ubuntu 10.10. I solved this problem by disabling bluetooth service.
The Inspiron 1501 doesn't have bluetooth. I am trying to save this computer for a friend of mine. Except the annoying freezing, Ubuntu works great on this computer where Windows really sucks.

---

### Post by Nuxer-India on 2011-02-12
> **mahman said:**
> The Inspiron 1501 doesn't have bluetooth. I am trying to save this computer for a friend of mine. Except the annoying freezing, Ubuntu works great on this computer where Windows really sucks.
Oh! thats ok.

My another suggestion is, try to boot ubuntu with "acpi=off" option.

---

### Post by mahman on 2011-02-13
Thanks all for the help.
None of the proposed solutions worked. I can reproduce the issue consistently though. When I try to copy pictures or music files from a USB external hard drive to the home folder, it automatically freezes.

---

### Post by tiger.seo on 2011-02-14
Confirming!
Have notebook Dell Inspiron 1501.
Seems that this freezing is related to HDD-using, cause there no no freezing when i`m using rdesktop to work on remote pc and freezes most time when doing heavy upgrade.
I`m think this is started after I upgraded OS from 10.4 to 10.10 ! =(

---

### Post by jcolyn on 2011-02-14
> **samacaster said:**
> GD! Dell 1501!!!! BS! I',m so tired of these OEM manufacturers , especially Dell. So Linux unfriendly!

I have 4 Dell laptops including the Inspiron 1501. All are running Linux without a single hitch. I've installed it on several Dells for friends family etc and all are working fine..

None of these are Linux unfriendly..

---

### Post by mahman on 2011-02-15
> **tiger.seo said:**
> Confirming!
Have notebook Dell Inspiron 1501.
Seems that this freezing is related to HDD-using, cause there no no freezing when i`m using rdesktop to work on remote pc and freezes most time when doing heavy upgrade.
I`m think this is started after I upgraded OS from 10.4 to 10.10 ! =(

I think you're right. The more I use it the more your statement is confirmed!

---

### Post by tiger.seo on 2011-02-15
> **jcolyn said:**
> I have 4 Dell laptops including the Inspiron 1501. All are running Linux without a single hitch. I've installed it on several Dells for friends family etc and all are working fine..

None of these are Linux unfriendly..

 And distro is Ubuntu 10.10 ?!

---

### Post by piquat on 2011-02-15
> **tiger.seo said:**
> And distro is Ubuntu 10.10 ?!

I'm on a 1501 right now.  I've had Mint on here, which is really a 10.10 with a pretty face on it.  I've had 2 crashes in the last four months.

There is even a site dedicated to it:
[http://www.ubuntu1501.com/](http://www.ubuntu1501.com/)
Mind you, it's not updated much, but it was quite compatible when it was.

I think I'd start with memtest and keep an eye on my temps.  Both times it crashed it didn't start the CPU fan.  If you shine a light in the back you can see the fan through the grill to the left of the keyboard.  Make sure yours is spinning....

Edit:  Re-read your post.  Does it when it's working hard.... Heat would be the first place I'd look.

---

### Post by tiger.seo on 2011-02-15
I already tried memtest and it was Ok. Also i noticed, that sometimes after freeze cooler goes faster and maybe at 100% speed.  About temp, i remember that in summer i was having hdd temp sometimes above 60c and OS does`nt freeze.

---

### Post by piquat on 2011-02-15
> **tiger.seo said:**
> I already tried memtest and it was Ok. Also i noticed, that sometimes after freeze cooler goes faster and maybe at 100% speed.  About temp, i remember that in summer i was having hdd temp sometimes above 60c and OS does`nt freeze.

I've seen 64 (CPU) and had it run fine.  However, both times it froze, no fan and temps (well the last time anyway) were 65, frozen on the screen.

I'm not sure what's up with it.  It should work.  I didn't have to do much to this except find the driver for the wireless in jockey.

Makes me wonder if there is a BIOS update for yours.  I'm not sure what mine is running, I've never had a need to look.

---

### Post by aqui_c on 2011-03-10
Hi all!
I'm having the same problems... The PC freezes randomly. 
I had the same problems with Debian after the upgrade (that's why I tried Ubuntu), so I'm a bit inclined to thinking it's a Linux Kernel problem. 

I would really like to try with an older kernel... Do you have any suggestions on how to do this?

---

### Post by mahman on 2011-03-24
I ended up with installing Linux Mint 10 instead of Ubuntu 10.10. The Inspiron 1510 works like a charm since then.

---

