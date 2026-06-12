---
title: "How do I get Firefox 3.5.3 in Ubuntu 9.04?"
date: 2009-10-20
forum: General Help
---

### Post by eboyer93 on 2009-10-20
How do I install the latest version of Mozilla Firefox in Ubuntu?

---

### Post by sports fan Matt on 2009-10-20
This can help:)

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation)

Just follow the instructions.

---

### Post by andymorton on 2009-10-20
You should be able to find it in Add/Remove software and the Synaptic Package Manager. :)

---

### Post by eboyer93 on 2009-10-20
I don't see the latest version there.

Also do any of you know how to get the latest version of OpenOffice.org, 3.1.1?

---

### Post by -=hazard=- on 2009-10-20
Or install it by repository.

1. Open terminal and type:

sudo gedit /etc/apt/sources.list

#Add the following 2 lines on the file you just opened

deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main

deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main

#Save and Exit

2.Now on terminal add the launchpad ppa gpg key by typing type:

sudo apt-key adv &#8211;keyserver keyserver.ubuntu.com &#8211;recv-keys 247510BE

3. Install firefox 3.5 by typing on terminal:

sudo apt-get update && sudo apt-get install firefox-3.5


You can comment out the 2 lines you added on sources.list to stop taking testing updates of firefox.
The browser would be called Shiretoko (Codename for Firefox till it next official release)

---

### Post by eboyer93 on 2009-10-20
I just want 3.5.3 how do I do that?

---

### Post by -=hazard=- on 2009-10-20
> **-=hazard=- said:**
> Or install it by repository.

1. Open terminal and type:

sudo gedit /etc/apt/sources.list

#Add the following 2 lines on the file you just opened

deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main

deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main

#Save and Exit

2.Now on terminal add the launchpad ppa gpg key by typing type:

sudo apt-key adv &#8211;keyserver keyserver.ubuntu.com &#8211;recv-keys 247510BE

3. Install firefox 3.5 by typing on terminal:

sudo apt-get update && sudo apt-get install firefox-3.5


You can comment out the 2 lines you added on sources.list to stop taking testing updates of firefox.
The browser would be called Shiretoko (Codename for Firefox till it next official release)

I just explained it here.... Follow this steps.

---

### Post by eboyer93 on 2009-10-20
> **-=hazard=- said:**
> I just explained it here.... Follow this steps.
That installs the 3.5.5 prerelease version

---

### Post by lidex on 2009-10-20
> **eboyer93 said:**
> That installs the 3.5.5 prerelease version

That's the latest version of 3.5 and should be more stable.

---

### Post by -=hazard=- on 2009-10-20
> **eboyer93 said:**
> That installs the 3.5.5 prerelease version

Oh, did you update after the install? You shouldn't. Or try sudo apt-get install firefox-3.5.3

---

### Post by eboyer93 on 2009-10-20
> **-=hazard=- said:**
> Oh, did you update after the install? You shouldn't. Or try sudo apt-get install firefox-3.5.3
I guess I did by accident

---

### Post by lidex on 2009-10-20
If you must, go to synaptic and un-install firefox 3.5 and related packages. Now select firefox-3.5 in right pane. Click on the package menu and select "Force Version". In the pop up box drop down menu select desired version and click the "Force Version" button.

---

### Post by lovinglinux on 2009-10-20
The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). 

There is also a detailed explanation of each installation method provided, comparing the most important differences. I personally tested all of them and they work like a charm.

---

### Post by wilee-nilee on 2009-10-20
This PPA will install the OO your looking for. [https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)  You might considor just installing Ubuntu Tweak the 3rd party section with a couple of clicks would have loaded the Mozilla PPA and OO and a bunch of other a sundry toys and the associated keys. This is the daily or often unstable PPA link, it is just called unstable I have never found it to be that way for my uses.  [https://launchpad.net/~ubuntu-tweak-testing/+archive/ppa](https://launchpad.net/~ubuntu-tweak-testing/+archive/ppa)  Here is the stable repository. [https://launchpad.net/~tualatrix/+archive/ppa](https://launchpad.net/~tualatrix/+archive/ppa)

---

### Post by eboyer93 on 2009-10-20
> **lovinglinux said:**
> The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR=DarkRed]Firefox optimization and troubleshooting thread[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=1193567"). 

There is also a detailed explanation of each installation method provided, comparing the most important differences. I personally tested all of them and they work like a charm.
Thanks I used the manual install of the Mozilla version and it worked thanks:)

---

### Post by lovinglinux on 2009-10-20
> **eboyer93 said:**
> Thanks I used the manual install of the Mozilla version and it worked thanks:)

You are welcome.

---

### Post by eboyer93 on 2009-10-21
> **eboyer93 said:**
> Thanks I used the manual install of the Mozilla version and it worked thanks:)
Could I do this in Ubuntu 9.10?

---

### Post by scouser73 on 2009-10-21
Ubuntu 9.10 already comes with Firefox 3.5.3 installed.

---

### Post by eboyer93 on 2009-10-21
> **scouser73 said:**
> Ubuntu 9.10 already comes with Firefox 3.5.3 installed.
I know, but I want the Mozilla version of Firefox and not the ubuntu version. So could I do this?

---

### Post by lovinglinux on 2009-10-21
> **eboyer93 said:**
> I know, but I want the Mozilla version of Firefox and not the ubuntu version. So could I do this?

Yes, you can if you want. I would recommend using Ubuntuzilla, so you can keep Firefox updated according to Mozilla's releases.

---

