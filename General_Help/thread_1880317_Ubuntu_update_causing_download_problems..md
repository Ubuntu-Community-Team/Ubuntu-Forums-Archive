---
title: "Ubuntu update causing download problems."
date: 2011-11-13
forum: General Help
---

### Post by AndrewGen on 2011-11-13
My work requires the use of Elluminate Live V10 ([http://www.elluminate.com/Services/Training/Elluminate_Live!/?id=418]("http://www.elluminate.com/Services/Training/Elluminate_Live%21/?id=418")) to conduct web conferences. Everything worked fine on Ubuntu prior to updates via update manager a few months ago

In an attempt to determine the cause, I reinstalled an old version of Ubuntu, as well as Mint 9, to find that everything worked perfectly after the initial installations. The problem is trying to determine which update of the 400+ is causing the problem.  

Can anyone help?  Perhaps there is a known problem with one of these updates.  Any help would be most appreciated.

Thanks.
Andrew

---

### Post by 2F4U on 2011-11-13
What problems do you have exactly?

---

### Post by AndrewGen on 2011-11-13
> **2F4U said:**
> What problems do you have exactly?

The normal process starts with a download of a .jnlp file. This initiates the download of about 20 live.jar files after which the Elluliminate Live V10 application start. 

If you like, you can test this process by accessing the following site - 
[https://sas.elluminate.com/site/external/jwsdetect/playback.jnlp?psid=2010-06-06.1807.M.85B019627DB0832C7C9D3C7265417B.vcr](https://sas.elluminate.com/site/external/jwsdetect/playback.jnlp?psid=2010-06-06.1807.M.85B019627DB0832C7C9D3C7265417B.vcr)

Nothing happens after the download of the 20 live.jar files. The Elluminate Live V10 client should start, allowing you to conduct the web conference.

PS - Jave WebStart is required and is installed

---

### Post by oldfred on 2011-11-13
I have had no issues with the Open java now installed by default. But used the Sun (now Oracle) Java in my older installs. Some software may have a unique dependency that the Open Java has not yet set up. You might try installing Sun's verison.

You can uninstall the open java in synaptic.

I used to run this as part of my updates to get Java, but commented it out when Ubuntu made open java standard.

# Get distro
distro=$(lsb_release -cs)

# Java - Sun/Oracle non-free use std openjdk-6-jdk
#swap the openjdk for the sun version, and document viewer 'evince' for the adobe 
#[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)
#add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) $distro partner"
# apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
# apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk  sun-java6-plugin 
# update-java-alternatives -s java-6-sun

---

### Post by oldfred on 2011-11-14
I know nothing about java web start.

[http://download.oracle.com/javase/6/docs/technotes/guides/javaws/](http://download.oracle.com/javase/6/docs/technotes/guides/javaws/)

---

### Post by Sollmeeya on 2011-11-20
I am having the same issue, with 11.04 there was no problem.

I've had a look round and followed a few ideas, specifically uninstall the open java, and then install all the sun-java packages, but still no luck.

Very frustrating as I will need this program quite a bit in the near future and I'd really like to use it from my desktop.. any ideas how to enable the java web-start? the link provided showed what it is, but no installation as far as I could tell.

I'd really appreciate a work around.

---

### Post by Pjotr123 on 2011-11-20
Java Web Start is apparently included in the standard Oracle JDK version 6. Since Oracle JDK ("Sun Java") has been removed from the Partner repo in Ubuntu 11.10, you need to install it manually.

You can install the latest secure Oracle JDK (6 update 29) as follows: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Note: the insecure 6u26 is still present in 11.04 and earlier (in the Partner repo), and also in some PPA's, but won't be updated anymore due to license trouble... Do not use it!

By the way: I fail to see why 6u26 isn't being removed instantly from the Partner repo's of 11.04 and earlier.... I've repeatedly brought this serious issue to the attention of the developers and of the Ubuntu Security Team. But to no avail yet. It's a shame. :(

---

### Post by Sollmeeya on 2011-11-21
Thanks for the tip on the java update, I followed all the instructions, and now according to the elluminate website, my system is perfectly setup to run elluminate.

Only it doesn't do it, opening the jnlp file normally starts off a series of downloads, but now it only opens a new window with the same jnlp file and an endless series of open file windows.

Any advice, should this now be filed as a bug? It worked beautifully in 11.04, with no fiddling around.:confused:

---

### Post by Sollmeeya on 2011-11-30
still having the same problem. Any help, ideas, commiserations, you know, all received happily.](*,)

---

### Post by Pjotr123 on 2011-11-30
> **Sollmeeya said:**
> still having the same problem. Any help, ideas, commiserations, you know, all received happily.](*,)

For the sake of troubleshooting: have you tested this website in another operating system? Windows, for example, with the same (latest) Java version, namely 6u29?

Anyway, you can try the following:

a. Clear the content of Java's cache and tame it a bit:
Control Panel - Tab General - Temporary Internet Files - Settings... - Disk Space: put the slider at 100 MB

Then press Delete Files... OK - OK - OK.

Note: there's an instruction on the easylinuxtipsproject page, how to start Java's control panel when you've installed Java manually.

b. Disable all add-ons that you have installed in Firefox, clear the cache and history of Firefox, and then try again;

c. If this doesn't help, repeat step a., and then try Google Chrome (not Chromium):
[http://www.google.com/chrome?hl=en](http://www.google.com/chrome?hl=en)

A "clean" Chrome without extensions is always handy for troubleshooting anyway, although I don't like it as much as Firefox. :-)

---

### Post by Sollmeeya on 2011-12-08
Firstly, 

thanks for the help!

I tried both options, firefox did exactly what it always did,

Chrome did the same, ie downloaded the jnlp file to downloads, but when I tried to open that file, it just opened another tab on the browser and downloaded a second version of the file. 

What used the happen is that the downloaded file would be run in a terminal, which would set off a series of downloads from elluminate, which then would open a new window. I can't remember if this was a firefox window, or a separate application.

It looks like all my browsers are not doing the correct thing with the downloaded file, the jnlp file.

It works fine on mac and windows. and with 11.04 the same.

According to the check your set up page of the elluminate website, everything is fine.

I am at a loss. 

:confused:

---

