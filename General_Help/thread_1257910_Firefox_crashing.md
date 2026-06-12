---
title: "Firefox crashing"
date: 2009-09-04
forum: General Help
---

### Post by SISU1375 on 2009-09-04
I know I shouldn't be repeating a message, but my Firefox keeps crashing, and it seems to randomly crash on different sites.  I always have to go back to boot it all back up to continue.  HELP!!!

---

### Post by mike555 on 2009-09-04
does it only crash when trying to get a full screen ? like on hulu.com?

---

### Post by SISU1375 on 2009-09-04
It crashes when:      I pull up the Barnes and Noble website, it shows the website, and then when the loading icon stops, it crashes.  I have no more front and back arrows to navigate, my toolbar doesn't show, and the Yahoo site works.  If try to restore the session, it doesn't bring me back to where I started.  Is the Firefox corrupted?

---

### Post by SISU1375 on 2009-09-04
PS...I'm doing this all off the first entry into the Firefox browser opening

---

### Post by StuartN on 2009-09-04
> **SISU1375 said:**
> my Firefox keeps crashing

I have Firefox 3.0.13 at present and the same problem - Firefox occasionally crashes without warning or error message, sometimes several times in a row, but not repeatably. It has been happening since the first 3.0 release.

---

### Post by ackanao on 2009-09-04
Start Firefox in Safe Mode - if everything looks OK. then the problem is with your Add-ons or plugins:

```
firefox -safe-mode
```

Check "Disable all add-ons" and then select "Make Changes and Restart".

---

### Post by SISU1375 on 2009-09-04
How do I start Firefox in the safe mode?  I did add some media plug ins last night

---

### Post by darco on 2009-09-04
you need to type the command above in a terminal .....

darco

---

### Post by |Porsche on 2009-09-04
You can also just start firefox from a terminal by typing 
```
firefox
```

when firefox crashes you will be left with the terminal and some clues as to why it crashed.

---

### Post by SISU1375 on 2009-09-04
[SIZE=4]I looks like it's just the Barnes & Noble site(?)[/SIZE]  [SIZE=4]However, I still can't bookmark sites...Can you help me so I can set  bookmarks & get my navigation tabs back?
[/SIZE]

---

### Post by lovinglinux on 2009-09-05
> **SISU1375 said:**
> [SIZE=4]I looks like it's just the Barnes & Noble site(?)[/SIZE]  [SIZE=4]However, I still can't bookmark sites...Can you help me so I can set  bookmarks & get my navigation tabs back?
[/SIZE]

It's probably a javascript or flash add crashing it. Install [NoScript](https://addons.mozilla.org/en-US/firefox/addon/722) and [AdBlock](https://addons.mozilla.org/en-US/firefox/addon/1865) Plus, to block the junk.

About the bookmarks, I have already posted the solution on your other thread.

---

### Post by dunkirk on 2009-09-05
I've had trouble since I started using Jaunty on my netbook. Same thing: sometimes the browser crashes, and there's no consistency. I've tried removing flash and using javascript blockers and disabling add-ons: nothing works. ALL browsers crash, not just Firefox. Even binary versions I download. I've even run Firefox from gdb, and there's just NO useful information dumped on a crash.

Something deeper than the browser is causing this problem.

I decided to try to look for an answer again, and it's clear that it's not my imagination. Other people are having the problem, and it's severely annoying. But it's also clear that it's not very widespread. Otherwise, it would get fixed.

I wonder if we're all on netbooks running UNR?

What I can't stand in all of this is the way people BLAME A WEB SITE. That's like blaming a program for causing a kernel panic. Like a kernel, a web browser ought to compartmentalize the web site. Any problems ought to make the page stop loading. It shouldn't crash the browser, let alone kill your session and leave you at the login screen. Heck, I even saw one exchange where someone blamed an animated GIF, and said there was nothing to fix with Firefox. Excuse me?! If a "bad" animated GIF crashes a browser, you've got a problem with the BROWSER, NOT THE GIF.

Anyway. Now that I got that off my chest, I guess I'm just waiting on the next version of UNR. Maybe it will magically fix whatever's wrong in the bowels of Ubuntu.

---

### Post by ackanao on 2009-09-05
Some users reported that the problem was with Safe Browsing feature of Firefox - Disable "Block reported attack sites" and "Block reported web forgeries" options and see if problem still exists.

Also, maybe you need to "preload" Flash plugin - that is, if Flash is the culprit.

---

### Post by amoose on 2009-09-06
I will echo what dunkirk said.  My whole notebook freezes - not just the browser, and this is happening with all of the browsers I've tried:  firefox, seamonkey, epiphany, and opera.  A site will cause the crash one time but not another.  I don't believe it's a flash problem as sites without flash - I think... - have caused the problem: my gmail inbox, for example.  On the other hand, there's sites with a ton of flash content which have never caused the problem.  I'm running 8.10 on a Dell D630.  I have NVIDIA.  I've installed both no script and ad block plus on firefox - to absolutely no effect.

---

### Post by StuartN on 2009-09-08
I can not replicate this crash every time, but it seems to me that it occurs more often if the history pane is open. Perhaps it has something to do with the sqlite database.

---

### Post by lovinglinux on 2009-09-08
> **StuartN said:**
> I can not replicate this crash every time, but it seems to me that it occurs more often if the history pane is open. Perhaps it has something to do with the sqlite database.

It could be. In this case, deleting the file places.sqlite from your profile should fix the problem (back it up first). It could also be that you have some extensions that are constantly accessing the places.sqlite database, where bookmarks, history and other stuff are stored. As a general rule, I always keep the history and bookmarks sidebar closed to avoid this type of problem.

---

### Post by StuartN on 2009-09-08
> **lovinglinux said:**
> It could also be that you have some extensions that are constantly accessing the places.sqlite database

The only extension that I have added is flashplugin-nonfree, but Ubuntu seems to add a few others. I don't expect any are querying sqlite.

> **lovinglinux said:**
> As a general rule, I always keep the history and bookmarks sidebar closed to avoid this type of problem.

That is a serious shortcoming of the software! I like my site & date ordered history.

---

### Post by lovinglinux on 2009-09-09
> **StuartN said:**
> The only extension that I have added is flashplugin-nonfree, but Ubuntu seems to add a few others. I don't expect any are querying sqlite.
That is a serious shortcoming of the software! I like my site & date ordered history.

Actually, I was exaggerating a little bit :)

What happen is that when you launch an extension sidebar, it will probably initiate some functions automatically. Those that access the places.sqlite database or any other database can be a little bit slower. But this usually happens only when you open the sidebar for a particular extension. Nevertheless, some extensions observes certain changes in other areas of the browser and launch it's functions when necessary. For instance, I have the extension TagSifter, which deals with lots of bookmark tags. Whenever I open the Add-ons sidebar (the one that lists all extensions installed), TagSifter initiate some sort of processing and slows down the process of displaying all installed extensions. Usually this is not an issue for regular browsing, but could slow down Firefox start up if you close and start Firefox with the sidebar open.

Anyway, I don't believe its your case.

---

### Post by StuartN on 2009-09-11
> **lovinglinux said:**
> As a general rule, I always keep the history and bookmarks sidebar closed to avoid this type of problem.

Yup, I have been mentally noting my use of the sidebar and Firefox only crashes if the history sidebar is open or has been opened earlier in the session. I don't use the bookmarks sidebar, and the bookmarks menu does not seem to cause a phut.

As with the earlier posters, Firefox is literally present one minute, then phut it vanishes, with no warning and no error message.

---

### Post by Darktrax on 2009-09-12
Duh - Normally I hate having to do the "me too" thing, but this is a seriously irritating bug.

Maybe we will have to start comparing Add-Ons lists to see if there is a common combination associated with the trouble.

Things I have noticed are..
1. Its definitely with us on Firefox3.
   It was also there just before the latest update 3.0.14.
2. This kind of quit does not leave a terminal open.
3. I have in the past had a "partial quit" where the attempt to restart is denied.
   That needed a hard kill of the running Firefox executable by  using the System
   Monitor tool. This random quit action is of a different nature
4. The re-start does recognise the stoppage was unexpected, and will allow to restore
   the tabs that were open.
5  If you just walk away from it for long enough, like 30 minutes, then it usually
   has quit.
6. There may be an association with having open Google's Gmail (a webmail application).
7. There may be an association with using  NoScript. I normally allow any site
   script, but deny the snooping scripts.
8. I happen to be using the 8.10 LTS. We who suffer this should compare versions.

PS. It drove me to try out Ephiphany, and Konqueror, and even Dillo! Epiphany seems to do most things, and faster.

---

### Post by StuartN on 2009-09-12
> **Darktrax said:**
> 4. The re-start does recognise the stoppage was unexpected, and will allow to restore the tabs that were open.
6. There may be an association with having open Google's Gmail (a webmail application).
7. There may be an association with using  NoScript. I normally allow any site script, but deny the snooping scripts.


Ditto everything except 6 & 7 - I have only one extension, flashplugin-nonfree, and don't use most of the websites mentioned, although I also feel that crashes are linked to some websites I use (e.g. RTE News but not BBC News). It is interesting that Firefox recognizes an unexpected halt and offers to resume the session, but has generated no error message or log entry. And ditto the Epiphany in parallel, pity it can't share the bookmarks...

I am on 8.10, but 8.04 had the same annoyance.

---

### Post by Darktrax on 2009-09-12
> **StuartN said:**
> 
I am on 8.10, but 8.04 had the same annoyance.

OK - I now have discovered at least one mechanism that makes it do this every time.
When I left-click on a PDF document icon on a certain site (farnell.co.uk), it crashes in the attempt to invoke the Firefox choice of default pdf viewer. The way these are started depend on the site, and the javascript. In this case, I can right-click->download, but not left-click->display in a pdf viewer. 

If I try the dodge of opening in a new tab, the expected behaviour is the tab stays empty, and the default pdf viewer displays it.

I am still trying out the options - disabling add-ons testing, etc. When I know, I will post.

If you happen to run NoScript control, try disabling it temporarily.

If you have protection from those 1 x 1 pixel GIFs that set those permanent "Super-Cookies", try a temporary disable.

If you run the TACO (Targeted Advertising Cookie Opt-Out) Try a temporary disable.

The Ubuntu Firefox Modifications present or otherwise, seems to make no difference.

---

### Post by UKBB on 2009-09-12
> **Darktrax said:**
> 
6. There may be an association with having open Google's Gmail (a webmail application).

For me it is Yahoo email that seems to bugger it up.

---

### Post by Darktrax on 2009-09-12
> **UKBB said:**
> For me it is Yahoo email that seems to bugger it up.

OK - we now have something a developer can get a grip on. It may not be the whole fix, but I suspect if this particular example gets sorted out, the other crashes might well either go away, or the basic common factor becomes clearer.

1. Firefox crashes in this way, irrespective of Add-Ons. It does it with or without them. I ran it with all of them disabled.

2. This site.. [http://www.neltron.com.tw/](http://www.neltron.com.tw/)
..crashes my Firefox in exactly the fashion you guys are experiencing. Only, it does it every time without fail. I had to use Epiphany browser to copy the URL, because I was trying to open it from a Google Link. TAKE CARE now. I did not make it a link, but the system seems to have automatically created one. Don't just click on it until you are good and ready for the Firefox re-spin act. So OK - I am betting that loads of you might make it open without a problem. So some bugs can be bitches like that. :|

3. The random nature of the thing is because it is related to scripts running (I think)
   When I have Google's Gmail web mail open, the crash keeps dogging me all the time.
   I would expect Yahoo and similar would be as bad or worse.

4. This happens even on a clean install on a new partition.

I can't think of any more to do. I have not worked the byzantian bug-reporting system yet, but maybe someone in Ubuntu developer-land is watching..
G

---

### Post by lovinglinux on 2009-09-13
> **Darktrax said:**
> 2. This site.. [http://www.neltron.com.tw/](http://www.neltron.com.tw/)
..crashes my Firefox in exactly the fashion you guys are experiencing. Only, it does it every time without fail. 

Works perfectly for me, on FF 3.5. No crash, even with NoScript and Adblock Plus disabled.

---

### Post by Darktrax on 2009-09-13
> **lovinglinux said:**
> Works perfectly for me, on FF 3.5. No crash, even with NoScript and Adblock Plus disabled.

I knew this would happen. Just because I find one thing that crashes it ... is not enough reason to say "Ahh! - That must be it! "

As it happens, my Firefox crashed out in the act of clicking on the "quote" button on your post. It seemed to do a re-draw first, then "went out to lunch".

I should make it clear that I had been testing ***without*** any Add-Ons. That link crashed my Firefox, whether Add-Ons were there or not. I am very wary of the way that URL works as a link in this forum, and I am not at all sure we should post it in the quote.
In my case, if the page is open in a new tab, and crashes, then all subsequent restores of Firefox are doomed, unless we start afresh with no tabs.

Also - there are differences in our installations. You have 9.04 Jaunty, and Firefox 3.5.
I have 8.10 Intrepid LTS (Long Term Support), and it updates Firefox to version 3.0.14

This is getting complicated, but from now on, those who report this "swift & silent FF crash" phenomenon, should post their Ubuntu and Firefox versions. I will have a scan up the previous posts to see if I can see a common factor. Also, to maybe eliminate a red herring, I will get at the example page via another browser, and start selectively knobbling a copy. There ***must*** be something we can do - short of a total re-install + hope.
PS. Plug-ins are not the same as Add-Ons. If yours crashes, mention what plug-ins you have.

---

### Post by lovinglinux on 2009-09-13
> **Darktrax said:**
> I knew this would happen. Just because I find one thing that crashes it ... is not enough reason to say "Ahh! - That must be it! "

As it happens, my Firefox crashed out in the act of clicking on the "quote" button on your post. It seemed to do a re-draw first, then "went out to lunch".

I should make it clear that I had been testing ***without*** any Add-Ons. That link crashed my Firefox, whether Add-Ons were there or not. I am very wary of the way that URL works as a link in this forum, and I am not at all sure we should post it in the quote.
In my case, if the page is open in a new tab, and crashes, then all subsequent restores of Firefox are doomed, unless we start afresh with no tabs.

Also - there are differences in our installations. You have 9.04 Jaunty, and Firefox 3.5.
I have 8.10 Intrepid LTS (Long Term Support), and it updates Firefox to version 3.0.14

This is getting complicated, but from now on, those who report this "swift & silent FF crash" phenomenon, should post their Ubuntu and Firefox versions. I will have a scan up the previous posts to see if I can see a common factor. Also, to maybe eliminate a red herring, I will get at the example page via another browser, and start selectively knobbling a copy. There ***must*** be something we can do - short of a total re-install + hope.
PS. Plug-ins are not the same as Add-Ons. If yours crashes, mention what plug-ins you have.

Check if you have **libflashsupport** or **flashplugin-nonfree-extrasound** package installed and remove it. They are known to be a FF crashers. I don't remember which one is available for Intrepid, but I guess is **libflashsupport**. BTW, Intrepid is not LTS. The current LTS version is 8.04 Hardy Heron. So which one do you have?

I have a notebook with Intrepid and FF 3.0.14. I will test it soon.

---

### Post by Shea7993 on 2009-09-13
I had similar issues... Firefox crashing on me when id go to random sites, or following links, ff would crash after 3rd or 4th link, forced me to restart ff, and sumtimes even have to reboot... then i went over to another ff maintained group for firefox 3.5, to get updates from them aswell as the newer later and beta releases of ff... the result? beter than canonicals ff, but still same issues freaquently every now and then... So i switched to chromium browser, and no issues at all (except for the whole flash bug that causes it to crash if you enable it) and then recently i discovered Opera 10 browser, and to be quite frank, its excellent, I have no issues with it after this past week using it, not one hickup this far... just thought id share my 2cents with you all

---

### Post by Darktrax on 2009-09-14
> **lovinglinux said:**
> Check if you have **libflashsupport** or **flashplugin-nonfree-extrasound** package installed and remove it. They are known to be a FF crashers. I don't remember which one is available for Intrepid, but I guess is **libflashsupport**. BTW, Intrepid is not LTS. The current LTS version is 8.04 Hardy Heron. So which one do you have?

I have a notebook with Intrepid and FF 3.0.14. I will test it soon.

OK - sorry about that.
I started out with 8.04LTS. Then at some stage, the UPDATE procedure was invoked to inadvertently move it on to 8.10, with some rework of the Xorg forced.

The present arrangement is just unstable with **Firefox**, and I don't have oodles of life here to be chasing it all the time. The present setup is running a lot of stuff quite hard 24/7. To go experimenting with the latest new bugset is not what I need.

For the present, I am discovering that **Epiphany** (strange name !? ) is way better than I thought. It seems to do it all. I have not figured how to add features, but it does do Adblocker, Flash, Youtube, Applets, etc.

I am also shocked at the sheer speed of **Dillo**. It is crudely basic - no bells and whistles at all, but it snaps along in a blink!
G

---

### Post by StuartN on 2009-10-17
> **StuartN said:**
> That is a serious shortcoming of the software! I like my site & date ordered history.

Well four weeks on and studiously avoiding any use of the history sidebar, and not a single crash.

---

