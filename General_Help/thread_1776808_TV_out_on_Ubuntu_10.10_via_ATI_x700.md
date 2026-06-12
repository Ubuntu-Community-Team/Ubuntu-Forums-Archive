---
title: "TV out on Ubuntu 10.10 via ATI x700"
date: 2011-06-06
forum: General Help
---

### Post by Ghosthaven on 2011-06-06
Today I finally hooked up my server/HTPC to my TV via S-video only 
to find out that tv-out doesn't seem to be working properly.

Through the bios boot process it mirrors on to the TV just fine,
but as soon as Ubuntu prompts for login/password it stops working.

Sound still works though, which is a little odd.

The TV isn't visible under System -> preferences -> monitors and
I can't figure out any other way to get it to work.

I tried googling for a solution but all I found is HDMI issues
and people with the same problem who never got a response.

I did try installing the atitvout package but it kept segfaulting
with no progress so I removed it.

Can anyone give me a hand with this?

Some info:
Running Ubuntu desktop 10.10

```
lspci -nn | grep VGA
``` gave me:
```

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV410 [Radeon X700] [1002:5e4f]

```

---

### Post by linuxinstalledfromhdd on 2011-06-06
I could never get TV working on the ATI drivers settings.   It does work fine with Nvidia cards and Nvidia settings in Ubuntu.  That's where you would need to configure it if it was a Nvidia card. Other than that, let's see if anyone else knows.

---

### Post by Ghosthaven on 2011-06-07
What all did you try? Did you have any progress at all?

Anyone else want to chime in? Looks like you've got two people
who would benefit from some linux-guru-ness.

---

### Post by Mark Phelps on 2011-06-07
You're limited by the unfortunate fact that ATI dropped restricted Linux driver support for your card YEARS ago, so now, you're limited to the open-source driver -- which is OK for general 2D graphics, but does not provide the extended feature set of the restricted drivers.

Apart from upgrading to a newer card, there's likely nothing else you can do with such an old card.

---

### Post by Ghosthaven on 2011-06-07
Is there any chance I could get the old driver?

I have a couple other questions...
Is there any way to access the tv-out of the x700 using a windows VM?

Would a device like:
[http://www.amazon.com/gp/product/B001CJOLBW/ref=ox_sc_act_title_1?ie=UTF8&m=A1BREQ8I6OHSBG](http://www.amazon.com/gp/product/B001CJOLBW/ref=ox_sc_act_title_1?ie=UTF8&m=A1BREQ8I6OHSBG)
Work better to get s-video? Would this device give me any problems with Ubuntu?

---

### Post by Mark Phelps on 2011-06-08
> **Ghosthaven said:**
> Is there any chance I could get the old driver?
NOT -- and have it work on any recent Ubuntu version.  ATI dropped support for some cards after Ubuntu 8.10 -- and I don't know if your card was dropped earlier or not.  But the more recent Ubuntu versions have upgraded the X-server so it will not work with the older ATI drivers.

> I have a couple other questions...
Is there any way to access the tv-out of the x700 using a windows VM?

Would a device like:
[http://www.amazon.com/gp/product/B001CJOLBW/ref=ox_sc_act_title_1?ie=UTF8&m=A1BREQ8I6OHSBG](http://www.amazon.com/gp/product/B001CJOLBW/ref=ox_sc_act_title_1?ie=UTF8&m=A1BREQ8I6OHSBG)
Work better to get s-video? Would this device give me any problems with Ubuntu?

Sorry ... don't use VM ... but my guess would be NO. I believe that virtualization works through the existing drivers -- which leaves you with the same problem you have now.

---

