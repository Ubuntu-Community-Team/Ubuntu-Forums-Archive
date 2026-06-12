---
title: "Firefox-bin not closing"
date: 2011-10-11
forum: General Help
---

### Post by wpshooter on 2011-10-11
Can anyone tell me why (on occasions but not always) the FIREFOX-BIN process is not being automatically closed when I close the Firefox browser ?

I know that I can close the process by going into SYSTEM MONITOR and closing it manually (which is what I have been doing when it is not automatically closed) but I don't think I should be having to do that.

Thanks.

---

### Post by foureyesboy on 2011-10-11
I have this problem before when using the stock Firefox on my Lucid (not sure what version are you using).

Should be the flash player, cuz I had tried uninstalling it and the problem was gone.  But once I reinstalled it back, the problem came back again.

I have now upgraded to Firefox 7 and the problem is gone.

---

### Post by halw on 2011-10-11
Having the same issue with the latest LTS version of Ubuntu. This started happening after the latest Firefox update a couple of days ago. This is FF v3.6.23

---

### Post by wpshooter on 2011-10-11
> **halw said:**
> Having the same issue with the latest LTS version of Ubuntu. This started happening after the latest Firefox update a couple of days ago. This is FF v3.6.23

Yes, that is the same Firefox version I have.

Any idea as to the cause of this or when it might be fixed.

Is getting sort of annoying.

Thanks.

---

### Post by wpshooter on 2011-10-11
> **foureyesboy said:**
> I have this problem before when using the stock Firefox on my Lucid (not sure what version are you using).

Should be the flash player, cuz I had tried uninstalling it and the problem was gone.  But once I reinstalled it back, the problem came back again.

I have now upgraded to Firefox 7 and the problem is gone.

I don't see any Firefox 7 being offered for installation by Ubuntu !!!

Thanks.

---

### Post by gusteman on 2011-10-12
Hi there,
I had the same issue on Hardy, Karmic and now on Lucid.
I am not quite certain yet, but it seems the problem occurs after doing an update of Firefox simultaneously with an update of FlashPlayer.
Still have to check it out once (should have two machines to check it out properly), but I would suggest the next time the Update Manager offers updates for Firefix as well as for FlashPlayer, you perform these updates separately.
Good luck!

---

### Post by mikejonesey on 2011-10-12
create a wrapper and log then check log at next occurance...

alias firefox="script.sh" >> .bashrc

script.sh::
/usr/bin/firefox >> ~/firefox.log

u may want to redir stderr to stdout too...

---

### Post by foureyesboy on 2011-10-12
> **wpshooter said:**
> I don't see any Firefox 7 being offered for installation by Ubuntu !!!

Thanks.

I use the Mozilla Team PPA.
```
 
sudo add-apt-respository ppa:mozillateam/firefox-stable
sudo apt-get update && sudo apt-get upgrade

```

---

### Post by codger76028 on 2011-10-12
Same problem here.  I just disabled the flash plugin and no more problem.

---

### Post by Man_Beach on 2011-10-12
> **codger76028 said:**
> Same problem here.  I just disabled the flash plugin and no more problem.

how?

---

### Post by wpshooter on 2011-10-13
> **codger76028 said:**
> Same problem here.  I just disabled the flash plugin and no more problem.

If you do that and then you wanted to go to a website like **_Springfield Armory_**, how do you get that website to be properly ran/displayed ?

Thanks.

---

### Post by Man_Beach on 2011-10-13
> **wpshooter said:**
> If you do that and then you wanted to go to a website like **_Springfield Armory_**, how do you get that website to be properly ran/displayed ?

Thanks.

Seems like for the moment you can either have Firefox-bin not closing, or no flash.

Great.

---

### Post by Man_Beach on 2011-10-16
Does anyone have any practical solution to this(and I don't consider manually shutting it down in System Monitor or using Chrome instead to be practical solutions) - or are we just going to have to wait for it to be fixed?

There are others in my family who use Firefox and I'm not sure that telling them to go to System - Administration - System Monitor - Processes - right click on Firefox-bin etc. every time it happens to be a particularly good idea.

---

### Post by wpshooter on 2011-10-16
> **Man_Beach said:**
> Does anyone have any practical solution to this(and I don't consider manually shutting it down in System Monitor or using Chrome instead to be practical solutions) - or are we just going to have to wait for it to be fixed?

There are others in my family who use Firefox and I'm not sure that telling them to go to System - Administration - System Monitor - Processes - right click on Firefox-bin etc. every time it happens to be a particularly good idea.

Man:

IMO, this is the very type of thing that is going to keep Ubuntu from ever being any real competition for that other OS.  This has been going on for, I think, about 3 weeks now and it is still not fixed.  This is just unacceptable !!!

It is really quite embarrassing to recommend Ubuntu to your friends and associates and them have them calling you about such a thing as this when you have been telling them what a great OS Ubuntu is.

And for those that might, please don't tell me that Firefox and Flashplugin are not Ubuntu.  If Ubuntu is going to use these facilities as parts of their O/S's functioning, then it is their responsibility to see that they JUST WORK.

Thanks.

---

### Post by solita on 2011-10-16
wpshooter is absolutely correct.

It is hard enough to get open source taken seriously by senior management teams as it is without this kind of thing.

Canonical must take ownership of this issue and get it fixed.

---

### Post by AsusDave on 2011-10-17
> I'm not sure that telling them to go to System - Administration - System Monitor - Processes - right click on Firefox-bin etc. every time it happens to be a particularly good idea.You could tell them to type 
```
ps aux | grep firefox
```then have them decipher the output and kill the process.

... just sayin'  (had to do it!) ;)

All joking aside, it is a quite annoying problem. I am trying the ppa upgrade route to see if it helps.

---

### Post by Man_Beach on 2011-10-22
> **Man_Beach said:**
> Does anyone have any practical solution to this(and I don't consider manually shutting it down in System Monitor or using Chrome instead to be practical solutions) - or are we just going to have to wait for it to be fixed?

There are others in my family who use Firefox and I'm not sure that telling them to go to System - Administration - System Monitor - Processes - right click on Firefox-bin etc. every time it happens to be a particularly good idea.

I was wrong - using Chrome _is_ a practical solution. Firefox is ditched. Now, I just need to sort out an alternative for Thunderbird and I can get rid of Mozilla completely.

---

### Post by as2000 on 2011-10-22
I found this fix:

Type: about:config
Click on "I will be careful" (Please do. you can really mess it up.)
In the filter box at the top type: dom.ipc.plugins.enabled
If this is set to false; right click and click on toggle to set to true.
Close and restart Firefox. 

This has solved my issue and has not affected flash.

---

### Post by wpshooter on 2011-10-22
> **as2000 said:**
> I found this fix:

Type: about:config
Click on "I will be careful" (Please do. you can really mess it up.)
In the filter box at the top type: dom.ipc.plugins.enabled
If this is set to false; right click and click on toggle to set to true.
Close and restart Firefox. 

This has solved my issue and has not affected flash.

AS2000:

I had also previously found that fix but for me it did/does not seem to work.  I think there is something else going on here.

Let us know if problem recurs or if you run across any other info on this.

Thanks.

---

### Post by masgeeks on 2011-10-22
There's a nice little addon for Firefox I use called QuickJava - it has ability to add little buttons to your Firefox launcher to quickly enable/disable flash, java scipt, images, etc.

---

### Post by wpshooter on 2011-10-23
> **as2000 said:**
> I found this fix:

Type: about:config
Click on "I will be careful" (Please do. you can really mess it up.)
In the filter box at the top type: dom.ipc.plugins.enabled
If this is set to false; right click and click on toggle to set to true.
Close and restart Firefox. 

This has solved my issue and has not affected flash.

Tried this again just to be on safe side.

Still does not work.  Firefox-bin still not being closed on various occasions.

Back to the drawing board !!!

---

### Post by whatthefunk on 2011-10-23
I get the same thing.  Firefox and something called plugin-container run for a few minutes after closing firefox.  Its driving me nuts.

---

### Post by eugene19 on 2011-10-24
Same problem for me too, and its absolutely unacceptable!
BTW, has anyone reported this bug?

---

### Post by oldtimer7777 on 2011-10-24
> **eugene19 said:**
> Same problem for me too, and its absolutely unacceptable!
BTW, has anyone reported this bug?

I had this problem until I upgraded to the latest version of Firefox. Here is the PPA:

[http://www.webupd8.org/2011/06/firefox-aurora-channel-ppa.html](http://www.webupd8.org/2011/06/firefox-aurora-channel-ppa.html)

---

### Post by wpshooter on 2011-10-24
> **eugene19 said:**
> Same problem for me too, and its absolutely unacceptable!
BTW, has anyone reported this bug?

Yes, I have.

But still not fixed yet.

Thanks.

---

### Post by wpshooter on 2011-10-24
> **oldtimer7777 said:**
> I had this problem until I upgraded to the latest version of Firefox. Here is the PPA:

[http://www.webupd8.org/2011/06/firefox-aurora-channel-ppa.html](http://www.webupd8.org/2011/06/firefox-aurora-channel-ppa.html)

I tried to update Firefox to version 7 but I could not figure out how to get it installed.  These Linux versions of programs give you very little to ZERO instructions as to how to get the application installed.  They need to remember when they are developing these applications that everyone is NOT a programmer like they are !!!!

---

### Post by as2000 on 2011-10-27
Sadly, after posting my fix I starting getting the error again....

But, I was able to install Firefox 7.0.1 (see screenshot) by using Ubuntu Tweak. You will have to enable the Firefox stable channel in the source center. Then sync and the download should come up. 

I will let you know if this solved it for me.

---

### Post by oldtimer7777 on 2011-10-27
Does this happen on the latest Aurora Firefox version? You can also enable the PPA in ubuntu-tweak if you want to try it.

Also if you need to rollback firefox, don't use Purge in Ubuntu-Tweak.. It never works..  You can install purge from the command line and run it to remove each PPA separately. It took me forever to figure that out.

> **as2000 said:**
> Sadly, after posting my fix I starting getting the error again....

But, I was able to install Firefox 7.0.1 (see screenshot) by using Ubuntu Tweak. You will have to enable the Firefox stable channel in the source center. Then sync and the download should come up. 

I will let you know if this solved it for me.

---

### Post by as2000 on 2011-10-27
> **oldtimer7777 said:**
> Does this happen on the latest Aurora Firefox version? You can also enable the PPA in ubuntu-tweak if you want to try it.


I did try the Aurora version and it did not work. It kept telling me dependencies were not met and so I just disabled it.

---

### Post by oldtimer7777 on 2011-10-27
Then I would probably recommend posting a bug report over with the guys at Mozilla development team about this.  There should be a PPA to add to 11.10 for development and bug testing on Ubuntu by now. Last time I checked their PPA worked in 11.04.

---

### Post by as2000 on 2011-10-27
Aurora is still in testing so I would not be surprised about this. Do you not get the ppa in Tweak?

---

### Post by oldtimer7777 on 2011-10-27
> **as2000 said:**
> Aurora is still in testing so I would not be surprised about this. Do you not get the ppa in Tweak?

Actually none of the Mozilla Firefox PPAs are updated to work with Ubuntu 11.10 yet. 

Here take a look:

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

---

### Post by zero244 on 2011-10-29
This is very irritating.........this started on my last Ubuntu update.
This bug has been reported.....but no fix in the works as far as I can see.

---

### Post by zero244 on 2011-10-29
> **as2000 said:**
> I found this fix:

Type: about:config
Click on "I will be careful" (Please do. you can really mess it up.)
In the filter box at the top type: dom.ipc.plugins.enabled
If this is set to false; right click and click on toggle to set to true.
Close and restart Firefox. 

This has solved my issue and has not affected flash.

Hey thanks.......that worked for me.

---

### Post by wpshooter on 2011-10-30
> **zero244 said:**
> Hey thanks.......that worked for me.

Hey, give it a few tries opening and closing Firefox and I think you might find that this did NOT fix it.  It did NOT fix mine.

---

### Post by zero244 on 2011-10-30
> **wpshooter said:**
> Hey, give it a few tries opening and closing Firefox and I think you might find that this did NOT fix it.  It did NOT fix mine.

Your right it worked the first time I closed it.......now its not working.
What makes it even more irritating is you cant even shut down Ubuntu without forcing it closed.

---

### Post by wpshooter on 2011-10-30
> **zero244 said:**
> Your right it worked the first time I closed it.......now its not working.
What makes it even more irritating is you cant even shut down Ubuntu without forcing it closed.

Yes, you can shutdown without going to the system monitor and manually ending the process, you will be prompted at shutdown, as to if you want to shutdown even if process is still running.

Since there seems to be no efforts being made to fix this problem, the only real solution that I found was to wipe out my Lucid installation and re-install using Natty instead from scratch which installs Firefox version 7 which does not (so far), seem to have this problem.  I DON'T REALLY THINK I SHOULD HAVE HAD TO DO THAT BUT I CAN NOT WAIT FOREVER TO SEE IF OR WHEN THIS PROBLEM MIGHT BE FIXED. 

Good luck.

---

### Post by valvegrid on 2011-10-30
I've been getting this problem for some time now, as I'm the only person using this computer I've installed FF 7 in my /home folder for now in the hope that there will be a fix, I must say it is working nicely, it loads much quicker than the  globally install version.

---

### Post by wpshooter on 2011-10-30
> **valvegrid said:**
> I've been getting this problem for some time now, as I'm the only person using this computer I've installed FF 7 in my /home folder for now in the hope that there will be a fix, I must say it is working nicely, it loads much quicker than the  globally install version.

Can you tell me how you managed to get this installed ?

I downloaded FF version 7 but there were NO instructions on how to install it that I could find !!!

Thanks.

---

### Post by valvegrid on 2011-10-30
Just download it and extract it in a folder, then to get it working just double click on the executable file called Firefox. You can make a short cut to it and put it on the launcher or desktop. I labelled mine Firefox Local so I could identify which FF I want to open.

---

### Post by zero244 on 2011-10-30
I just made Midori my default browser.
I think the when I started having problems the update manager did have a flash and firefox update at the same time.
It would seem a fix for this problem couldnt be too difficult.

---

### Post by as2000 on 2011-10-30
I have been running FF7 since updating at that seemed to do the trick.

---

### Post by whatthefunk on 2011-11-01
I found a solution!

I purged firefox and made Opera my default browser.

---

### Post by pedja_portugalac on 2011-11-02
I have same problem and it is since I updated flash. Playing higher definitions clips on flash make images flashing and white, firefox-bin won't stop normally and I can't turn off my computer without answering "close it anyway". Very annoying and make me believe my installation was compromised in some way.

---

### Post by reset3x on 2011-11-11
I'm running 10.04.3 LTS with Gnome. I've tried the suggestions listed above except installing FF7. Nothing works. This is VERY annoying!! I wound up creating a launcher on my top gnome-panel and gave it the command ```
killall firefox-bin
``` It's handier than opening a terminal or an Alt-F2...

reset :(

---

### Post by zero244 on 2011-11-11
Hey guys there was a update for firefox today.....I updated and the firefox.bin problem seems to have gone away.
Check your updates.

---

### Post by texaswriter on 2011-11-11
> **whatthefunk said:**
> I get the same thing.  Firefox and something called plugin-container run for a few minutes after closing firefox.  Its driving me nuts.

If you want to solve the problem easily, for the sake of "restarting" firefox, or whatever, make a script that starts by 'killall firefox-bin' and/or whatever else file is refusing to close. Then launch firefox. Tie this script to a link on your taskbar with a firefox icon. 

If you just want to kill firefox with a click of a button. Make another script with just the killall. 

Possible fixes: 
1) upgrade your operating system
2) use a ppa to upgrade firefox
3) disable flash
4) use an alternative to flash (gnash/etc), try searching linux flash alternative
5) use something to disable flash selectively
6) use another browser: 
    a) chromium
    b) opera
    c) chrome
    d) google linux browsers


These are all fixes. Canonical supports the operating system, not the browser + addins + extensions. 

I hope this doesn't come off as rude, that is not my intention. There are SEVERAL very good solutions to your problem. Whining about how "Canonical owes me a flash fix" is not going to solve it. Adobe Flash is a very messed up piece of work, it is getting better (and faster).

Please try some of those solutions and good luck.

---

### Post by reset3x on 2011-11-11
> **zero244 said:**
> Hey guys there was a update for firefox today.....I updated and the firefox.bin problem seems to have gone away.
Check your updates.

Just saw this.. We'll see what happens..

Reset

EDIT: That was a Flash update. Still no joy....

---

### Post by texaswriter on 2011-11-11
> **reset3x said:**
> Just saw this.. We'll see what happens..

Reset

EDIT: That was a Flash update. Still no joy....


scroll and read all the posts. the one right before your last post (by me) has multiple solutions.

---

### Post by whatthefunk on 2011-11-12
Im really liking Opera.  It took me a few weeks to get used to and to get setup in a good way, but I find its much quicker and easier to use.  The only thing that sucks is I have occasional flash problems.

---

### Post by reset3x on 2011-11-12
> **texaswriter said:**
> scroll and read all the posts. the one right before your last post (by me) has multiple solutions.

I read your post.


EDIT: [This]("http://ubuntuforums.org/showpost.php?p=11394760&postcount=12") works for me.

Cheers,

Reset

---

### Post by nrundy on 2011-11-12
> **wpshooter said:**
> Can anyone tell me why (on occasions but not always) the FIREFOX-BIN process is not being automatically closed when I close the Firefox browser ?

I know that I can close the process by going into SYSTEM MONITOR and closing it manually (which is what I have been doing when it is not automatically closed) but I don't think I should be having to do that.

Thanks.

This is a memory leak bug in Firefox. A long existing one.

---

### Post by wpshooter on 2011-11-12
> **nrundy said:**
> This is a memory leak bug in Firefox. A long existing one.

Doesn't not seem to exist or at least exhibit itself under Ubuntu/Natty using Firefox version 7, at least not so far, while crossing fingers & knocking on some wood !!!

Thanks.

---

### Post by texaswriter on 2011-11-12
> **wpshooter said:**
> Doesn't not seem to exist or at least exhibit itself under Ubuntu/Natty using Firefox version 7, at least not so far, while crossing fingers & knocking on some wood !!!

Thanks.

if this thread is solved, please mark it solved. :D

---

### Post by wpshooter on 2011-11-13
> **texaswriter said:**
> if this thread is solved, please mark it solved. :D

I don't know if it is solved for Lucid because my solution was (unfortunately) to have to move up to Natty just to get rid of this problem (I can not wait the rest of my life for this problem to get fixed).  

Someone that is still using Lucid will have to make a posting to this thread that it has been solved for that version and then I can mark this threads problem as solved.

---

### Post by reset3x on 2011-11-13
> **wpshooter said:**
> I don't know if it is solved for Lucid because my solution was (unfortunately) to have to move up to Natty just to get rid of this problem (I can not wait the rest of my life for this problem to get fixed).  

Someone that is still using Lucid will have to make a posting to this thread that it has been solved for that version and then I can mark this threads problem as solved.


I'm using Lucid (10.04.3). [[COLOR="Red"]This[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11394760&postcount=12") fix works fine for me. I haven't had any problems with the process shutting down since I changed the settings in FF config.

Cheers!

Reset :)

---

### Post by Man_Beach on 2011-11-13
The solution is simple: ditch Firefox and use something else.
Try Google Chrome, for example. That worked for me.

---

### Post by texaswriter on 2011-11-14
> **Man_Beach said:**
> The solution is simple: ditch Firefox and use something else.
Try Google Chrome, for example. That worked for me.

That's one possible solution, but it is certainly not the only. I've NEVER had this issue with firefox, so I would recommend fixing the issue before taking something extreme like switching browsers. 

That said, I do keep Opera and Chromium installed as backup browsers, although my primary browser is firefox.

---

### Post by wildbill300z on 2011-11-20
; ;   FIXED ;   I'VE had the same thing happen however i've found firefox has a plugin called FLASH-AID Iit says it is just for ubuntu conflict with the flash player I'll post the results after i try it for a few days

---

### Post by wpshooter on 2011-11-20
> **wildbill300z said:**
> ; ;   FIXED ;   I'VE had the same thing happen however i've found firefox has a plugin called FLASH-AID Iit says it is just for ubuntu conflict with the flash player I'll post the results after i try it for a few days

Wouldn't it be better for Ubuntu to have the correct plugins, etc. in their package offerings in Synaptic instead of the users having to go out and hunt down a possible fix for these type of problems ?

Thanks.

---

### Post by grey1beard on 2011-12-02
I've recently updated Flash, then Adobe air, both as a precursor to installing BBC iPlayer on this 64 bit AMD, running 10.10.
Have now got even fewer grey hairs :(

I, too, now get occasional "Firefox-bin not responding" messages when shutting down, and so have to poke it in the eye to do what I tell it.
Any final consensus on the best way to deal with the problem permanently, or is everyone waiting for an update to solve the problem ?

John

---

### Post by wpshooter on 2011-12-04
> **grey1beard said:**
> I've recently updated Flash, then Adobe air, both as a precursor to installing BBC iPlayer on this 64 bit AMD, running 10.10.
Have now got even fewer grey hairs :(

I, too, now get occasional "Firefox-bin not responding" messages when shutting down, and so have to poke it in the eye to do what I tell it.
Any final consensus on the best way to deal with the problem permanently, or is everyone waiting for an update to solve the problem ?

John

Grey1beard:

The way I solved it was by moving from Lucid which was using older version 3. something of Firefox to Natty which is using Firefox 7. something.

I waited around for a fix for about 3 or 4 months after I had reported this as a bug.  You can wait for fix if you like but I sure wouldn't want to try to hold my breath until it might be fixed !!!!

Good luck.

---

### Post by oldtimer7777 on 2011-12-04
If it is an occational issue with Firefox not closing, I use Bleachbit to clean out my system, which usually resolves this issue.  Even Ubuntu needs housekeeping if you do quite a bit of internet surfing.

sudo apt-get install bleachbit
sudo bleachbit

Careful not to delete your passwords or bookmarks with Bleachbit.

> **wpshooter said:**
> Can anyone tell me why (on occasions but not always) the FIREFOX-BIN process is not being automatically closed when I close the Firefox browser ?

I know that I can close the process by going into SYSTEM MONITOR and closing it manually (which is what I have been doing when it is not automatically closed) but I don't think I should be having to do that.

Thanks.

---

### Post by grey1beard on 2011-12-04
I did think I had spotted a pattern, when I noticed that the problem didn't occur if I hadn't opened any video links during a session of web browsing. That proved to be a false idea after a couple of days.
I also thought I'd killed it when I accidentally crashed the pc by hitting the power switch, but after a couple of days, it reappeared.

I've now learnt to live with it, as one of life's mysterious puzzles, and good for my karma.

John

---

### Post by oldtimer7777 on 2011-12-04
> **grey1beard said:**
> I did think I had spotted a pattern, when I noticed that the problem didn't occur if I hadn't opened any video links during a session of web browsing. That proved to be a false idea after a couple of days.
I also thought I'd killed it when I accidentally crashed the pc by hitting the power switch, but after a couple of days, it reappeared.

I've now learnt to live with it, as one of life's mysterious puzzles, and good for my karma.

John

What kind of graphics card/adapter are you using?

---

### Post by grey1beard on 2011-12-04
Nvidia Geforce GT200, or so Sysinfo tells me, and who am I to argue !
John

---

### Post by suelynnes on 2011-12-26
I found that disabling the ice-tea plugin fixes this problem. None of the other fixes I have seen here actually work longterm.  Try that. :confused:

---

### Post by grey1beard on 2011-12-26
If I disable it, how do java applets run, and  is this a Good thing or a Bad thing ?

I don't really know what that means, but it seems sensible to ask :)

John

---

### Post by zero244 on 2012-01-08
Ive been having this same problem for months.
On top of the firefox.bin problem, I also had the problem of setting the default browser.

Yesterday I updated my kernel and firefox version 9 with update manager and both problems went away including firefox.bin not closing.
I am running 10.04 by the way.

---

### Post by crylex on 2012-01-20
Hi

Just arrived here after months of general lurking with xubuntu probs and so on.

But, to solve this problem, as a workaround, write a small script, firefox-start, and put it in your home directory, and make it executable (note, it can go anywhere in the path). Put this in the script

killall firefox-bin
firefox

then right click on the firefox icon in the top panel (this is in xubuntu, not sure how you ubuntu chaps do it), and edit the command to point to this script.

Then whenever its called, if firefox is running, its killed.

Chris

---

### Post by wpshooter on 2012-01-22
> **crylex said:**
> Hi

Just arrived here after months of general lurking with xubuntu probs and so on.

But, to solve this problem, as a workaround, write a small script, firefox-start, and put it in your home directory, and make it executable (note, it can go anywhere in the path). Put this in the script

killall firefox-bin
firefox

then right click on the firefox icon in the top panel (this is in xubuntu, not sure how you ubuntu chaps do it), and edit the command to point to this script.

Then whenever its called, if firefox is running, its killed.

Chris

Sounds like a winner but I don't think you should have to do this in Ubuntu !!!

---

### Post by grey1beard on 2012-01-28
I've observed a curious but consistent pattern.

I generally have Evolution open at the same time as Firefox, and if I close Evolution first, then Firefox, then shut down procedes normally.
Closing Firefox first, then Evolution, always leaves Firefox-bin running.

When I first started using 10.10, I often closed the desktop without closing all the running programmes separately first.
I don't know if this set up the problem, or has nothing to do with it.
Anyone else noticed anything similar ?

---

### Post by psablo on 2012-02-06
Lynx 10.04 - Gnome

None of the solutions presented here seem any easier than simply opening
System Monitor > Processes > right-click Firefox > End Process

Even though I have just gotten used to this, I would like to see a more permanent solution so I hope this thread stays open.


For any newbies, adding System Monitor to your panel is a good first step:
System > Administration > right-click System Monitor > Add this launcher to panel

---

