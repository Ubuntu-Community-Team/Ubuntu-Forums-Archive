---
title: "Ubuntu Maverick amd64: Adobe Flash, BIG problem!"
date: 2010-12-02
forum: General Help
---

### Post by madmax.santana on 2010-12-02
I inspired my roommate to install Linux on his laptop... And he is a keen Youtube user.

He thinks of me as some kinda Linux Guru (which I have already tried to clarify that I am not...) So I was really embarrassed yesterday when after a lot of thoughts and acts, I couldn't manage to find a way for him to install Adobe flash player on his computer... 

Last time I had to install Flash was back when I was using Lucid and at that time I just had to install the restricted-extras meta-pack which installed all necessary prop. codecs and other stuff, including flash player... 

It is not the case anymore. It seems that what that meta-pack installs is a 32-bit flash player which is not longer supported by amd64 release... So I will have to uninstall that 32-bit version and install the correct 64-bit flash player instead.

That much is clear.

The problem is "how"...

I googled it and found out that the problem is very common and there are various scripts lying on internet which could automatically uninstall the wrong versions and install the correct ones. But none of them work, at least on none of the PCs that I have tried on.

I tried downloading the 64-bit player manually. But I cannot find the link to the specific version. When I go to the install page on Adobe website, it downloads the same 64-bit version. However, there is a link there saying "64-bit users .... blah blah blah"... When I click that link it takes me to another page which lists all the current releases of flash player for Windows and Mac... But all I can find there is beta and 32... Not stable and 64...

What should I do now?

---

### Post by Vaphell on 2010-12-02
worry not, here is your savior [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/) it will keep flash updated

even if it's beta, it works

---

### Post by TBABill on 2010-12-02
+1!!!!!!!!!! I install Flash-Aid every time I install Ubuntu because it just works flawlessly and keeps you up to date by checking and upgrading to the newest if necessary, plus it knows if you need 32 bit or 64 bit, which you can't do with the repo!

---

### Post by madmax.santana on 2010-12-03
FLASH-AID installed. Run... This came out.

```
Please wait...DON'T CLOSE THIS TERMINAL!
[sudo] password for mambo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package lightspark
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package swfdec-mozilla is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mozilla-plugin-gnash is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package browser-plugin-gnash is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'adobe-flashplugin' can't be removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-installer is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Hit http://archive.canonical.com maverick Release.gpg
Hit http://pk.archive.ubuntu.com maverick Release.gpg               
Hit http://security.ubuntu.com maverick-security Release.gpg        
Hit http://extras.ubuntu.com maverick Release.gpg                   
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en    
Ign http://pk.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US 
Hit http://archive.canonical.com maverick Release                    
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://pk.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Hit http://archive.canonical.com maverick/partner Sources            
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Hit http://extras.ubuntu.com maverick/main Sources                   
Hit http://archive.canonical.com maverick/partner amd64 Packages     
Hit http://extras.ubuntu.com maverick/main amd64 Packages            
Ign http://pk.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://pk.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://pk.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://pk.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Ign http://pk.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Hit http://security.ubuntu.com maverick-security Release
Ign http://pk.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Hit http://security.ubuntu.com maverick-security/main Sources
Hit http://security.ubuntu.com maverick-security/restricted Sources
Hit http://pk.archive.ubuntu.com maverick-updates Release.gpg
Hit http://security.ubuntu.com maverick-security/universe Sources
Ign http://pk.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://pk.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Hit http://security.ubuntu.com maverick-security/multiverse Sources
Hit http://security.ubuntu.com maverick-security/main amd64 Packages
Ign http://pk.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Hit http://security.ubuntu.com maverick-security/restricted amd64 Packages
Ign http://pk.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Hit http://security.ubuntu.com maverick-security/universe amd64 Packages
Ign http://pk.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Hit http://security.ubuntu.com maverick-security/multiverse amd64 Packages
Ign http://pk.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://pk.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://pk.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://pk.archive.ubuntu.com maverick Release
Hit http://pk.archive.ubuntu.com maverick-updates Release
Hit http://pk.archive.ubuntu.com maverick/main Sources
Hit http://pk.archive.ubuntu.com maverick/restricted Sources
Hit http://pk.archive.ubuntu.com maverick/universe Sources
Hit http://pk.archive.ubuntu.com maverick/multiverse Sources
Hit http://pk.archive.ubuntu.com maverick/main amd64 Packages
Hit http://pk.archive.ubuntu.com maverick/restricted amd64 Packages
Hit http://pk.archive.ubuntu.com maverick/universe amd64 Packages
Hit http://pk.archive.ubuntu.com maverick/multiverse amd64 Packages
Hit http://pk.archive.ubuntu.com maverick-updates/main Sources
Hit http://pk.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://pk.archive.ubuntu.com maverick-updates/universe Sources
Hit http://pk.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://pk.archive.ubuntu.com maverick-updates/main amd64 Packages
Hit http://pk.archive.ubuntu.com maverick-updates/restricted amd64 Packages
Hit http://pk.archive.ubuntu.com maverick-updates/universe amd64 Packages
Hit http://pk.archive.ubuntu.com maverick-updates/multiverse amd64 Packages
Reading package lists... Done
--2010-12-03 19:18:16--  http://download.macromedia.com/pub/labs/flashplayer10/flashplayer_square_p2_64bit_linux_092710.tar.gz
Connecting to 192.168.100.1:8080... connected.
Proxy request sent, awaiting response... 502 Proxy Error ( The request was rejected by the HTTP filter. Contact your ISA Server administrator.  )
2010-12-03 19:18:16 ERROR 502: Proxy Error ( The request was rejected by the HTTP filter. Contact your ISA Server administrator.  ).

Finished! You can close this terminal. You must restart Firefox now.

```

Flash still not working. What now?

---

### Post by Vaphell on 2010-12-03
as you can see downloading of flash failed, ask lovinglinux how to fix that
you got some kind of proxy or what? because it connects to your local network ip address (192.168.x.x) and it says gtfo

can you download that file [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer_square_p2_64bit_linux_092710.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer_square_p2_64bit_linux_092710.tar.gz) manually using web browser?

---

### Post by madmax.santana on 2010-12-03
Hahaha! That is exactly the case... I got a proxy and it connects to the proxy server and the server says gtfo!
What should I do now? Can't I manually do what FLASH-AID does? Because as it appears to me, it s trying to download the source code and then it is going to install it manually. If I can download the source code, how to compile it... And where to get the source code from?

---

### Post by Vaphell on 2010-12-03
flash aid is a convenience tool
it automates the flash installation - it purges conflicting packages and existing plugins (frequent cause of pain for the user) and for 32 bit it uses repo (afaik) to install, for 64bit it downloads latest beta from adobe and unpacks it 'manually' where it belongs

if you manage to download that tar.gz file manually to your computer, there will be libflashplayer.so inside

on my box it is located in
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
firefox uses the one located in /usr/lib/mozilla/plugins/ (according to about:****plugins) so move the file there

---

### Post by madmax.santana on 2010-12-03
> it downloads latest beta from adobe and unpacks it 'manually' where it belongs

Does a mirror to that beta version exist?

---

### Post by Irony on 2010-12-03
The 64 bit flashes have once again mysteriously disappeared from here, adobe isn't committed to 64 bit;

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by galvatron408 on 2010-12-03
> **Irony said:**
> The 64 bit flashes have once again mysteriously disappeared from here, adobe isn't committed to 64 bit;

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

I'm running it and it crashes like there's no tomorrow. 64-bit flash just isn't ready for prime time.

ThinkPad-T61:/var/log$ grep segfault /var/log/messages | grep flash | wc -l
16

---

### Post by gmargo on 2010-12-03
> **Irony said:**
> The 64 bit flashes have once again mysteriously disappeared from here, adobe isn't committed to 64 bit;

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

The 64-bit stuff seems to have moved here:
[http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html)

---

### Post by Irony on 2010-12-04
Thanks for that... wondered where it had gone!

---

### Post by madmax.santana on 2010-12-04
*sigh*

That is still not accessible for me. Could anyone please find me a mirror to that or be kind enough to create a mirror (you know, upload it to a file server)...?

---

### Post by Irony on 2010-12-04
> **madmax.santana said:**
> That is still not accessible for me.
Do you mean the following link is not accessible? [http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html)

---

### Post by madmax.santana on 2010-12-04
Sometimes it says "Access Denied" and sometimes "Host Unreachable"... I guess there's some problem with proxy server

---

### Post by madmax.santana on 2010-12-10
> **Vaphell said:**
> flash aid is a convenience tool
it automates the flash installation - it purges conflicting packages and existing plugins (frequent cause of pain for the user) and for 32 bit it uses repo (afaik) to install, for 64bit it downloads latest beta from adobe and unpacks it 'manually' where it belongs

if you manage to download that tar.gz file manually to your computer, there will be libflashplayer.so inside

on my box it is located in
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
firefox uses the one located in /usr/lib/mozilla/plugins/ (according to about:****plugins) so move the file there

Thanks a lot. It worked. I download the libflashplayer.so and put it in the above mentioned dirs. The flash plugin is now working. :)

---

