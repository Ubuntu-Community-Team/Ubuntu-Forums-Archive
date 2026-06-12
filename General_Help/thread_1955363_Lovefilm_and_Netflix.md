---
title: "Lovefilm and Netflix"
date: 2012-04-09
forum: General Help
---

### Post by boo12345679 on 2012-04-09
Help ! I will need to move to windows as it seems to be impossible to stream Netflix or Lovefilms using Ubuntu.  This is pretty bad news.  Can anyone else assist ?  Alternatively is there anything that can be done via the governance people to bring this to the attention of the providers.  

It looks like they have fallen out of love with Linux.  This is a great pain in the backside.

Alternatively if someone can post the weakness of silverlight perhaps it will shatter their illusion of more secure microsoft products.

---

### Post by CatKiller on 2012-04-09
They are aware that their move to Silverlight leaves their Linux streaming customers in the cold, but they estimate that there aren't enough of them to make a difference. To be fair, they're probably right. And they probably got a big chunk of cash from Microsoft for doing so to enable them to crow about how everyone's using Silverlight, so it must be brilliant.

As a business decision it makes a lot of sense. Sucks a bit, though, especially because the machines that actually serve up the video feeds are probably running Linux.

---

### Post by leecheroflife on 2012-04-09
Long way for a shortcut, But I have an XP Virtual machine for netflix

---

### Post by raja.genupula on 2012-04-09
try moonlight , i came to read that it supports only limited versions of slight . but try it ,if it works fine to you then no need of moving to windows

---

### Post by jerome1232 on 2012-04-09
> **raja.genupula said:**
> try moonlight , i came to read that it supports only limited versions of slight . but try it ,if it works fine to you then no need of moving to windows

Moonlight won't work due to the drm in netflix. I have a virtual machine with xp on it that I fire up for netflix.

---

### Post by cybpabeofm on 2012-04-10
I think I found a fix.
On wines appdb the most recent silverlight appears to be installable and runable ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=24783](http://appdb.winehq.org/objectManager.php?sClass=version&iId=24783))
So if one installed firefox for windows, then silverlight they might be able to get movies.
My box doesnt have wireless yet, Ill test this then tell you guys what I get! \\:D/

Anyone else think microsoft and their damn DRM is twisted? :twisted:

---

### Post by idoitprone on 2012-04-10
> **cybpabeofm said:**
> I think I found a fix.
On wines appdb the most recent silverlight appears to be installable and runable ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=24783](http://appdb.winehq.org/objectManager.php?sClass=version&iId=24783))
So if one installed firefox for windows, then silverlight they might be able to get movies.
My box doesnt have wireless yet, Ill test this then tell you guys what I get! \\:D/

Anyone else think microsoft and their damn DRM is twisted? :twisted:

It is neither microsoft fault nor Netflix. It the friken content holders who impose ridiculous rules that force us to do these strange workaround. Microsoft only provide the tools, but the content holders forced Netflix to implement them

---

### Post by jerome1232 on 2012-04-10
> **idoitprone said:**
>  Microsoft only provide the tools,

Microsoft chose not to provide the tools for Linux, that is the point. Truly Microsoft is the one to give the stink eye. If they'd license the drm portion of silverlight and assist with integrating it into moonlight (they are already cooperating with the development of moonlight) Then we wouldn't have this problem.

I doubt the content providers influenced Netflix, I'm pretty sure they [Netflix] were interested in not having the content pirated in and of themselves, Netflix wants you to subscribe and stay that way, not subscribe for a month so you can pirate all their content and cancel.

Just as Microsoft chooses to not provide any support for open sourced file-systems, just as they choose to provide lackluster support for open sourced document formats, etc...

---

### Post by idoitprone on 2012-04-10
> **jerome1232 said:**
> Microsoft chose not to provide the tools for Linux, that is the point. Truly Microsoft is the one to give the stink eye. If they'd license the drm portion of silverlight and assist with integrating it into moonlight (they are already cooperating with the development of moonlight) Then we wouldn't have this problem.

I doubt the content providers influenced Netflix, I'm pretty sure they [Netflix] were interested in not having the content pirated in and of themselves, Netflix wants you to subscribe and stay that way, not subscribe for a month so you can pirate all their content and cancel.

Just as Microsoft chooses to not provide any support for open sourced file-systems, just as they choose to provide lackluster support for open sourced document formats, etc...

a drm cannot exist as a opensource product. It is a fundamental problem with open source. Microsoft does not have any control on the integration of the drm when it becomes open source, since anyone is able to modify it source code.

I have to agree with you on the open sourced file-systems. Arrrgs i wish mac and windows at least adopted ext4. arrrg

Content provides have netflix on a strangle hold. Cable and content providers are trying to kill netflix. It it is the reason why netflix have a 60 percent price increase

---

### Post by cybpabeofm on 2012-04-10
Well then why doesnt microsoft just give us a silverlight for linux. Oh, yeah thats right we didnt pay for it.:mad::mad::mad:

---

### Post by jerome1232 on 2012-04-10
> **idoitprone said:**
> a drm cannot exist as a opensource product. It is a fundamental problem with open source. Microsoft does not have any control on the integration of the drm when it becomes open source, since anyone is able to modify it source code.


The drm itself doesn't have to be open sourced to be integrated into moonlight, I admit I don't know a whole lot about it, but I'd assume Microsoft would have to provide some sort of api and a binary so that moonlight could work with the drm. Silverlight has been ported to OS X (drm and all), so it's possible. I think it's a matter of "is the work worth the reward?", and Microsoft has decided that no, it's not worth it.

The drm has also been licensed out to embedded systems, such as all 3 major consoles, most blu-ray players etc. It's is simply a matter of Microsoft porting the code.

> Well then why doesnt microsoft just give us a silverlight for linux. Oh, yeah thats right we didnt pay for it Reiterating, silverlight has been ported to OS X.

---

### Post by EoRaptor013 on 2012-04-18
Answer me this: Netflix runs just fine on my Android phone (htc Evo 4G). Ergo, Netflix runs on Linux. Would it really be that hard for someone in the Linux community to port the phone app to a desktop app?
:popcorn:

---

### Post by lisanels47 on 2012-04-18
I also run Windows XP in a virtualbox for those pesky "Windows-only" apps... Use a stripped down version of XP if you have the license, and it runs really good in a window on my desktop.

---

### Post by jerome1232 on 2012-04-18
> **EoRaptor013 said:**
> Answer me this: Netflix runs just fine on my Android phone (htc Evo 4G). Ergo, Netflix runs on Linux. Would it really be that hard for someone in the Linux community to port the phone app to a desktop app?
:popcorn:

Android uses a modified Linux kernel, so the kernel is different, how different? I don't know. It's also a licensing issue, Microsoft has not licensed that drm code to run on Linux Desktops.

---

### Post by MonkeyPaw on 2012-04-18
The lack of Netflix compatibility was an issue for me for a while--until we canceled Netflix. We just realized that we hadn't used it in 2 months. Consequently, I also unplugged our Wii, since it was basically a Netflix streaming machine.

I know it's not the same, but we just rent stuff through our local library. You often have to wait a few weeks, but it's free unless you forget to turn it in on time or somehow manage to destroy the discs. We've watched entire TV series that way.

---

### Post by al111 on 2012-04-18
+1 running windows xp in a virtualbox to stream Netflix-

---

### Post by gencon on 2012-09-17
Has there been any movement or advance on this in the 5 months since the last post on the issue?

I recently bought a new laptop and want to install Ubuntu on it instead of Windows 7 which came pre-installed. My only reservation is that I'd quite like to stream the occasional LoveFilm movie on it. I would consider installing VirtualBox and running XP (for which I have a licensed version) as a virtual machine and use that (since others have reported that it works that way) but I'd much prefer the simplicity of a native Linux solution.

Thanks all.

---

### Post by SeijiSensei on 2012-09-17
This problem will never be resolved.  The studios do not want them to support Linux, so Netflix cannot either.  It is pretty obvious that Netflix will never release a Linux-compatible player.  There is no technical limitation that keeps them from doing so; there is just no will to do so.

---

### Post by sreeslinux on 2012-11-21
Looks like they have solved the issue and got it working on Wine.
[http://www.omgubuntu.co.uk/2012/11/how-to-use-netflix-on-ubuntu](http://www.omgubuntu.co.uk/2012/11/how-to-use-netflix-on-ubuntu)

---

### Post by ADTJ on 2012-12-03
That link was definitely interesting, I had a quick look and downloaded the player, I wonder why they locked out the firefox stuff such that you can only easily access Netflix.
Unfortunately, our netflix subscription had recently expired, so I thought I'd try it for Lovefilm.
I made a quick HTML file to link to LoveFilm, and used Ctrl+O from the Netflix firefox to access it.

On Lovefilm instant, the silverlight thingy would appear and it would look like it was loading but then firefox would just crash. I don't know if this is just my machine or not but it may be worthwhile others taking a look.

If it works, then glad to have helped, 

if not, then sorry to have wasted your time, haha...

---

### Post by evilsoup on 2012-12-03
You can get to other websites within the netflix 'app' by hitting alt+d; but yeah, I've found that lovefilm instant doesn't work at all. Then again, I'm on a netbook, maybe those with more high-powered computers might have better luck.

---

### Post by ADTJ on 2013-01-19
Just FYI, I just tried it again now. (There have been a few updates since). Lovefilm works now. I just loaded Inception =D Hooray

---

