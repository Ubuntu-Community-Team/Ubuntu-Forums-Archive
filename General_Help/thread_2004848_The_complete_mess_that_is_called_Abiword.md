---
title: "The complete mess that is called Abiword"
date: 2012-06-16
forum: General Help
---

### Post by neu5eeCh on 2012-06-16
Rumor has it that Ubuntu accidentally released an unstable "development" version of Abiword with 12.04.

Whatever the reason, it's a complete disaster.

Can any of you recommend a PPA to bring Abiword back to stability? - or is there a better solution?

---

### Post by SeijiSensei on 2012-06-16
[http://abisource.com/wiki/Install_on_Ubuntu](http://abisource.com/wiki/Install_on_Ubuntu)

---

### Post by neu5eeCh on 2012-06-16
Unfortunately, this PPA doesn't appear to offer an update for precise. Is there a way to tweak this?

> 
W: Failed to fetch [http://ppa.launchpad.net/abiword-stable/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/abiword-stable/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/abiword-stable/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/abiword-stable/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

---

### Post by SeijiSensei on 2012-06-16
You could try removing your current version and installing the 11.10 version from [here](http://packages.ubuntu.com/oneiric/abiword).  Go to the bottom of the page and click on the link appropriate for your system's architecture.

---

### Post by neu5eeCh on 2012-06-24
From what I can tell, Abiword is looking dead. The Stable PPA hasn't been updated in over two years and the Wikipedia article seems to imply that the Ubuntu version is based on a three year old version. Seems to be as dead as AWN. Oh well... moving on.

---

### Post by sgage on 2012-06-24
> **VTPoet said:**
> Unfortunately, this PPA doesn't appear to offer an update for precise. Is there a way to tweak this?

Yes, many times you can edit the sources from "precise" to "oneiric" and it will work. If you have Synaptic installed, it's easily done from Settings/Repositories/Other Software. Select the ppa, click "edit", change "precise" to "oneiric".

Reload the repos in Synaptic (or sudo apt-get update) and see how it goes.

---

### Post by derekpock on 2012-06-24
You could simply install libreoffice. It has all components that abiword has and more. Its a small mimic of microsoft office and is a subtree of open office.

---

### Post by arkanabar on 2012-07-03
LibreOffice is a fork of OpenOffice, not a subtree.  When the community (rightly) suspected that Oracle wouldn't support OpenOffice any more than they did OpenSolaris, they forked the source code and started putting in all the development patches that Sun had been essentially sitting on for a couple of years.  It's available in the repositories and can be installed with your choice of software management packages.  

Unfortunately, it's a fair bit slower to launch than Abiword, and has a lot of features that I have no use for.  WordPad may be a Microsoft program, but it was pretty much all the word processor I ever needed.  Who's going to build me something like that?

---

### Post by kansasnoob on 2012-07-10
I'm trying to figure out what to do here also. I've used Abiword for a very long time, originally in Windows ME, and a quick google search found this bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/960089](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/960089)

It's now closed and marked invalid due to the bug filer not following up but of importance:

> Dear Christopher and canoncial,

It iflls me with frustration that Canonical chose to distribute our
development version of abiword, abiword-2.9.2 with your 12.04 LTS
distribution. This was done without any consultation with the abiword
community AT ALL. Please revert to version 2.8.6. Failing this please
advise how we will be able to support our users on Ubuntu as Canoncial
does not release updates either.

Best regards,

Martin Sevior

A bit more googling tells me that Martin Sevior is connected to the abiword project so I'll continue to look into this and hopefully find a solution by the time 12.04.1 releases :)

BTW the Oneiric version worked flawlessly for me.

---

### Post by kansasnoob on 2012-07-10
Another bug report:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/991399](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/991399)

I found that one through Ubuntu answers:

[http://askubuntu.com/questions/142268/how-to-restore-scroll-wheel-functionality-in-abiword](http://askubuntu.com/questions/142268/how-to-restore-scroll-wheel-functionality-in-abiword)

Same basic answer:

> Hi everyone,

AbiWord-2.9.2 is very much a development release and should never have
been included in Ubuntu 12.04. Please revert to abiword-2.8.6

Best regards,

Martin Sevior

So I need to do two things:

#1: Figure out how to downgrade, won't be super straight forward :(

#2: Make a feature request for 12.04.1. I've done it before but I'll have to put my thinking cap on to try and remember how :)

---

### Post by kansasnoob on 2012-07-10
It appears that someone is working on a PPA:

[https://launchpad.net/~degeneracypressure/+archive/abiword](https://launchpad.net/~degeneracypressure/+archive/abiword)

Not done yet though :(

---

### Post by kansasnoob on 2012-07-10
Here's a bug that's not marked invalid:

[https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1019621](https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1019621)

I'll try and turn up the heat there :D

---

### Post by sgage on 2012-07-10
You folks might be interested in this article I just stumbled across:

[AbiWord is ready to work with you]("http://worldofgnome.org/abiword-is-ready-to-work-with-you/")

"On this article I will try to examine what is the current usability state of AbiWord, and whether it can replace LibreOffice writer for doing both simple and more advanced tasks."

---

### Post by kansasnoob on 2012-07-10
> **sgage said:**
> You folks might be interested in this article I just stumbled across:

[AbiWord is ready to work with you]("http://worldofgnome.org/abiword-is-ready-to-work-with-you/")

"On this article I will try to examine what is the current usability state of AbiWord, and whether it can replace LibreOffice writer for doing both simple and more advanced tasks."

Thanks for that :)

I seriously increased the heat here:

[https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1019621](https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1019621)

One of the saddest things about FOSS is when users wrongfully call a project "dead". No doubt sometimes projects do die, but Abiword is NOT one of them.

The problem with Abiword in Precise is due to inadequate testing and as an iso-tester I'm a huge part of the problem :redface:

Right now I'm going to focus on a work-around and see how I come out :)

---

### Post by uRock on 2012-07-10
> **kansasnoob said:**
> Thanks for that :)

I seriously increased the heat here:

[https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1019621](https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1019621)

One of the saddest things about FOSS is when users wrongfully call a project "dead". No doubt sometimes projects do die, but Abiword is NOT one of them.

The problem with Abiword in Precise is due to inadequate testing and as an iso-tester I'm a huge part of the problem :redface:

Right now I'm going to focus on a work-around and see how I come out :)

I just +1ed the bug. Hope it gets fixed soon.

---

### Post by rickm1945 on 2012-07-10
I was going to install this today from the Software Manager, but I guess I'll wait until it is stable. Thanks for posting.

---

### Post by neu5eeCh on 2012-07-10
> **kansasnoob said:**
> One of the saddest things about FOSS is when users wrongfully call a project "dead". No doubt sometimes projects do die, but Abiword is NOT one of them.

You must be referring to _me_. 

I'm glad to hear that the Abiword project isn't dead. Maybe comatose would have been better?

---

### Post by kansasnoob on 2012-07-11
> **VTPoet said:**
> You must be referring to _me_. 

I'm glad to hear that the Abiword project isn't dead. Maybe comatose would have been better?

I didn't mean to pick on you if that's what you think :(

Abiword is simply having some trouble adapting to gtk-3, and they're not alone. I'm at fault here because I failed to adequately test Abiword during Precise development :oops:

I'm continually pushing for a new iso-tester recruitment effort but so far my whining seems to have fallen on deaf ears.

---

### Post by kelvin spratt on 2012-07-11
Abiword is not dead in any way the stable version is still outstanding. Its a Ubuntu problem releasing alpha software happens all the time.

---

### Post by kansasnoob on 2012-07-11
**[COLOR="Red"]Update: There is now a PPA available[/COLOR]**:

[http://ubuntuforums.org/showpost.php?p=12106840&postcount=25](http://ubuntuforums.org/showpost.php?p=12106840&postcount=25)

I've come up with a temporary work-around, but **you must know that this installs Oneiric packages that will NOT be updated w/o physical action by the user! The user also [COLOR="Red"]must follow through with changing the repos back to Precise[/COLOR] after completing the conversion to Oneiric's version of Abiword, otherwise you'll fail to get appropriate updates to Precise - [COLOR="Red"]even security updates[/COLOR]!** My hope is that someone will get a PPA completed for Precise soon but **if you're a brave soul or a tester here's what I came up with, just remember I'm only another end user, I can't be responsible for breakage!**

Note: I have crosstested this with Ubuntu, Lubuntu, Xubuntu, and Kubuntu - somewhat of a mix of amd64 and i386 installs - but **I have NOT tested this with persistent live images**! I made some "cross-distro" allowances when it comes to purging packages so you may notice messages like "not installed so not removed" and you'll notice that some "gtk-3" packages remain installed in Kubuntu, but we DO NOT want to purge any of the "gtk" packages in the other distros (apt-get -f install takes care of that when appropriate).

**[COLOR="Red"]Final warning, if this breaks your Precise or eats your dog I want to know, but don't send a hit man after me![/COLOR]**

I highly recommend that your Precise be upgraded before beginning so:

```
sudo apt-get update && sudo apt-get upgrade

```
Also check for any package irregularities before proceeding:

```
sudo apt-get -f install
```

If any irregularities are present I highly recommend fixing them before proceeding.

So, if and when you're ready to begin, you must first purge the Precise version of 'abiword' and it's dependencies:

```
sudo apt-get purge abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview libabiword-2.9 libgdome2-0 libgdome2-cpp-smart0c2a libgsf-1-114 libgsf-1-common libgtkmathview0c2a liblink-grammar4 libloudmouth1-0 libots0 libtidy-0.99-0 libwv-1.2-4 link-grammar-dictionaries-en ttf-lyx -y
```

When that is complete you must change to the Oneiric repos:

```
sudo sed -i s'/precise/oneiric/g' /etc/apt/sources.list
```

But **you absolutely must NOT "upgrade" or "dist-upgrade"**. Doing so could totally hose your OS!

Instead just run this as one command to install Oneiric's Abiword and it's dependencies:

```
sudo apt-get update && sudo apt-get install abiword -y
```

Now you must place a "hold" on the Oneiric version of 'abiword' and it's dependencies:

```
for p in abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview libabiword-2.8 libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libgdome2-0 libgdome2-cpp-smart0c2a libgoffice-0.8-8 libgoffice-0.8-8-common libgsf-1-114 libgsf-1-common libgtkmathview0c2a libjpeg62 liblink-grammar4 libloudmouth1-0 libots0 libwv-1.2-3 link-grammar-dictionaries-en ttf-lyx ; do echo $p hold | sudo dpkg --set-selections; done
```

[B][COLOR="Red"]Now you absolutely must switch back to the Precise repos, failure to do so will cause you serious problems!
[/COLOR][/B]
```
sudo sed -i s'/oneiric/precise/g' /etc/apt/sources.list

```
Then update the repos again:

```
sudo apt-get update

```
Check for package irregularities:

```
sudo apt-get -f install
```

You should see something like:

0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded. (14 not upgraded with Kubuntu)

**If, or more likely when, you wish to release the "hold" on those packages in the future run**:

```
for p in abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview libabiword-2.8 libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libgdome2-0 libgdome2-cpp-smart0c2a libgoffice-0.8-8 libgoffice-0.8-8-common libgsf-1-114 libgsf-1-common libgtkmathview0c2a libjpeg62 liblink-grammar4 libloudmouth1-0 libots0 libwv-1.2-3 link-grammar-dictionaries-en ttf-lyx ; do echo $p install | sudo dpkg --set-selections; done
```

**Note**: You will have to release that "hold" from time to time and rinse-n-repeat the above commands just to see if the Oneiric version of Abiword has been updated, but I've checked to the best of my abilty and none of the packages installed along with Abiword seem to carry a "security" tag. You'll also need to release that "hold" when a proper PPA becomes available or after Ubuntu corrects those packages in Precise!

I hope to hear that I actually ate NO OS's or dogs :)

---

### Post by kansasnoob on 2012-07-11
> **kelvin spratt said:**
> Abiword is not dead in any way the stable version is still outstanding. Its a Ubuntu problem releasing alpha software happens all the time.

+1!

I probably could've stopped it but I goofed :oops:

---

### Post by claracc on 2012-07-12
I have replaced abiword in my lubuntu 12.04 pentium III by libreoffice-writer, you don't need to install the entire suite but only the software you need. I did it through lubuntu software center.

Libreoffice-writer renders much better than abiword released in 12.04. It doesn't take as much CPU as current abiword.

I hope the problem will be fixed soon in the new 12.04.01 release since I prefer a ligther writer software for such an old pc.

---

### Post by kansasnoob on 2012-07-12
> **claracc said:**
> I have replaced abiword in my lubuntu 12.04 pentium III by libreoffice-writer, you don't need to install the entire suite but only the software you need. I did it through lubuntu software center.

Libreoffice-writer renders much better than abiword released in 12.04. It doesn't take as much CPU as current abiword.

I hope the problem will be fixed soon in the new 12.04.01 release since I prefer a ligther writer software for such an old pc.

Sadly I've not yet found a way to easily read existing .abw files in Libreoffice :(

---

### Post by phillw on 2012-07-12
> **kansasnoob said:**
> I've come up with a temporary work-around, but **you must know that this installs Oneiric packages that will NOT be updated w/o physical action by the user! The user also [COLOR="Red"]must follow through with changing the repos back to Precise[/COLOR] after completing the conversion to Oneiric's version of Abiword, otherwise you'll fail to get appropriate updates to Precise - [COLOR="Red"]even security updates[/COLOR]!** My hope is that someone will get a PPA completed for Precise soon but **if you're a brave soul or a tester here's what I came up with, just remember I'm only another end user, I can't be responsible for breakage!** ...... 

Thanks for taking the time out to get a work around. At least the actual [bug](https://bugs.launchpad.net/bugs/1019621) is now being actioned and will hopefully be resolved soon. I'll pop a link up onto the [ Lubuntu Workarounds ](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Workarounds) until such time the bug is resolved.

Regards,

Phill.

---

### Post by kansasnoob on 2012-07-16
Lionel Le Folgoc has now added abiword 2.8.6 to one of his PPA's:

[https://launchpad.net/~mrpouit/+archive/ppa?field.series_filter=precise](https://launchpad.net/~mrpouit/+archive/ppa?field.series_filter=precise)

It appears to work OK for me but more testing is needed. I wrote these commands to take into consideration that someone may have already tried my work-around.

First release the "hold" on the abiword packages if there is one:

```
for p in abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview libabiword-2.8 libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libgdome2-0 libgdome2-cpp-smart0c2a libgoffice-0.8-8 libgoffice-0.8-8-common libgsf-1-114 libgsf-1-common libgtkmathview0c2a libjpeg62 liblink-grammar4 libloudmouth1-0 libots0 libwv-1.2-3 link-grammar-dictionaries-en ttf-lyx ; do echo $p install | sudo dpkg --set-selections; done
```

Then update & upgrade:

```
sudo apt-get update && sudo apt-get upgrade
```

And check for package irregularities (follow the recommendations provided in the terminal):

```
sudo apt-get -f install
```

Now install Lionel's PPA:

```
sudo add-apt-repository ppa:mrpouit/ppa
```

Then update the repos:

```
sudo apt-get update
```

And this should install or update the required 'abiword' packages:

```
sudo apt-get install abiword
```

Then check for any package irregularities again (follow the recommendations provided in the terminal):

```
sudo apt-get -f install
```

******************************************
******************************************

Should you wish to disable that PPA and revert the change run these commands:

```
sudo apt-get install ppa-purge
```

```
sudo ppa-purge ppa:mrpouit/ppa
```

******************************************
******************************************

Note: I have subscribed to this thread so please just reply here if you encounter any problems.

---

### Post by claracc on 2012-07-16
Thankyou Kansasnoob, I will try.

---

### Post by RHTopics on 2012-08-10
Successfully installed Lionel Le Folgoc's Abiword 2.8.6 from his mrpouit PPA on a Bodhi 2.0.1 (Ubuntu 12.04 based) installation.

Works fine after briefly testing it.

Somewhat surprised by the lack of feedback on this solution.

---

### Post by garethfoxwilliams on 2012-09-01
Thanks **Kansasnoob** for that splendid easy-to-follow process. I've downgraded on all our family machines now and have a happier wife who can now scroll !!

Thanks to all who contributed to the knowledge.

---

### Post by kansasnoob on 2012-09-01
Dmitry Smirnov is implementing a lot of Abiword bug fixes into 12.10:

[http://ubuntuforums.org/showthread.php?t=2027325&page=2](http://ubuntuforums.org/showthread.php?t=2027325&page=2)

Hopefully I'll be able to convince the devs to include the Quantal version in either Precise proposed or at least backports soon.

**Please don't even think about upgrading Precise to Quantal though!**

A lot of things are broken in Quantal ATM and I still like the idea of Precise being supported until April 2017 ;)

---

### Post by stedevil on 2012-09-25
Before finding this thread (and mrpouit PPA) I tried to remove 2.9.2 abiword and manually compile and install the 2.8.6 from the original sourcecode from the abiword webpage.

The compile however fails 

```
libtool: link: rm -fr .libs/libabiword-2.8.lax .libs/libabiword-2.8.lax
libtool: link: ( cd ".libs" && rm -f "libabiword-2.8.la" && ln -s "../libabiword-2.8.la" "libabiword-2.8.la" )
../doltlibtool --tag=CXX   --mode=link g++  -g -O2  --no-undefined -avoid-version -export-dynamic  -o abiword abiword-UnixMain.o libabiword-2.8.la  -pthread -lfribidi -lgthread-2.0 -lrt -lwv -lwmf -lwmflite -lX11 -lexpat -ljpeg -lpng -lgsf-1 -lxml2 -lz -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lpangocairo-1.0 -lpango-1.0 -lfreetype -lfontconfig -lrsvg-2 -lm -lgio-2.0 -lgdk_pixbuf-2.0 -lcairo -lgobject-2.0 -lglib-2.0   -ljpeg 
libtool: link: g++ -g -O2 --no-undefined -o .libs/abiword abiword-UnixMain.o -pthread -Wl,--export-dynamic  ./.libs/libabiword-2.8.so /usr/lib/libfribidi.so -lgthread-2.0 -lrt -lwv -lwmf -lwmflite -lX11 /usr/lib/i386-linux-gnu/libexpat.so -lpng -lgsf-1 /usr/lib/i386-linux-gnu/libxml2.so -lz -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lpangocairo-1.0 -lpango-1.0 /usr/lib/i386-linux-gnu/libfreetype.so -lfontconfig -lrsvg-2 -lm -lgio-2.0 -lgdk_pixbuf-2.0 /usr/lib/i386-linux-gnu/libcairo.so -lgobject-2.0 -lglib-2.0 -ljpeg -pthread
g++: error: unrecognized option '--no-undefined'

```



First I removed only abiword and the obvious deps manually via synaptic, now I also tried what was posted in this thread (that also removes/breaks Gnumeric in the process), but I got the same compile error.

```

sudo apt-get purge abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview libabiword-2.9 libgdome2-0 libgdome2-cpp-smart0c2a libgsf-1-114 libgsf-1-common libgtkmathview0c2a liblink-grammar4 libloudmouth1-0 libots0 libtidy-0.99-0 libwv-1.2-4 link-grammar-dictionaries-en ttf-lyx -y

```

I'm using this to Install the compile prereqs (for me on a fresh Xubuntu 12.04 the below was enough, ymmv)

```

sudo apt-get install libpng12-dev libjpeg-dev libfribidi-dev libglib2.0-dev libgsf-1-dev libwv-dev librsvg2-dev

```

I guess now I'll go try the PPA and then try to repair the broken Gnumeric as well. :p


Update: Installing Abiword after adding the PPA leaves me with a working 2.8.6 version, at least in short testing. Also, Gnumeric just needed to be reinstalled to get working again. :)

---

### Post by Statia on 2012-09-26
Comparable errors on compiling here as well:

```
libtool: link: g++ -g -O2 --no-undefined -o .libs/abiword abiword-UnixMain.o -pthread -Wl,--export-dynamic  ./.libs/libabiword-2.8.so /usr/lib/libfribidi.so -lgthread-2.0 -lrt -lwv -lwmf -lwmflite -lX11 /usr/lib/x86_64-linux-gnu/libexpat.so -lpng -lgsf-1 /usr/lib/x86_64-linux-gnu/libxml2.so -lz -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lpangocairo-1.0 -lpango-1.0 /usr/lib/x86_64-linux-gnu/libfreetype.so -lfontconfig -lrsvg-2 -lm -lgio-2.0 -lgdk_pixbuf-2.0 /usr/lib/x86_64-linux-gnu/libcairo.so -lgobject-2.0 -lglib-2.0 -ljpeg -pthread
g++: error: unrecognized option '--no-undefined'
make[3]: *** [abiword] Error 1
make[3]: Leaving directory `/home/statia/sources/abiword-2.8.6/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/statia/sources/abiword-2.8.6/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/statia/sources/abiword-2.8.6'
make: *** [all] Error 2

```

---

### Post by kansasnoob on 2012-09-26
> **stedevil said:**
> Before finding this thread (and mrpouit PPA) I tried to remove 2.9.2 abiword and manually compile and install the 2.8.6 from the original sourcecode from the abiword webpage.

The compile however fails 

```
libtool: link: rm -fr .libs/libabiword-2.8.lax .libs/libabiword-2.8.lax
libtool: link: ( cd ".libs" && rm -f "libabiword-2.8.la" && ln -s "../libabiword-2.8.la" "libabiword-2.8.la" )
../doltlibtool --tag=CXX   --mode=link g++  -g -O2  --no-undefined -avoid-version -export-dynamic  -o abiword abiword-UnixMain.o libabiword-2.8.la  -pthread -lfribidi -lgthread-2.0 -lrt -lwv -lwmf -lwmflite -lX11 -lexpat -ljpeg -lpng -lgsf-1 -lxml2 -lz -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lpangocairo-1.0 -lpango-1.0 -lfreetype -lfontconfig -lrsvg-2 -lm -lgio-2.0 -lgdk_pixbuf-2.0 -lcairo -lgobject-2.0 -lglib-2.0   -ljpeg 
libtool: link: g++ -g -O2 --no-undefined -o .libs/abiword abiword-UnixMain.o -pthread -Wl,--export-dynamic  ./.libs/libabiword-2.8.so /usr/lib/libfribidi.so -lgthread-2.0 -lrt -lwv -lwmf -lwmflite -lX11 /usr/lib/i386-linux-gnu/libexpat.so -lpng -lgsf-1 /usr/lib/i386-linux-gnu/libxml2.so -lz -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lpangocairo-1.0 -lpango-1.0 /usr/lib/i386-linux-gnu/libfreetype.so -lfontconfig -lrsvg-2 -lm -lgio-2.0 -lgdk_pixbuf-2.0 /usr/lib/i386-linux-gnu/libcairo.so -lgobject-2.0 -lglib-2.0 -ljpeg -pthread
g++: error: unrecognized option '--no-undefined'

```



First I removed only abiword and the obvious deps manually via synaptic, now I also tried what was posted in this thread (that also removes/breaks Gnumeric in the process), but I got the same compile error.

```

sudo apt-get purge abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview libabiword-2.9 libgdome2-0 libgdome2-cpp-smart0c2a libgsf-1-114 libgsf-1-common libgtkmathview0c2a liblink-grammar4 libloudmouth1-0 libots0 libtidy-0.99-0 libwv-1.2-4 link-grammar-dictionaries-en ttf-lyx -y

```

I'm using this to Install the compile prereqs (for me on a fresh Xubuntu 12.04 the below was enough, ymmv)

```

sudo apt-get install libpng12-dev libjpeg-dev libfribidi-dev libglib2.0-dev libgsf-1-dev libwv-dev librsvg2-dev

```

I guess now I'll go try the PPA and then try to repair the broken Gnumeric as well. :p


**Update: Installing Abiword after adding the PPA leaves me with a working 2.8.6 version, at least in short testing. Also, Gnumeric just needed to be reinstalled to get working again**. :)

Glad to hear the PPA worked for you.

It seems so far that the Quantal version of Abiword works quite well, so after Quantal hits final I'm going to try my best to convince the devs to add the Quantal version to the Precise proposed repos.

---

### Post by stedevil on 2012-09-26
Glad to hear the QQ version is better. Any easy way to be able to test it already now in PP via eg a ppa?

Meanwhile, still annoys me that the compile from source fails, so if anyone can help shed light on that it would be great. :)

Googling just gets me this, which doesn't help me solve it.
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=628267](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=628267)

And this AFAICT suggests it's a bug/error in the source-code
[http://gcc.gnu.org/bugzilla/show_bug.cgi?id=46410](http://gcc.gnu.org/bugzilla/show_bug.cgi?id=46410)


And some more googling leads me to 
[https://aur.archlinux.org/packages.php?ID=25601](https://aur.archlinux.org/packages.php?ID=25601)
and the patch to fix it
[https://projects.archlinux.org/svntogit/packages.git/plain/abiword/repos/extra-i686/abiword-2.8.6-no-undefined.patch](https://projects.archlinux.org/svntogit/packages.git/plain/abiword/repos/extra-i686/abiword-2.8.6-no-undefined.patch)

---

### Post by kansasnoob on 2012-09-26
> Glad to hear the QQ version is better. Any easy way to be able to test it already now in PP via eg a ppa?


Not yet :(

> Meanwhile, still annoys me that the compile from source fails, so if anyone can help shed light on that it would be great.

I've never compiled a package from source in my life so I'm clueless.

---

### Post by stedevil on 2012-09-26
Ok, from reading the Ubuntu patchfile for 11.10 Abiword 2.8.6 package

[https://launchpadlibrarian.net/78771212/abiword_2.8.6-0.3ubuntu2.diff.gz](https://launchpadlibrarian.net/78771212/abiword_2.8.6-0.3ubuntu2.diff.gz)

it's shown that all 
--no-undefined
needs to be replaced with
-Wl,--no-undefined

in both Makefile.am and Makefile.in
and then according to the comment automake needs to be run to propagate these changes to all children files.

Sounds doable for the motivated, but currently I'm happy with the PPA 2.8.6 :)

---

### Post by skywalk on 2012-10-06
kansasnoob thanks for your help.

---

### Post by JosephWheatley on 2012-11-09
Thanks [kansasnoob]("http://ubuntuforums.org/member.php?u=554595") that worked for me.

Has Abiword been sorted out for 12.10?

---

### Post by kansasnoob on 2012-11-09
> **JosephWheatley said:**
> Thanks [kansasnoob]("http://ubuntuforums.org/member.php?u=554595") that worked for me.

Has Abiword been sorted out for 12.10?

Yes, it works OK in 12.10. but if you're using Unity or one of the Gnome DE's I'd suggest staying with 12.04.

---

### Post by anon_private on 2012-12-17
> **kansasnoob said:**
> Lionel Le Folgoc has now added abiword 2.8.6 to one of his PPA's:

[https://launchpad.net/~mrpouit/+archive/ppa?field.series_filter=precise](https://launchpad.net/~mrpouit/+archive/ppa?field.series_filter=precise)

It appears to work OK for me but more testing is needed. I wrote these commands to take into consideration that someone may have already tried my work-around.

First release the "hold" on the abiword packages if there is one:

```
for p in abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview libabiword-2.8 libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libgdome2-0 libgdome2-cpp-smart0c2a libgoffice-0.8-8 libgoffice-0.8-8-common libgsf-1-114 libgsf-1-common libgtkmathview0c2a libjpeg62 
liblink-grammar4 libloudmouth1-0 libots0 libwv-1.2-3 link-
grammar-dictionaries-en ttf-lyx ; do echo $p install | sudo dpkg --set-selections; done
```

Then update & upgrade:

```
sudo apt-get update && sudo apt-get upgrade
```

And check for package irregularities (follow the recommendations provided in the terminal):

```
sudo apt-get -f install
```

Now install Lionel's PPA:

```
sudo add-apt-repository ppa:mrpouit/ppa
```

Then update the repos:

```
sudo apt-get update
```

And this should install or update the required 'abiword' packages:

```
sudo apt-get install abiword
```

Then check for any package irregularities again (follow the recommendations provided in the terminal):

```
sudo apt-get -f install
```

******************************************
******************************************

Should you wish to disable that PPA and revert the change run these commands:

```
sudo apt-get install ppa-purge
```

```
sudo ppa-purge ppa:mrpouit/ppa
```

******************************************
******************************************

Note: I have subscribed to this thread so please just reply here if you encounter any problems.



-----

---

### Post by anon_private on 2012-12-17
This is probably not the recommended method but

I have downloaded abiword 2.8.6 and it is in /home/lubuntu/Downloads

My current version of abiword is in menu://applications/Office

I tried to mouse over the 2.8.6 version with the idea of deleting abiword and then renaming 2.8.6 to abiword.

But it will not mouse over.

Can I use the 2.8.6 version that I have downloaded?

Thanks

Ref. Lubuntu 12.04

UPDATE

The abiword file that I downloaded to: /home/lubuntu/Downloads has vanished after the session. I wonder if this was due to the fact that I run Lubuntu from a pendrive?

---

### Post by kansasnoob on 2012-12-18
> **anon_private said:**
> This is probably not the recommended method but

I have downloaded abiword 2.8.6 and it is in /home/lubuntu/Downloads

My current version of abiword is in menu://applications/Office

I tried to mouse over the 2.8.6 version with the idea of deleting abiword and then renaming 2.8.6 to abiword.

But it will not mouse over.

Can I use the 2.8.6 version that I have downloaded?

Thanks

Ref. Lubuntu 12.04

UPDATE

The abiword file that I downloaded to: /home/lubuntu/Downloads has vanished after the session. I wonder if this was due to the fact that I run Lubuntu from a pendrive?

Hmmm, well this was fixed in 12.10, and if you're running a live USB I'd think your best bet is performing a fresh install of Lubuntu 12.10.

Otherwise the preferred method of downgrading Abiword in 12.04 is to use Lionel's PPA:

[https://launchpad.net/~mrpouit/+archive/ppa?field.series_filter=precise](https://launchpad.net/~mrpouit/+archive/ppa?field.series_filter=precise)

---

### Post by anon_private on 2012-12-18
> **kansasnoob said:**
> Hmmm, well this was fixed in 12.10, and if you're running a live USB I'd think your best bet is performing a fresh install of Lubuntu 12.10.

Otherwise the preferred method of downgrading Abiword in 12.04 is to use Lionel's PPA:

[https://launchpad.net/~mrpouit/+archive/ppa?field.series_filter=precise](https://launchpad.net/~mrpouit/+archive/ppa?field.series_filter=precise)

Is the downgrade method liable to work for someone using the LiveCD?

I have had a quick look at Lionel's page. I must say, I am bit lost.

Best wishes.

A

---

### Post by kansasnoob on 2012-12-18
> **anon_private said:**
> Is the downgrade method liable to work for someone using the LiveCD?

I have had a quick look at Lionel's page. I must say, I am bit lost.

Best wishes.

A

Using a live CD ....... absolutely NOT!

If you're using an Lubuntu live USB with persistence it may be possible, but I'm not very knowledgeable in that regard.

IMHO if you are using an Lubuntu 12.04 live USB I'd think the best option would be to backup anything important to another device and then create a fresh Lubuntu 12.10 live USB since it's version of Abiword works fine.

---

### Post by anon_private on 2012-12-18
Thanks.

Do you know if I can use Lubuntu 12.04 on a USB to create another live Lubuntu 12.10 USB

---

### Post by CK000 on 2013-01-26
[SIZE=2]Hello to you all,

[SIZE=2]I am using [SIZE=2]Abiword 2.8.6 and all worked fine until very recent[SIZE=2]ly[SIZE=2] a[SIZE=2]nd mostly it still does. 
[SIZE=2]I can read files and crea[SIZE=2]te files in all formats. My concern is that others may not [SIZE=2]be able to read files I s[SIZE=2]end[SIZE=2] them[SIZE=2] beca[SIZE=2]use:-[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]
[SIZE=2]
[SIZE=2][SIZE=2]I often [/SIZE]save a file as Micro[SIZE=2]soft Word [SIZE=2]*.[/SIZE]doc format and then email it to my Black[SIZE=2][SIZE=2]Berry (in case I need to email the f[SIZE=2]il[SIZE=2]es to some-one [/SIZE]when out and ab[SIZE=2]out[SIZE=2]) they [SIZE=2]are likely to be using Windows and only Microsoft Word.[/SIZE]

[SIZE=2]However, m[SIZE=2]y BlackBerry (which can usually open [SIZE=2].doc files with Documents[SIZE=2] to Go Application [/SIZE]and *.doc ones created by Abiword)[SIZE=2] recently tells me the file can not be opened because it is a [SIZE=2]*.[/SIZE]rtf file[SIZE=2] - whi[SIZE=2]ch can not be read b[SIZE=2]y a BlackBerry.

[SIZE=2]I do not really want a[SIZE=2]n *.rtf file I would prefer ubuntu[SIZE=2] to create a perfect *.doc file.

[SIZE=2](I have tried [/SIZE]Libre Office and had exactly [SIZE=2]t[/SIZE]he same problem by the way...)
[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]
[SIZE=2]Ca[SIZE=2]n anyone help m[SIZE=2]e t[SIZE=2]o get Abiword[SIZE=2] working [SIZE=2]like it was a week ago, for I have not changed anythi[SIZE=2]ng and I don't think there have been [SIZE=2]an[SIZE=2]y u[SIZE=2]pdates for it.

[SIZE=2]Many tha[SIZE=2]n[SIZE=2]ks in advance.[/SIZE][/SIZE][/SIZE]
[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]

---

### Post by JKyleOKC on 2013-01-26
Have there been any updates for your Blackberry or Documents To Go?

Abiword, and I believe the Open/Libre Office programs as well, has always written MS Word files out in "rtf" format because that's the only "MS Word" format that all versions of Word recognize. The native "doc" format is very different for Word97, Word2000, and Word2007, so any output acceptable to one of those would not necessarily be readable on the other two. The "rtf" format, however, is documented openly and is automatically converted by all versions of Word.

What I'm saying is simply that since nothing significant has changed with Abiword recently (I use it to convert "docx" files to "doc" format since my copies of Word won't handle "docx" files. and would get any updates to it), the problem must be a bit later in the chain of events: either at Documents To Go, or at the Blackberry. Since I don't use either of those, I can't even make an educated guess at which it may be...

---

### Post by CK000 on 2013-01-26
Thank you very much for your response, very helpful in narrowing down the solution, I will try to update my BlackBerry and see if that solves it.

---

### Post by newbasford on 2013-02-03
I just wanted to say thank you to Kansasnoob and Lionel for providing this advice on this thread and the PPA. It has worked fine for me - after a lot of messing about looking for other ways to downgrade abiword. Thank you!

:D

---

