---
title: "Install Thunderbird 3"
date: 2009-12-09
forum: General Help
---

### Post by blazemore on 2009-12-09
How can I install Thunderbird 3 via a deb file or PPA, rather than the tarball provided on the official website?

---

### Post by balaknair on 2009-12-09
This PPA has Thunderbird-3.0 RC3

[https://launchpad.net/~micahg/+archive/mozilla-beta](https://launchpad.net/~micahg/+archive/mozilla-beta)

---

### Post by varsamakos on 2009-12-10
This version in PPA works fine but is it the same as the official one from mozilla ?

---

### Post by EndPerform on 2009-12-10
> **varsamakos said:**
> This version in PPA works fine but is it the same as the official one from mozilla ?

If it's beta 3, then no, it's an older version of Thunderbird 3.

---

### Post by rogerdean on 2009-12-10
I've been looking around, and can't yet find a PPA or a .deb for the final stable non-development version of TB3. If some kind soul makes it available, please let us know here!
Many thanks
Roger

---

### Post by aysiu on 2009-12-10
> **rogerdean said:**
> I've been looking around, and can't yet find a PPA or a .deb for the final stable non-development version of TB3. If some kind soul makes it available, please let us know here!
Many thanks
Roger
In the meantime, this may help:
[http://www.psychocats.net/ubuntu/thunderbird](http://www.psychocats.net/ubuntu/thunderbird)

---

### Post by nanotube on 2009-12-10
> **aysiu said:**
> In the meantime, this may help:
[http://www.psychocats.net/ubuntu/thunderbird](http://www.psychocats.net/ubuntu/thunderbird)

or this:
[http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)
:)

---

### Post by aysiu on 2009-12-10
> **nanotube said:**
> or this:
[http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)
:)
I have it linked to at the bottom of the page, along with the PPA.

---

### Post by scouser73 on 2009-12-10
Delete post.

---

### Post by aysiu on 2009-12-10
> **scouser73 said:**
> Check here: [[COLOR="Red"]**Kabatology: A Single Line Command To Install Thunderbird 3 In Ubuntu**[/COLOR]]("http://www.kabatology.com/12/09/a-single-command-to-install-thunderbird-3-in-ubuntu/")
This may seem self-serving, but I wouldn't recommend that link.

First of all, it assumes you want the en-US version of Thunderbird. And second of all, it doesn't actually *install* Thunderbird. All it does is extract the compressed file to your home directory.

My link actually installs Thunderbird with a single command.

And nanotube's link also does so and is far more sophisticated (can update Thunderbird as well, prompts you for locale info, verifies the download).

---

### Post by scouser73 on 2009-12-10
> **aysiu said:**
> This may seem self-serving, but I wouldn't recommend that link.

First of all, it assumes you want the en-US version of Thunderbird. And second of all, it doesn't actually *install* Thunderbird. All it does is extract the compressed file to your home directory.

My link actually installs Thunderbird with a single command.

And nanotube's link also does so and is far more sophisticated (can update Thunderbird as well, prompts you for locale info, verifies the download).

Ahh right, I see.

---

### Post by nanotube on 2009-12-10
> **aysiu said:**
> I have it linked to at the bottom of the page, along with the PPA.

ah cool :)
btw, could you create the same page as you have for firefox and thunderbird, but for seamonkey? then you'll have a complete set of alternatives for ubuntuzilla. :)

---

### Post by Jerry N on 2009-12-10
Upgraded TB2 to TB3 on my Windows 7 drive.  Didn't like it - reinstalled TB2.  Don't think I will put it on my Ubuntu or Mint drive.

Jerry

---

### Post by natrium42 on 2009-12-11
> **Jerry N said:**
> Didn't like it
Haha, thank you for the detailed report XD

---

### Post by aysiu on 2009-12-11
> **nanotube said:**
> ah cool :)
btw, could you create the same page as you have for firefox and thunderbird, but for seamonkey? then you'll have a complete set of alternatives for ubuntuzilla. :) That would be. Maybe I'll get around to it.

---

### Post by Umang on 2009-12-11
Isn't there a PPA for all stable releases? Can I have TB3 Final Stable and not a daily build?

Thanks

Edit: Shouldn't it be here? : [https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa?field.series_filter=karmic](https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa?field.series_filter=karmic)

---

### Post by tobyS23 on 2009-12-12
Same issue here. I used the daily PPA for installing RCs, but now the final is out, I'd love to have stable releases only. Installing manually is not an option, since I don't want to take care about updating TB manually all the time.  Any solution for this? Guess there are more people desiring stable TB 3.0 for Karmic. Not?  Cheers, Toby

---

### Post by Agent Smith on 2009-12-12
Just install ubuntuzilla. Then follow the instructions on their website for installing the latest version of Thunderbird. This will take care of any updates. I have used this method for ages now and it works flawlessly. By the way if you dont like the new smart folder layout in t/bird just click view, folders, and select all instead of smart. All your emails and settings will be saved and transferred to the new t/bird.

---

### Post by Umang on 2009-12-12
Don't want to sound picky, but I want a PPA so that I can upgrade them using the Update Manager.

Anyone?

---

### Post by kindofabuzz on 2009-12-16
Here's the PPA for FF and TB daily Branch and Trunk builds.

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa) 

If you want to run a daily trunk or branch I personally think it's just easier to download the tars from Mozilla then just hit "Check for Updates" everyday to get the new builds instead of running update manager every day.

---

### Post by blazemore on 2009-12-16
Nono I don't want a bleeding edge dev branch!
I just want the version on the website in handy .deb format

---

### Post by kindofabuzz on 2009-12-16
> **blazemore said:**
> Nono I don't want a bleeding edge dev branch!
I just want the version on the website in handy .deb format

Then why not use the Ubuntuzilla script? It downloads the current vanilla build and even has an option to update it when a update is released.

---

### Post by Umang on 2009-12-16
Wouldn't it be much simpler if someone maintained a PPA of all the ***latest stable*** releases from Mozilla?

I'm a little irritated that there isn't any such thing and am going to go with ubuntuzilla, but that defeats the point of having Update Manager/Synaptic then if we need to update our applications from different locations...

---

### Post by kindofabuzz on 2009-12-16
> **Umang said:**
> Wouldn't it be much simpler if someone maintained a PPA of all the ***latest stable*** releases from Mozilla?

I'm a little irritated that there isn't any such thing and am going to go with ubuntuzilla, but that defeats the point of having Update Manager/Synaptic then if we need to update our applications from different locations...

Well why don't you start that PPA then? I don't see what's so hard about downloading it from Mozilla, extract it somewhere in your /home/, then just make a link to ~/<user>/thunderbird/thunderbird. Simple. The reason it's not in synaptic is because it just came out and has not been tested to work with Karmic yet. They don't just release stuff because it's new. If you want that, then install Sidux.

---

### Post by Umang on 2009-12-16
No, you've mistaken me. I actually understand the whole idea behind repositories.

The only reason I want a PPA is that I trust Mozilla as much as I trust Canonical, if not more. That's why I don't need Canonical to test Mozilla products before they give it to me. For other software, I like the fact that Canonical does its own tests.

What I want is to have the advantage of the package managers as well as the latest stable from Mozilla, which I am sure is very very safe and stable. (I'd question anyone who thinks that they are much better off having Canonical test Mozilla products).

Launchpad has PPAs for exactly this reason: if I want _certain_ upstream program that are either not in the repositories or are at an old version in the repositories, I can download the packages from the PPA and have them behave as if they were from the repos.

---

### Post by rogerdean on 2009-12-16
I'm with Umang, I'd love a .deb on a stick to carry around, or a PPA with mozilla releases. Is there any kind soul out there with the know-how to do either of these things?
Many thanks in advance
Roger

---

### Post by kindofabuzz on 2009-12-16
> **rogerdean said:**
> I'm with Umang, I'd love a .deb on a stick to carry around, or a PPA with mozilla releases. Is there any kind soul out there with the know-how to do either of these things?
Many thanks in advance
Roger

No one does it because there is really no reason to, when you can download the TAR from Mozilla and extract it and you're done.

---

### Post by rogerdean on 2009-12-16
yeah. it's clear that you don't see the point. so really i'm asking others that might like to help out...

---

### Post by jschneider on 2009-12-16
I am also looking for a PPA with the latest Mozilla *releases*. If anyone can get that up, i'll be very thankful.

---

### Post by running_rabbit07 on 2009-12-16
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

---

### Post by running_rabbit07 on 2009-12-16
> **kindofabuzz said:**
> No one does it because there is really no reason to, when you can download the TAR from Mozilla and extract it and you're done.

I installed via the tarball and it would not work on Jaunty. Adding the Mozilla PPA did work.

---

### Post by kindofabuzz on 2009-12-16
Running_rabbit I already posted that. they don't want branch or trunk build. they want final release in .deb form because it's hard to extract a file but easier to install a .deb. :rolleyes:

---

### Post by kindofabuzz on 2009-12-16
> **running_rabbit07 said:**
> I installed via the tarball and it would not work on Jaunty. Adding the Mozilla PPA did work.

I been running off a tarball for two years. Don't tell me they don't work. Just extract it and you get a folder, open the folder and click on firefox. you did something wrong. you think they make tarballs just for the fun of it?

---

### Post by running_rabbit07 on 2009-12-16
I do not understand why people get mad when other people do not want to install via their method. Installing a tarball can be a real pain for noobs, while a Deb installs perfectly with minimal interaction. Adding the PPA also allows the install to get updates from the source which is important with a new release being there may be security patches coming out in the near future. Adding the PPA takes longer, but it is the most thorough way to go.

We should be throwing in options and not getting upset when others ask for a different way.

---

### Post by running_rabbit07 on 2009-12-16
> **kindofabuzz said:**
> I been running off a tarball for two years. Don't tell me they don't work. Just extract it and you get a folder, open the folder and click on firefox. you did something wrong. you think they make tarballs just for the fun of it?

I was talking about the new Thunderbird, not Firefox. I did it right. I read the manual. I did the same process, step for step with Karmic and Jaunty. It worked on Karmic, but there were dependency problems with Jaunty that prevented it from properly installing.

You are barking at the wind. This is a help forum and you aren't being helpful.

---

### Post by karamu on 2009-12-16
> **running_rabbit07 said:**
> I do not understand why people get mad when other people do not want to install via their method. Installing a tarball can be a real pain for noobs, while a Deb installs perfectly with minimal interaction. Adding the PPA also allows the install to get updates from the source which is important with a new release being there may be security patches coming out in the near future. Adding the PPA takes longer, but it is the most thorough way to go.

We should be throwing in options and not getting upset when others ask for a different way.

Agreed completely. I went to the Mozilla website and got the tarball but it's not really what I want. One of the things I love about Ubuntu is that all the updates get done together (as long as you install via repositories). So, I agree I would like a PPA of the stable releases so that I don't need to worry about updates.

Kindofabuzz you aren't really helping things. I came across this thread by googling for a Thunderbird 3 PPA so there obviously are people who want that option.

---

### Post by scouser73 on 2009-12-16
**Off topic** I find installing the tarball very easy, but I agree that there should be a (.deb) file provided by Mozilla.

If you want to install the tarball then follow these instructions.

Download the **.tar.bz2** file from

[[COLOR="Red"]**Mozilla Messaging: Thunderbird 3**[/COLOR]]("http://en-gb.www.mozillamessaging.com/en-GB/thunderbird/")

**1** - Extract the **.tar.bz2** file

**2** - Enter **gksudo nautilus** in terminal

**3** - Go to the folder **/opt**

**4** - Copy & paste the Thunderbird file that you extracted to **/opt**

**5 -** Enter these commands into **Terminal** > **sudo -i**

*Enter your password if asked.*

> **cd /opt**
> **chown -R username filename**

[COLOR="Red"]**Obviously the username refers to you, and the filename to the file**[/COLOR]

**6** - Go to **System > Preferences > Main Menu**

**7** - In Main Menu, click on **New Item**

**8** - In the **Name** field enter **Mozilla Thunderbird Mail/News**

**9** - In the **Command** field enter **/opt/thunderbird/thunderbird**

**10** - In the **Comment** field enter **Mozilla Thunderbird Mail/News**

[[IMG]http://img121.imageshack.us/img121/7329/screenshot2c.png[/IMG]](http://img121.imageshack.us/img121/7329/screenshot2c.png/)

---

### Post by running_rabbit07 on 2009-12-16
^^^^^^^That is a great tarball howto.

---

### Post by Endolith on 2009-12-16
Now where's the .deb howto for normal people who don't want to use the tarball?

---

### Post by running_rabbit07 on 2009-12-16
> **Endolith said:**
> Now where's the .deb howto for normal people who don't want to use the tarball?
I guess nobody has made one yet. I installed via the PPA method. I like the new thunderbird, it looks better.

---

### Post by Umang on 2009-12-16
This is the PPA we are all looking for: [https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa) 

BUT, and unfortunately there has to be a "but", this does not have TB3. This is surprising, because FF3 was put on this on the very same day that it was released. Don't know why TB3 hasn't got the same treatment. 

Since this PPA is supposed to be what we want it to be, do you think we should write to the maintainer?

---

### Post by running_rabbit07 on 2009-12-17
> **Umang said:**
> This is the PPA we are all looking for: [https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa]("https://launchpad.net/%7Eubuntu-mozilla-security/+archive/ppa") 

BUT, and unfortunately there has to be a "but", this does not have TB3. This is surprising, because FF3 was put on this on the very same day that it was released. Don't know why TB3 hasn't got the same treatment. 

Since this PPA is supposed to be what we want it to be, do you think we should write to the maintainer?
I went back through my terminal history and this is what I did to install Thunderbird 3. Add```
http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu
```to your sources list.```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 247510BE
``````
sudo apt-get update
``````
sudo apt-get install thunderbird-3.0
``` This was taken from [http://digitizor.com/2009/12/10/how-to-install-thunderbird-3-shredder-in-ubuntu-9-10/](http://digitizor.com/2009/12/10/how-to-install-thunderbird-3-shredder-in-ubuntu-9-10/)

---

### Post by running_rabbit07 on 2009-12-17
This link shows the command that will get you the key, too. [http://www.facebook.com/note.php?note_id=197656644742](http://www.facebook.com/note.php?note_id=197656644742)

---

### Post by running_rabbit07 on 2009-12-17
... double post.

---

### Post by Umang on 2009-12-17
No, no, no. I'm laughing in frustration.

To anyone who hasn't read this whole thread, here a summary: 

A asks, "how do I get TB3"
B replies, "daily builds PPA"
C says, "if I want stable releases?"
D says, "ubuntuzilla"
C says, "no I want a .deb"
E says "daily builds PPA?"
C says "no I want stable"
F says "tarball?"
C says "no I want .deb"
G says "daily builds PPA?"
C says "no I want stable"
H says "I have the solution: tarball"
C says "no, I want .deb"
J says "daily builds PPA!"

In short, don't bother reading this thread, you will not find a PPA for stable releases from Mozilla. (Unless [https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa) is updated soon)

---

### Post by running_rabbit07 on 2009-12-17
> **Umang said:**
> No, no, no. I'm laughing in frustration.

To anyone who hasn't read this whole thread, here a summary: 

A asks, "how do I get TB3"
B replies, "daily builds PPA"
C says, "if I want stable releases?"
D says, "ubuntuzilla"
C says, "no I want a .deb"
E says "daily builds PPA?"
C says "no I want stable"
F says "tarball?"
C says "no I want .deb"
G says "daily builds PPA?"
C says "no I want stable"
H says "I have the solution: tarball"
C says "no, I want .deb"
J says "daily builds PPA!"

In short, don't bother reading this thread, you will not find a PPA for stable releases from Mozilla. (Unless [https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa]("https://launchpad.net/%7Eubuntu-mozilla-security/+archive/ppa") is updated soon)
The release I have is stable.

---

### Post by Umang on 2009-12-17
I don't think you have a *_release_*. You have a _*daily build*_, which is very different.

---

### Post by running_rabbit07 on 2009-12-17
> **Umang said:**
> I don't think you have a *_release_*. You have a _*daily build*_, which is very different.
They have not done any more work to the most recent release. If they did it would have a newer version number. I guess you will be stuck with the older version until Lucid comes out.

---

### Post by Endolith on 2009-12-17
> **running_rabbit07 said:**
> I went back through my terminal history and this is what I did to install Thunderbird 3. 

We want Thunderbird 3, not Shredder.

---

### Post by running_rabbit07 on 2009-12-17
> **Endolith said:**
> We want Thunderbird 3, not Shredder.

I guess you will be stuck with the older version until Lucid comes out. Unless you install the tarball.

---

### Post by Umang on 2009-12-17
> **running_rabbit07 said:**
> They have not done any more work to the most recent release. If they did it would have a newer version number. I guess you will be stuck with the older version until Lucid comes out.
But that doesn't mean they won't do any more work on TB3, right? And any work they do on TB3 before releasing a TB 3.0.x will be reflected in the PPA since it is a daily build. Any of these changes *could* be problematic because changes in the VCS repos are not tested as intensively as a "release" is before it is released.

---

### Post by Umang on 2009-12-17
> **Endolith said:**
> We want Thunderbird 3, not Shredder.
If you get a newer version of any Mozilla product, than the one available in the repos, from a PPA instead of the tarball, you will see it as its codename not the release name. Firefox 3.5 was Shiretoko on Jaunty.

Edit: We want Shredder, but we want _*stable*_ Shredder from a _PPA_.

---

### Post by Endolith on 2009-12-17
**Q:** Why is Ubuntu a joke?

**A:** > **running_rabbit07 said:**
> I guess you will be stuck with the older version until Lucid comes out.

---

### Post by Umang on 2009-12-17
No, I have to say I disagree. With Shredder you will get TB3, without the name. The stability, the security, the features and everything else of TB3 you will get.

Just because TB3 is given a codename doesn't make Ubuntu a joke.

If you really want TB3 as TB3, get ubuntuzilla. Otherwise, stick around in this thread untill we find the PPA we want...

---

### Post by Agent Smith on 2009-12-17
@ rogerdean. Just going back a few threads to when you asked for a usb stick version of TB3. I use this. [http://portableapps.com/](http://portableapps.com/) You do need write access to the usb stick though, so if you are using it on a company pc, admin will have to give you those privaleges. Its not a .deb but it does the job.

---

### Post by rogerdean on 2009-12-17
Hi Agent Smith, many thanks indeed for that. Actually I meant that I'd like to carry the .deb around so I can install it on all the machines I look after. Portableapps are great for other uses though.

Props also to scouser for the tarball howto - good contributions are much appreciated!

In that vein, I might try to make the .deb myself if I can find a good howto. I've never done this before and will likely break all sorts of rules, but if anyone knows where I should start looking...

Cheers!
R

---

### Post by rogerdean on 2009-12-17
Heh, portableapps has had TB3 for over a week now... C'mon community! ;)

---

### Post by rogerdean on 2009-12-17
Found a link to a Debian AMD64 .deb, down near the foot of the page

[http://www.osside.net/?p=2259](http://www.osside.net/?p=2259)

No warranties! I've not tried it

---

### Post by Umang on 2009-12-17
> **rogerdean said:**
> Found a link to a Debian AMD64 .deb, down near the foot of the page

[http://www.osside.net/?p=2259](http://www.osside.net/?p=2259)

No warranties! I've not tried it
I suspect it's been downloaded from the daily builds PPA and then made available from download.

Anyway, I've given up on finding the must desired PPA and am going to install ubuntuzilla tomorrow.

---

### Post by rogerdean on 2009-12-17
Oh you're right, it's Shredder. Apologies

Yes, I've done ubuntuzilla too. We'll get there some day...

---

### Post by fabrixx on 2009-12-17
> **Umang said:**
> I suspect it's been downloaded from the daily builds PPA and then made available from download.

Anyway, I've given up on finding the must desired PPA and am going to install ubuntuzilla tomorrow.

I have made this deb.

To compile i have used **OFFICIAL** Thunderbird 3 source (not nightly or beta):
```

http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/3.0/source/thunderbird-3.0.source.tar.bz2
```
[http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/3.0/source/thunderbird-3.0.source.tar.bz2](http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/3.0/source/thunderbird-3.0.source.tar.bz2)

But the name & logo is manteined shredder....

In this topic you find my link & other .debs
[http://forums.debian.net/viewtopic.php?f=10&t=47582&p=273342#p273342](http://forums.debian.net/viewtopic.php?f=10&t=47582&p=273342#p273342)

Bye :)

---

### Post by running_rabbit07 on 2009-12-17
> **Umang said:**
> But that doesn't mean they won't do any more work on TB3, right? And any work they do on TB3 before releasing a TB 3.0.x will be reflected in the PPA since it is a daily build. Any of these changes *could* be problematic because changes in the VCS repos are not tested as intensively as a "release" is before it is released.

Did you notice in my screen shot that the PPA was disabled? I enable it every now and then to see what updates they have done. You do not have to install the updates/upgrades as they come out.

I have Shiretoko and Shredder. They work.

---

### Post by running_rabbit07 on 2009-12-17
> **Endolith said:**
> **Q:** Why is Ubuntu a joke?

**A:**

:-({|=

---

### Post by Umang on 2009-12-17
> **running_rabbit07 said:**
> Did you notice in my screen shot that the PPA was disabled? I enable it every now and then to see what updates they have done. You do not have to install the updates/upgrades as they come out.

I have Shiretoko and Shredder. They work.
Can I conveniently get out of this confusion that I've created by just saying that 12 hours from now, I will have ubuntuzilla installed on my computer? :p

---

### Post by running_rabbit07 on 2009-12-17
> **Umang said:**
> Can I conveniently get out of this confusion that I've created by just saying that 12 hours from now, I will have ubuntuzilla installed on my computer? :p

No confusion. I see exactly what you want. Sadly The only Ubuntu PPA that will have the non-shredder version will be Lucid's. You may also find the .rpm version and install it. Fedora has been using the Thunderbird 3.0 for Fedora 11 and 12, so it is out there.

---

### Post by Umang on 2009-12-17
No, no. You've got me wrong again. I wasn't the one who didn't want Shredder... I was the one who wanted a PPA with only realeases and no dailies, and knew I'd get Shredder... I used Shiretoko for a long time, I had no problem. (That was of course taken from the Mozilla Security PPA, but they don't seem to update TB now...)

---

### Post by scouser73 on 2009-12-17
> **Endolith said:**
> We want Thunderbird 3, not Shredder.

It looks like you'll either have to admit defeat, install the PPA or install it using the instructions I posted previously.

[[COLOR="Red"]**PPA for Ubuntu Mozilla Daily Build Team**[/COLOR] ]("https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa")

For the avoidance of doubt I'd like to mention that Mozilla Thunderbird 3 is the finished version, it is not Shredder!

**Mozilla Thunderbird 3** & **Mozilla Thunderbird [Codename Shredder]**

[IMG]http://img215.imageshack.us/img215/2230/aboutmozillathunderbird.png[/IMG]  [IMG]http://people.mozilla-russia.org/sergeys/thunderbird/shredder.png[/IMG]

---

### Post by fabrixx on 2009-12-17
[IMG]http://www.osside.net/wp-content/uploads/2009/12/Schermata-About-Shredder.jpg[/IMG]

Compiled in Debian whith this sources:

h ttp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/3.0/source/thunderbird-3.0.source.tar.bz2

Why name is not Thunderbird ?? :confused:

---

### Post by nanog on 2009-12-28
ubuntuzilla is not a good option for 64 bit users because it installs ia32-libs  (buggy steaming pile of sh***) and borks 64 bit flash. 

> Why name is not Thunderbird ?? 

i believe mozilla limits compilation of branded versions to "approved" distributors...hence iceweasel. mozilla protects its branding and software copyrights like an evil monopolistic for-profit company. go figure.

---

### Post by nanotube on 2009-12-28
> **nanog said:**
> ubuntuzilla is not a good option for 64 bit users because it installs ia32-libs  (buggy steaming pile of sh***)
that may be true, but people report that these libs do their job, for the most part
> 
 and borks 64 bit flash. 

indeed, since the mozilla build is 32bit. all you need to 'unbork' flash is to grab 32bit flash plugin.

that said - it is true that running 32bit mozilla binaries on 64bit os is kind of a kludge - certainly if there was a 64bit build it would be better, but mozilla doesn't provide.

> 
i believe mozilla limits compilation of branded versions to "approved" distributors...hence iceweasel. mozilla protects its branding and software copyrights like an evil monopolistic for-profit company. go figure.

somewhat inaccurate.  if you compile the original source without modifications, you are free to do it and distribute it, with the mozilla branding. what they /are/ trying to prevent is random people hacking the source and breaking crap, then distributing their broken binaries as 'mozilla firefox'. so if you plan to patch the source with your own modifications, then you need to run those by them before they'll approve you distributing the binaries under their brand. 

the history of iceweasel et al. is that the debian packagers made some mods to the source and got into a row with mozilla about using the logos, so then they just decided to use new branding. there are all sorts of writeups about this on the web if you care to search. 

but to sum it all up, they are not being evil, they are just trying to prevent joe-shmoe's patched buggy firefox from being distributed under the official branding, so that people don't get it, see that it sucks, and get the impression that firefox sucks - even though the fault lies with joe-shmoe's patches, rather than mozilla project's source.

---

### Post by litlfrog on 2009-12-29
I'd just like to point out that after reading all seven pages of this thread, I still can't install Thunderbird 3. One promising link gave a software source to add, but no instructions on how to add a new software source. I can successfully install into the /opt directory from the tarball, but that gives me no way to import data from my existing Firefox 2 installation.

Thunderbird is the most popular mail client for Ubuntu. Why, WHY is this made so hard? I'm at least experienced with computers--I can't imagine how hard this must be for people who are really new to this.

---

### Post by a0u on 2009-12-29
[SIZE=4][SIZE=2]As a public service: [FONT=Arial][SIZE=2]**[thunderbird-3-custom_3.0-1_amd64.deb]("http://www.box.net/shared/y9nz3vto9f")**[/SIZE][/FONT]
This is a statically linked, officially branded build of Thunderbird 3.0 for [/SIZE][/SIZE][SIZE=4][SIZE=2]x86_64.[/SIZE][/SIZE][SIZE=4]
[SIZE=2]Note that you must create your own *.desktop menu entry.  To launch Thunderbird from the terminal, simply enter:
```
thunderbird
```[/SIZE] 
HOWTO: Build Thunderbird 3.0 (DEB)[/SIZE]

(FYI, I am using Kubuntu 9.10, but that should not matter.)

[LIST=1]
[*]Install prerequisites:
```
sudo apt-get install build-essential autoconf pkg-config libgtk2.0-dev libidl-dev checkinstall
```
[*]Download/untar the source:
```
wget ftp://ftp.mozilla.org/pub/mozilla.org/thunderbird/releases/3.0/source/thunderbird-3.0.source.tar.bz2
``````
tar xjvf thunderbird-3.0.source.tar.bz2
```
[*]Enter the source directory:
```
cd comm-*
```
[*]Create a [**.mozconfig** ]("https://developer.mozilla.org/En/Configuring_Build_Options")file and place it in the source directory.
Here is what I used:
```

mk_add_options MOZ_MAKE_FLAGS="-j4"

ac_add_options --enable-application=mail
mk_add_options MOZ_CO_PROJECT=mail
mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/tbird-obj
ac_add_options --enable-official-branding
ac_add_options --disable-tests
ac_add_options --disable-debug
ac_add_options --enable-optimize
ac_add_options --disable-crashreporter
ac_add_options --disable-updater
ac_add_options --enable-static
ac_add_options --disable-ogg --disable-wave

```Note that the resulting object files will be located in the '**tbird-obj**' subdirectory.
[*]Configure and build (this may take a while):
```
make -f client.mk build
```
[*]Use checkinstall to create a *.deb package.  Follow the onscreen instructions interactively:
```
cd tbird-obj
``````
sudo checkinstall -D
```
[*]If all goes well, there should be a *.deb file in the 'tbird-obj' directory.
[/LIST]

---

### Post by a0u on 2009-12-29
> **litlfrog said:**
> One promising link gave a software source to add, but no instructions on how to add a new software source.
[Adding a software repository]("https://help.ubuntu.com/9.10/add-applications/C/adding-repos.html")

Scroll down for PPA-specific instructions.

---

### Post by litlfrog on 2009-12-29
> **a0u said:**
> [Adding a software repository]("https://help.ubuntu.com/9.10/add-applications/C/adding-repos.html")

Scroll down for PPA-specific instructions.

I tried the official help files, but the earlier instructions give only the URL of a PPA. It didn't give the entire command to put in, and when I tried to add [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) to the sources list using the command deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) main, I got some kind of error in the source list and it wouldn't let me update anything until I removed the source. 

I've got the tarball and I'd be happy to install it over my existing copy of Thunderbird 2 IF I knew that I could safely import my profile into Thunderbird 3. But I don't know what location I should extract it to or what permissions I'd have to use to overwrite my existing installation.

I do thank you for the link, but I've been at this for more than a day now and still can't use the program. I want to get Thunderbird 3 set up because we have a lot of customers buying Windows 7 machines only to find that there's no mail client installed. We've been directing them to Thunderbird, but the mail account setup in Tbird3 is very, very different from how it used to be. It'd be nice to have the program to use as reference when I walk them through setups.

---

### Post by a0u on 2009-12-29
> **litlfrog said:**
> I tried the official help files, but the earlier instructions give only the URL of a PPA. It didn't give the entire command to put in, and when I tried to add [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) to the sources list using the command deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) main, I got some kind of error in the source list and it wouldn't let me update anything until I removed the source.

Don't forget the distribution name:
```
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/ **karmic** main
```Other than that, did you also add the GPG key?
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 247510BE
```(All this information is available under the "Technical details about this PPA" section on the [PPA page]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa").)

---

### Post by scouser73 on 2009-12-29
> I've got the tarball and I'd be happy to install it over my existing copy of Thunderbird 2 IF I knew that I could safely import my profile into Thunderbird 3. But I don't know what location I should extract it to or what permissions I'd have to use to overwrite my existing installation.

Download the **.tar.bz2** file from

[[COLOR="Red"]**Mozilla Messaging: Thunderbird 3**[/COLOR]]("http://en-gb.www.mozillamessaging.com/en-GB/thunderbird/")

**1** - Extract the **.tar.bz2** file

**2** - Enter **gksudo nautilus** in terminal

**3** - Go to the folder **/opt**

**4** - Copy & paste the Thunderbird file that you extracted to **/opt**

**5 -** Enter these commands into **Terminal** > **sudo -i**

*Enter your password if asked.*

> **cd /opt**
> **chown -R username filename**

[COLOR="Red"]**Obviously the username refers to you, and the filename to the file**[/COLOR]

**6** - Go to **System > Preferences > Main Menu**

**7** - In Main Menu, click on **New Item**

**8** - In the **Name** field enter **Mozilla Thunderbird Mail/News**

**9** - In the **Command** field enter **/opt/thunderbird/thunderbird**

**10** - In the **Comment** field enter **Mozilla Thunderbird Mail/News**

[[IMG]http://img121.imageshack.us/img121/7329/screenshot2c.png[/IMG]](http://img121.imageshack.us/img121/7329/screenshot2c.png/)

---

### Post by litlfrog on 2009-12-29
scouser73,

Yes, I did that yesterday. It's installed and working fine, BUT it gives me no way to important my profile. This is a work computer and I've got mail and settings for four accounts that would need to be imported. I asked in another thread how to import that profile, but didn't get a response, so I figured I'd have to install Thunderbird3 in the standard Ubuntu installation location so it would know where to find my profile!

---

### Post by running_rabbit07 on 2009-12-29
> **litlfrog said:**
> scouser73,

Yes, I did that yesterday. It's installed and working fine, BUT it gives me no way to important my profile. This is a work computer and I've got mail and settings for four accounts that would need to be imported. I asked in another thread how to import that profile, but didn't get a response, so I figured I'd have to install Thunderbird3 in the standard Ubuntu installation location so it would know where to find my profile!

I don't think that is possible with the new version. At least not until the upgrade is in the PPAs.

---

### Post by Umang on 2009-12-30
That is extremely simple.
```

$ mv ~/.thunderbird ~/.thunderbird-old
$ mv ~/.mozilla-thunderbird ~/.thunderbird

```
Done.

When you install Lucid a few months later, 
```

$ mv ~/.mozilla-thunderbird ~/.thunderbird-old
$ mv ~/.thunderbird ~/.mozilla-thunderbird

```

Anyway, I was just wondering, for every upcomming Mozilla release (like TB3, FF3, FF3.5 in the recent past), can Ubuntu get an additional verision of the product from the repos but clearly marked as "BETA" somewhere. When the final is released, it can be upgraded in the repos also. This way, there won't be a new addition to the repos after the release (which will suit Ubuntu's policies) and everyone will not have to fuss. Just go to synaptic, install thunderbird-3. If the final has not been released, then we'll get the beta, which we will clearly know, because the short description will have BETA in capitals. When the final is released, the "BETA" goes and we can all get TB3 easily.

---

### Post by MrGreen on 2009-12-30
Its not that clear from thread how to install Thunderbird 3 [which is the best way]

Would just like to try it out so guessing tarball is best option, so long as back up first....

Wish Ubuntu could be more like Arch :)

MrG

---

### Post by Umang on 2009-12-30
No, ubuntuzilla is better than the tarball. But there needs to be something better than ubuntuzilla. There isn't, unfortunately.

---

### Post by wojox on 2009-12-30
Check out my page: [http://wojox.homelinux.net](http://wojox.homelinux.net)

---

### Post by MrGreen on 2009-12-30
Have tried ubuntuzilla and now have thunderbird 3 up and running... might add ppa if its safe?

---

### Post by MrGreen on 2009-12-30
Tried PPA got key error warning will robinson!!!!

---

### Post by Tuliku on 2009-12-31
> **wojox said:**
> Check out my page: [http://wojox.homelinux.net](http://wojox.homelinux.net)

Thanks man, worked perfect.
For those who installed it but can not see it, it is in your menu called Shredder 3, instead of Thunderbird.

---

### Post by MrGreen on 2009-12-31
```
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BE

```

Not working here! something is wrong .....

---

### Post by Umang on 2009-12-31
MrGreen, you can still install the package. Nothing will happen. If you don't want that error, just do this:
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 247510BE
```

EDIT: For full instructions, click "Technical Details" then "Read about installing" in [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

---

### Post by MrGreen on 2009-12-31
Followed PPA install guide works fine :P thank you

MrG

---

### Post by nanotube on 2009-12-31
> **Umang said:**
> No, ubuntuzilla is better than the tarball. But there needs to be something better than ubuntuzilla. There isn't, unfortunately.

Well, ubuntuzilla is now better than before :), in that it is an actual repository with the mozilla builds of firefox, seamonkey, and thunderbird, packaged into .debs and published in an apt repository.

See the ubuntuzilla website, [http://ubuntuzilla.sourceforge.net](http://ubuntuzilla.sourceforge.net) for details.

---

### Post by Umang on 2009-12-31
Yes! Thank you! :) You're awesome. Will switch to this new ubuntuzilla soon. Just wanted to know, when did this happen?
EDIT: Switched, it's great! Everyone who was looking for the same solution as me: ubuntuzilla is now the best solution. (And for someone who had that petty concern about it being called "Shredder", it's not. It's called "Mozilla Build of Thunderbird" in the Main Menu and just "Thunderbird" in Help->About.)

---

### Post by nanotube on 2009-12-31
> **Umang said:**
> Yes! Thank you! :) You're awesome. Will switch to this new ubuntuzilla soon. Just wanted to know, when did this happen?
EDIT: Switched, it's great! Everyone who was looking for the same solution as me: ubuntuzilla is now the best solution. (And for someone who had that petty concern about it being called "Shredder", it's not. It's called "Mozilla Build of Thunderbird" in the Main Menu and just "Thunderbird" in Help->About.)

Been working on this and testing for the past week or so, just went public with it today. Glad you like :)

---

### Post by Umang on 2010-01-01
What's the average delay between the release and the .deb on the PPA likely to be?

---

### Post by nanotube on 2010-01-01
> **Umang said:**
> What's the average delay between the release and the .deb on the PPA likely to be?

unless i meet with untimely doom :(, or a prolonged internet deprivation :(, shouldn't be longer than a day. :)

i'm toying with the idea of setting up a cron job to do it all automagically from a server... but not sure if i should let it do stuff completely without human oversight... but i think eventually i'll do that anyway. the packager is based partly on the previous ubuntuzilla script, so has been tested by thousands. the only problems can crop up if mozilla suddenly changes stuff around on their website/release servers, and throws the packager script for a loop...

---

### Post by rogerdean on 2010-01-03
oh nanotube, that is a heroic contribution. many many thanks!
Roger

to those who may use this repo, nanotube has done lots of work (and committed to more in the future) to keep our mozilla software up-to-date. on the project page you'll see he welcomes donations. if you've got something to contribute to a useful project, maybe this'd be a good one... 
cheers

---

### Post by nanotube on 2010-01-03
> **rogerdean said:**
> oh nanotube, that is a heroic contribution. many many thanks!
Roger

to those who may use this repo, nanotube has done lots of work (and committed to more in the future) to keep our mozilla software up-to-date. on the project page you'll see he welcomes donations. if you've got something to contribute to a useful project, maybe this'd be a good one... 
cheers

thank you for your very positive feedback! :)

---

### Post by CrusaderAD on 2010-01-06
Thanks nanotube! Worked like a charm!

---

### Post by nanotube on 2010-01-06
> **raptormanad said:**
> Thanks nanotube! Worked like a charm!

great! :)

---

### Post by Bluemilk on 2010-01-07
I just tried to install thunderbird 3 on Ubuntu. I followed the instructions on the Ubuntuzila website. However, upon running the apt-get update command, I get this error message.

> W: Failed to fetch [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/Release](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.I then tried to run the command 
sudo apt-get install thunderbird-mozilla-build

and got this error message:

> E: Couldn't find package thunderbird-mozilla-buildanyone knows what's causing this?

---

### Post by Umang on 2010-01-07
System -> Administration -> Software Source -> Other Software

Do you see a line with:
deb [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main

?

If not, add it. Then do a "sudo apt-get update" before trying again.

Sorry if you've already done this, just checking.

---

### Post by Bluemilk on 2010-01-07
> **Umang said:**
> System -> Administration -> Software Source -> Other Software

Do you see a line with:
deb [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main

?

If not, add it. Then do a "sudo apt-get update" before trying again.

Sorry if you've already done this, just checking.


The URL is the same as that you just listed. The deb word isn't there though. From the rest of the URLs in the Other Software tab, I don't think it's supposed to be displayed.

That exact string does appear in /etc/apt/sources.list.

---

### Post by Umang on 2010-01-07
Oops.

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#64bit_users](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#64bit_users)

---

### Post by Bluemilk on 2010-01-07
> **Umang said:**
> Oops.

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#64bit_users](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#64bit_users)


Oops indeed! :redface:. That worked. Thanks!

---

### Post by GeekGirl1 on 2010-01-08
> **wojox said:**
> Check out my page: [http://wojox.homelinux.net](http://wojox.homelinux.net)Worked perfectly. Thank you. The [daily build](https://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa) includes amd64.

---

### Post by nanotube on 2010-01-08
> **GeekGirl1 said:**
> Worked perfectly. Thank you. The [daily build](https://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa) includes amd64.

note: the daily builds are daily trunk builds, not releases, so are more likely to have various bugs. e.g., note that the firefox 3.5 branch in the repo is actually 3.5.8 pre-release, not the just-made 3.5.7 release. 

that said, it's a good option for 64bit users, since mozilla doesn't make 64bit builds of their releases. 

but for 32bit users - if you want more stability probably it's better to use the release stream rather than the daily build stream.

---

### Post by fabrixx on 2010-01-09
I've compiled Thunderbird 3 & Firefox 3.6a5 (cairo anabled) with ubuntu 9.10 amd64 an apply official branding whith my obf logo ;) see picture (no shredder brand).

Works great !!

[[IMG]http://upload.centerzone.it/images/2p4nh734xqbxg9g84fqb_thumb.png[/IMG]]("http://upload.centerzone.it/viewer.php?file=2p4nh734xqbxg9g84fqb.png")     []("http://upload.centerzone.it/viewer.php?file=041wl1b5sazhf09g9y.png") [[IMG]http://upload.centerzone.it/images/041wl1b5sazhf09g9y_thumb.png[/IMG]](http://upload.centerzone.it/viewer.php?file=041wl1b5sazhf09g9y.png)

Official thunderbird 3 branding:
[http://mxr.mozilla.org/comm-1.9.1/source/other-licenses/branding/thunderbird/](http://mxr.mozilla.org/comm-1.9.1/source/other-licenses/branding/thunderbird/)


My brandig guide (in italian..)
[http://www.osside.net/?p=2482](http://www.osside.net/?p=2482)

---

### Post by mrtwice99 on 2010-01-11
> **a0u said:**
> 
]Install prerequisites:
```
sudo apt-get install build-essential autoconf pkg-config libgtk2.0-dev libidl-dev checkinstall
```


Tried the instructions and ran into two missing packages when trying to build.  I don't remember the first, it was obvious from the error message.  Second error was not obvious, I just got a message that said:

"Could not compile basic X program"

I needed the package: libxt-dev

---

### Post by Umang on 2010-01-13
@nanotube, could you also provide a large icon with the Thunderbird package. If you use GNOME-Do you'll see that there is a need to have a larger icon also.

---

### Post by nanotube on 2010-01-13
> **Umang said:**
> @nanotube, could you also provide a large icon with the Thunderbird package. If you use GNOME-Do you'll see that there is a need to have a larger icon also.

could you clarify what you mean? do you mean you want the 'Icon' resource of the .desktop file to point to a larger image? Is that what's being picked up by gnome-do?

---

### Post by Umang on 2010-01-14
Oh, Sorry, I didn't realized that the .desktop file had an absolute path to the Icon, and so you were assigning a size to the icon menus and applications like GNOME-Do pick up. 

Anyway, since that is the case, yes it would be better if the the .desktop file pointed to a larger icon.

Alternatively (I have just learnt this), you could install the icons in /usr/share/applications/icons/hicolor and put images of different sizes into the appropriate folders. Then in the desktop file, leave the icon file as "thunderbird-mozzila-build" (without path or extension) and the menus and GNOME-Do will automatically search for icons for in the appropriate folders. ([https://wiki.ubuntu.com/PackagingGuide/Complete#.desktop%20Files](https://wiki.ubuntu.com/PackagingGuide/Complete#.desktop%20Files)). So if you put a variety of sizes here different applications will pick up different sizes depending on the need (as far as I understand).

---

### Post by nanotube on 2010-01-14
hey umang - thanks, a wealth of information there :)

so... it /seems/ that the packaging guide is not quite correct. i went to the source, the freedesktop specification:
[http://standards.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html](http://standards.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html)

and there it seems that the preferred location is /usr/share/icons rather than /usr/share/pixmaps (though pixmaps is also allowed, it's last in the list)

and if you investigate the file structude inside /usr/share/icons, in the 'default' hicolor theme e.g., you'll see that they have subdirectories for the different sizes and all, which makes it possible for the various programs to pick out the proper size that they want, or the largest size available, or whatever. 

so... if i were to deal with that, i'd stick thunderbird (and seamonkey and firefox) icons into /usr/share/icons/hicolor/(32x32|64x64|128x128|...)/apps/(seamonkey|firefox|thunderbird)-mozilla-build.(png|xpm)

all that said, however, that seems like way too much trouble to deal with, considering the fact that absolute paths /are/ allowed in the icon field in .desktop, according to the official freedesktop spec:
[http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s05.html](http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s05.html)
and that sticking in the largest available icon in there has no ill effect - it scales down without any problems for places where it needs to be small (the menu, e.g.), and scales up nicely when it needs to be large. 

since that requires less sticking of various files in various places in the filesystem, i think i'll just full-path it to the largest provided icons. 

so if nobody has any strong objections to this approach, would you care to test it out for me before i do it (since i don't have/use gnome-do, or anything else that requires large icons)? just manually edit the thunderbird .desktop (/usr/share/applications/mozilla.thunderbird.desktop) to point to the largest icon (where it says default48.png, use default256.png) and see if that makes gnome-do happy. 

Thanks! :)

p.s. among other things, i learned about 'desktop-file-validate', which throws warnings even on 'ubuntu-official' .desktops. heh.

---

### Post by Umang on 2010-01-14
That's great also! (Now I'm going to go and do some research for my package). I just compared /usr/share/pixmaps/firefox-3.5.png to the icon of firefox that comes in GNOME-Do. They seem to be exactly the same (including size, when viewing the file at 100%). So it seems to me that 128x128 is all that GNOME-Do requires.

(Now that I've seen that, I'm going to remove all the complicated '.xpm's and '.png's that I've got in a package I'm trying to upload and just put one large png in pixmaps, seems acceptable by the standards.)

So I guess either way seems to be fine: put a large icon in pixmaps and leave don't make an absolute path to the icon in the .desktop or make the .desktop link to a larger icon (i.e. 128x128. I don't know where 256 will be required and whether it will be worth putting a 256 instead of 128 ).

---

### Post by nanotube on 2010-01-14
> **Umang said:**
> That's great also! (Now I'm going to go and do some research for my package). I just compared /usr/share/pixmaps/firefox-3.5.png to the icon of firefox that comes in GNOME-Do. They seem to be exactly the same (including size, when viewing the file at 100%). So it seems to me that 128x128 is all that GNOME-Do requires.

(Now that I've seen that, I'm going to remove all the complicated '.xpm's and '.png's that I've got in a package I'm trying to upload and just put one large png in pixmaps, seems acceptable by the standards.)


yea, seems much simpler that way. :)

> 
So I guess either way seems to be fine: put a large icon in pixmaps and leave don't make an absolute path to the icon in the .desktop or make the .desktop link to a larger icon (i.e. 128x128. I don't know where 256 will be required and whether it will be worth putting a 256 instead of 128 ).

i figure, if they provide 256, then i'm gonna use it just because it's there! ;)

---

### Post by Irvine_himself on 2010-01-15
I installed TB3 a few days ago from the tar-ball and it works fine. However after reading this post with great interest, I think I might be missing something important.

First of all, I have a very small internal hard-disk, (only 30 GB,) and have to use an external hard-disk of 500 GB. On the external disk I have created a directory F/home/programs where I have extracted various tar-balls like TB3, Make-Human and Kompozer. (The Kompozer version in the repo's has a fatal bug!)

Right clicking on the Ubuntu icon on the launch bar and choosing "edit menus" I then added a launcher to the appropriate shell-script. As I say, everything seems to work fine, but I am worried that my simple solution does not seem to be the way anyone else has tackled this installation.

I would be grateful if someone with superior knowledge could explain what potential problems I have opened myself up for.

Ps

I have set TB3 to automatically check for updates

:(

---

### Post by Umang on 2010-01-15
^ That is simply because on Ubuntu, a .deb installation is much simpler. So we're all in love with nanotube's PPA (if that's what SF calls it)

---

### Post by nanotube on 2010-01-15
> **Umang said:**
> ^ That is simply because on Ubuntu, a .deb installation is much simpler. So we're all in love with nanotube's PPA (if that's what SF calls it)

heh thanks :)
by the way - have you tested to see if using a bigger icon in the .desktop makes gnome-do happy?

---

### Post by nanotube on 2010-01-15
> **Irvine_himself said:**
> I installed TB3 a few days ago from the tar-ball and it works fine. However after reading this post with great interest, I think I might be missing something important.

First of all, I have a very small internal hard-disk, (only 30 GB,) and have to use an external hard-disk of 500 GB. On the external disk I have created a directory F/home/programs where I have extracted various tar-balls like TB3, Make-Human and Kompozer. (The Kompozer version in the repo's has a fatal bug!)

Right clicking on the Ubuntu icon on the launch bar and choosing "edit menus" I then added a launcher to the appropriate shell-script. As I say, everything seems to work fine, but I am worried that my simple solution does not seem to be the way anyone else has tackled this installation.

I would be grateful if someone with superior knowledge could explain what potential problems I have opened myself up for.

Ps

I have set TB3 to automatically check for updates

:(

nothing wrong with that, if you know what you're doing, and if you're willing to keep each individual application updated separately. 

this problem on windows of keeping dozens of different apps all with their own updaters happy is what the repositories solve nicely (among other things) on ubuntu, all the updates come through the same channel.

but if it works for you (and sometimes up to date repos are not available), it's fine.

---

### Post by Umang on 2010-01-15
Yes. Just tested it. Looks very nice. (I used this [http://www.iconarchive.com/icons/benjigarner/softdimension/256/Thunderbird-icon.png](http://www.iconarchive.com/icons/benjigarner/softdimension/256/Thunderbird-icon.png))

---

### Post by Irvine_himself on 2010-01-15
Whew.... thats a relief, I was a bit worried there.

I have noticed quite a few of the  repo versions  of my favourite programs are a bit behind the times, the repo version of Kompozer in particular has a major bug. 

In fact, I tried installing TB2 from the repo but the "Lightning" calender extension did not work very well. I then tried installing "Evolution" from the repo, but I got hit with some documented bugs with the "imap updater". Which finally brought me to TB3 and its tar-ball. 

All in all, given the small size of my internal hard-disk, I am quite pleased with my solution. I even managed to get the launcher buttons to load the correct, (larger) icons by copying the appropriate jpeg or png into an icon directory I set up on the internal hard-disk and typing, not browsing, to the address. (I have to keep the icons on the internal hard-drive because mounting the external disk is the very last task at boot.)

:D

---

### Post by nanotube on 2010-01-15
> **Umang said:**
> Yes. Just tested it. Looks very nice. (I used this [http://www.iconarchive.com/icons/benjigarner/softdimension/256/Thunderbird-icon.png](http://www.iconarchive.com/icons/benjigarner/softdimension/256/Thunderbird-icon.png))

well, in that case, expect the next thunderbird release (3.0.1 is slated for jan 20) to have a nice big icon in the .desktop. :)

---

### Post by Penguin Guy on 2010-01-16
I made a post on how to install Thunderbird (both version 2 and 3) the proper way (through apt and PPAs). [Click here]("http://ubuntuforums.org/showpost.php?p=8674623").

---

### Post by jonathan22 on 2010-01-18
> **a0u said:**
> [SIZE=4][SIZE=2]As a public service: [FONT=Arial][SIZE=2]**[thunderbird-3-custom_3.0-1_amd64.deb]("http://www.box.net/shared/y9nz3vto9f")**[/SIZE][/FONT]
This is a statically linked, officially branded build of Thunderbird 3.0 for [/SIZE][/SIZE][SIZE=4][SIZE=2]x86_64.[/SIZE][/SIZE][SIZE=4]
[SIZE=2]Note that you must create your own *.desktop menu entry.  To launch Thunderbird from the terminal, simply enter:
```
thunderbird
```[/SIZE] 

[/LIST]

aOu, your 64-bit Thunderbird 3 deb file works great!  Thank you!

---

### Post by nanotube on 2010-01-20
> **nanotube said:**
> well, in that case, expect the next thunderbird release (3.0.1 is slated for jan 20) to have a nice big icon in the .desktop. :)

fyi: tbird 3.0.1 is in the ubuntuzilla repo as of earlier today, and uses a 256x256 size icon for the .desktop file. 

i have also changed the setup so that the icon is placed into /usr/share/pixmaps, and only the filename rather than the full pathname is used in .desktop - works nice. 

thanks Umang for the pointers on this. :)

---

### Post by Umang on 2010-01-21
I upgraded TB today. The icon looks great on GNOME-Do. :) 

Thank you too!

---

### Post by nanotube on 2010-01-21
> **Umang said:**
> I upgraded TB today. The icon looks great on GNOME-Do. :) 

Thank you too!

excellent - thanks for the feedback! :)

---

### Post by mgol on 2010-01-23
> **Umang said:**
> To anyone who hasn't read this whole thread, here a summary: 

(...)
C says, "if I want stable releases?"
D says, "ubuntuzilla"


The problem is, I don't only want a stable release, but one that actually uses Cairo. I hate when fonts are so sharp as in Mozilla build. That's why Ubuntuzilla isn't a proper solution...

> **a0u said:**
> Here is what I used:
```

mk_add_options MOZ_MAKE_FLAGS="-j4"

ac_add_options --enable-application=mail
mk_add_options MOZ_CO_PROJECT=mail
mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/tbird-obj
ac_add_options --enable-official-branding
ac_add_options --disable-tests
ac_add_options --disable-debug
ac_add_options --enable-optimize
ac_add_options --disable-crashreporter
ac_add_options --disable-updater
ac_add_options --enable-static
ac_add_options --disable-ogg --disable-wave

```

I'd rather advise to add this line:
```
ac_add_options --enable-default-toolkit=cairo-gtk2 --enable-system-cairo
```
to a .mozconfig file. If one wants to compile TB3 oneself why to use these ugly default fonts? Cairo is a proper way.

Besides that, as far as I know Mozilla doesn't allow to distribute officially branded versions in public (I don't know how Ubuntu can, but maybe there is some deal). So if You want to share deb files with others, please turn this option off. Sorry, that's Mozilla policy.

---

### Post by nanotube on 2010-01-23
> **mgol said:**
> 
Besides that, as far as I know Mozilla doesn't allow to distribute officially branded versions in public (I don't know how Ubuntu can, but maybe there is some deal). So if You want to share deb files with others, please turn this option off. Sorry, that's Mozilla policy.

according to [http://www.mozilla.org/foundation/trademarks/faq.html](http://www.mozilla.org/foundation/trademarks/faq.html)

if you're redistributing the mozilla-built binaries (which is what ubuntuzilla ppa does), there's no problem using the official branding.

also, as far as ubuntu - mozilla also allows you to apply for permission to distribute official branding, even if you're doing your own modified builds - which is what ubuntu is doing.

---

### Post by mgol on 2010-01-23
> **nanotube said:**
> if you're redistributing the mozilla-built binaries (which is what ubuntuzilla ppa does), there's no problem using the official branding.
Seems reasonable. But a0u didn't distribute Mozilla builds, he published his own one.

> **nanotube said:**
> also, as far as ubuntu - mozilla also allows you to apply for permission to distribute official branding, even if you're doing your own modified builds - which is what ubuntu is doing.
Again - I doubt that a0u asked for permission... That's why he shouldn't distribute the package.

---

### Post by nanotube on 2010-01-23
> **mgol said:**
> Seems reasonable. But a0u didn't distribute Mozilla builds, he published his own one.

Again - I doubt that a0u asked for permission... That's why he shouldn't distribute the package.

indeed, i was just talking about ubuntuzilla. :)

however, upon further review of the full trademark policy (rather than just the faq): [http://www.mozilla.org/foundation/trademarks/policy.html](http://www.mozilla.org/foundation/trademarks/policy.html)
it also specifies that a compilation of the unmodified code can use the trademarks without any problems as well. the following quote, from the 'unaltered binaries' section, makes it clear:

> If you compile Mozilla unmodified source code (including code and config files in the installer) and do not charge for it, you do not need additional permission from Mozilla to use the relevant Mozilla Mark(s) for your compiled version.

so, based on that, i'd guess a0u is in the clear as well.

all that said - it's good that you brought it up. :)

---

### Post by FrancoNero on 2010-01-24
> **kindofabuzz said:**
> Here's the PPA for FF and TB daily Branch and Trunk builds.

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa) 

If you want to run a daily trunk or branch I personally think it's just easier to download the tars from Mozilla then just hit "Check for Updates" everyday to get the new builds instead of running update manager every day.

again, that's the daily PPA.

there's a Firefox Stable PPA, why not for Thunderbird, too?

and i'm (no offense) getting tired of all these "use ubuntuzilla" posts, which clearly are useless if you are on a 64bit system and the whole thread is full of people asking for a comfortable PPA (or at least .deb download). I mean, it's linux for human beings, not "linux for people who like to spend hours finding workarounds because mozilla is unable to offer .deb downloads"  ;)

---

### Post by mgol on 2010-01-24
> **nanotube said:**
> 
it also specifies that a compilation of the unmodified code can use the trademarks without any problems as well
Oh, I wasn't aware of that. Then everything is fine. :)

> **FrancoNero said:**
> there's a Firefox Stable PPA, why not for Thunderbird, too?
Wait, wait - I thought there is only a PPA with daily builds, where is this Firefox Stable PPA? I can't find this one and if it exists I would probably use it...

**EDIT:** Ah, OK, I found it. But this build doesn't support Cairo, so I guess I'll stick to official Ubuntu version...

---

### Post by nanotube on 2010-01-24
> **mgol said:**
> Wait, wait - I thought there is only a PPA with daily builds, where is this Firefox Stable PPA? I can't find this one and if it exists I would probably use it...

**EDIT:** Ah, OK, I found it. But this build doesn't support Cairo, so I guess I'll stick to official Ubuntu version...

yea, apparently it's something that was just created very recently...

---

### Post by FrancoNero on 2010-01-25
doesn't support cairo? how can I tell? it looks fine here. slapped some nice Personas on it and good to go. fast as hell this 3.6 foxky

---

### Post by mgol on 2010-01-25
> **FrancoNero said:**
> doesn't support cairo? how can I tell? it looks fine here. slapped some nice Personas on it and good to go. fast as hell this 3.6 foxky
It seems so. Fonts aren't smooth as in Ubuntu main version.

---

### Post by FrancoNero on 2010-01-25
ah I see. you're right. But I can live with that. This foxky is fast as hell and I like Personas :)

---

### Post by corkscrew on 2010-03-08
where is your command I can't see it? and will it work for 64 bit

---

### Post by DonkeyShark on 2010-08-02
Hello ubuntu world,

I'm new to linux (this is my first post), just installed ubuntu yesterday and am trying to tweak things a bit.  I currently have evolution installed as my email client but would like to switch to Thunderbird as I'm familiar with Windows version of the software (I hope that's not a swear word in these parts of town, if so I do apologize).  I've tried following about 5 different links and installation instructions I've read from this forum as well as the sourceforge ubuntuzilla page and the mozilla website.  I have failed in all attempts.  I have a degree in mathematics and a fairly dense background in computers and feel like banging my head against the wall when trying to install anything on ubuntu.

Here are my latest efforts, if anyone could tell me what I'm doing wrong, I would greatly appreciate it.

I installed the latest version of Ubuntu 10.4.0 or 10.0.4 something like that...
I believe I have successfully enabled multiverse and universe portals (or w/e you call it)
I have successfully downloaded the bz2 file from the mozilla website and have extracted the file to my /tmp folder (another flag goes up, not sure where it "belongs" though).
I then got stuck.

I attempted to install via the terminal client by following the SourceForge ubuntuzilla instructions but they didn't work, well at least not for me.

I opened the Terminal Client where i'm logged in as user@computername:~$ 
(I fear I've already gone wrong by not changing the directory, but haven't been directed otherwise from any of the instructions I've followed).  
I typed the following command: 
sudo apt-get install thunderbird-mozilla-build

I received the following response:
E: Couldn't find package thunderbird-mozilla-build

This was after a successful (I believe) command of: sudo apt-get update

Please forgive me for being a noob as this is my first posting in the world of ubuntu.

---

### Post by Irvine_himself on 2010-08-02
Welcome to Linux and yes, installing programs can sometimes be a problem though not in this case :D

First of all  repositories have an address that you need to add by manually  editing a special file or using a graphical based editor ("system->administration->software sources")

Thunderbird-2  is already in the "safe" Ubuntu repository whose address is present by default, ("sytem-administration->synaptic" -> "search Thunderbird, mark install and apply.)

In general Ubuntu is a flavour of Debian Linux and any package marked *.deb should install in a manner similar to a windows installer. (You may need to install the Debian package installer through Ubuntu's repository?)

In _some_ cases, the package may be completely self contained, ie no specific installation required, just unpack and run. (For technical reasons I had to do this with Thunderbird 3, see my earlier post in this thread.)

For more detail about the availability of Thunderbird deb packages see [https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion)

For windows users, the breadth of choice offered by Linux can be intimidating but it is worth persevering and once you have overcome the initial shock to the system I suspect you will be very happy with your Ubuntu box. I say this as someone who just spent three weeks screaming in anguished frustration trying to compile from source an obscure and esoteric piece of must have software that came with the choice of a either a windows installer binary  or compiling source code whose makefiles were garbage ](*,)

Anyway, have fun and I hope you stick with it, although I agree with you that Thunderbird-3 should be available through the Ubuntu repository.

PS. treat external repositories in the same way that you would treat a windows installer of unknown provenance, be careful that they are not malicious :roll:

Irvine

---

### Post by mgol on 2010-08-03
You made a complicated thing from something very simple. ;)

You should just enable multiverse and universe through System -> Administration -> Software Sources and then just go to Application -> Software Center (or sth similar) and just find Thunderbird there. That's all. :)

---

### Post by DonkeyShark on 2010-08-09
Thanks guys!  I got it up and running. I'm really starting to like Linux :)

---

### Post by FrancoNero on 2010-08-09
> **mgol said:**
> You made a complicated thing from something very simple. ;)

You should just enable multiverse and universe through System -> Administration -> Software Sources and then just go to Application -> Software Center (or sth similar) and just find Thunderbird there. That's all. :)

the latest thunderbird isn't in the repos though

---

