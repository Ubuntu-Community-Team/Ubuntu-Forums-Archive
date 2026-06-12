---
title: "Black YouTube Video with Sound"
date: 2011-10-22
forum: General Help
---

### Post by Joseph Schwenker on 2011-10-22
I've been having a problem in Google Chrome with YouTube and Adobe Flash. Hardware acceleration in Flash is disabled, but for some reason, when I try loading videos on YouTube, they'll sometimes load with only sound and a black rectangle where the player is supposed to be. The only way to fix the problem is to refresh the page, which sometimes takes several times (most it's ever taken is four). I've cleared my cache and cookies twice, but the problem hasn't gone away. I'm on Ubuntu 11.04 32-bit with Google Chrome 14.0.835.202 and Adobe Flash 11.0.1.152.

---

### Post by Tikidel on 2011-10-24
I also have this problem. It is present in 11.04 in both 32 and 64-bit versions. I don't have this problem in Firefox or in 11.10 though. If I change to another tab and back whatever is displayed on the other tab will be displayed in place of the black box.

---

### Post by oldtimer7777 on 2011-10-24
> **Tikidel said:**
> I also have this problem. It is present in 11.04 in both 32 and 64-bit versions. I don't have this problem in Firefox or in 11.10 though. If I change to another tab and back whatever is displayed on the other tab will be displayed in place of the black box.

I had this problem until I installed it from the PPA:

wget -q -O - [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) | sudo apt-key add - 
sudo sh -c 'echo "deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main" >> /etc/apt/sources.list.d/google.list' 
sudo apt-get update 
sudo apt-get install google-chrome-stable

---

### Post by Joseph Schwenker on 2011-10-24
Tikidel - That's the same for me. I'll try the solution posted above and see if that fixes things.

---

### Post by Tikidel on 2011-10-25
Didn't help. :(

Some more information about what I'm running in case it helps:
Ubuntu 11.04 64-bit
Linux 2.6.38-12
Google Chrome 15.0.874.106
Flash 11.0.1

---

### Post by oldtimer7777 on 2011-10-27
> **Tikidel said:**
> I also have this problem. It is present in 11.04 in both 32 and 64-bit versions. I don't have this problem in Firefox or in 11.10 though. If I change to another tab and back whatever is displayed on the other tab will be displayed in place of the black box.

Have you guys added the update PPA for Google Chrome? 

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

It is about half the way down that list so you can add them. 

Then update all your browsers and Adobe flash packages.

---

### Post by Joseph Schwenker on 2011-10-27
> **oldtimer7777 said:**
> Have you guys added the update PPA for Google Chrome? 

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

It is about half the way down that list so you can add them. 

Then update all your browsers and Adobe flash packages.

I already have the official Google Chrome PPA in my Software Sources from when I first installed Chrome. Also, Chrome automatically updates Flash, so there's no need to update any Flash packages.

---

### Post by oldtimer7777 on 2011-10-27
> **Joseph Schwenker said:**
> I already have the official Google Chrome PPA in my Software Sources from when I first installed Chrome. Also, Chrome automatically updates Flash, so there's no need to update any Flash packages.

Did you install the Beta Version of Google Chrome from the above list yet?

Chromium uses the same flash that Mozilla uses to open flash videos.  But Chrome uses it's own flash plugin that comes with the Chrome package..

---

### Post by Joseph Schwenker on 2011-10-27
> **oldtimer7777 said:**
> Did you install the Beta Version of Google Chrome from the above list yet?

No. However, I looked at that article, and the command to install the beta version is the same that oldtimer7777 posted. In other words, it's the same command that didn't solve the issue for Tikidel.

---

### Post by gandaran on 2011-10-27
> **Tikidel said:**
> Didn't help. :(

Some more information about what I'm running in case it helps:
Ubuntu 11.04 64-bit
Linux 2.6.38-12
Google Chrome 15.0.874.106
Flash 11.0.1
for 64-bits google-chrome you need to install 64-bits adobe flash (only the 32-bits version has built in flash) install the [flash-aid addon]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") in firefox to remove the 32-bits flash and install 64-bits flash to the system for all browsers.

---

### Post by Tikidel on 2011-10-28
I've tried updating flash using flash-aid and using the beta version of Google Chrome but neither of these helped. :(

---

### Post by houseworkshy on 2011-11-02
Not a fix but in the short term while working it out you can watch youtube by installing firefox and then "flashplugin-nonfree" from the repositories via synaptic.

---

### Post by Joseph Schwenker on 2011-11-02
> **houseworkshy said:**
> Not a fix but in the short term while working it out you can watch youtube by installing firefox and then "flashplugin-nonfree" from the repositories via synaptic.

Thanks for your suggestion, but refreshing the page a few times as necessary fixes the problem, though more refreshes will be necessary when the problem inevitably appears again.

---

### Post by houseworkshy on 2011-11-02
Still not fixing it but a wild idea which could be the result of tiny bits of knowlage being misleading.  I've only tried chrome and chromium for a few minets each then got rid of them, just because they wern't to my taste, I'm not slamming them.  One of the selling features was that they were fast, this was due to preloading.  Bit of knowlage one.

I watch films on youtube using firefox, abrowser or seamonkey; the mozzila stuff is to my taste.  These films are often in several parts and because I hate watching several bits only to discover that one of the parts is missing, I open each part in a tab to make sure it is there pause it and only start watching the film when I'm sure it is complete.  Sometimes for longer ones, and there are a lot of tabs open, I've had the same effect of having to refresh to get the picture.  Scrap of knowlage two.

So could it be that chrome is preloading everything on the page and over loading somehow.  If so looking at network traffic may be informative, as would ( if one can get one ) a selective flash blocker such as no script in firefox.  It may even be something to do with lso's.

Just wild ideas for diagnosing the problem.  It may also be worth getting something like puppylinux or one of the pupplets which has chrome on it to cross check and see if the same problem applies on other operating systems. Bit off the wall but count it as a bump.

Might be worth seeing if movie player can run youtube vids too.  If one clicks the down arrow next to playlist you should have a youtube search choice.  That would bypass the browser and play direct ..... in theory ( I just got a gstreamer error ....ah well.. not a totem feature I use much anyway, I'll worry about that some other time  ).  Worth a try perhaps.

Also see if the problem is site specific.  [http://video.google.com](http://video.google.com)  really should work.
 
[http://www.metacafe.com](http://www.metacafe.com)

 [http://vimeo.com](http://vimeo.com)  are similar to youtube

[http://www.archive.org/details/Ask_a_Policeman_1939](http://www.archive.org/details/Ask_a_Policeman_1939)  works on mine just got lost in it.


Good luck anyway.

---

### Post by Tikidel on 2011-11-04
I did a bit more testing and it turns out not only is this problem not present in 11.10 but it's also not present in "Ubuntu Classic (No Effects)" only in "Ubuntu" or "Ubuntu Classic" which to me implies something is up with Compiz, but I don't really know much about Compiz so hopefully someone else will be able to help.

EDIT: I found someone else with this problem here: [http://ubuntuforums.org/showthread.php?t=1815975](http://ubuntuforums.org/showthread.php?t=1815975) and they have a similar graphics card to me (I have a HD5870 and they have HD4550) what graphics card do you have Joseph?
Because the problem seems to be with Compiz somehow and because my graphics card is similar to the person in the other thread I tried using both the open-source and proprietary drivers for my video card but the problem existed with both.
I also tried installing the 11.10 3.0 kernel in to 11.04 to see if this was why the problem wasn't present in 11.10 but the problem still existed after I had done that. :(

---

### Post by Joseph Schwenker on 2011-11-04
No matter how many times it happens, it always alarms me when people call me by my first name on Ubuntu Forums, despite the fact that my full name is my username. I'd change it if I could.

I have an nVidia GeForce 8800GT, 512MB video RAM.

---

### Post by Tikidel on 2011-11-05
Haha :P

I guess that rules out video cards then. It must just be some general incompatibility with Compiz and Google Chrome in 11.04. Hopefully someone who knows more will read this and be able to help find a solution.

---

### Post by Joseph Schwenker on 2011-11-05
Since you seem to think that Compiz might be the culprit, you might find this interesting: when I first switched to Ubuntu 11.04, I had to downgrade the default version of Compiz to 0.8.6 due to performance issues.

---

### Post by Tikidel on 2011-11-05
Hmm, I've never had any problems with Compiz apart from when Compiz is enabled my terminal bell doesn't play, I've never had to play around with settings or versions though.

I'm pretty sure it has to be related somehow otherwise the problem would exist when I select "Ubuntu Classic (No Effects)" from the login screen. As far as I know the only thing that is different between that and normal Ubuntu Classic is that Compiz is disabled. I don't really know much about Compiz though so I could be wrong.

---

### Post by oldtimer7777 on 2011-11-27
> **Joseph Schwenker said:**
> bump

My recommendation is to take it to a nice airy lofty rooftop and do comes naturally.  Use whatever throwing arm is your dominate arm.  Pretend that it is small discus like in shape, and fling it as far as you can.  Pretend it is the olympics, and you are going for for the Gold Metal.

In all seriousness, if it doesn't work by now, you need to reinstall on different hardware until it is resolved.  We can only work with what we have, and when that fails, it is time to purchase/attain replacement hardware.

Or you can always install Windows on it and ask them for support.  They will tell you to buy a new computer too, if it doesn't work. :)

---

### Post by overdrank on 2011-11-27
Some post have been removed. Please keep the Ubuntu Forums Code of Conduct in mind when posting. We are all volunteers here. Thanks

---

### Post by houseworkshy on 2011-12-03
I haven't been on for a while, looks like I missed something.  Here are  some more ideas anyway.  gnash can sometimes cause problems with flash  so check to see if it is installed too, if you have non-free flash you  don't need it anyway.  Use the "sudo apt-get purge....." method followed  by "sudo apt-get autoremove" to get rid of any associated settings.

Pulse audio has sometimes had various bad effects on video playback ( I  had to remove it once to stop video playback sticking ).  There are  plenty of threads on that, so that's something else to research if you  wish.

Do try a puppy distro as a cross check: not an install just a quick live  session, chrome should be small enough to install to ram during that  session, it will vanish at the end of the live session of course.  As  long as you don't do any writing to your hard drives your pc won't even  know a puppy session happened.  The reason I repeate this advice is that  it would be a shame to bang your head against software if it turns out  to be a hardware thing.  It could be too, don't remember the details but  a few years ago there were a lot of problems with flash running hot and  big which caused errors.  As far as I remember this, or the fix, had  something to do with swapiness. Doubt swappiness is relevent and only mention it in case you want to search for the threads.  What may be relevant is that flash video  can be very hungry for resourses.  When did you last clean your  machine?  As they get dusty it takes less and less to make them  overheat.  If that is a factor the heavy resources stuff gets flaky  first, could be an early sign.  

You could also try youtubing until it  fails, then shutting the program, going offline then entering "sudo  gnome-system-log"  This will give you the full system logs where you can  search for recorded errors ( easy as they are listed by time and you'll  have made a note of that ).  It'd be nice to sudo the system monitor  too but as you'd want to be online to see the processes in real time  while the error happened, I'd feel uneasy about doing it.  However  System monitor ( not sudoed ) may be usefull anyway, you'd be able to  see how much ram was being used etc.  Top, which is one of the default  commands in a fresh install and Htop, available in the repositories,  could be useful too.  Both have man pages.

Paraniod perhaps but if you are on wireless try using wired and see how youtube functions then.  Some friends of mine had similar problems and it turned out that they had uninvited hitch-hikers shareing the connection.  That said they live in a block, were on windows and used facebook on a wireless connection so ... nuff said.

Disabling desktop effects should take compiz out of the picture, normal boot then turn them off via preferances.

I don't know what I missed as things have been deleted but assume they  wern't so good, please don't judge the forums by whatever it was.   Generally a pretty good crowd in here.

I get the impression that you must favor chrome a lot to persevere so  long.  Google should have a help section tucked away somewhere, it's their product after all.  You may have to give your grandmothers banking details and powers of atourney over your estate to get it but if the problem is software based and as others have had it perhaps there's some info there.

---

### Post by Joseph Schwenker on 2011-12-03
> **houseworkshy said:**
> I haven't been on for a while, looks like I missed something.  Here are  some more ideas anyway.  gnash can sometimes cause problems with flash  so check to see if it is installed too, if you have non-free flash you  don't need it anyway.  Use the "sudo apt-get purge....." method followed  by "sudo apt-get autoremove" to get rid of any associated settings.

Pulse audio has sometimes had various bad effects on video playback ( I  had to remove it once to stop video playback sticking ).  There are  plenty of threads on that, so that's something else to research if you  wish.

Do try a puppy distro as a cross check: not an install just a quick live  session, chrome should be small enough to install to ram during that  session, it will vanish at the end of the live session of course.  As  long as you don't do any writing to your hard drives your pc won't even  know a puppy session happened.  The reason I repeate this advice is that  it would be a shame to bang your head against software if it turns out  to be a hardware thing.  It could be too, don't remember the details but  a few years ago there were a lot of problems with flash running hot and  big which caused errors.  As far as I remember this, or the fix, had  something to do with swapiness. Doubt swappiness is relevent and only mention it in case you want to search for the threads.  What may be relevant is that flash video  can be very hungry for resourses.  When did you last clean your  machine?  As they get dusty it takes less and less to make them  overheat.  If that is a factor the heavy resources stuff gets flaky  first, could be an early sign.  

You could also try youtubing until it  fails, then shutting the program, going offline then entering "sudo  gnome-system-log"  This will give you the full system logs where you can  search for recorded errors ( easy as they are listed by time and you'll  have made a note of that ).  It'd be nice to sudo the system monitor  too but as you'd want to be online to see the processes in real time  while the error happened, I'd feel uneasy about doing it.  However  System monitor ( not sudoed ) may be usefull anyway, you'd be able to  see how much ram was being used etc.  Top, which is one of the default  commands in a fresh install and Htop, available in the repositories,  could be useful too.  Both have man pages.

Paraniod perhaps but if you are on wireless try using wired and see how youtube functions then.  Some friends of mine had similar problems and it turned out that they had uninvited hitch-hikers shareing the connection.  That said they live in a block, were on windows and used facebook on a wireless connection so ... nuff said.

Disabling desktop effects should take compiz out of the picture, normal boot then turn them off via preferances.

I don't know what I missed as things have been deleted but assume they  wern't so good, please don't judge the forums by whatever it was.   Generally a pretty good crowd in here.

I get the impression that you must favor chrome a lot to persevere so  long.  Google should have a help section tucked away somewhere, it's their product after all.  You may have to give your grandmothers banking details and powers of atourney over your estate to get it but if the problem is software based and as others have had it perhaps there's some info there.

This may be of interest: I tried using YouTube in Firefox (with Flash installed from Adobe's website), and was unable to produce the black screen, further reinforcing that this is most likely not a hardware issue. I haven't tried anything without Compiz yet, though Tikidel didn't have this issue when he disabled Compiz.
It might be worth a try to see if I experience the issue in Chromium, which doesn't come precompiled with Flash.
The fact that I have Adblock installed (which blocks ads in YouTube videos) might play a part, too.
I'm on a wired connection, so the problem is most likely not related to my network connection.
I haven't given my computer a compressed air blast in quite some time, so I might do that sometime soon.

Thanks for your response!

---

### Post by oldtimer7777 on 2011-12-03
Well, since you aren't really willing to put in the time to reinstall Ubuntu 11.10 from a step-by-step walk-through how-to guide, I don't know what else to tell you except that you need to put more time and consideration into what you want to accomplish here because that is part of the trade-off by using a free operating system like linux.  I understand that the only thing most users want "seems" to be just one thing (for example, like getting flash to work in Firefox), when it can very much be a combination of several different configuration aspects and/or user installation errors.   When you use a walk-through to guide you through the entire process of getting Ubuntu freshly installed on your computer, you can certainly "weed-out" the potential "culprits" from ruining your experience with Ubuntu.  It is a step-by-step slow steady process of getting everything on there, that can do everything Windows or a Mac can do right out of the box.  This isn't something where you can jam, throw Ubuntu on your computer and be completely done installing packages.  There is quite a bit of work involved in having a completely fully working Ubuntu OS system.  It is do-it-yourself from beginning to end, and we can only help users that understand the entire process requires 2x the effort on their part to accomplish problem solving solutions. 

The walk-through I always recommend for new users is:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

I personally use it everytime I install Ubuntu on a fresh system. Just take it one step at a time, until you have everything listed installed, and you should be perfect. Most users that have used it have no issues at all.  That walk-through how-to guide is a very straight forward list of everything that needs to be installed from a to z. 

Once you are done with that, I recommend creating a custom.iso backup with Remastersys. Burn that custom.iso of your fully installed system on a dvd-r disc or use Startup Disc Creator and a Flash USB Stick to create a live bootable USB Flash Drive of your entire system in case you ever need to reinstall it again, and save yourself a considerable amount of frustration having to remember everything you did to have things just the way you like them.  Always have a custom backup OS to reinstall your system in the future.

> **Joseph Schwenker said:**
> This may be of interest: I tried using YouTube in Firefox (with Flash installed from Adobe's website), and was unable to produce the black screen, further reinforcing that this is most likely not a hardware issue. I haven't tried anything without Compiz yet, though Tikidel didn't have this issue when he disabled Compiz.
It might be worth a try to see if I experience the issue in Chromium, which doesn't come precompiled with Flash.
The fact that I have Adblock installed (which blocks ads in YouTube videos) might play a part, too.
I'm on a wired connection, so the problem is most likely not related to my network connection.
I haven't given my computer a compressed air blast in quite some time, so I might do that sometime soon.

Thanks for your response!

---

### Post by Joseph Schwenker on 2011-12-03
> **oldtimer7777 said:**
> Well, since you aren't really willing to put in the time to reinstall Ubuntu 11.10 from a step-by-step walk-through how-to guide, I don't know what else to tell you except that you need to put more time and consideration into what you want to accomplish here because that is part of the trade-off by using a free operating system like linux.  I understand that the only thing most users want "seems" to be just one thing (for example, like getting flash to work in Firefox), when it can very much be a combination of several different configuration aspects and/or user installation errors.   When you use a walk-through to guide you through the entire process of getting Ubuntu freshly installed on your computer, you can certainly "weed-out" the potential "culprits" from ruining your experience with Ubuntu.  It is a step-by-step slow steady process of getting everything on there, that can do everything Windows or a Mac can do right out of the box.  This isn't something where you can jam, throw Ubuntu on your computer and be completely done installing packages.  There is quite a bit of work involved in having a completely fully working Ubuntu OS system.  It is do-it-yourself from beginning to end, and we can only help users that understand the entire process requires 2x the effort on their part to accomplish problem solving solutions. 

The walk-through I always recommend for new users is:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

I personally use it everytime I install Ubuntu on a fresh system. Just take it one step at a time, until you have everything listed installed, and you should be perfect. Most users that have used it have no issues at all.  That walk-through how-to guide is a very straight forward list of everything that needs to be installed from a to z. 

Once you are done with that, I recommend creating a custom.iso backup with Remastersys. Burn that custom.iso of your fully installed system on a dvd-r disc or use Startup Disc Creator and a Flash USB Stick to create a live bootable USB Flash Drive of your entire system in case you ever need to reinstall it again, and save yourself a considerable amount of frustration having to remember everything you did to have things just the way you like them.  Always have a custom backup OS to reinstall your system in the future.

Actually, I hate Ubuntu 11.10, and I'll be switching to another distro before I upgrade. I'm currently using 11.04, and this problem isn't big enough that I'd want to re-install. Thanks for your advice, though. It may be helpful to me in the future.

---

### Post by oldtimer7777 on 2011-12-03
> **Joseph Schwenker said:**
> Actually, I hate Ubuntu 11.10, and I'll be switching to another distro before I upgrade. I'm currently using 11.04, and this problem isn't big enough that I'd want to re-install. Thanks for your advice, though. It may be helpful to me in the future.

It sounds like it hates you even more Joseph.:lolflag:

Sorry to hear about all your trouble lately.  Maybe consider hiring a young kid to help with you that? Craiglist is pretty inexpensive to find a computer techie nerd to hire per hour. The economy being as lousey as it has been lately, you should be able to find yourself someone real cheap. You should find someone for like 15 bucks an hour or maybe even a flat rate. Peanuts and well worth not having to deal with the frustration too.  Goodluck Schwenker.

---

### Post by Joseph Schwenker on 2011-12-03
> **oldtimer7777 said:**
> It sounds like it hates you even more Joseph.:lolflag:

[IMG]https://lh3.googleusercontent.com/-Y4lWwVbsbX8/TlBwxkyU8YI/AAAAAAAACmE/xm3P-w3bB9E/s617/Screenshot-%252523ubuntu.png[/IMG]

It hates a lot of people!

In all seriousness, however, I don't think I'd be interested in hiring anyone to fix it for me. Every release so far that I've had has had some problems, but I'm usually able to eliminate the major ones. 
This problem isn't *that* major, thankfully, and will probably disappear when I move to another distro. Heck, it disappears when I use another *browser*, so the problem isn't deeply rooted into my system.

Thanks for your help!

---

### Post by oldtimer7777 on 2011-12-03
Ubuntu just loves me. :) 

But that takes a considerable amount of college, and experience. 

Seriously though, you should hire someone at some point if it gets to be too much for you. Just because it is DYI do it yourself, doesn't mean you can't find a kid on craiglist for next to nothing to help get that running for you.  Just make sure you talk to them on the phone, and find out if they are knowledgable about installing Ubuntu on your make/model system. Be as specific as possible with them to save yourself even more hassle with them.   Saves you money that way in the long run, or you can stick with virus prone windows or really pricey fancy Apple, where they have fan dancers that wait on your every need and want. You'll be back down this road sooner than you think too.

Kids have more patience sometimes for technological gadgetry. You get what you pay for sometimes. That is the breaks. 

I usually tell people to check on Ubuntu Friendly to find a computer that absolutely works with Ubuntu and buy it on Ebay or Fry's Electronics. I got one the other day for 150.  Works perfectly, right off the bat.. :)   But you can blame it on whatever you want I guess.  

> **Joseph Schwenker said:**
> [IMG]https://lh3.googleusercontent.com/-Y4lWwVbsbX8/TlBwxkyU8YI/AAAAAAAACmE/xm3P-w3bB9E/s617/Screenshot-%252523ubuntu.png[/IMG]

It hates a lot of people!

In all seriousness, however, I don't think I'd be interested in hiring anyone to fix it for me. Every release so far that I've had has had some problems, but I'm usually able to eliminate the major ones. 
This problem isn't *that* major, thankfully, and will probably disappear when I move to another distro. Heck, it disappears when I use another *browser*, so the problem isn't deeply rooted into my system.

Thanks for your help!

---

### Post by Joseph Schwenker on 2011-12-03
> **oldtimer7777 said:**
> Ubuntu just loves me. :) 

But that takes a considerable amount of college, and experience. 

Seriously though, you should hire someone at some point if it gets to be too much for you. Just because it is DYI do it yourself, doesn't mean you can't find a kid on craiglist for next to nothing to help get that running for you.  Just make sure you talk to them on the phone, and find out if they are knowledgable about installing Ubuntu on your make/model system. Be as specific as possible with them to save yourself even more hassle with them.   Saves you money that way in the long run, or you can stick with virus prone windows or really pricey fancy Apple, where they have fan dancers that wait on your every need and want. You'll be back down this road sooner than you think too.

Kids have more patience sometimes for technological gadgetry. You get what you pay for sometimes. That is the breaks. 

I usually tell people to check on Ubuntu Friendly to find a computer that absolutely works with Ubuntu and buy it on Ebay or Fry's Electronics. I got one the other day for 150.  Works perfectly, right off the bat.. :)   But you can blame it on whatever you want I guess.

Actually, I am a "kid", and Ubuntu's never been too much for me. I switched from Windows two years ago, and I've rarely regretted switching. All my hardware works nicely with Linux, and I've found some great applications thanks to it.

---

### Post by Tikidel on 2011-12-04
Just to clarify because I think some of the details got lost when a bunch of posts were deleted, the problem doesn't exist on 11.10 it only exists on 11.04 and it doesn't exist when I disable desktop effects. However I can't stand 11.10 and when I have desktop effects disabled I don't get the window resizing feature when you drag a window to a side of the screen which I use a lot. :(

---

### Post by oldtimer7777 on 2011-12-04
> **Tikidel said:**
> Just to clarify because I think some of the details got lost when a bunch of posts were deleted, the problem doesn't exist on 11.10 it only exists on 11.04 and it doesn't exist when I disable desktop effects. However I can't stand 11.10 and when I have desktop effects disabled I don't get the window resizing feature when you drag a window to a side of the screen which I use a lot. :(

Yes, that is why I installed Gnome 3 and used that instead.  Worked better.

---

### Post by Joseph Schwenker on 2011-12-04
> **Tikidel said:**
> Just to clarify because I think some of the details got lost when a bunch of posts were deleted, the problem doesn't exist on 11.10 it only exists on 11.04 and it doesn't exist when I disable desktop effects. However I can't stand 11.10 and when I have desktop effects disabled I don't get the window resizing feature when you drag a window to a side of the screen which I use a lot. :(

The only posts that seem to have been removed are a a bump from you and a bump from me, which really had no relevance to the trolling that went on. I'm still not sure why they were removed.

Your post where you mentioned that you didn't experience the issue without Compiz still exists. Do you experience the problem when using Firefox, or is it just with Chrome?

EDIT: I just tried using YouTube in Chrome with Metacity instead of Compiz, and I was unable to cause the black screen bug.

---

### Post by Tikidel on 2011-12-06
> **Joseph Schwenker said:**
> Your post where you mentioned that you didn't experience the issue without Compiz still exists. Do you experience the problem when using Firefox, or is it just with Chrome?

I'll give you the full details of the testing I've done, hopefully someone will find it useful. I get the problem in 11.04 but not 11.10, I get the problem in Chrome and Chromium (tested versions 13 - 16) but not Firefox, I get the problem with flash 10.3 and 11.0 and I get the problem with Chrome's in-built flash, flash from Adobe's website and flash from the repositories (both adobeflash-plugin and flashplugin-installer). I don't get the problem if I disable desktop effects. I also don't get the problem if I use gnash but I got so many other problems that the problem could've still been occurring and I just couldn't tell. Also I didn't specifically test with 10.10 but I never remember the problem occurring for the six months I used that. I also used flashaid and tried changing a bunch of different settings through that but none of them fixed the problem.

---

### Post by jockyburns on 2011-12-07
I too have this problem with You Tube, but find a quick reload of the page usually starts the video player working again. Sometimes does this with certain games on Facebook too, so I'm wondering if it is a problem with Flash.

---

### Post by Joseph Schwenker on 2011-12-07
> **jockyburns said:**
> I too have this problem with You Tube, but find a quick reload of the page usually starts the video player working again. Sometimes does this with certain games on Facebook too, so I'm wondering if it is a problem with Flash.

Glad to hear the it's not just Tikidel and I experiencing the issue. Refreshing usually fixes the problem for me, as well, however I've sometimes needed to refresh up to four times in order to get a working video.

Do you experience the problem when desktop effects (Compiz) are disabled? Do you experience the problem when using Firefox?

---

### Post by jockyburns on 2011-12-07
I'm not that experienced an Ubuntu user to even know where to start to disable Compiz. I use Google Chrome as my main browser (used it when I was on Windoze too as my preferred browser)I'll try using Firefox and post back tomorrow if I have any problems with Youtube videos. ;);)

PS It will be tomorrow as it's 23:10 here, and I have to be up early for work. ;)

---

### Post by Joseph Schwenker on 2011-12-07
> **jockyburns said:**
> I'm not that experienced an Ubuntu user to even know where to start to disable Compiz. I use Google Chrome as my main browser (used it when I was on Windoze too as my preferred browser)I'll try using Firefox and post back tomorrow if I have any problems with Youtube videos. ;);)

You can use the following to disable Compiz:

```
metacity --replace
```

And the following to enable Compiz:

```
compiz --replace
```

Those are both commands that can be run either from a terminal or an alt+f2 dialog.

---

### Post by jockyburns on 2011-12-10
Just tried Firefox and all video's worked on Youtube. Having said that. I tried Chrome too and no problems today (tried both for about 30 vid's each. )

---

### Post by oldtimer7777 on 2011-12-11
> **Joseph Schwenker said:**
> bump

Are you running 64-bit? or 32-bit Ubuntu?  I've had issues with Flash in 64-bit more frequently than in 32-bit Ubuntu. It also depends on what kind of video card you have installed on your MB. You may want to give Ubuntu 32-bit a try with a live usb of Ubuntu to boot from. Install Ubuntu on a flash drive and test your flash with the live bootable usb of Ubuntu to see it is makes a difference with your make/model computer. Other than that I think you are pretty much S.O.L, unless you want to provide us the specs for your make/model computer so we can do a comparison with other successful installations of Ubuntu with the hardware you are running.. It is up to you, but I think it is a hardware issue and compatibility. What kind of time do you want to invest in this?

---

### Post by Joseph Schwenker on 2011-12-11
> **oldtimer7777 said:**
> Are you running 64-bit? or 32-bit Ubuntu?  I've had issues with Flash in 64-bit more frequently than in 32-bit Ubuntu. It also depends on what kind of video card you have installed on your MB. You may want to give Ubuntu 32-bit a try with a live usb of Ubuntu to boot from. Install Ubuntu on a flash drive and test your flash with the live bootable usb of Ubuntu to see it is makes a difference with your make/model computer. Other than that I think you are pretty much S.O.L.

I'm on 32-bit Ubuntu, though my motherboard is 64-bit capable. My graphics card is an nVidia GeForce 8800GT 512MB. I'm not so sure about trying with a flash drive, but I could try with a live CD. The problem goes away when in Firefox or Metacity, so it's definitely not a problem with my computer model.
Perhaps this is a driver issue?

---

### Post by Tikidel on 2011-12-12
I experience the problem on both 32-bit and 64-bit Ubuntu and my graphics card is a HD5870.

---

### Post by oldtimer7777 on 2011-12-12
> **Joseph Schwenker said:**
> I'm on 32-bit Ubuntu, though my motherboard is 64-bit capable. My graphics card is an nVidia GeForce 8800GT 512MB. I'm not so sure about trying with a flash drive, but I could try with a live CD. The problem goes away when in Firefox or Metacity, so it's definitely not a problem with my computer model.
Perhaps this is a driver issue?

So what browser -are- you using that this happens in?  Chrome uses it's own flash plugin, and Chromium uses the same one as Firefox. So that would be why it would work in Firefox and not in Chrome.

If this happens in Chrome, you should add the Chrome development PPA in your repositories:

[http://www.multimediaboom.com/how-to-install-chrome-in-ubuntu-11-04-natty-narwhal/](http://www.multimediaboom.com/how-to-install-chrome-in-ubuntu-11-04-natty-narwhal/)

And try each version of Chrome to test the results.  Try the stable, the unstable beta, and the nightly release.

If you think it is your Nvidia video card you can try adding the latest Nvidia drivers for your Nvidia graphics adapter:

Open your Terminal, cut and paste:

 ```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install nvidia-current
```Let us know the result of installing the latest drivers, and if it appeared to help or not at all.

---

### Post by oldtimer7777 on 2011-12-12
> **Tikidel said:**
> I experience the problem on both 32-bit and 64-bit Ubuntu and my graphics card is a HD5870.

That's because you are running on an ATI card, a hardware compatibility issue, and you should buy a better supported graphics card (if it is a desktop computer), and here is a good list of supported Nvidia graphics cards for desktop computer:

[http://www.nvidia.co.uk/object/linux-display-ia32-270.41.19-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-270.41.19-driver-uk.html)

If it is a laptop pc then you really don't have much choice in switching out your video card for a better supported Nvidia card, and you can try manually installing the very latest linux ATI drivers for your system to see if this helps:

```

1. [Go to amd.com and download your driver]("http://support.amd.com/us/gpudownload/Pages/index.aspx")
2. Run: sudo apt-get &#8211;purge remove fglrx*
3. Run: sudo apt-get install dh-make execstack dh-modaliases dkms lib32gcc1 libc6-i386
4. Go to the directory you [downloaded]("http://support.amd.com/us/gpudownload/Pages/index.aspx") the driver in (usually ~Downloads)
Run: sudo chmod +x ati-driver-installer-11-10-x86.x86_64.run
Run: sudo sh ati-driver-installer-11-10-x86.x86_64.run &#8211;buildpkg Ubuntu/oneiric
Here I assume you are using Ubuntu 11.10. If you&#8217;re using another version, use that version&#8217;s name, for example Ubuntu/maverick
5. Run: sudo dpkg -i *.deb
6. Run: sudo aticonfig &#8211;initial -f
``` Now reboot and it maybe it help with your flash video playback issues. If it is a an ATI card on an PC desktop computer, it would be best to switch it out with a Nvidia supported card instead from the list in that link above. Just saying. :)

But before you do anything, always install Flash Aid plugin for Firefox, and switch from the Beta to Stable version of Flash plugin, to test your results too.

---

### Post by Joseph Schwenker on 2011-12-12
> **oldtimer7777 said:**
> So what browser -are- you using that this happens in?  Chrome uses it's own flash plugin, and Chromium uses the same one as Firefox. So that would be why it would work in Firefox and not in Chrome.

If this happens in Chrome, you should add the Chrome development PPA in your repositories:

[http://www.multimediaboom.com/how-to-install-chrome-in-ubuntu-11-04-natty-narwhal/](http://www.multimediaboom.com/how-to-install-chrome-in-ubuntu-11-04-natty-narwhal/)

And try each version of Chrome to test the results.  Try the stable, the unstable beta, and the nightly release.

If you think it is your Nvidia video card you can try adding the latest Nvidia drivers for your Nvidia graphics adapter:

Open your Terminal, cut and paste:

 ```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install nvidia-current
```Let us know the result of installing the latest drivers, and if it appeared to help or not at all.

I experience the problem in Google Chrome Stable 15.0.874.121. I do NOT experience the problem when Compiz is disabled, nor in Firefox.
I've tried updating Ubuntu's graphics driver several times before, and none of them ever ended in anything good. I don't think it's a driver issue, as the issue does not occur with the same driver when in Metacity or Firefox, though I'm not going to completely rule drivers out as a possibility.

Also, is it really necessary to tell Tikidel that he needs to buy new hardware? The issue has been reproduced on my own nVidia card, certain software options make the issue go away, and the problem was never present in any previous Ubuntu versions. There's no need to cause him/her stress over "hardware" problems when there's not enough evidence to support a hardware problem at this point.

---

### Post by oldtimer7777 on 2011-12-12
Yes, it is necessary because I build computers for a living, and when someone tells me they want a system to work correctly I explain to them that they -must- use the correct hardware to run Ubuntu OS for free. Everything in life is a trade-off, and that should be doubly expected if you want to run a Free OS. If they want to pay for Windows, they still need to use the right hardware depending on what they want to do with it eventually.  Ubuntu doesn't get along with ATI drivers very well. If you think you have problems, try using a ATI graphics card on your system for a while using Ubuntu OS. Then you will know how bad video playback issues can get with flash video.  Everyone would be better off installing on IntelCPU/IntelVideoAdapters -if- they want the kind of result that they would have on Windows OS using native Win Drivers to install their video adapters. Ubuntu development has better support from Intel to get those drivers included in the Linux Kernel in comparison to Radeon ATI video drivers.  ATI expects you to be using Windows and only Windows.  They don't give a darn as much as Nvidia or even Intel apparently. 

As for Google Chrome acting differently than your other browsers, well Joseph, I already kindly explained to you that Google Chrome uses it own flash plugin. Not the same plugin as firefox or any other browser....etc etc etc...  Google Chrome has an -independent- flash plugin component. It is part of the Google Chrome installation deb package you used to install Google Chrome on your Ubuntu OS too. There is nothing Ubuntu developers can do about a package you downloaded from Google.   The issue isn't with Ubuntu OS. It is a Chrome issue and their buggy flashplugin. Talk to Google if you want to get them to update Google Chrome to work with your specs. There is a reason the Adobe plugin works on your computer but not the plugin included with Chrome made by Google.  It is a google developer issue.  You can try installing google chrome beta and see if that has an updated patched flash plugin by now for your make/model system. 3 years ago the Adobe Plugin barely worked in Ubuntu, and we don't get very much support from Google or Adobe to make their codecs work properly in Linux. They are developed by Adobe primary to be used on Windows system.   There is a reason why iPhones can't do flash playback too. Adobe can be a real stinker about it. 

And please note, Chromium doesn't use a google flash plugin to playback  flash video/audio in Ubuntu. Chromium uses the same Adobe flash plugin  as Mozilla Firefox and the rest. 

Does this make sense now??? There really should not be any more argument about it.

> **Joseph Schwenker said:**
> I experience the problem in Google Chrome Stable 15.0.874.121. I do NOT experience the problem when Compiz is disabled, nor in Firefox.
I've tried updating Ubuntu's graphics driver several times before, and none of them ever ended in anything good. I don't think it's a driver issue, as the issue does not occur with the same driver when in Metacity or Firefox, though I'm not going to completely rule drivers out as a possibility.

Also, is it really necessary to tell Tikidel that he needs to buy new hardware? The issue has been reproduced on my own nVidia card, certain software options make the issue go away, and the problem was never present in any previous Ubuntu versions. There's no need to cause him/her stress over "hardware" problems when there's not enough evidence to support a hardware problem at this point.

---

### Post by Tikidel on 2011-12-13
> **Joseph Schwenker said:**
> I experience the problem in Google Chrome Stable 15.0.874.121. I do NOT experience the problem when Compiz is disabled, nor in Firefox.

Can you please try testing with Chromium to see if the flash plugin is related to the problem for you? I expect you'll get the same results as my testing but it would be nice to get that confirmed. Thanks.

---

### Post by oldtimer7777 on 2011-12-13
> **Tikidel said:**
> Can you please try testing with Chromium to see if the flash plugin is related to the problem for you? I expect you'll get the same results as my testing but it would be nice to get that confirmed. Thanks.

Did you read what I wrote him? That is exactly what I said. I wish users would take the time to read instructions, and they wouldn't have to deal with the kind of frustration they appear to have with Ubuntu OS sometimes too.

---

### Post by Joseph Schwenker on 2011-12-13
> **oldtimer7777 said:**
> Did you read what I wrote him? That is exactly what I said. I wish users would take the time to read instructions, and they wouldn't have to deal with the kind of frustration they appear to have with Ubuntu OS sometimes too.

We don't know for certain that the problem is with the varying versions of Flash. His request is perfectly appropriate, as it will help confirm whether or not Flash is causing the problem.

I'll see what happens in Chromium.

---

### Post by Joseph Schwenker on 2011-12-13
Interestingly, the problem did indeed surface in Chromium (15.0.874.121). Even more interestingly, the problem seems to have disappeared with the latest Google Chrome update (also 15.0.874.121). I'm not completely certain that the problem has been solved, though, so I'll wait a while before marking this as solved.

Tikidel, does upgrading Google Chrome to 15.0.874.121 solve the issue for you?

**EDIT:** I spoke too soon. The problem still surfaces in Google Chrome 15.0.874.121.

---

### Post by Tikidel on 2011-12-14
That we seem to be experiencing the problem under identical conditions and that we have completely different video cards along with the fact that all the different drivers I've tried made no difference implies to me that the problem is between Chrome/Chromium and Compiz under 11.04. I've seen no evidence of flash version or video drivers making any difference.

It'd be good if someone running Chrome/Chromium and 11.04 with Compiz enabled could confirm that the problem is unique to Joseph and I so we could narrow down what's causing it.

---

### Post by SnickerSnack on 2011-12-18
I've had a somewhat similar problem which I fixed by having a panel button to kill npviewer.bin.

I assume npviewer.bin is part of the flash plugin, and it gets stuck somehow.  Running

```
killall npviewer.bin
```

and then reloading the youtube page always fixed the problem for me.  I made a panel button to run this command, but you could also make a keyboard shortcut.

---

### Post by Joseph Schwenker on 2011-12-20
> **SnickerSnack said:**
> I've had a somewhat similar problem which I fixed by having a panel button to kill npviewer.bin.

I assume npviewer.bin is part of the flash plugin, and it gets stuck somehow.  Running

```
killall npviewer.bin
```

and then reloading the youtube page always fixed the problem for me.  I made a panel button to run this command, but you could also make a keyboard shortcut.

Thanks for the suggestion, SnickerSnack. I tried running that command when I experienced the problem, but I got an error about there being no such process. On what browser did this work for you?

---

### Post by SnickerSnack on 2011-12-23
> **Joseph Schwenker said:**
> Thanks for the suggestion, SnickerSnack. I tried running that command when I experienced the problem, but I got an error about there being no such process. On what browser did this work for you?

This was on Chromium, but i think it also happened with Firefox.  I think npviewer.bin is part of the flash plugin.

Apparently your problem is different.  If you have a different flash plugin (if that's even a thing), then I would recommend you look at top to see if there is anything running that may be the culprit.

---

### Post by Joseph Schwenker on 2011-12-26
I ran top when I experienced the problem, and "chrome" was the top process. I looked in Chrome's task manager, and Shockwave Flash was using the most CPU.

Edit:

In Chromium, the same thing happens, except the process with the most CPU is "chromium-browser" instead of "chrome".

---

### Post by Joseph Schwenker on 2012-02-17
How strange, several pages of bumps seem to have mysteriously disappeared...
I wonder who could have possibly had the power to remove several pages of posts indiscriminately...

Regardless, the problem still persists.

---

### Post by Tikidel on 2012-02-18
Problem still exists in Google Chrome 17.0.963.56 with Adobe Flash 11.1.102.62.

The only reason I'm running Compiz is for the window resizing feature when you drag a window to a side of the screen, if I could get this behaviour without Compiz then it would effectively fix the problem for me.

EDIT: If I could get HTML5 to work for all videos on youtube without having to disable the flash plugin that would also effectively fix the problem for me.

---

### Post by Joseph Schwenker on 2012-03-02
bump

---

### Post by uRock on 2012-03-02
Excessive bumps removed. Please do not excessively bump the thread.

---

### Post by uRock on 2012-03-02
> **Tikidel said:**
> Problem still exists in Google Chrome 17.0.963.56 with Adobe Flash 11.1.102.62.

The only reason I'm running Compiz is for the window resizing feature when you drag a window to a side of the screen, if I could get this behaviour without Compiz then it would effectively fix the problem for me.

EDIT: If I could get HTML5 to work for all videos on youtube without having to disable the flash plugin that would also effectively fix the problem for me.

Have you tried upgrading flash using flashaid? I am using Chrome with the Adobe Flash 11.2 version without any issues, though I have never had any issues with Flash.

---

### Post by Joseph Schwenker on 2012-03-03
> **uRock said:**
> Excessive bumps removed. Please do not excessively bump the thread.

I bump this thread, at most, every twenty-four hours, which is hardly excessive. I recall being informed in the past that bumping more frequently than every twenty-four hours is considered bad etiquette, and have thus respected said limit. You may have a point if the bumps were occurring more frequently than every twenty-four hours, but otherwise, I see no reason to label my bumps as "excessive". 

The problem still persists for both Tikidel and I, and, with all due respect, you're hardly doing us a favor by policing this thread.

I appreciate your suggestion with regard to FlashAid, however. Unfortunately, as that extension is for Firefox and not Chrome, it would seem unhelpful to our situation.

---

### Post by uRock on 2012-03-03
> **Joseph Schwenker said:**
> I bump this thread, at most, every twenty-four hours, which is hardly excessive. I recall being informed in the past that bumping more frequently than every twenty-four hours is considered bad etiquette, and have thus respected said limit. You may have a point if the bumps were occurring more frequently than every twenty-four hours, but otherwise, I see no reason to label my bumps as "excessive". 

The problem still persists for both Tikidel and I, and, with all due respect, you're hardly doing us a favor by policing this thread.

I appreciate your suggestion with regard to FlashAid, however. Unfortunately, as that extension is for Firefox and not Chrome, it would seem unhelpful to our situation.

Ten bumps in a row is excessive. If you have a problem with moderation, then post in the Resolution Center.

If you and/or the OP are unwilling to use Firefox to install the latest Adobe Flash, then maybe installing it via the Adobe site is the answer. It would appear that a hardware upgrade may be in order as well.

---

### Post by Joseph Schwenker on 2012-03-03
> **uRock said:**
> Ten bumps in a row is excessive. If you have a problem with moderation, then post in the Resolution Center.

If you and/or the OP are unwilling to use Firefox to install the latest Adobe Flash, then maybe installing it via the Adobe site is the answer.

I am the OP. To my understanding, Chrome has Flash compiled into it, so I'm unsure as to how to upgrade it. Additionally, Firefox reports Adobe Flash at version 11.1.102.62, and Chrome reports it at 11.1 r102. According to Firefox, as well as Adobe's website, the latest version of Flash I can download is 11.1.102.62.

---

### Post by uRock on 2012-03-03
> **Joseph Schwenker said:**
> I am the OP. To my understanding, Chrome has Flash compiled into it, so I'm unsure as to how to upgrade it. Additionally, Firefox reports Adobe Flash at version 11.1.102.62, and Chrome reports it at 11.1 r102. According to Firefox, as well as Adobe's website, the latest version of Flash I can download is 11.1.102.62.

If you had/have flashaid installed, then you'd have the newer version and your problems may be gone. Chrome is using the 11.2 version on my system.

---

### Post by Tikidel on 2012-03-07
I downloaded flashaid and it successfully upgraded my flash to 11.2 however the problem still persists for me, I believe (correct me if I'm wrong) that you're not experiencing the same issue as Joseph and I because you're not running 11.04 or you don't have desktop effects enabled.

Also what do you mean by a hardware upgrade may be needed? As far as I can tell the problem is unrelated to hardware as Joseph and I have fairly different hardware, the only hardware I think that could cause this would be video card and Joseph has an 8800GT and I have a HD5870, I've also tried both the open source and proprietary drivers but it didn't make any difference. So far no one has confirmed they don't have the problem on 11.04 so I'm assuming that it's unrelated to hardware.

---

### Post by uRock on 2012-03-07
I do have an install with 11.04 and Chromium plays videos on Youtube flawlessly.

---

### Post by Tikidel on 2012-03-07
I finally found the source of the problem, in CCSM I had to go in to options for the OpenGL plugin and disable "Sync to VBlank". Hopefully this resolves the problem for you too Joseph.

---

