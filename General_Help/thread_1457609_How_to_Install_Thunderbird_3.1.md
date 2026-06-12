---
title: "How to Install Thunderbird 3.1"
date: 2010-04-18
forum: General Help
---

### Post by dannymichel on 2010-04-18
Wondering if i could get some help installing Thunderbird 3.1 on Lucid Lynx x64.
Thanks in advance for any help

---

### Post by spcwingo on 2010-04-18
You can add the ubuntuzilla repository...that's what I did on Hardy. :)  Here's a link to instructions:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page")

---

### Post by nanotube on 2010-04-19
> **spcwingo said:**
> You can add the ubuntuzilla repository...that's what I did on Hardy. :)  Here's a link to instructions:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page")

ubuntuzilla is only for 32bit.

also note that thunderbird 3.1 has not been released yet. the latest official release from mozilla is thunderbird 3.0.4

---

### Post by dannymichel on 2010-04-20
> **nanotube said:**
> ubuntuzilla is only for 32bit.

also note that thunderbird 3.1 has not been released yet. the latest official release from mozilla is thunderbird 3.0.4

ok then can someone help me install 3.0.4?

---

### Post by aysiu on 2010-04-20
As far as I know, the only way to do it is to install Ubuntu 10.04 beta, 64-bit edition.
[http://packages.ubuntu.com/lucid/amd64/thunderbird/download](http://packages.ubuntu.com/lucid/amd64/thunderbird/download)

The Mozilla download mirrors have only an i686 Thunderbird:
[http://pv-mirror01.mozilla.org/pub/mozilla.org/thunderbird/releases/3.0.4/](http://pv-mirror01.mozilla.org/pub/mozilla.org/thunderbird/releases/3.0.4/)

---

### Post by cYbercOsmOnauT on 2010-06-25
I know I answer a little late, but I think it's a good information for others like me who has a 64bit system running.

To get the newest Thunderbird 64Bit you can add the following PPA to your sources
```
deb http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu lucid main
```or if you want to compile on your own

[LIST]
[*]Surf to **[ftp://ftp.mozilla.org/pub/mozilla.org/thunderbird/releases/latest-3.0/source/](ftp://ftp.mozilla.org/pub/mozilla.org/thunderbird/releases/latest-3.0/source/) **and download the newest source
[*]**tar xjvf** **thunderbird-3.0.5.source.tar.bz2**
[*]**sudo apt-get install build-essential**
[*][B]sudo apt-get build-dep thunderbird
[/B]
[*]Go into the new dir and do [B]./configure --enable-application=mail --enable-static --enable-calendar --enable-official-branding
[/B]
[*]After that **make -j4**
[*]Last step is **sudo**** checkinstall -D --install=no --pkgname='thunderbird' --pkgversion='3.1' **to create a .deb that you can install.
[/LIST]

---

### Post by FrancoNero on 2010-06-28
can't the getdeb.net people make a 64bit .deb file or something? i mean the way ubuntu delivers 64bit 3.0.x thunderbird debs in its official repos, the same principle can work for 3.1 too, that's why i reject most of the excuses i've heard so far (for example on the mozilla boards, etc)

---

### Post by skierpage on 2010-06-28
> **cYbercOsmOnauT said:**
> To get the newest Thunderbird 64Bit you can add the following PPA to your sources ```
deb http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu lucid main
```
But that does not contain thunderbird3.1 for 32- or 64-bit, even though it was released three days ago.

You can download 32-bit Thunderbird 3.1 from Mozilla and unpack it, but you'll lack integration and theming.

I think the hardworking Ubuntu mozilla developers/packagers just haven't got to TB3.1 yet.

---

### Post by cYbercOsmOnauT on 2010-06-29
Patience my young padawan. I believe that they will add the 3.1 branch soon. We will see. :)

---

### Post by nanotube on 2010-06-29
> **skierpage said:**
> But that does not contain thunderbird3.1 for 32- or 64-bit, even though it was released three days ago.

You can download 32-bit Thunderbird 3.1 from Mozilla and unpack it, but you'll lack integration and theming.

I think the hardworking Ubuntu mozilla developers/packagers just haven't got to TB3.1 yet.

if you're looking for 32bit, the ubuntuzilla repo has it.

---

### Post by cYbercOsmOnauT on 2010-07-04
[[URL=http://img251.imageshack.us/i/tb31.png/][IMG]http://img251.imageshack.us/img251/5857/tb31.th.png[/IMG]]("http://img692.imageshack.us/i/tb31.png/")
[/URL]
Here is my proof that the manual build works. ;) I just used a german Internationalisation after I installed 3.1.

If you also want it in your language go to [ftp://ftp.mozilla.org/pub/thunderbird/releases/latest-3.1/win32/xpi/](ftp://ftp.mozilla.org/pub/thunderbird/releases/latest-3.1/win32/xpi/) and grab the language you need.

Btw, it seems that **--enable-calendar** doesn't work for Linux x86_64 but you can get Lightning from [here.]("http://www.mozilla.org/projects/calendar/releases/lightning1.0b2.html#contributedbuilds")[URL="http://img202.imageshack.us/i/tb31.png/"]
[/URL]

---

### Post by timgood on 2010-07-07
I have made a 64 bit .deb for Thunderbird 3.1 which you can download [here]("http://eekageek.co.uk/index.php?page=downloads"). Remember, this works for me - it may not work for you.

Hope this helps.

---

### Post by sayantandas on 2010-07-09
Hello all,

I have found another way to install thunderbird on my 64 bit ubuntu. 
64bit rpms for fedora 13 are already available at [http://rpm.pbone.net/index.php3/stat/4/idpl/14181537/dir/fedora_13/com/thunderbird-3.1-1.fc13.remi.x86_64.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/14181537/dir/fedora_13/com/thunderbird-3.1-1.fc13.remi.x86_64.rpm.html)

. Download the rpm and convert it do deb and install using alien

sudo alien -i thunderbird-3.1-1.fc13.remi.x86_64.rpm


Cheers!

---

### Post by timgood on 2010-07-09
> **sayantandas said:**
> Hello all,

I have found another way to install thunderbird on my 64 bit ubuntu. 
64bit rpms for fedora 13 are already available at [http://rpm.pbone.net/index.php3/stat/4/idpl/14181537/dir/fedora_13/com/thunderbird-3.1-1.fc13.remi.x86_64.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/14181537/dir/fedora_13/com/thunderbird-3.1-1.fc13.remi.x86_64.rpm.html)

. Download the rpm and convert it do deb and install using alien

sudo alien -i thunderbird-3.1-1.fc13.remi.x86_64.rpm


Cheers!

Hmmm... when I try this I get:

chown: cannot access `thunderbird-3.1//usr/lib64/thunderbird-3.1/components/compreg.dat': No such file or directory
failed chowning /usr/lib64/thunderbird-3.1/components/compreg.dat to 0:0: Illegal seek at /usr/share/perl5/Alien/Package/Rpm.pm line 265, <GETPERMS> line 38.

And indeed - checking inside the rpm compreg.dat is missing.

---

### Post by Strubbl on 2010-07-10
> **timgood said:**
> Hmmm... when I try this I get:

chown: cannot access `thunderbird-3.1//usr/lib64/thunderbird-3.1/components/compreg.dat': No such file or directory
failed chowning /usr/lib64/thunderbird-3.1/components/compreg.dat to 0:0: Illegal seek at /usr/share/perl5/Alien/Package/Rpm.pm line 265, <GETPERMS> line 38.

And indeed - checking inside the rpm compreg.dat is missing.
I get the same error.

---

### Post by cYbercOsmOnauT on 2010-07-10
> **Strubbl said:**
> I get the same error.
Just compile on your own. It's really easy.

---

### Post by Strubbl on 2010-07-10
> **cYbercOsmOnauT said:**
> Just compile on your own. It's really easy.
but what do i have to do if the 3.1 comes from the repo? i'd like to use the repo's version then. i don't wanna fiddle too much

---

### Post by cYbercOsmOnauT on 2010-07-10
It's not really a fiddling. For example I take almost everything from repositorys but Firefox and Thunderbird I compile on my own when I see a message that a new version is out.

It's fast done and I dn't have to wait for days until they are in the official repos. I wrote 2 shell scripts that do the job for me. I just start them and wait until xterm asks for my interaction. :D

---

### Post by Strubbl on 2010-07-10
> **cYbercOsmOnauT said:**
> It's not really a fiddling. For example I take almost everything from repositorys but Firefox and Thunderbird I compile on my own when I see a message that a new version is out.

It's fast done and I dn't have to wait for days until they are in the official repos. I wrote 2 shell scripts that do the job for me. I just start them and wait until xterm asks for my interaction. :D
can you share your scripts?

---

### Post by cYbercOsmOnauT on 2010-07-10
> **Strubbl said:**
> can you share your scripts?
Sure but I am no scripting god. I believe that it could be solved in a alot better way. Here is my Thunderbird dl and compile script. I created a directory called "thunderbird_source" inside my download folder and put the script in it.
```
#!/bin/bash

function showNotification()
{
    notify-send -i /usr/share/pixmaps/thunderbird.png Thunderbird "$1"
}

showNotification "Downloading new Source and Internationalisation"
wget -qrnd -nH -l 0 -A thunderbird-*.source.tar.bz2 ftp://ftp.mozilla.org/pub/mozilla.org/thunderbird/releases/latest-3.1/source/
wget -q ftp://ftp.mozilla.org/pub/thunderbird/releases/latest-3.1/win32/xpi/de.xpi
TBVERSION=`ls | grep thunderbird- | egrep -o "3\.[0-9]+(\.[0-9]+)?"`
showNotification "Unpacking Source"
tar xjf thunderbird-"$TBVERSION".source.tar.bz2
SRCDIR=`ls | grep comm-`
cd $SRCDIR
showNotification "Starting configure"
xterm -e "./configure --enable-application=mail --enable-official-branding  --enable-default-toolkit=cairo-gtk2 --enable-static --disable-tests"
showNotification "Starting make"
xterm -e "make -j4"
showNotification "Creating deb"
xterm -e "sudo checkinstall -D --install=no --pkgname='thunderbird' --pkgversion='$TBVERSION'"
xterm -e "sudo chmod a+w thunderbird_"$TBVERSION"_amd64.deb"
showNotification "Finished compiling and creating of deb paket"
```If you don't need an internationalisation. Delete the line
```
wget -q ftp://ftp.mozilla.org/pub/thunderbird/releases/latest-3.1/win32/xpi/de.xpi
```or if you want a different then german edit it to the language you need. You have to install the xpi in thunderbird after installing tb 3.1. So when you first start it it's english.

It's almost the same script for firefox.

---

### Post by Strubbl on 2010-07-11
@[cYbercOsmOnauT]("http://ubuntuforums.org/member.php?u=1042590") nice one! worked of course for me. but after i installed de.xpi and restartet thunderbird it still is not german. if i look at addons->languages DE is listed as installed...

---

### Post by cYbercOsmOnauT on 2010-07-11
That's odd because that is completely the way I went. Installed TB.. started it.. went to Addons -> Install -> Choosed out de.xpi.. restarted TB.. German

Is German activated inside your Languages tab?

---

### Post by Strubbl on 2010-07-11
yes, it is:

[http://img337.imageshack.us/img337/5016/bildschirmfotoh.png](http://img337.imageshack.us/img337/5016/bildschirmfotoh.png)

---

### Post by cYbercOsmOnauT on 2010-07-11
Strange.. it's the same version of language that I installed.

Did you try starting thunderbird in a terminal and checked the error messages you see? Maybe there is something that gives us a clue what wrong.

---

### Post by TonyFordz on 2010-07-11
Hello,

I was having issues with this too because I am not native to Linux so anything that doesn't just install leaves me up .... creek. The easiest way to get Thunderbird installed was for me to go under,

> System
> Administration
> Synaptic Package Manager

Then in the search area at the top I typed in Thunderbird, and I installed it from there.

Most times if I am wanting to install something I try to search first in Synaptic Package Manager first to save myself the headaches of getting something I need installed including WINE.

Hope this helps if you haven't already gotten the help you needed.

---

### Post by cYbercOsmOnauT on 2010-07-11
The problem is that the official repositorys don't have thunderbird 3.1 atm

Strubbl: Try to start TB with **thunderbird -UILocale de-DE -contentLocate DE**

---

### Post by Strubbl on 2010-07-11
> **cYbercOsmOnauT said:**
> The problem is that the official repositorys don't have thunderbird 3.1 atm

Strubbl: Try to start TB with **thunderbird -UILocale de-DE -contentLocate DE**
yeah! cool. works.

```
strubbl@holly:~$ thunderbird -UILocale de-DE -contentLocate DE
Warning: unrecognized command line flag -contentLocate
```

so i left out the second flag and it worked too. german UI now :D

---

### Post by cYbercOsmOnauT on 2010-07-11
I just don't understand why it works for me without this option. But if it works for you now everything is fine :)

---

### Post by sayantandas on 2010-07-12
> **Strubbl said:**
> I get the same error.
guys, there is a bug in alien.
[https://bugs.launchpad.net/ubuntu/+source/alien/+bug/507326](https://bugs.launchpad.net/ubuntu/+source/alien/+bug/507326)
update alien to the latest version.. (8.81)


```
sudo alien -d --scripts thunderbird-3.1-1.fc13.remi.x86_64.rpm 
warning: thunderbird-3.1-1.fc13.remi.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 00f97f56
warning: thunderbird-3.1-1.fc13.remi.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 00f97f56
warning: thunderbird-3.1-1.fc13.remi.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 00f97f56
warning: thunderbird-3.1-1.fc13.remi.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 00f97f56
warning: thunderbird-3.1-1.fc13.remi.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 00f97f56
warning: thunderbird-3.1-1.fc13.remi.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 00f97f56
warning: thunderbird-3.1-1.fc13.remi.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 00f97f56
warning: thunderbird-3.1-1.fc13.remi.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 00f97f56
warning: thunderbird-3.1-1.fc13.remi.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 00f97f56
warning: thunderbird-3.1-1.fc13.remi.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 00f97f56
warning: thunderbird-3.1-1.fc13.remi.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 00f97f56
warning: thunderbird-3.1-1.fc13.remi.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 00f97f56
warning: thunderbird-3.1-1.fc13.remi.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 00f97f56
warning: thunderbird-3.1-1.fc13.remi.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 00f97f56
warning: thunderbird-3.1-1.fc13.remi.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 00f97f56
warning: thunderbird-3.1-1.fc13.remi.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 00f97f56
warning: thunderbird-3.1-1.fc13.remi.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 00f97f56
thunderbird_3.1-2_amd64.deb generated
```

---

### Post by timgood on 2010-07-13
Installing the new version of Alien worked for me. The resulting 64 bit .deb for Thunderbird 3.1 can be downloaded [here]("http://eekageek.co.uk/index.php?page=downloads").

I hope this helps.

---

### Post by cYbercOsmOnauT on 2010-07-13
Why are you people so lazy and don't compile it on your own? :p

---

### Post by timgood on 2010-07-15
> **cYbercOsmOnauT said:**
> Why are you people so lazy and don't compile it on your own? :p

Yes, whenever I install Linux I build and design a new operating system from scatch, rather than use a prebuilt Distro. ;)

---

### Post by cYbercOsmOnauT on 2010-07-15
There is a difference in compiling just one app or a whole operating system ;)

---

### Post by FrancoNero on 2010-07-17
will the above posted .deb "update" my 3.0.X or should I remove my thunderbird installation first?

---

### Post by cYbercOsmOnauT on 2010-07-17
I uninstalled TB 3.0.x first but to be sure that you don't loose anything you should backup your TB profile which is normally found in **~/.thunderbird**

---

### Post by BanjoBoy on 2010-07-21
Are you sure your script works? When I use it, I get thunderbird-1.9.2-1.deb building Thunderbird v3.1.1, but it installs thunderbird v3.1.1, but without using the .deb file, it's installed by the makefile in the Thunderbird source.

> **cYbercOsmOnauT said:**
> Sure but I am no scripting god. I believe that it could be solved in a alot better way. Here is my Thunderbird dl and compile script. I created a directory called "thunderbird_source" inside my download folder and put the script in it.
```
#!/bin/bash

function showNotification()
{
    notify-send -i /usr/share/pixmaps/thunderbird.png Thunderbird "$1"
}

showNotification "Downloading new Source and Internationalisation"
wget -qrnd -nH -l 0 -A thunderbird-*.source.tar.bz2 ftp://ftp.mozilla.org/pub/mozilla.org/thunderbird/releases/latest-3.1/source/
wget -q ftp://ftp.mozilla.org/pub/thunderbird/releases/latest-3.1/win32/xpi/de.xpi
TBVERSION=`ls | grep thunderbird- | egrep -o "3\.[0-9]+(\.[0-9]+)?"`
showNotification "Unpacking Source"
tar xjf thunderbird-"$TBVERSION".source.tar.bz2
SRCDIR=`ls | grep comm-`
cd $SRCDIR
showNotification "Starting configure"
xterm -e "./configure --enable-application=mail --enable-static --enable-calendar --enable-official-branding"
showNotification "Starting make"
xterm -e "make -j4"
showNotification "Creating deb"
xterm -e "sudo checkinstall -D --install=no --pkgname='thunderbird' --pkgversion='$TBVERSION'"
xterm -e "sudo chmod a+w thunderbird_"$TBVERSION"_amd64.deb"
showNotification "Finished compiling and creating of deb paket"
```If you don't need an internationalisation. Delete the line
```
wget -q ftp://ftp.mozilla.org/pub/thunderbird/releases/latest-3.1/win32/xpi/de.xpi
```or if you want a different then german edit it to the language you need. You have to install the xpi in thunderbird after installing tb 3.1. So when you first start it it's english.

It's almost the same script for firefox.

---

### Post by FrancoNero on 2010-07-21
there's a new thunderbird out. what's the best way to upgrade now?

---

### Post by cYbercOsmOnauT on 2010-07-21
> **BanjoBoy said:**
> Are you sure your script works? When I use it, I get thunderbird-1.9.2-1.deb building Thunderbird v3.1.1, but it installs thunderbird v3.1.1, but without using the .deb file, it's installed by the makefile in the Thunderbird source.
First of all I said that I am no bashscript god. ;)

Second I changed the configure a bit to
**./configure --enable-application=mail --enable-official-branding --enable-default-toolkit=cairo-gtk2 --enable-static --disable-tests**

Third libmozz.so was missing in the thunderbird dir. I took it from **comm-1.9.2/mozilla/modules/zlib/src/libmozz.so** and copied it into the application drectory of thunderbird 3.1.1

For your question: 1.9.2 is the version number of comm. When doing checkinstall you see a page with all possible variables. One of them is/was version. Normally (I tried it today for 3.1.1) my script recognizes the version number on its own and puts it into the version line. But before pressing <ENTER> I always look at the lines. It seems you didn't. ;)

---

### Post by zerubbabel on 2010-07-21
You can find an amd64 package for Thunderbird 3.1.1 [here]("https://launchpad.net/~ricotz/+archive/staging/+build/1881094"). I installed it on my system yesterday and it's working fine.

---

### Post by FrancoNero on 2010-07-21
it sais it's for 9.10...

---

### Post by FrancoNero on 2010-07-21
nevermind, found this ppa [https://launchpad.net/~ricotz/+archive/ppa](https://launchpad.net/~ricotz/+archive/ppa)

---

### Post by FrancoNero on 2010-08-06
another update is out... i hope the above posted PPA will have it ;)

---

### Post by cYbercOsmOnauT on 2010-08-06
Thanks FrancoNero. I used my script and created the deb immediately :)

---

### Post by FrancoNero on 2010-08-06
you should cooperate with this you that runs the PPA, so we have timely updates

---

### Post by cYbercOsmOnauT on 2010-08-06
I am just not sure how to name my deb. For example the one I created is named **thunderbird_3.1.2_amd64.deb** but the versions on the ppa have other names. Also I am not sure if my compiled version really works for everyone. If you want to check it I can upload it somewhere and you try it for us :)

---

### Post by FrancoNero on 2010-08-06
> **cYbercOsmOnauT said:**
> I am just not sure how to name my deb. For example the one I created is named **thunderbird_3.1.2_amd64.deb** but the versions on the ppa have other names. Also I am not sure if my compiled version really works for everyone. If you want to check it I can upload it somewhere and you try it for us :)

hm.... I used to use your 3.1 deb, then found that ppa and used theirs (because ppas are nice), and not sure if it works if i revert back to a different source...

i understand too little about the technology of all this....

---

### Post by cYbercOsmOnauT on 2010-08-06
I uploaded my version onto my website. So whoever wants to give it a try:

[http://www.cybercosmonaut.de/debs/thunderbird_3.1.2_amd64.deb](http://www.cybercosmonaut.de/debs/thunderbird_3.1.2_amd64.deb)

There should be no problem with different sources because both packages  have the same name (thunderbird). Mostly you have different sources for a  package. Just check inside Synaptic to see it.

---

### Post by FrancoNero on 2010-08-10
> **cYbercOsmOnauT said:**
> I uploaded my version onto my website. So whoever wants to give it a try:

[http://www.cybercosmonaut.de/debs/thunderbird_3.1.2_amd64.deb](http://www.cybercosmonaut.de/debs/thunderbird_3.1.2_amd64.deb)

There should be no problem with different sources because both packages  have the same name (thunderbird). Mostly you have different sources for a  package. Just check inside Synaptic to see it.

can't test it because gdebi crashes upon start :(

---

### Post by cYbercOsmOnauT on 2010-08-10
What about **sudo dpkg -i thunderbird_3.1.2_amd64.deb** ?

---

### Post by FrancoNero on 2010-08-10
> **cYbercOsmOnauT said:**
> What about **sudo dpkg -i thunderbird_3.1.2_amd64.deb** ?

yes that worked. it does look a bit different (fonts etc), but otherwise fine. and that icon was gone again from the task bar ;) nothing serious though

yay thanks a bunch

---

### Post by gunksta on 2010-08-19
Works a charm for compiling thunderbird but I couldn't seem to quite figure out how to get it to compile lightning too. Fortunately, I was able to find a x64 version from Mozilla.

Odd that they compile Lightning to x64 but not Thunderbird.

---

### Post by cYbercOsmOnauT on 2010-08-21
Lightning is not part of the x64 package anymore. So whoever wants the calendar takes the addon.

---

### Post by gunksta on 2010-08-21
I compiled from the calendar tarball.

---

### Post by zerubbabel on 2010-10-07
I installed the latest update, version 3.1.5 (Lucid, amd64), but does anyone know where there is a compatible version of the Lightning plug-in?

---

### Post by zerubbabel on 2010-10-07
Found it [here]("https://help.ubuntu.com/community/ThunderbirdLightning").

---

### Post by FahadMKS on 2010-10-07
You may just open the Ubuntu Software Center and then type Thunderbird and then install it.
Its very simple.

---

### Post by J14e on 2012-07-01
Thanks a bunch for this thread... after the unity desktop becoming mainstream ive made the switch to debian 6 and having the repository for the 64 bit thunderbird mail has made all the difference.

---

