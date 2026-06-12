---
title: "How to build Twinkle 1.4.2 ?"
date: 2009-07-12
forum: General Help
---

### Post by UranUtan on 2009-07-12
Hi,

Using Ubuntu 9.04 x64. The softphone Twinkle in the Ubuntu repository is outdated (1.2 March 2008). I would like to install the latest version 1.42 [http://www.twinklephone.com/](http://www.twinklephone.com/)

Downloaded twinkle-1.4.2.tar.gz, extract and ran (as instructed by Twinkle FAQ: ```
./configure --enable-libsuffix=64
```

Got the following error:
[COLOR="Red"]checking for libccrtp1 >= 1.6.0... Package libccrtp1 was not found in the pkg-config search path. Perhaps you should add the directory containing `libccrtp1.pc' to the PKG_CONFIG_PATH environment variable No package 'libccrtp1' found
configure: error: Library requirements (libccrtp1 >= 1.6.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
[/COLOR]
How to solve this error?
Thanks in advance for any help.

---

### Post by VCoolio on 2009-07-12
```
sudo apt-get install libccrtp1
```

It can't find it, so probably you don't have it installed. Don't be tempted to follow the other instructions it gives, that's an endless road paved with jargon and unintelligible manuals.

---

### Post by UranUtan on 2009-07-12
I have already attempted [B]sudo apt-get install libccrtp1
[/B]. Here is the responses I got:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libccrtp1

---

### Post by VCoolio on 2009-07-12
apt-cache search libccrtp1

That should give you the exact name. Or maybe you need to add extra repositories, check in synaptic (settings > repositories) or system > administration > software sources if you have universe enabled, that's where it comes from.

---

### Post by UranUtan on 2009-07-12
**apt-cache search libccrtp1**
console output:
libccrtp1-1.6-1 - Common C++ class framework for RTP packets

So seems like it is there. Well I think I am going to give up on building this program. It's too complex. I would prefer a *.deb package ready to install. Wonder why the author didn't bother to create it. Hope I can find a better softphone program to replace it.

---

### Post by VCoolio on 2009-07-12
sudo apt-get install libccrtp1-1.6-1

do that then, or open up synaptic and tick the box in front it. And check the link you gave, at the download section there like 5 more dependencies, you can check them too in synaptic.

---

### Post by UranUtan on 2009-07-12
**sudo apt-get install libccrtp1-1.6-1**

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libccrtp1-1.6-1 is already the newest version.
libccrtp1-1.6-1 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

It is already installed. I had already did it in Synaptic package Manager before I create a post. But still have the error so I thought that there should be something else.

I was reading the INSTALL doc that came with the source. Followed the instructions for ./configure and various make syntax in the doc. EACH of them yielded an error message! v1.42 pre-Alpha would be a more appropriate version name.

---

### Post by VCoolio on 2009-07-13
Last shot: install libccrtp-dev

---

### Post by UranUtan on 2009-07-13
> **VCoolio said:**
> Last shot: install libccrtp-dev
You are right! fixed the error. Then still failed b/c ./configure didn't find libxml-2.0, then qt-mt, But this time, I used the same trick you suggested. I went to Synactic Package Manager and check the corresponding ...-dev component and it seems to solve the issue.

Then another run with ./configure, this time, there is another kind of error message:

[COLOR="Red"]checking value of $QTDIR... not set
configure: error: Set $QTDIR to the Qt directory, eg. /usr/lib/qt3
[/COLOR]

---

### Post by VCoolio on 2009-07-13
We're getting somewhere. No run
```
export QTDIR=/usr/share/qt3
```

or where-ever your qt folder is and try ./configure again.

---

### Post by UranUtan on 2009-07-13
Hi,

You are a persistent fellow, Thank for your patience. Next error:

[COLOR="Red"]checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!
[/COLOR]

---

### Post by VCoolio on 2009-07-14
Hi again, thought I'd check if you'd gotten anywhere. Ok, next error. According to [this]("http://ubuntuforums.org/showthread.php?t=376026") you need to install kdelibs-dev, which sounds reasonable (although in synaptic I have only kdelibs4-dev). Matter of putting error message between quotation marks in google. 
Note that the first reply suggests to install kubuntu-desktop, which would mean a 500 Mb for an extra desktop environment. I guess you don't want / need that, so always be careful on what you install following tips. You can run "aptitude show <package>" to get info on packages, e.g. dependencies and install size.

---

### Post by UranUtan on 2009-07-14
Hi,

I think I am going to stop the experiment there. The reason I wanted to try the latest version of Twinkle is because I am having voice quality issue. By lucks, I have found that it's  codec issue and could make Ekiga work OK (using G722 codec). I see in [http://www.twinklephone.com/](http://www.twinklephone.com/) that G722 codec is not supplied so I think that even the new version won't fix the issue.

BTW, the installation of Twinkle 1.42 is overly complicate. Fortunately for me, at the time I learnt Linux (last year!), there was no program like that. This kind of program is bad publicity for Linux.

---

### Post by kmcgrath on 2009-07-20
> **UranUtan said:**
> Hi,

I think I am going to stop the experiment there. The reason I wanted to try the latest version of Twinkle is because I am having voice quality issue. By lucks, I have found that it's  codec issue and could make Ekiga work OK (using G722 codec). I see in [http://www.twinklephone.com/](http://www.twinklephone.com/) that G722 codec is not supplied so I think that even the new version won't fix the issue.

BTW, the installation of Twinkle 1.42 is overly complicate. Fortunately for me, at the time I learnt Linux (last year!), there was no program like that. This kind of program is bad publicity for Linux.


Don't stop yet... I found this thread after suffering though the same problem described here.  For the life of me I could not figure out why the sound from the person I was talking to was extremely choppy.  I followed the steps in this thread but ran the following to compile Twinkle

```
./configure --without-kde
```  

Once I had the new version (1.4.2) of Twinkle installed everything worked.  Even with the same codecs that had been giving me problems before.  Hope this helps.

---

### Post by akolahi on 2009-07-21
You can add a line to your software source and update ubuntu...
 
[FONT=Verdana][[COLOR=#800080]https://launchpad.net/~gnutelephony/+archive/ppa[/COLOR]]("https://launchpad.net/~gnutelephony/+archive/ppa")[/FONT]
[FONT=Verdana][/FONT] 
[FONT=Verdana]this will upgrade Twinkle to 1.4.2...[/FONT]

---

### Post by UranUtan on 2009-07-24
> **akolahi said:**
> You can add a line to your software source and update ubuntu...
 
[FONT=Verdana][[COLOR=#800080]https://launchpad.net/~gnutelephony/+archive/ppa[/COLOR]]("https://launchpad.net/~gnutelephony/+archive/ppa")[/FONT]
[FONT=Verdana][/FONT] 
[FONT=Verdana]this will upgrade Twinkle to 1.4.2...[/FONT]

I can't believe this thread is still alive. Thanks very much for this excellent answer. It is so simple I could get Twinkle 1.42 in less than 5 minutes. From my communication with the author himself and the Twinkle mailing list. None of them know about this GNU Telephony PPA.

In anyway, the new Twinkle 1.42 could start and unfortunately the same choppy sound issue occurs again. This time I focused on the codec. For the test number I used (my ISP tech suppport line where there is a lot of pre-recorded IVR messages), both Ekiga 3.20 and Twinkle 1.42 used the same codec. Twinkle calls it G711u, Ekiga calls it PCMU. Ekiga works OK, while Twinkle 1.42 has the choppy sound and a lot of lags. So may be this could be a software issue after all.

I don't know what's wrong with Twinkle but I find it's GUI not very intuitive. Its toolbar is better than Ekiga's one however. In anyway, I am having too much trouble with it for now. Not sure if I will use it again in the future.

Thanks again for all your help.

---

### Post by bernehj on 2009-09-22
Hi

I'm having the same problem, the sound is really chopy but works excellent in other apps. I have found a possible solution in another forum post saying that Firefox is the culprit, hijacking the soundcard...

Link to the other post
[http://ubuntuforums.org/showthread.php?t=1142463](http://ubuntuforums.org/showthread.php?t=1142463)

---

### Post by dyfet on 2009-10-12
Everything needed to build the most current version of Twinkle (1.4.2) for Jaunty, Intrepid, and Hardy, with full and functional ZRTP support, and including Twinkle itself, can be found in this ppa:

deb [http://ppa.launchpad.net/gnutelephony/ppa/ubuntu](http://ppa.launchpad.net/gnutelephony/ppa/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/gnutelephony/ppa/ubuntu](http://ppa.launchpad.net/gnutelephony/ppa/ubuntu) jaunty main

deb [http://ppa.launchpad.net/gnutelephony/ppa/ubuntu](http://ppa.launchpad.net/gnutelephony/ppa/ubuntu) intrepid main 
deb-src [http://ppa.launchpad.net/gnutelephony/ppa/ubuntu](http://ppa.launchpad.net/gnutelephony/ppa/ubuntu) intrepid main

deb [http://ppa.launchpad.net/gnutelephony/ppa/ubuntu](http://ppa.launchpad.net/gnutelephony/ppa/ubuntu) hardy main 
deb-src [http://ppa.launchpad.net/gnutelephony/ppa/ubuntu](http://ppa.launchpad.net/gnutelephony/ppa/ubuntu) hardy main 

There is no need for this for Karmic, because Karmic already includes latest builds...

---

### Post by zerubbabel on 2009-12-10
I am running Twinkle 1.4.2 under Karmic on a strong internet connection (10 Mbps down, 1 Mbps up), but sound quality for phone calls is very choppy. What do I need to adjust to get better quality? Or should I switch to another softphone, and if so, which one?

---

