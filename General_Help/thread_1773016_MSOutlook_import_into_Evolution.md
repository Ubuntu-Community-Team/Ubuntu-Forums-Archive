---
title: "MSOutlook import into Evolution"
date: 2011-06-01
forum: General Help
---

### Post by r2d211 on 2011-06-01
I was told and I tried to 

import mails and contacts from MSOutlook in windows to Thunderbird. It worked and even kept the folder hierarchy of the emails, as well as the contacts. My only task now is to find the /.evolution folder in ubuntu and past everything.

But was disappointed that thunderbird has no calendar, no ToDos  and tasks so I'm wondering how could I import these great Outlook features into evolution, too. Anyone with such an experience willing to share it with us?

---

### Post by etienne@Rofti on 2011-06-01
Dear d2d211

Thank you for the question. If you open up Ubuntu Software Centre and search for "Thunderbird calendar" you will find an item with the name of Lightning.

If you install this, (you can also install it by opening up Synaptic and searching in the same way) you can re-start Thunderbird and the calendar will be there instantly.

I don't know why it needs to be installed separately, but at least there is an easy way to get it!

Please reply to let me know if you get it right or not.

---

### Post by r2d211 on 2011-06-01
Etiene, thak you for the thoughtfulness. My problem is that I don't have yet an internet connection for my ubuntu, so I download packages from windows and then try to install them in Natty. Do you think I could find such a package at packages.ubuntu?

I'll give it a try. But anyway, how will thunderbird (in ubuntu) import calendar settings from Outlook (in XP)?

Should I try anyway?

---

### Post by jamesisin on 2011-06-01
Thunderbird and Lightning are two separate projects from Mozilla.  This is why they are installed separately.  I think you will find that Lightning gives Thunderbird the functionality you are seeking.

(There is a Lightning stand-alone application and what you want is the Lightning extension for Thunderbird.)

Unfortunately I'm not seeing Lightning in Synaptic under 10.04 (there is something for programming called "lightning" but that's not it).  You may have to visit the Thunderbird site to get it:

[https://addons.mozilla.org/en-US/thunderbird/](https://addons.mozilla.org/en-US/thunderbird/)

---

### Post by r2d211 on 2011-06-01
Okay, Jamey, I'll give it a try and keep you update!

---

### Post by etienne@Rofti on 2011-06-01
Jamesisin is right. You can download the Lightning extension directly from Mozilla on the internet.

Here is a direct link:
[https://addons.mozilla.org/thunderbird/downloads/latest/2313/platform:2/addon-2313-latest.xpi](https://addons.mozilla.org/thunderbird/downloads/latest/2313/platform:2/addon-2313-latest.xpi)

Download this file to your hard disk (probably to your Downloads directory), and then open Thunderbird, go to the Tools menu and select Add-ons. Under Extensions, click on Install, and then find the place where you downloaded "addon-2313-latest.xpi" and then press Open (or whatever you need to install it).

Once you close and restart Thunderbird, it should work fine.

Feel free to search [https://addons.mozilla.org/en-US/thunderbird/](https://addons.mozilla.org/en-US/thunderbird/) for extra add-ons. Although Thunderbird is supposed to support Microsoft Exchange and Gmail from the start, there are add-ons for those servers if it doesn't want to work.

---

### Post by r2d211 on 2011-06-02
I just tried today the "import from Outlook" plugin olof evolution and it seems to work, but only for emails and contacts. Notes, to dos and calendar is left out, even if it has options for importing them.

I'll try tomorrow the TB way.

---

### Post by r2d211 on 2011-06-02
I just tried today the "import from Outlook" plugin of evolution and it seems to work, but only for emails and contacts. Notes, to dos and calendar is left out, even if it has options for importing them.

I'll try tomorrow the TB way.

---

### Post by jamesisin on 2011-06-02
For the calendar (and perhaps for the notes and to-dos) there are tools for synchronizing Tb with Google calendar and I believe also for Outlook.  This would allow you to sync Outlook with GCal and then sync GCal with Tb.

---

### Post by r2d211 on 2011-06-03
Yes, but you forget my MAIN problem: cannot get to the internet yet in ubuntu, bbtether doesn't work properly.

---

### Post by jamesisin on 2011-06-03
So fix your connection problem?

---

### Post by linuxinstalledfromhdd on 2011-06-03
He wouldn't have a problem using Thunderbird and Thunderbird's PST import plugin. :P

Then he can just transfer it over to evolution.

---

### Post by r2d211 on 2011-06-03
I'll try both solutions, my friends!

---

### Post by jamesisin on 2011-06-03
Not familiar with that extension.  Link?

---

### Post by r2d211 on 2011-06-03
I download it yesterday and I'll give it a try as soon as I can. Anyway, the fact that there's no viable solution to my tethering  problem, still keeps me away of adopting ubuntu as my first OS of choice. I discovered yesterday that the ubuntu working team had knowledge of this idea and workarounds since 2009 but no one was interested (see the link under my signature).Too bad for an OS that is advertised as 'recognizing instantly whatever you plug into your computer'.
Hey, I am just tired, don't be upset of my words.

---

### Post by jamesisin on 2011-06-03
Oh.  You're using a Blackberry.  I'm sorry.

---

### Post by Thewhistlingwind on 2011-06-03
> **r2d211 said:**
> I download it yesterday and I'll give it a try as soon as I can. Anyway, the fact that there's no viable solution to my tethering  problem, still keeps me away of adopting ubuntu as my first OS of choice. I discovered yesterday that the ubuntu working team had knowledge of this idea and workarounds since 2009 but no one was interested (see the link under my signature).Too bad for an OS that is advertised as 'recognizing instantly whatever you plug into your computer'.
Hey, I am just tired, don't be upset of my words.

Theres instructions in the comments. On the page you linked.

You should try them in terminal.

---

