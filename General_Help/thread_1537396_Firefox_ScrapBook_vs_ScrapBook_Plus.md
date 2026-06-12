---
title: "Firefox ScrapBook vs ScrapBook Plus?"
date: 2010-07-23
forum: General Help
---

### Post by 2CV67 on 2010-07-23
I am triple-booting XP & Current Ubuntu (10.04) & LTS Ubuntu (8.04).

For years, I have been using Firefox ScrapBook Add-on, keeping all the data common in my shared drive & accessing it via all 3 OS's.
So far - so good.

Recently (not sure when it started) my current Ubuntu Firefox has lost ScrapBook.
When I check in Tools > Add-ons > Extensions, it tells me:
"ScrapBook 1.3.3.9 Not compatible with Firefox 3.6.7"
Back in 8.04, I still have ScrapBook 1.3.7 working fine in Firefox 3.6.6

If (in 10.04) I go to "Get Add-ons" & look for ScrapBook, I get offered ScrapBook Plus, but not ScrapBook.

Anybody know what is going on?

Can I no longer use ScrapBook with Firefox 3.6.7 ?

Do I have to use ScrapBook Plus?
Why?
Is it tried & tested?
I am perfectly satisfied with ScrapBook.

If I switch to Plus in 10.04, will it work OK with ScrapBook in 8.04 & XP, sharing the same data?
Or do I have to switch all 3?

Thanks for any info.

---

### Post by ajgreeny on 2010-07-23
Scrapbook 1.3.7 is still available for FF 3.6.7 according to the add-ons page here
[https://addons.mozilla.org/en-US/firefox/addon/427/](https://addons.mozilla.org/en-US/firefox/addon/427/)
See if you can install it rather than the scrapbook plus from
[https://addons.mozilla.org/en-US/firefox/addon/8186/](https://addons.mozilla.org/en-US/firefox/addon/8186/)

It seems  from the info on those pages that you have to uninstall **scrapbook** before installing **scrapbook plus**.

---

### Post by lovinglinux on 2010-07-24
Are you sure the error was about 3.6.7 and not 3.7? The information on ScrapBook page shows that it is compatible with Firefox 3.6*, which means it should work up to Firefox 3.6.9.

Anyway, you can override the compatibility check to force it to install and enable. The easiest way of doing that is by using [Add-on Compatibility Reporter](https://addons.mozilla.org/en-US/firefox/addon/15003/) extension. Be careful tho if you decide to use Firefox 4, since [several extensions will break and interact badly with each other]("http://ubuntuforums.org/showthread.php?t=1531119") under that version at this moment. Nevertheless, Scrapbook works with the compatibility check disabled up to Firefox 4.0b3pre.

---

### Post by 2CV67 on 2010-07-24
> **lovinglinux said:**
> Are you sure the error was about 3.6.7 and not 3.7?
Yes:
[IMG]http://i838.photobucket.com/albums/zz309/2CV67/screenshot_01.png[/IMG]

---

### Post by dearingj on 2010-07-24
If you click the 'Find Updates' button in the add-ons window, does it offer to update ScrapBook to a newer version?

---

### Post by lovinglinux on 2010-07-24
> **dearingj said:**
> If you click the 'Find Updates' button in the add-ons window, does it offer to update ScrapBook to a newer version?

Is it possible that it only needs a compatibility "patch". Click the Find Updates button and see how it goes. Otherwise, try to install it again from mozilla site.

---

### Post by lovinglinux on 2010-07-24
BTW, current version of Scrapbook is 1.3.7. That version you have is compatible with Firefox 3.0.x.

---

### Post by 2CV67 on 2010-07-24
> **dearingj said:**
> If you click the 'Find Updates' button in the add-ons window, does it offer to update ScrapBook to a newer version?
No:
[IMG]http://i838.photobucket.com/albums/zz309/2CV67/screenshot_03.png[/IMG]

---

### Post by lovinglinux on 2010-07-24
> **2CV67 said:**
> No:
[IMG]http://i838.photobucket.com/albums/zz309/2CV67/screenshot_03.png[/IMG]

I think the problem is that you were using version 1.3.3.9 on Ubuntu 8.04, which until recently had Firefox 3.0.19. Since Mozilla stopped supporting Firefox 3.0 series, Firefox 3.6 was pushed into Hardy repositories. For some reason, your old Scrapbook version is not updating itself. So get the latest version from Mozilla site. It should overwrite the old version.

---

### Post by 2CV67 on 2010-07-24
> **lovinglinux said:**
> I think the problem is that you were using version 1.3.3.9 on Ubuntu 8.04, which until recently had Firefox 3.0.19. Since Mozilla stopped supporting Firefox 3.0 series, Firefox 3.6 was pushed into Hardy repositories. For some reason, your old Scrapbook version is not updating itself. So get the latest version from Mozilla site. It should overwrite the old version.
My "current" Ubuntu has been continuously updated through 6.10 > 7.04 > 7.10 > 8.04 > 8.10  > 9.04 > 9.10 > 10.04 and always accepting whatever updates were offered for FF etc, so I don't understand how I got to this situation.

Anyway, I installed ScrapBook 1.3.7 from Mozilla site, as you suggested (I try to avoid installing & updating Ubuntu stuff via external sites) & it is working OK.

So - thanks very much for your interest! :D

---

### Post by lovinglinux on 2010-07-24
> **2CV67 said:**
> Anyway, I installed ScrapBook 1.3.7 from Mozilla site, as you suggested (I try to avoid installing & updating Ubuntu stuff via external sites) & it is working OK.

So - thanks very much for your interest! :D

You are welcome. BTW, as long as you don't install extensions that are experimental (yellow button) or those that are hosted on external web sites, then you are secure, since all hosted approved extensions (green button) on Mozilla site are scanned and reviewed by an editor before being approved.

---

