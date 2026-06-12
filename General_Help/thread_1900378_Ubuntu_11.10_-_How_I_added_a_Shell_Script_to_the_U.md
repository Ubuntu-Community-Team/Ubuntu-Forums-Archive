---
title: "Ubuntu 11.10 - How I added a Shell Script to the Unity Launcher"
date: 2011-12-26
forum: General Help
---

### Post by zxMarce on 2011-12-26
Well, my mom got a netbook (Acer Aspire One D255E). Came with Win7 english, but she needed it in her native tongue.

I used the USB method to wipe the disk and put Ubuntu 11.10 on it, after checking the various hardware parts were working in the "Live" environment, before wiping Win7. But when I put a 3G modem (Huawei E173), tho, it did NOT work. The solution for these modems still seems to be to use **Sakis3G**. Downloaded it and tried it: Success.

But mom is not that computer literate, so I wanted to add a Launcher Icon for her Sakis3G. Here the drama begun. After seeking hi and lo for a solution, and finding none but clues, I tried a mix-N-match which works. At least for me & her!

So this is what I did:

Downloaded & installed **alacarte** (Main Menu), which should include **gnome-desktop-item-edit** (GDIE for short). I did not use alacarte, but GDIE.

I put the Sakis3G shell and a nice PNG Icon for it in **~/Sakis3g**.

In a terminal, I ran the following:

```
**gnome-desktop-item-edit ~/Sakis3g/ --create-new**
```This created an old-fashioned Dektop launcher, but in the Sakis shell folder. I filled in the details (Name, Description, Target, Icon) and saved it. I did NOT want it in the Desktop, because once added to the launcher I wanted to erase the spare desktop icon... Action which also erased the Launcher Bar icon #-o

Then, I opened **gedit** and drag-dropped the launcher into it and changed the **Terminal=true** entry to **=false**. This removes the background terminal when launching Sakis3G. Your particular script may still need it, so test thoroughly before and after editing this launcher key :-k

Last step: I drag-dropped the icon to the Unity Launcher Bar, action that I had to do more than once, but in the end Unity understood that I wanted to add the icon :-P

_Disclaimer:_ I KNOW the folder I used may not be optimum (I would like to have done all this in a more "publicly accessible, app-oriented folder" so everyone logged in could use Sakis3G), but I was in a hurry to have my mom connected. So, while the folder may not be best-suited, the steps are the same regardless of where the launcher creted with GDIE reside :-\"

Hope this mini-tutorial helps someone else!

Regards,
zxMarce.

---

