---
title: "Whats up with firefox 3.6.4 update?"
date: 2010-06-23
forum: General Help
---

### Post by aviramof on 2010-06-23
it's been quite a while since firefox 3.6.4 was released and yet i don't see any update 
and it seem to be that there is nothing in the stable ppa of firefox that i found.

Thanks in advance.

---

### Post by wilee-nilee on 2010-06-23
Do you ever use the web for questions?

---

### Post by aviramof on 2010-06-23
I don't follow you.

---

### Post by wilee-nilee on 2010-06-23
> **aviramof said:**
> I don't follow you.

Hmm, why am I not surprised.

---

### Post by aviramof on 2010-06-23
Could you please give me a straight answer and stop being so rude?

---

### Post by Rubi1200 on 2010-06-23
Perhaps this might help:

[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by mikewhatever on 2010-06-23
The stable version of Firefox 3.6.4 was released yesterday, June 22.
From 3.6.4 release notes:
```
v.3.6.4, released June 22nd, 2010
```
[http://www.mozilla.com/en-US/firefox/3.6.4/releasenotes/](http://www.mozilla.com/en-US/firefox/3.6.4/releasenotes/)

---

### Post by aviramof on 2010-06-23
> **mikewhatever said:**
> The stable version of Firefox 6.3.4 was released yesterday, June 22.

I am aware of it but the stable ppa have not being updated in 8 weeks or more.
[https://launchpad.net/~mozillateam/+archive/firefox-stable]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable")

And even there web site is already have the Firefox 6.3.4 so why is it taking so long to release an update?

---

### Post by wojox on 2010-06-23
> **aviramof said:**
> It's been quite a while since firefox 3.6.4 was released and yet i don't see any update 
and it seem to be that there is nothing in the stable ppa of firefox that i found.

Thanks in advance.

If the Firefox doesn't why would the ppa's?

I've been running 3.6.4 For about for about five months now and there have hardly been any updates.

Where did you download from?

---

### Post by aviramof on 2010-06-23
But the Firefox does have been updated what you were using was probably not an official release but a testing version but yesterday 
an official and stable version was released and if you check the stable ppa i gave you can see that it's still 3.6.3 there.

[https://launchpad.net/%7Emozillateam/+archive/firefox-stable]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable")

You can also see it in post #7.

---

### Post by mikewhatever on 2010-06-23
Could be connected to [-->this<--]("http://blog.qa.ubuntu.com/node/94"). They've been testing the supported Ubuntu releases, pending the upgrade of all to 3.6.4. I imagine they must be quite busy. Curiously enough, the URL you posted has '**archive**/firefox-**stable**' in it.

---

### Post by wojox on 2010-06-23
> **aviramof said:**
> But the Firefox does have been updated what you were using was probably not an official release but a testing version but yesterday 
an official and stable version was released and if you check the stable ppa i gave you can see that it's still 3.6.3 there.

[https://launchpad.net/%7Emozillateam/+archive/firefox-stable]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable")

You can also see it in post #7.

That's from the ppa's. I never said it didn't get updates. I said there haven't been a lot of update..

---

### Post by aviramof on 2010-06-23
This is the only ppa google can find when i search firefox stable ppa:
[http://www.google.com/search?client=ubuntu&channel=fs&q=firefox+stable+ppa&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=firefox+stable+ppa&ie=utf-8&oe=utf-8)

If you know about other ppa address that would be great and thanks for the blog information.

> **wojox said:**
> That's from the ppa's. I never said it didn't get  updates. I said there haven't been a lot of update..

There is an update now:
[http://www.mozilla.com](http://www.mozilla.com)

And by the way a second ago one of my sites posted 
[B][URL="http://www.softexia.com/graphics-design/photo-editing-resizing/827-gimp.html"]GIMP  2.6.9 - Final/ GIMP 2.7.0 Rev 28070 I Want to see how long it takes for it to be updated.
[/URL][/B]

---

### Post by mikewhatever on 2010-06-23
I've recently installed 3.6.4 from the following
```
deb http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu karmic main

```
If you don't have Karmic installed, adjust the lines accordingly.

---

### Post by aviramof on 2010-06-23
Thanks but it's not working i'll guess i'll continue waiting for the ppa or the main repos to update.

---

### Post by mexicanseaf00d on 2010-06-23
this helped me:
[http://ubuntuforums.org/showthread.php?t=330386](http://ubuntuforums.org/showthread.php?t=330386)

I used the ubuntuzilla way and it seems to work perfectly

---

### Post by aviramof on 2010-06-23
Thanks i downloaded the deb file and the local translation file.

---

### Post by XSAlliN on 2010-06-23
They fixes some problems with flash, which is great. :guitar:

---

### Post by JanusDC on 2010-06-23
```
sudo add-apt-repository ppa:ubuntu-mozilla-security/ppa \
     && sudo apt-get update \
     && sudo apt-get upgrade
```

---

### Post by malspa on 2010-06-23
You can avoid the whole issue and get Firefox from outside of the repositories.  Download it directly from the Mozilla site.  They have instructions there for Linux users.  I've been using that one for a few years now in every distro.  That gives you updates when they come out, you don't have to wait for them to show up in your distro's repos.  Perhaps it's "not recommended," but it works fine here.

---

### Post by Excalibre on 2010-06-23
> **malspa said:**
> You can avoid the whole issue and get Firefox from outside of the repositories.  Download it directly from the Mozilla site.  They have instructions there for Linux users.  I've been using that one for a few years now in every distro.  That gives you updates when they come out, you don't have to wait for them to show up in your distro's repos.  Perhaps it's "not recommended," but it works fine here.
The problem is the font rendering is hell because it doesn't do subpixel antialiasing. I've tried the instructions I've found around here on how to do that, and none of them have helped me.

I guess it's my fault I use Linux, though, so I'll just wait meekly and hope there's an official Ubuntu-ized version sometime soon. :(

---

### Post by chrisccoulson on 2010-06-23
We're currently in the process of preparing 3.6.4 for all the supported releases, but there are still a few issues to resolve. In the meantime, you can use the ubuntu-mozilla-security PPA (someone has already given instructions for that in this thread). The packages in there are pretty much what we expect to release to the archive (as long as we don't find any last minute issues), and I don't expect them to change no

(Edit: I should emphasize that whilst the previous sentence is true for Lucid, there will be a lot of packages uploaded to the PPA for karmic tomorrow as we port applications from xulrunner 1.9.1 to 1.9.2. This isn't needed for Lucid, which already uses 1.9.2, and most of the work has already been completed for Hardy and Jaunty)

---

### Post by nanotube on 2010-06-24
Try the ubuntuzilla repository - .deb packs of the official mozilla releases:
[http://ubuntuzilla.sourceforge.net](http://ubuntuzilla.sourceforge.net)

---

### Post by FrancoNero on 2010-06-24
btw neither mozilla.com nor ubuzilla offer 64bit support (yet).... so off to the mozilla/security ppa ;)

---

### Post by malspa on 2010-06-24
> **Excalibre said:**
> The problem is the font rendering is hell because it doesn't do subpixel antialiasing.


This "problem" hasn't been an issue here.  Maybe I just don't notice it?

---

### Post by Excalibre on 2010-06-24
> **malspa said:**
> This "problem" hasn't been an issue here.  Maybe I just don't notice it?
Could be, or else it's not occurring for you. (I'm running 64-bit Lucid. Or maybe it has to do with something else about my system.) I tried some fixes I found but none of them worked -- it looks like it's doing only regular anti-aliasing rather than subpixel, and it's obviously different compared to the official 3.6.3 package from Ubuntu (or, for that matter, compared to Chrome.) It just looks awful. I also couldn't get Youtube to work at all but that could just be some issue with me having symlinked the plugin directory wrong or something like that.

---

### Post by dabelser on 2010-06-24
[FONT="Georgia"]**JanusDC on page 2, your upgrade method worked and worked very quickly.  Thank you.**[/FONT]

These are the steps I repeated from the post:
1.) Make sure that the synaptic package manager is not currently running.
2.) Make sure that Firefox is not currently running.
3.) Open a terminal session.
4.) Paste this string of commands at the prompt and hit Enter.

[I]sudo add-apt-repository ppa:ubuntu-mozilla-security/ppa && sudo apt-get update && sudo apt-get upgrade
[/I]
5.) Supply the password as needed.

Even with my laughably "fast" USA 8mbps cable connection, the upgrade took me less than two minutes.  You will probably have a faster experience, if you are in a European or Asian locale.

---

### Post by Budchekov on 2010-06-26
> **wilee-nilee said:**
> Do you ever use the web for questions?

I finally registered because this type of post is all too familiar around here.
The question is easy and clear, when will FF 3.6.4 be available as a simple Ubuntu update. Read: :**Without a bunch of farting around.**
The OP  initially gets snide remarks as a reply to his/her question.
Users like that do **nothing but  dissuade folks learning how to use or thinking of trying Ubuntu**, they need weeding out and removal from this forum. 
I have come to believe that there's a large element of smug snobs that don't want new users permeating Linux discussions, long winded answers to simple questions,( often it's like drawing blood out of a stone) rudeness and just general arrogance is all too familiar.
'Keep it a mystery and they'll go away'.....well I have news for those unpleasant egghead geeks, It aint that hard to learn in spite of you, some of us are willing to persevere. Get off the high horse I know what you're up to...and to Ubuntu's detriment it's not encouraging new users.

---

### Post by mikewhatever on 2010-06-26
Budchekov, the update will be available when it's tested and ready. From past experience, it usually takes about a week after Mozilla's release it out.

---

### Post by Budchekov on 2010-06-26
Thanks mikewhatever, I also realize there are a whole lot of 'good guys' in the community, where would I be without you. :)

@Looks like 3.6.4 will  be a pass 3.6.6 is being hurried out.

---

### Post by Kirk M on 2010-06-28
For everybody's info, I've been doing some research and there's a  problem with the timing of the new OOPP ("Out Of Process Plugins" that  is incorporated in 3.6.4) for Flash causing the plugin to crash if  waiting time for any Flash process (Flash based application, uploader,  etc) that takes over 10 seconds which is the default setting. Because of  this, Firefox 3.6.6 has recently been released by Mozilla which I  believe changes this timeout to 30 seconds.

So basically every time the Firefox devs fix problems like this and then  release a new official "point" release so quickly after the previous  version (in this case, Firefox 3.6.4), Ubuntu devs have to reconnoiter  and basically begin again with the building of the new Firefox version  before they shove it to the update servers. And as most here know, this  takes time since there is more than one versions and types of Ubuntu  that require separate builds.

Patience is and all that... ):P

---

### Post by chrisccoulson on 2010-06-28
> **Kirk M said:**
> For everybody's info, I've been doing some research and there's a problem with the timing of the new OOPP ("Out Of Process Plugins" that is incorporated in 3.6.4) for Flash causing the plugin to crash if waiting time for any Flash process (Flash based application, uploader, etc) that takes over 10 seconds which is the default setting. Because of this, Firefox 3.6.6 has recently been released by Mozilla which I believe changes this timeout to 30 seconds.

So every time the Firefox devs fix problems like these and then release a new official "point" release so quickly after the previous version (in this case, Firefox 3.6.4), Ubuntu devs have to reconnoiter and basically begin again with the building of the new Firefox version before they shove it to the update servers. And as most here know, this takes time since there is more than one versions and types of Ubuntu that require separate builds.

Patience is and all that... ):P

I've already uploaded 3.6.6 to the [ubuntu-mozilla-security PPA]("https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa") for all Ubuntu releases ;)

---

### Post by Kirk M on 2010-06-28
> **chrisccoulson said:**
> I've already uploaded 3.6.6 to the [ubuntu-mozilla-security PPA]("https://launchpad.net/%7Eubuntu-mozilla-security/+archive/ppa") for all Ubuntu releases ;)

Okay, so maybe not such a long time after all. :lolflag:

---

