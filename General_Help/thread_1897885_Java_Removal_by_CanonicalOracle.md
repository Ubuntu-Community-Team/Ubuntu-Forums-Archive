---
title: "Java Removal by Canonical/Oracle"
date: 2011-12-20
forum: General Help
---

### Post by Condor Cluster on 2011-12-20
Just read an article on [OMG Ubuntu]("http://www.omgubuntu.co.uk/2011/12/java-to-be-removed-from-ubuntu-uninstalled-from-user-machines/") regarding Sun Java being automatically removed from users machines in the not too distant future.

I was going to pre-empt this, what would be the best way to remove Sun Java, and replace with OpenJDK, with the least amount of problems?

Thanks.

---

### Post by Condor Cluster on 2011-12-20
This will affect Linux Mint aswell. [A suggestion from the Mint forums:]("http://forums.linuxmint.com/viewtopic.php?f=47&t=89256")

> sudo apt-get remove --purge icedtea-6-jre-cacao icedtea6-plugin openjdk-6-dbg openjdk-6-demo openjdk-6-doc openjdk-6-jdk openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib openjdk-6-source sun-java6-jdk sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin icedtea-7-jre-cacao icedtea7-plugin openjdk-7-dbg openjdk-7-demo openjdk-7-doc openjdk-7-jdk openjdk-7-jre openjdk-7-jre-headless openjdk-7-jre-lib openjdk-7-source sun-java7-jdk sun-java7-bin sun-java7-fonts sun-java7-jre sun-java7-plugin icedtea-plugin ; sudo apt-get install -y icedtea-plugin && sudo apt-get update -y && sudo apt-get upgrade -y

This should remove all Java software, and then install Icedtea plugin.

---

### Post by AgentZ86 on 2011-12-20
Is this why todays updates for ubuntu 10.10 broke my java ?
And will this get things working again ? 
Is this for all linux at this point ? that you must install manually from now on ?


Please advise, 
Thanks

P.S Oanda trading charts and applet says loading 40% but freezes with icetea so this is not going to work for me

The java test sites says java is installed after removing all jre and installing icetea, but it's lacks compatibility and function FYI

NOW WHAT ?

---

### Post by Condor Cluster on 2011-12-20
Not entirely sure what is going on at the moment. Package manager says I still have Sun Java 6 installed, but cannot find the java add-ons/plugins via Firefox or Chrome. Also, the java test page comes up with no plug-in available.

:confused:

---

### Post by HotShotDJ on 2011-12-20
DON'T PANIC.  The world has not come to an end. ;)  If you absolutely need the Oracle (Sun) Java rather than OpenJDK/IcedTea, you'll just need to download and install it yourself: [http://www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html)

---

### Post by HotShotDJ on 2011-12-20
> **Condor Cluster said:**
> Not entirely sure what is going on at the moment. Package manager says I still have Sun Java 6 installed, but cannot find the java add-ons/plugins via Firefox or Chrome. Also, the java test page comes up with no plug-in available.
According to [https://lists.ubuntu.com/archives/ubuntu-security-announce/2011-December/001528.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2011-December/001528.html)

"Due to the severity of the security risk, Canonical is immediately
releasing a security update for the Sun JDK browser plugin which will
disable the plugin on all machines. This will mitigate users' risk from
malicious websites exploiting the vulnerable version of the Sun JDK."

---

### Post by Condor Cluster on 2011-12-20
I followed the advice [here]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes/Java6Transition") to migrate to OpenJDK

...hope they don't pull this crap with other stuff like flash player :mad:

---

### Post by fragos on 2011-12-20
> **Condor Cluster said:**
> I followed the advice [here]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes/Java6Transition") to migrate to OpenJDK

...hope they don't pull this crap with other stuff like flash player :mad:

Just want to make sure the realize the guilty party is Oracle who bought Sun and not Ubuntu. Flash is an Adobe product, thankfully Adobe is nothing like Oracle.

---

### Post by Condor Cluster on 2011-12-22
Yeah, I know Ubuntu's hand was forced on this one by Oracle. But nethertheless, they (Ubuntu) could have handled the process better, rather than just disabling java silently on users' machines with no warning or replacement (unless they check the Linux websites regularly)

Would have been better if they removed Sun JDK, then installed OpenJDK, so the user doesn't notice a difference.

Could ultimately end up turning new people back to Windows/Mac :(

Just my two cents though...

;)

---

### Post by mastablasta on 2011-12-22
what the hell? seriously? they will do remote remove of programmes i already installed? 
 
also OpenJDk doesn't work with all programmes.
 
edit: i see users can install Oracle version by simple 1 page procedure. :-( this is rubish
 
does anyone have a .deb file?

---

### Post by Condor Cluster on 2011-12-22
Not remote removal, but remote disable when you update next.

You don't have to use OpenJDK, I think you can manually install Oracle Java from their website.

---

### Post by TBABill on 2011-12-22
> **mastablasta said:**
> what the hell? seriously? they will do remote remove of programmes i already installed? 
 
also OpenJDk doesn't work with all programmes.
Beyond the implication that they can remotely disable an active program on a Linux install, apparently involuntarily, what about those who installed Sun Java via PPA? Can it just be put back in via the same PPA? Are we forced to Open JDK that is sub-par in performance? Some websites simply do not work with the icedtea plugin so I'm curious how this will play out.

---

### Post by MartijnNL on 2011-12-22
I assume it doesn't influence the PPA. And you could decide not to update and keep your current version (by locking the version in synaptic for example). Or download and install a version from Oracle yourself. They are not disabling anything you have on your computer (as long as you don't update the sun-java packages).

By the way: the reason is an expired license. Ubuntu is no longer licensed to distribute the software. So they stop doing so. It's Oracle causing this, don't blame Ubuntu/Canonical. [See here]("http://www.omgubuntu.co.uk/2011/12/java-to-be-removed-from-ubuntu-uninstalled-from-user-machines/").

---

### Post by vasa1 on 2011-12-22
> **TBABill said:**
> Beyond the implication that they can remotely disable an active program on a Linux install, apparently involuntarily, what about those who installed Sun Java via PPA? Can it just be put back in via the same PPA? Are we forced to Open JDK that is sub-par in performance? Some websites simply do not work with the icedtea plugin so I'm curious how this will play out.

> ... you have two options:

1- Install the OpenJDK packages that are provided in the main Ubuntu
   archive. (icedtea6-plugin for the browser plugin, openjdk-6-jdk or
   openjdk-6-jre for the virtual machine)
2- Manually install Oracle's Java software from their web site [4].
[Source]("https://lists.ubuntu.com/archives/ubuntu-security-announce/2011-December/001528.html")

I'm sure there are other distros that aren't particularly bothered about licenses ...

---

### Post by vasa1 on 2011-12-22
[http://blogs.computerworlduk.com/simon-says/2011/12/why-java-isnt-dead-on-ubuntu/index.htm](http://blogs.computerworlduk.com/simon-says/2011/12/why-java-isnt-dead-on-ubuntu/index.htm)

---

### Post by BC59 on 2011-12-22
> **TBABill said:**
> Beyond the implication that they can remotely disable an active program on a Linux install, apparently involuntarily, what about those who installed Sun Java via PPA? Can it just be put back in via the same PPA? Are we forced to Open JDK that is sub-par in performance? Some websites simply do not work with the icedtea plugin so I'm curious how this will play out.

As far as I know they will put empty files on the PPA. So when you update this will remove the installed package. This is not affecting the manually installed packages.

---

### Post by mastablasta on 2011-12-22
> **MartijnNL said:**
> I assume it doesn't influence the PPA. And you could decide not to update and keep your current version (by locking the version in synaptic for example). Or download and install a version from Oracle yourself. They are not disabling anything you have on your computer (as long as you don't update the sun-java packages).
 

yeah my first though as well on what i will do. i hope there is a PPA as the install instructions found on oracle site are jibberish to me and probably to most people. they lost me on browser plugin install part....
 
> 
By the way: the reason is an expired license. Ubuntu is no longer licensed to distribute the software. So they stop doing so. It's Oracle causing this, don't blame Ubuntu/Canonical. [See here]("http://www.omgubuntu.co.uk/2011/12/java-to-be-removed-from-ubuntu-uninstalled-from-user-machines/").
 
i understand the reason, however the packages on my computer were ALREADY distributed. If you ask me this only means that new installs can't be done via repos, not to disable old installs on computers where progamme is already installed. in windows exe. would remain on the maschine even if they somehow found a way to remotelly disable the programme
 
additonally they are only not allowed to distribute it, but nothing prevents them from helping oracle make a .deb file for it, right?.

---

### Post by MartijnNL on 2011-12-22
> **mastablasta said:**
> i understand the reason, however the packages on my computer were ALREADY distributed. If you ask me this only means that new installs can't be done via repos, not to disable old installs on computers where progamme is already installed. in windows exe. would remain on the maschine even if they somehow found a way to remotelly disable the programme

An update would probably count as a distribution and thus be unlicensed. Apart from that I'm not well versed in legal issues. They're not preventing you from keeping the currently installed version (as long as you don't update).

@BC59: I understood the empty files are in the normal repositories. So the PPA should be safe. But I'm not sure about that. You could ask the PPA maintainer.

---

### Post by cybergalvez on 2011-12-22
> **HotShotDJ said:**
> DON'T PANIC.  The world has not come to an end. ;)  If you absolutely need the Oracle (Sun) Java rather than OpenJDK/IcedTea, you'll just need to download and install it yourself: [http://www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html)

I followed these instructions ([http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html](http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html)) to get java 7 installed. Only deviated slightly by adding a link to the browser plugin in alternatives rather than linking the way they said to

---

### Post by mastablasta on 2011-12-22
thank you for the link to instrcutions. those do seem a bit more easy than default ones written on Oracle's site. still not an easy task for beginners that want sun java to face


does it work the same way if you use other browsers (chromium, chrome, opera, rekonq, konqueror...)? i mean the plugin? though firefox is used on this maschine...

---

### Post by Condor Cluster on 2011-12-22
Just added the [OpenJDK ppa]("https://launchpad.net/~openjdk/+archive/ppa"), and updated.

I noticed OpenJDK 7 appear in synaptic package manager, is it worth installing this over OpenJDK 6?

---

### Post by BC59 on 2011-12-22
There are many options but I believe the Oracle Java 7 is working perfectly. The only problem is the installation part which is not that simple as double clicking on a file. I followed the same instructions as @cybergalvez suggested above. Finally WebUpd8 is one of the best references.

---

### Post by fragos on 2011-12-22
> **TBABill said:**
> Beyond the implication that they can remotely disable an active program on a Linux install, apparently involuntarily, what about those who installed Sun Java via PPA? Can it just be put back in via the same PPA? Are we forced to Open JDK that is sub-par in performance? Some websites simply do not work with the icedtea plugin so I'm curious how this will play out.

They offer updates as they always have which we can refuse on a per package basis. That is hardly involuntary. I changed months ago from the Sun packages to the open ones and have had no issues with any software I run including Chrome.

---

### Post by mastablasta on 2011-12-24
yes, but how many people understand what the security packages actually do?

it all depends which sites you visit not which programmes you are running. unless they are java games like minecraft.

---

