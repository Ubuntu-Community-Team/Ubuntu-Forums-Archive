---
title: "Firefox won't open external links"
date: 2011-05-11
forum: General Help
---

### Post by miesogeno on 2011-05-11
its more weird than the title suggests.

when I click an external link, it opens a NEW Firefox window, instead of opening a new tab in a ALREADY OPEN Firefox instance, and worst of all, IT STAYS IN THE HOMEPAGE, not going to wherever it was supposed to.

this is bad, and it renders useless some software functions, like Gmail Notifier, when I click to go to my account.

if I set Chromium as default browser, it works like a charm. I believe this is happening since Natty upgrade. and I'm using Firefox 4.

any ideas?

---

### Post by trozamon on 2011-05-11
Go to firefox preferences and make it open links in a new tab.

---

### Post by miesogeno on 2011-05-11
thats already checked, I think its a bit more complicated than that :D but thanks for your help.

like I said, even opening in a new window, it doesn't get past my homepage. it doesn't go to where the link was intended to.

---

### Post by miesogeno on 2011-05-12
anyone? this is getting really anoying, I have to copy every link to the adressbar instead of clicking it.

---

### Post by Gingalone on 2011-06-22
I have just the same problem and it started after upgrading Ubuntu to Natty...

What about?????:confused:

---

### Post by pqwoerituytrueiwoq on 2011-06-22
is this just on one site or all?
if just one can we get a link

---

### Post by Gingalone on 2011-06-23
> is this just on one site or all?

any link to any site!
I tried to edit my Firefox profile (or to create a new one) with ```
firefox -P
```
but even in this case I got a new Firefox window with my homepage open!!!

Is that a bug?

---

### Post by miesogeno on 2011-06-23
if you want to know, the problem only went away with a fresh install of Natty.

believe me, I tried everything I could think of before doing that.

good luck!

---

### Post by Gingalone on 2011-06-23
> **miesogeno said:**
> if you want to know, the problem only went away with a fresh install of Natty.


I would prefer not to.
I set Chrome as default browser, so Chrome opens on the right site when I click an external link and use Firefox for normal web navigation with all my bookmarks and everything.
And I am pretty happy on this "hybrid" solution!

(But I really would like to know what went wrong with my Firefox and why!)

---

### Post by miesogeno on 2011-06-23
as long as you're happy with that.

I realized chrome worked, but at a given time it was very strange having two different browsers open simultaneously for the same purpose.

---

### Post by leetlover on 2011-08-03
I'm experiencing the same issue, soon after updating to Natty. I ran gconf-editor and checked the url-handler for http and https and it appears to be broken. It's just "firefox" instead of "firefox %s". I changed that, but still doesn't work. It's weird how it's only affecting firefox, but not any other browser. Every link you try to open from any application will result in a new firefox window being spawned with the startpage (in my case, blank).

---

### Post by leetlover on 2011-08-07
OK, after doing some stracing on xdg-open and gvfs-open, I finally fixed the issue.
The firefox.desktop file in your ~/.local/share/applications/ folder is using a wrong **Exec** value. In my case, it was missing a %U (the url to open I assume). So just change the Exec param from **Exec=firefox** to **Exec=firefox %U** and it should fix it.

---

### Post by craig.o on 2012-01-30
> **leetlover said:**
> ...change the Exec param from **Exec=firefox** to **Exec=firefox %U** and it should fix it.

Leet, thanks.  I can confirm this solved my system's problem (oneric 11.10 32-bit & Moz rolling stable).

-C

---

### Post by phubert28 on 2012-04-24
Well, this won't be of any help. I've been trying to trace the same problem after a reinstall of Firefox 11.0.

Actually, I had to remove it AND my .mozilla directory to fix something corrupted in my profile. Firefox had been using excessive CPU and RAM and finally simply began to hang every time I opened it, even with no tabs at all!

Anyway, I FIXED my Firefox issues and now the Thunderbird links don't open properly as described above. Running 64 bit 11.04.

**

oops, I was reading the thread in the wrong order!!! Mea culpa!

Turned out in MY ~/.local/share/applications folder, I had an entry for Firefox Safe Mode. Deleted it, and all is well!!!!

---

### Post by techsupport on 2012-04-24
> **phubert28 said:**
> Well, this won't be of any help. I've been trying to trace the same problem after a reinstall of Firefox 11.0.

Actually, I had to remove it AND my .mozilla directory to fix something corrupted in my profile. Firefox had been using excessive CPU and RAM and finally simply began to hang every time I opened it, even with no tabs at all!

Anyway, I FIXED my Firefox issues and now the Thunderbird links don't open properly as described above. Running 64 bit 11.04.

**

oops, I was reading the thread in the wrong order!!! Mea culpa!

Turned out in MY ~/.local/share/applications folder, I had an entry for Firefox Safe Mode. Deleted it, and all is well!!!!

Have you installed the Stable Firefox PPA to update Firefox? Maybe they have an update. I can't replicate your issue on my updated version of Firefox here.

---

### Post by phubert28 on 2012-04-24
Well, yes, I HAVE the PPA - BUT - apparently when I completely REMOVED, deleted my .mozilla directory, and reinstalled, I wound up back on 11.0! Hmmmmm. Have to do an update, I guess!

Thanks for the heads-up!

Since I UPGRADED 10.04 to 10.10, Update Manger and Software Center cannot INSTALL. Another problem with MY profile, perhaps??

I'm STILL a novice. I tried sudo apt-get update and only got recognized updates.

Update Manager doesn't SEE any for Firefox perhaps because I was already at the latest version?

So "completely remove" didn't remove any indicator Update Manager interrogates to FIND FF updates??

***

FF 12 is out, I can wait for that since my problem has been resolved.

Unfortunately, in the process of working toward a solution, I came across some advice to add two network.protocol-handler.expose.foo entries to about:config and now I have to see how I can DELETE the two entries!

O.K. finally looked into Software Sources and found NO PPA  for FF - I KNOW I had one!!! - will get it in again and check for updates once more!

---

### Post by techsupport on 2012-04-24
I'm not going to say your system is borked, because it really isn't borked. But it is getting close to being borked. If you can't install, and you can't update, and you can't even use your browser anymore the right way, my suggestion would be to maybe save yourself some time and simply do a fresh install. There are kind users here that may or may not help guide you through the process of fixing everything. But as I see your situation, at least for now you can backup your stuff and move it to somewhere else like an external device.  Build yourself a nice USB Flash Drive with Ubuntu 12.04 LTS Live on it, boot your computer from that USB Thumb Drive,  and repartition and reformat your hard drive. Wipe it clean.

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

You'll probably be back in business faster than trying to fix whatever is wrong, in my own experience with novices. If you were a little more familar with Ubuntu it might make more sense to wait it out for somebody here to walk you through a repair process to fix all of these problems you are experiencing. 

Try the guide.  Give it a try. Backup everything you got. But I will also tell you this much, if you keep messing around with a system and you don't know what you are doing or even what is wrong, and you might not be able to backup everything you have anymore either. Tick tick tick.

Oh and there is always the alternative:

[http://www.ubuntu.com/business/services/overview](http://www.ubuntu.com/business/services/overview)

---

### Post by phubert28 on 2012-04-24
Got the PPA back in and am now on FF 12.0.

Of course I can update with Synaptic and from terminal.

I REALLY don't like Unity, so I'm waiting for Mint 12 to be declared ready for general use, then I plan to install that on my 2nd hard drive and see what's next.

I'd already fixed my problems with FF 11.0 - but I plan to check about:config to see if the two errant entries remain after the upgrade to 12 - if so, I'll have to edit .profile.js, I think.

**

I'm also not happy that Canonical is dropping support for Kubuntu (even though I'm not using it) ... generally unhappy with the direction Canonical is headed in. But Mint IS Ubuntu, is it not?? Just a different approach to the UI.

---

### Post by techsupport on 2012-04-24
> **phubert28 said:**
> Got the PPA back in and am now on FF 12.0.

Of course I can update with Synaptic and from terminal.

I REALLY don't like Unity, so I'm waiting for Mint 12 to be declared ready for general use, then I plan to install that on my 2nd hard drive and see what's next.

I'd already fixed my problems with FF 11.0 - but I plan to check about:config to see if the two errant entries remain after the upgrade to 12 - if so, I'll have to edit .profile.js, I think.

I'm using the Ubuntu Classic Fallback DE session in Ubuntu 12.04 LTS Beta 2 and I have to say, with the gnome-tweak-tool and the fact that I can now add better themes, I'm happy again with Ubuntu. I don't use Unity at all. It is too intrusive when you need more real estate on your desktop to work with i.e. programming or graphic design.  It is great for tablets and mini screens though, so I see how it could make a great tablet OS to compete with Apple's iOS.

---

### Post by phubert28 on 2012-04-24
Yes, that's my problem with Unity, as well. I LOATHE Windows 7 and can't imagine why any provider would go in that direction.

However, my 11.04 has some video problems using classic (I'm running an Nvidia GEForce something on a Dell Optiplex 360, dual 1920x1200 24" monitors), so I figured ALL classic fallbacks are likely not to work well for me.

---

### Post by phubert28 on 2012-04-24
Are most of the vendors trying to do a "one size fits all" with emphasis on tablets & phones?????

I am unlikely to use a tablet and VERY unlikely to do that much with my phone!

To me, it looks like Mint is the way to go.

I don't want to be caught at the whim (or philosophy) of Canonical in this.

---

### Post by techsupport on 2012-04-24
> **phubert28 said:**
> Are most of the vendors trying to do a "one size fits all" with emphasis on tablets & phones?????

I am unlikely to use a tablet and VERY unlikely to do that much with my phone!

To me, it looks like Mint is the way to go.

I just can't stand how they brand their version of Firefox. The search results look and feel different to me when I use Firefox in Mint. I can't even find stuff I use with Google daily anymore, like I do in Ubuntu's Firefox. Weird, I know, but that was my experience with Mint. It is a big deal to me because I am constantly using Google for searching information.  I don't even think the image results look the same. Mint's branded browser just ruins the whole Google feel for me. I think there is a whole web site dedicated to helping Mint users try to somehow remove whatever Mint did to brand Firefox too. It is a real headache, and I wasn't able to remove the branding.  I gave up on Mint that day. lol

---

### Post by phubert28 on 2012-04-24
(shaking head)

Well, it's always good to talk with others... (sigh)

I guess I'll take a stab at it, anyway.

Yeah, I like my Google, plain and simple.

Can't ANYONE just LEAVE THINGS ALONE????

(1) interface should be simple
(2) BUT highly and easily configurable

I know that under the hood this ISN'T QUITE so simple.

Gawd, I loved the green screen (NON-IBM 3270) days.

I wrote my own interfaces and tools then!

---

### Post by phubert28 on 2012-04-24
So, next I consider Kubuntu 12.04?????

---

### Post by techsupport on 2012-04-24
> **phubert28 said:**
> (shaking head)

Well, it's always good to talk with others... (sigh)

I guess I'll take a stab at it, anyway.

Yeah, I like my Google, plain and simple.

Can't ANYONE just LEAVE THINGS ALONE????

(1) interface should be simple
(2) BUT highly and easily configurable

I know that under the hood this ISN'T QUITE so simple.

Gawd, I loved the green screen (NON-IBM 3270) days.

I wrote my own interfaces and tools then!

Mint would be perfect if they didn't brand their Firefox browser. At least in Ubuntu and Firefox there isn't anything getting the way of me doing what I would do on any other operating system, like windows or mac.  I understand that Mint has to make money by branding Firefox browser, but I can think of several better ways for them to make money from Mint, like paid support.

Until they can figure that out, I'm just going to avoid recommending Mint because of the Firefox Branding situation.

---

### Post by phubert28 on 2012-04-24
I even donated to them without having tried it yet (and, of course, to LibreOffice which I DO use).

---

### Post by techsupport on 2012-04-24
> **phubert28 said:**
> I even donated to them without having tried it yet (and, of course, to LibreOffice which I DO use).

Stick with Ubuntu 12.04. I use the Ubuntu Fallback desktop environment. It's awesome! 

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

Cheers

:guitar:

---

### Post by phubert28 on 2012-04-24
Thanks for the link, but the fallback looks as bad as Unity - or perhaps worse!

I like tiny icons on a launcher strip! Classic on 11.04 is fine. So, nothing like this for 12.04???????

---

### Post by pqwoerituytrueiwoq on 2012-04-24
> **techsupport said:**
> I just can't stand how they brand their version of Firefox. The search results look and feel different to me when I use Firefox in Mint. I can't even find stuff I use with Google daily anymore, like I do in Ubuntu's Firefox. Weird, I know, but that was my experience with Mint. It is a big deal to me because I am constantly using Google for searching information.  I don't even think the image results look the same. Mint's branded browser just ruins the whole Google feel for me. I think there is a whole web site dedicated to helping Mint users try to somehow remove whatever Mint did to brand Firefox too. It is a real headache, and I wasn't able to remove the branding.  I gave up on Mint that day. lol
just disable stylish (or a pre installed style) and download firefox from mozilla open ythe archive and copy the searchplugins folder to ~/.mozilla/firefox/*.default (help->trouble shooting information ->open folder)

---

### Post by tomdkat on 2012-05-10
> **leetlover said:**
> OK, after doing some stracing on xdg-open and gvfs-open, I finally fixed the issue.
The firefox.desktop file in your ~/.local/share/applications/ folder is using a wrong **Exec** value. In my case, it was missing a %U (the url to open I assume). So just change the Exec param from **Exec=firefox** to **Exec=firefox %U** and it should fix it.
Thanks for posting this!  This solved my problem!  :guitar:

Peace...

---

### Post by jrioublanc on 2012-06-05
> **leetlover said:**
> OK, after doing some stracing on xdg-open and gvfs-open, I finally fixed the issue.
The firefox.desktop file in your ~/.local/share/applications/ folder is using a wrong **Exec** value. In my case, it was missing a %U (the url to open I assume). So just change the Exec param from **Exec=firefox** to **Exec=firefox %U** and it should fix it.

Thanks, it helped me too, actually I had to update the firefox-3.5.desktop file. This is the one called when clicking on external link.

Great job - was painful to copy/paste links....

---

