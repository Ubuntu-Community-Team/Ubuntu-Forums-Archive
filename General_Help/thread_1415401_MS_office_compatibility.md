---
title: "MS office compatibility"
date: 2010-02-24
forum: General Help
---

### Post by kooldino on 2010-02-24
I have several friends with Windows machines that have issues.  I'd like to convert them to kubunutu.  However, they REQUIRE MS Office for their schoolwork.  They've tried openoffice in the past, but had compatibility issues when they'd turn in their assignments.  

What are their options if they run linux?

Here's what I could come up with.

-Wine: Don't know the Office compatibility with WINE.
--Pros: ?
--Cons: ?

-Virtualbox: 
--Pros: Will definitely work.
--Cons: May be complex for a non-technical user to retrieve saved files, slow load times.

-OpenOffice: 
--Pros: Fast and free.
--Cons: Questionable MS Office compatibility, interface difference may confuse user who is used to MS Office.

Can anyone add to these?

---

### Post by drdanielfc on 2010-02-24
> **kooldino said:**
> I have several friends with Windows machines that have issues.  I'd like to convert them to kubunutu.  However, they REQUIRE MS Office for their schoolwork.  They've tried openoffice in the past, but had compatibility issues when they'd turn in their assignments.  

What are their options if they run linux?

Here's what I could come up with.

-Wine: Don't know the Office compatibility with WINE.
--Pros: ?
--Cons: ?

-Virtualbox: 
--Pros: Will definitely work.
--Cons: May be complex for a non-technical user to retrieve saved files, slow load times.

-OpenOffice: 
--Pros: Fast and free.
--Cons: Questionable MS Office compatibility, interface difference may confuse user who is used to MS Office.

Can anyone add to these?

openoffice works fine for me, though I totally agree that they dont always come out, well, as expected. AFAIK office works fine in wine and i believe wine-doors may be of assistance in setting up most software you may need

---

### Post by kooldino on 2010-02-24
> **drdanielfc said:**
> openoffice works fine for me, though I totally agree that they dont always come out, well, as expected. 

Agreed. For my needs it works fine, but it's caused issues for my friends before and they got in trouble for handing in assignments late and such since the professor couldn't read the file properly.

> AFAIK office works fine in wine and i believe wine-

I checked the WINE compatibility list, but it wasn't very clear.

> doors may be of assistance in setting up most software you may need

Doors?

---

### Post by davidpramana on 2010-02-24
> **kooldino said:**
> However, they REQUIRE MS Office for their schoolwork.  They've tried openoffice in the past, but had compatibility issues when they'd turn in their assignments.

I used to have the same problem. However, you need to make it clear what you really require. Is it just the extention (doc, docx, etc) or something else.

I'm using OpenOffice.org 3.1.1 and you can open or create MS Office file.

> **kooldino said:**
> Questionable MS Office compatibility, interface difference may confuse user who is used to MS Office.

I believe functionality is more important than user interface. You will need some time to adjust with the new environment. I think OOo is simpler. I just need to right click to access the important things (page setup, line spacing, etc). Of course you can do it through Format > Page, etc too.

If you need some guides, you can  download : [http://documentation.openoffice.org/manuals/userguide3/0100GS3-GettingStartedOOo3.pdf](http://documentation.openoffice.org/manuals/userguide3/0100GS3-GettingStartedOOo3.pdf)

Check this one too:  [http://wiki.services.openoffice.org/wiki/Documentation/OOo3_User_Guides/Chapters](http://wiki.services.openoffice.org/wiki/Documentation/OOo3_User_Guides/Chapters)

Good luck.:P

---

### Post by QIII on 2010-02-24
Pragmatism is a virtue.

A pragmatic person would keep Windows as necessary.

Have you considered the idea of a dual boot, so that your friends may keep the Windows functionality while having Ubuntu as their OS of choice?

---

### Post by kooldino on 2010-02-24
> **davidpramana said:**
> I used to have the same problem. However, you need to make it clear what you really require. Is it just the extention (doc, docx, etc) or something else.

I'm not sure, exactly.  I know that at minimum they need .doc and .xls compatibility...but it has to be 100% compatible, not 99% like OpenOffice often is.

> I'm using OpenOffice.org 3.1.1 and you can open or create MS Office file.

Ditto.

> I believe functionality is more important than user interface. You will need some time to adjust with the new environment. I think OOo is simpler. I just need to right click to access the important things (page setup, line spacing, etc). Of course you can do it through Format > Page, etc too.

I agree, but these people aren't computer gurus.  Make a few small changes to an interface that they're used to, and they'll panic.  If I'm changing their OS on them, I want it to be as seamless as possible.

---

### Post by kooldino on 2010-02-24
> **QIII said:**
> Pragmatism is a virtue.

A pragmatic person would keep Windows as necessary.

Have you considered the idea of a dual boot, so that your friends may keep the Windows functionality while having Ubuntu as their OS of choice?

I considered this option, and have done this before for people.  It would generally turn out that my efforts were in vain, since they'd never choose to boot into linux.  If I give them no other option, it will force them to learn.  This is exactly how I converted myself to linux - sink or swim mentality.

---

### Post by drdanielfc on 2010-02-24
personally ive gone 99% linux (1% - virtualbox for music, cant get away from foobar :(), so i no longer use wine like tools. However *wine-doors* is a good application that helps with the installation of most windows apps you may need ie photoshop. It worked well with me, though I never had the need to install office so im not sure if its on their list (pretty sure it is cant install to check now not on my home pc)

---

### Post by kooldino on 2010-02-24
Hmm, the only downside about wine-doors is that they couldn't run KDE.

---

### Post by drdanielfc on 2010-02-24
> **kooldino said:**
> Hmm, the only downside about wine-doors is that they couldn't run KDE.

cant help you there - im gnome :-).

just checked and doors DOES include office (though youll need a lisence).

2 plans:

```
Plan A.
1. get gnome
2. use wine-doors to install everything
3. uninstall gnome (if you wish, or just keep it if you want to use it in the future. you can pick gnome or kde at the login if both are installed.)
4. add some menu links in kde :-)
```
```
Plan B.
Step 1. http://www.codeweavers.com/products/cxlinux/ (You have to PAY THOUGH)
```

cheers :D

---

### Post by kooldino on 2010-02-24
> **drdanielfc said:**
> cant help you there - im gnome :-).

just checked and doors DOES include office (though youll need a lisence).

2 plans:

```
Plan A.
1. get gnome
2. use wine-doors to install everything
3. uninstall gnome (if you wish, or just keep it if you want to use it in the future. you can pick gnome or kde at the login if both are installed.)
4. add some menu links in kde :-)
```
```
Plan B.
Step 1. http://www.codeweavers.com/products/cxlinux/ (You have to PAY THOUGH)
```

cheers :D

I've tried installing KDE on an ubuntu box int he past and it didn't go to well.

I might just have to set them up with ubuntu if they really need MS office.  Or go the codeweavers may be doable.

---

### Post by drdanielfc on 2010-02-24
> **kooldino said:**
> I've tried installing KDE on an ubuntu box int he past and it didn't go to well.

I might just have to set them up with ubuntu if they really need MS office.  Or go the codeweavers may be doable.

have you tried installing gnome on a kubuntu box? :mrgreen:

---

### Post by bkcevilmonkey on 2010-02-24
office in wine works perfectly (except outlook) with no need for wine-doors.

I did use winetricks to install some fonts or something.

The most important part is to USE WINE VERSION 1.1.14, look in the archives for it.  AFAIK, this is the only version of wine which will work.

I currently use MSoffice and I have removed OOo

---

### Post by drdanielfc on 2010-02-24
> **bkcevilmonkey said:**
> office in wine works perfectly (except outlook) with no need for wine-doors.

I did use winetricks to install some fonts or something.

The most important part is to USE WINE VERSION 1.1.14, look in the archives for it.  AFAIK, this is the only version of wine which will work.

I currently use MSoffice and I have removed OOo

thanks for the correction, i have little recent wine experience :)

---

### Post by bkcevilmonkey on 2010-02-24
no problem.

for a full tutorial, you can check out this page [http://ieurope.blogspot.com/2009/06/microsoft-office-2007-on-ubuntu-linux.html](http://ieurope.blogspot.com/2009/06/microsoft-office-2007-on-ubuntu-linux.html)[FONT=&quot]
[/FONT]

---

### Post by kooldino on 2010-02-25
> **bkcevilmonkey said:**
> office in wine works perfectly (except outlook) with no need for wine-doors.

Excellent!

> I did use winetricks to install some fonts or something.

What's winetricks?

> The most important part is to USE WINE VERSION 1.1.14, look in the archives for it.  AFAIK, this is the only version of wine which will work.

I currently use MSoffice and I have removed OOo


Thank you!

---

