---
title: "ubuntu on android"
date: 2012-03-13
forum: General Help
---

### Post by tbhatia4 on 2012-03-13
hello
just outta curiosity i want to try ubuntu on my android device
galaxy s
i don't care about warranty kindly suggest me if there is a way possilble

---

### Post by tbhatia4 on 2012-03-13
my android device meets all minimum specs provided on ubuntu's site for an android device to run ubuntu

---

### Post by Mark Phelps on 2012-03-13
Once again ... what I read from the Ubuntu on Android site clearly indicates that what REALLY is happening is that Android is running a Unity-like desktop, not Ubuntu itself.

This is the same idea as replacing the Unity desktop on your Ubuntu-running PC with Gnome Classic -- it changes the desktop, not the underlying OS.

---

### Post by Paqman on 2012-03-13
Sorry, no can do. Ubuntu for Android hasn't been released publicly yet, so there's nothing to download.

---

### Post by rg4w on 2012-03-13
> **Paqman said:**
> ...Ubuntu for Android hasn't been released publicly yet...
If it's based on GPL's code isn't that a requirement?

---

### Post by tbhatia4 on 2012-03-14
> **Paqman said:**
> Sorry, no can do. Ubuntu for Android hasn't been released publicly yet, so there's nothing to download.

Sad I am eager to try this.....

---

### Post by kimikelku on 2012-03-14
Its not official but it works like a charm on a old gw620.
[http://forum.xda-developers.com/showthread.php?t=1390351&highlight=ubuntu](http://forum.xda-developers.com/showthread.php?t=1390351&highlight=ubuntu)

---

### Post by tbhatia4 on 2012-03-14
> **Mark Phelps said:**
> Once again ... what I read from the Ubuntu on Android site clearly indicates that what REALLY is happening is that Android is running a Unity-like desktop, not Ubuntu itself.

This is the same idea as replacing the Unity desktop on your Ubuntu-running PC with Gnome Classic -- it changes the desktop, not the underlying OS.

i don't agree
i have seen a demo video....
even if its only the desktop we are ale to install native ubuntu applications over this
so it wont make much of a difference 
its a great idea and should work wonders
my wishes with colonial :D

---

### Post by tbhatia4 on 2012-03-14
here's the link see for yourself
[http://www.youtube.com/watch?v=AyeFcldavTk](http://www.youtube.com/watch?v=AyeFcldavTk)

---

### Post by tbhatia4 on 2012-03-14
> **kimikelku said:**
> Its not official but it works like a charm on a old gw620.
[http://forum.xda-developers.com/showthread.php?t=1390351&highlight=ubuntu](http://forum.xda-developers.com/showthread.php?t=1390351&highlight=ubuntu)

great news

---

### Post by tbhatia4 on 2012-03-14
> **Mark Phelps said:**
> Once again ... what I read from the Ubuntu on Android site clearly indicates that what REALLY is happening is that Android is running a Unity-like desktop, not Ubuntu itself.

This is the same idea as replacing the Unity desktop on your Ubuntu-running PC with Gnome Classic -- it changes the desktop, not the underlying OS.

hey mark plz check this out
[http://www.engadget.com/2012/02/24/ubuntu-for-android-hands-on/](http://www.engadget.com/2012/02/24/ubuntu-for-android-hands-on/)

---

### Post by UnknownFearNG on 2012-03-14
I for one am VERY excited for this. Does anyone have a release date?

---

### Post by Mark Phelps on 2012-03-14
> **tbhatia4 said:**
> hey mark plz check this out
[http://www.engadget.com/2012/02/24/ubuntu-for-android-hands-on/](http://www.engadget.com/2012/02/24/ubuntu-for-android-hands-on/)


Thanks all for the corrections ...

I actually saw some new articles on the Linux Today forums about this and also about some other approaches.  

This approach evidently configures your Android device so it runs Android normally, and when tethered to a PC or Tablet, runs Ubuntu.  Pretty cool idea.

There is also another approach there that installs Ubuntu OS to the phone.  That is NOT the approach that Ubuntu for Android currently uses.

Strongly suggest everyone interested in this go to the Linuux Today forums and read through the different articles.

---

### Post by tbhatia4 on 2012-03-14
> **Mark Phelps said:**
> Thanks all for the corrections ...

I actually saw some new articles on the Linux Today forums about this and also about some other approaches.  

This approach evidently configures your Android device so it runs Android normally, and when tethered to a PC or Tablet, runs Ubuntu.  Pretty cool idea.

There is also another approach there that installs Ubuntu OS to the phone.  That is NOT the approach that Ubuntu for Android currently uses.

Strongly suggest everyone interested in this go to the Linuux Today forums and read through the different articles.
plz post the link for linux today forum thread

---

### Post by Mark Phelps on 2012-03-14
> **tbhatia4 said:**
> plz post the link for linux today forum thread

There are several threads, each with different information.

The best way to find them all is to do the following:
1) type Linux Today into your Browser URL box
2) scroll down through the list of topics until you find the one dealing with Ubuntu on Android
3) open that and, at the bottom, there are additional links covering other approaches to using Ubuntu and Android.

---

### Post by tbhatia4 on 2012-03-14
> **Mark Phelps said:**
> How hard is it to type Linux Today into your Browser URL box?

i was asking for the specific thread bro never mind leave that
i have come across many though

---

### Post by tbhatia4 on 2012-03-14
> **UnknownFearNG said:**
> I for one am VERY excited for this. Does anyone have a release date?

they are not planning to release this as another ubuntu variant colonial is in talks with many phone manufacturers and wants to embed ubuntu as a factory install
they are absolutely right with this as one can loose warranty if he tries rooting the phone by himself

---

### Post by Paqman on 2012-03-14
> **rg4w said:**
> If it's based on GPL's code isn't that a requirement?

If it is GPL they'll have to release source code at some point, but unless you're able to compile it yourself that's not necessarily much use to you. A bit like the way Red Hat release RHEL as source, but charge megabucks for the actual binaries.

You never know, they might release it for public consumption in a useful form. But it's not a requirement of the GPL that they do so.

So far Ubuntu for Android is targeted at phone OEMs, not individuals installing it on their existing handsets. Canonical might be keen on developing a community around it though, so you might see it being let out into the wild. Who knows?

---

### Post by tbhatia4 on 2012-03-15
till now there is no news about any handset manufacturer joining with ubuntu as of yet hoping for this sooooon

---

### Post by Klas Lindberg on 2012-03-17
I'm hoping that this initiative will make Android behave more like  regular .deb packable libraries/applications in the long run. Something  that can be installed using apt-get on a regular desktop machine, not  just specially prepared devices.

Overall, I'm very curious about the technical details of this project. A short selection of topics:

[LIST]
[*]Is  Ubuntu run in a chroot, with standard Android apps modified to  communicate with the desktop? This would be the easiest to implement but  also the most limited. On the other hand, re-targeting Android on  glibc and OpenJDK is a huge undertaking and a compatibility minefield.
[/LIST]

[LIST]
[*]How  is Ethernet set up in docked mode? The default setting from Google  seems to be that the device uses RNDIS (instead of CDC-ECM), assigns  itself the IP number 192.168.42.129 and announces the presence of a  DHCP server. The PC then uses that server to assign an IP to *its* end of the connection. This works nicely on two assumptions:
[/LIST]

[LIST]
[*]
[LIST]
[*]Only  one device will be connected to a PC at the same time. If more than one  is connected, it's OK that the PC can't tell them apart based on IP  address. (Basically nothing above ARP level works reliably.)
[*]The  device will never need to connect to the internet through the PC's LAN.  It always uses its modem for data traffic and that's it.
[/LIST]
 
[/LIST]
[INDENT]I really *do* need to tell connected devices apart based on IP address (for work related reasons), so I'd much prefer that the device *asks* for an IP address (using DHCP). If that doesn't work, the device can fall back on the current behavior.
[/INDENT]
[LIST]
[*]How  is the product configured? Regular Android uses Repo and a monolithic  build system (not talking about Market apps here). Regular Ubuntu uses  Debian packages and binary integration. The two models don't play well together.
[/LIST]
Anyway, very exciting project.

---

### Post by MountainX on 2012-03-20
> **Paqman said:**
> Sorry, no can do. Ubuntu for Android hasn't been released publicly yet, so there's nothing to download.

This "behind closed doors" development process is opposed to the spirit of open source. 

**Code should be developed in the open.**

This issue is one reason why Google is being criticized over Android. Indeed, many groups say that Android is not even a *true* open source project*. I hope someone starts demanding that Ubuntu uphold its open source principles on this Android project. There should be some kind of community preview already. Development should be happening in the open -- now.

Here's a quote from the first reference below:
> Facebook&#8217;s Joe Hewitt, the Firefox co-creator who is now rumored to  be working on a Facebook-branded mobile OS based on Android, chimed in  over Twitter. Hewitt says the lack of transparency in the Android  development process makes it &#8220;no different than iOS to me,&#8221; adding, &#8220;[open source means sharing control with the community]("http://twitter.com/joehewitt/statuses/27878912110"), not show and tell.&#8221;


 The next day, [Hewitt followed up]("http://joehewitt.com/post/android-and-open-source/") with a blog post clarifying his remarks.
 &#8220;It kills me to hear the term &#8216;open&#8217; watered down so much. It bothers  me that so many people&#8217;s first exposure to the idea of open source is  an occasional code drop, and not a vibrant community of collaborators  like I discovered ten years ago with Mozilla.&#8221;


 He also recommends people look at Google&#8217;s Chrome OS project, which  is being run with a level of transparency and community involvement  largely absent from Android, and which is a better representation, he  says, of Google&#8217;s values.


 Unfortunately, even if Google were to develop Android in the open, as  the Mozilla foundation does with Firefox, it probably wouldn&#8217;t help  Android be any more open.
 While Google&#8217;s approach may be a disingenuous use of the word open &#8212;  as Hewitt says, Google is doing &#8220;bare minimum to meet the definition of  open&#8221; ...*References:
[http://www.wired.com/epicenter/2010/10/is-android-open/](http://www.wired.com/epicenter/2010/10/is-android-open/)
[http://arstechnica.com/open-source/news/2011/08/study-android-is-least-open-of-open-source-mobile-platforms.ars](http://arstechnica.com/open-source/news/2011/08/study-android-is-least-open-of-open-source-mobile-platforms.ars)
[http://www.visionmobile.com/research.php#OGI](http://www.visionmobile.com/research.php#OGI)
[http://www.extremetech.com/mobile/108911-is-android-the-most-closed-open-source-project](http://www.extremetech.com/mobile/108911-is-android-the-most-closed-open-source-project)
[http://www.guardian.co.uk/technology/2011/sep/19/android-free-software-stallman](http://www.guardian.co.uk/technology/2011/sep/19/android-free-software-stallman)

---

### Post by tbhatia4 on 2012-03-22
It Doesn't make any difference if its open source or closed 
most of us don't even know  coding and can't help there 
as long it's ubuntu it's meant to be free that's it

---

### Post by MountainX on 2012-03-22
> **tbhatia4 said:**
> It Doesn't make any difference if its open source or closed 
most of us don't even know  coding and can't help there 
as long it's ubuntu it's meant to be free that's it

You might not know how to code yourself, but if the project is open source you will benefit from the work done by those who do know how to code. Open source is about a lot more than zero-cost (free) software. 

A free (zero-cost) but closed source project lacks ***freedom***. The most important meaning of "free" software is related to the freedom we have to use it as we wish. It's not about no-cost software. It is all about rights, freedom and transparency.

If the project is closed source, you miss all the community-driven development that happens in open projects and you also suffer problems such as potential vendor lock-in, lack of transparency about bugs, etc.

If the project is partially open, you only get partial benefits. It appears that Ubuntu is not taking a truly open source approach to its Android project, and that signals problems if you ask me.

---

### Post by 3djake on 2012-03-22
another good one to try is [http://replicant.us/](http://replicant.us/)

but you need 

HTC Dream/HTC Magic
Nexus One
Nexus S

---

### Post by rg4w on 2012-03-22
> **tbhatia4 said:**
> as long it's ubuntu it's meant to be free that's it
[http://en.wikipedia.org/wiki/Free_software#Definition](http://en.wikipedia.org/wiki/Free_software#Definition)

---

