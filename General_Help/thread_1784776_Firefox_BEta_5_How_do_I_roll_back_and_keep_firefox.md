---
title: "Firefox BEta 5: How do I roll back and keep firefox at latest stable release"
date: 2011-06-17
forum: General Help
---

### Post by 13east on 2011-06-17
How do i roll back firefox5beta to firefox4 and keep updating to the latest stable releases w/out upgrading to beta?  The only extension that isn't working is FEBE which is incompatible w/ firefox5beta (profile, extension and preference backup). Have to use FEBE beta7 under Firefox4 so I don't think a compatible release for Firefox5beta is going to come out any time soon.

---

### Post by pqwoerituytrueiwoq on 2011-06-17
open synaptic locate firefox
click it
click package->force version (menu bar)
BTW the beta will be stable in 4 days

---

### Post by 13east on 2011-06-17
> **pqwoerituytrueiwoq said:**
> open synaptic locate firefox
click it
click package->force version (menu bar)
BTW the beta will be stable in 4 days

thank you...
it's not the fact that its beta... I just wanna be able to use the FEBE extension

---

### Post by pqwoerituytrueiwoq on 2011-06-17
you can use the nightly testers addon to disable the compatibility check

---

### Post by 13east on 2011-06-17
> **pqwoerituytrueiwoq said:**
> you can use the nightly testers addon to disable the compatibility check

Not all extensions work properly by just disabling the compatibility check... but will try and report back... thx

---

### Post by 13east on 2011-06-17
> **pqwoerituytrueiwoq said:**
> you can use the nightly testers addon to disable the compatibility check

Where do i find this extension?  I tried both firefox addon website and synaptic, but couldn't find it.

EDIT:
I couldn't find it directly on firefox addon site but a google search did it.  The nightly testers addon by itself doesn't disable the compatibility check, but the "Add-On Compatibility Reporter" referenced on the nightly addons page does w/out even having nightly installed.  So far febe works fine... tried partial and full backup, as well as uploading backup to box.net... so far so good.

Thank you for your help.

---

### Post by pqwoerituytrueiwoq on 2011-06-17
it is under tools->nightly testers just so you know

---

### Post by 13east on 2011-06-17
> **pqwoerituytrueiwoq said:**
> it is under tools->nightly testers just so you know

Missed that... I have the compact menu option enabled w/ personal menu extension so overlooked that... 

The nightly add-on doesn't have any other functions that I need thus far so I'm just going to keep Add-on Compatibility Reporter for now...

Thank you for all of your help... saved me some headache in case I messed around w/ my firefox profile and didn't have a timely backup on hand.

---

### Post by lovinglinux on 2011-06-18
> **13east said:**
> Missed that... I have the compact menu option enabled w/ personal menu extension so overlooked that... 

The nightly add-on doesn't have any other functions that I need thus far so I'm just going to keep Add-on Compatibility Reporter for now...

Thank you for all of your help... saved me some headache in case I messed around w/ my firefox profile and didn't have a timely backup on hand.

Just for the record, you can downgrade to Firefox 4 by disabling the *firefox-next* ppa and installing the *firefox-stable* ppa. If you are not using a ppa, then is because you have enabled the *proposed* repositories. In this case you need to use the "Lock version" feature in Synaptic.

See [Firefox 4,5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247") for more information and support.

---

### Post by inameiname on 2011-06-18
Actually in the official natty-proposed repo they decided to add Firefox 5 beta (5.0~b5+build1+nobinonly-0ubuntu0.11.04.1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-proposed/main i386 Packages). I had the exact same problem as you, and for a while just downgraded to Firefox 4 to avoid it since it screwed up several of my extensions.

Basically what I did was just install the older version of firefox, and put a hold on firefox so it wouldn't update. 

to hold...

```

echo "package_name hold" | sudo dpkg --set-selections

```to unhold...

```

echo "package_name install" | sudo dpkg --set-selections

```But I decided last night to just install the latest firefox, as it seems to work just fine, and manually update those extensions that weren't working due to being 'incompatible'. How I did that was to go inside the ~/.mozilla folder, find the extensions folder inside the main one (the one with the random numbers), and inside each 'install.rtf' file (either in a folder or inside the compressed file), I changed the version number where it said Max. Version for Firefox to 5.1.*. Works just fine for me now, and I'm cool with leaving it.

Therefore, if you want to use this latest Firefox 5 beta release, just update that one extension using the method I described, and you will be fine. Its just a matter of finding the right one, if only one is what you are going to change to make compatible. It often says inside that 'install.rtf' file.

---

### Post by lovinglinux on 2011-06-18
> **inameiname said:**
> Actually in the official natty-proposed repo they decided to add Firefox 5 beta (5.0~b5+build1+nobinonly-0ubuntu0.11.04.1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-proposed/main i386 Packages).

Yes, that is what I think the OP has.

> **inameiname said:**
> 
[CODE]But I decided last night to just install the latest firefox, as it seems to work just fine, and manually update those extensions that weren't working due to being 'incompatible'. How I did that was to go inside the ~/.mozilla folder, find the extensions folder inside the main one (the one with the random numbers), and inside each 'install.rtf' file (either in a folder or inside the compressed file), I changed the version number where it said Max. Version for Firefox to 5.1.*. Works just fine for me now, and I'm cool with leaving it.

Therefore, if you want to use this latest Firefox 5 beta release, just update that one extension using the method I described, and you will be fine. Its just a matter of finding the right one, if only one is what you are going to change to make compatible. It often says inside that 'install.rtf' file.

Please don't do that. When you use testing versions, you can simply disable the add-on compatibility check by using [Add-on Compatibility Reporter]("https://addons.mozilla.org/en-US/firefox/addon/15003/") extension. No need to edit files manually. Additionally, there is a reason why some of your extensions are not compatible. Since Mozilla changed the development model, they are bumping the extensions compatibility automatically for beta releases, like Firefox 5. In theory, all you need is to update your extensions through the add-ons manager, to get the patches. However, some extensions are not being bumped automatically. The reason for that is that they contain code that isn't compatible with Firefox 5. So is not just a matter of disabling the compatibility check or editing the install.rdf file. Those extensions will probably function improperly and cause errors, that sometimes can even affect Firefox.

---

### Post by inameiname on 2011-06-18
Its not a usual way to do it, and of course not all addons will work anyway, even if you manually update the version numbers they can handle (such as Fast Dial, i've noticed), but for an easy hack, it works well enough. In many Firefox versions I've tried that diable compatibility check and that never lasted long or something always happened. As such, I decided to try this. It's my first time doing it, actually.

Basically it was either do this, or downgrade to the latest stable Firefox and put a hold on it. I don't mind bleedy software so long as they are stable enough, and since this one was actually found inside the official natty-proposed repo, not a PPA, I am inclined to trust it well enough.

Oh, and usually I do wait for Firefox to update their addons, but sometimes for a few it takes a very long time, even months after the release has gone stable. So if it works, I'll try it.

...I didn't know beta versions have a built-in disable compatibility check built-in. Usually I've had to manually disable it.

---

### Post by lovinglinux on 2011-06-18
> **inameiname said:**
> Its not a usual way to do it, and of course not all addons will work anyway, even if you manually update the version numbers they can handle (such as Fast Dial, i've noticed), but for an easy hack, it works well enough. In many Firefox versions I've tried that diable compatibility check and that never lasted long or something always happened. As such, I decided to try this. It's my first time doing it, actually.

Basically it was either do this, or downgrade to the latest stable Firefox and put a hold on it. I don't mind bleedy software so long as they are stable enough, and since this one was actually found inside the official natty-proposed repo, not a PPA, I am inclined to trust it well enough.

Oh, and usually I do wait for Firefox to update their addons, but sometimes for a few it takes a very long time, even months after the release has gone stable. So if it works, I'll try it.

...I didn't know beta versions have a built-in disable compatibility check built-in. Usually I've had to manually disable it.

The reason why disabling the compatibility check doesn't last is because they need to be specific for each Firefox branch. The Add-on Compatibility Reporter takes care of that, no matter which version you are using.

The main reason I am not using FF 5 right now, is because Fast Dial indeed doesn't work at all. That is why it's compatibility  hasn't been automatically updated by the new system on Mozilla site.

I also advise to look if some of the extensions are in fact being updated by the developer. Some extensions are simply abandonware and bumping their compatibility is just delaying the inevitable. The probability of these extensions causing problems to Firefox and other extension is higher than those that are already fully compatible with Firefox 4.

---

### Post by inameiname on 2011-06-18
It does, but I always tend to have the add-ons that get disabled by it. :P Dumb me for picking the not-frequently-updated ones. Hehe

The lack of Fast Dial working was why I downgraded for a while, but I decided just to try Speed Dial instead, as it will work with Firefox 5. Not as good, but good enough to use until Fast Dial gets updated. 

Very true. I'm sure that is a part of why some may stop functioning after specific updates. I have 29 extensions, and one goes bad every now and then. Oddly, for a while it was Firefox 4 that wouldn't run several, and it was a long while before they got updated. Hopefully it wont be that long for Firefox 5.

---

### Post by lovinglinux on 2011-06-18
> **inameiname said:**
> It does, but I always tend to have the add-ons that get disabled by it. :P Dumb me for picking the not-frequently-updated ones. Hehe

The lack of Fast Dial working was why I downgraded for a while, but I decided just to try Speed Dial instead, as it will work with Firefox 5. Not as good, but good enough to use until Fast Dial gets updated. 

Very true. I'm sure that is a part of why some may stop functioning after specific updates. I have 29 extensions, and one goes bad every now and then. Oddly, for a while it was Firefox 4 that wouldn't run several, and it was a long while before they got updated. Hopefully it wont be that long for Firefox 5.

I also switch between Fast Dial and Speed Dial, but I prefer Fast Dial.

I am currently using 55 add-ons and the only one that really don't work with FF 5 is Fast Dial.

The changes between Firefox 3.6 and Firefox 4 were considerably higher than the changes between FF 4 and FF 5. So they might be updated sooner this time. Then, after 6 weeks...Firefox 6. :-)

---

### Post by inameiname on 2011-06-18
Agreed. Speed Dial is awful in comparison. You have to highly tweak it to just get it down to sort of resemble Fast Dial. Plus, I haven't quite figured out how to get full page images of the the pages on there, not just the top left little section.

55?! Wow, and here I thought I had quite a few! I think a total of 3-5 didn't work with Firefox 5.

Ah. Thanks for the clarification.

I just found it funny how 4 had barely came out before they decided to throw out 5 beta in the repos. Wayyyy too quick if you ask me. Previous releases had quite a few stages between whole number releases, like 3.1, 3.2, 3.3, and etc.

---

### Post by lovinglinux on 2011-06-18
> **inameiname said:**
> Agreed. Speed Dial is awful in comparison. You have to highly tweak it to just get it down to sort of resemble Fast Dial. Plus, I haven't quite figured out how to get full page images of the the pages on there, not just the top left little section.

I just corrected my previous post, I meant I prefer Fast Dial. I make names confusion all the time :-)

> **inameiname said:**
> 55?! Wow, and here I thought I had quite a few! I think a total of 3-5 didn't work with Firefox 5.

We both have a lot more add-ons than the average. Usually, people don't use so many add-ons. But I have seen people with more than 90. I do a lot of add-on testing so I am constantly disabling those I don't use frequently and enabling news ones. Too many add-ons means slow startup and more conflicts. 

> **inameiname said:**
> I just found it funny how 4 had barely came out before they decided to throw out 5 beta in the repos. Wayyyy too quick if you ask me. Previous releases had quite a few stages between whole number releases, like 3.1, 3.2, 3.3, and etc.

Until now Mozilla released a new major version when it was ready, with all the new features they wanted working properly. But since the release of FF 4, they decided to follow Google Chrome release model, in which new major versions are released more frequently and new features are disabled or removed if they are not ready by the time of release. The prediction is to have a new major version every 6 to 12 weeks. Firefox 7 is already being developed and after they release Firefox 5 in 3 days, won't take long to start developing Firefox 8.

The Ubuntu developers decided to add FF 5 to the repos because is not actually very different than FF 4 and Mozilla will no longer provide security updates for older versions like FF 3.6. So, Ubuntu developers had no choice but to upgrade to the latest stable version. They could upgrade to FF 4, since Natty already has it, but that would only delay the inevitable, so it makes sense to jump to FF 5.

---

### Post by 13east on 2011-06-19
> **lovinglinux said:**
> I just corrected my previous post, I meant I prefer Fast Dial. I make names confusion all the time :-)



We both have a lot more add-ons than the average. Usually, people don't use so many add-ons. But I have seen people with more than 90. I do a lot of add-on testing so I am constantly disabling those I don't use frequently and enabling news ones. Too many add-ons means slow startup and more conflicts. 



Until now Mozilla released a new major version when it was ready, with all the new features they wanted working properly. But since the release of FF 4, they decided to follow Google Chrome release model, in which new major versions are released more frequently and new features are disabled or removed if they are not ready by the time of release. The prediction is to have a new major version every 6 to 12 weeks. Firefox 7 is already being developed and after they release Firefox 5 in 3 days, won't take long to start developing Firefox 8.

The Ubuntu developers decided to add FF 5 to the repos because is not actually very different than FF 4 and Mozilla will no longer provide security updates for older versions like FF 3.6. So, Ubuntu developers had no choice but to upgrade to the latest stable version. They could upgrade to FF 4, since Natty already has it, but that would only delay the inevitable, so it makes sense to jump to FF 5.

Hi, I'm getting the same issues w/ fullscreen streaming videos as before that kept crashing my computer whenever flash video was sent to fullscreen.  Now, the glitch seems to happen all the time whenever the desktop effects is running under OpenGL but not Xrender.  This might be a problem since the latest kubuntu system update but I'm not too sure.  I'm having other problems w/ plasma desktop where folder-view layout and plasmoid cannot handle renaming files w/out crashing the desktop.  I thought the problem was emanating from me using proposed, unsupported, experimental and beta repositories so I scraped my installation and reinstalled kubuntu but the problems persist.

Is there any way to fix these issues?

---

### Post by inameiname on 2011-06-20
> 
I just corrected my previous post, I meant I prefer Fast Dial. I make names confusion all the time :smile:


I assumed you meant Fast Dial anyway, so no worries.

> 
We both have a lot more add-ons than the average. Usually, people don't  use so many add-ons. But I have seen people with more than 90. I do a  lot of add-on testing so I am constantly disabling those I don't use  frequently and enabling news ones. Too many add-ons means slow startup  and more conflicts. 


Ah. Ever since I first switched to Firefox from Opera (the first tab browser), I found addons essential, and before I knew anything about Linux and Live CDs, I loved being able to throw on a flash drive and run a heavy addoned Firefox for whatever I need. It is also probably these addons that keep me with Firefox over Google Chrome/Chromium. Their selection just isn't the same. At least yet.

> 
Until now Mozilla released a new major version when it was ready, with  all the new features they wanted working properly. But since the release  of FF 4, they decided to follow Google Chrome release model, in which  new major versions are released more frequently and new features are  disabled or removed if they are not ready by the time of release. The  prediction is to have a new major version every 6 to 12 weeks. Firefox 7  is already being developed and after they release Firefox 5 in 3 days,  won't take long to start developing Firefox 8.

The Ubuntu developers decided to add FF 5 to the repos because is not  actually very different than FF 4 and Mozilla will no longer provide  security updates for older versions like FF 3.6. So, Ubuntu developers  had no choice but to upgrade to the latest stable version. They could  upgrade to FF 4, since Natty already has it, but that would only delay  the inevitable, so it makes sense to jump to FF 5. 	


I appreciate the info. Its all news to me, but makes sense now.

---

### Post by iX9 on 2011-06-20
Hi!
I just considering return back to FF4, because v5 is breaking my history - file "places.sqlite.corrupt" appears in profile and history is gone...
Happend this behavior to anyone?

---

### Post by inameiname on 2011-06-20
No, I'm afraid I haven't had that issue before. But then again, I never keep history in my browser, and often run Bleachbit, which cleans up Firefox and vacuums 'places.splite', among many other things.

---

### Post by lovinglinux on 2011-06-20
> **iX9 said:**
> Hi!
I just considering return back to FF4, because v5 is breaking my history - file "places.sqlite.corrupt" appears in profile and history is gone...
Happend this behavior to anyone?

You could try this:

[LIST]
[*]return to Firefox 4
[*]export your bookmarks from the Bookmark Manager
[*]make a backup of places.sqlite and delete it
[*]upgrade to FF 5 and import your bookmarks
[/LIST]

See if that helps. If something goes wrong, restore your places.sqlite file.

---

