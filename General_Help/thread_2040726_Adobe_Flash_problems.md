---
title: "Adobe Flash problems"
date: 2012-08-11
forum: General Help
---

### Post by Robert Finley on 2012-08-11
I have a machine dual-booting WinXP and a fresh install of lubuntu 12.04.  I have installed lubuntu-restricted-extras.

The machine has a P-III 930MHz and 512 RAM.  I understand that this is well below the minimum hardware requirements for flash according to adobe.com.

I use Chromium as the sole browser in both OSs.

I am wondering why WinXP/Chromium runs flash with no problem but Lubuntu/Chromium will not run flash at all without crashing.

---

### Post by cwsnyder on 2012-08-11
Do you have the same version of Chromium on both machines?  Chrome/Chromium actually doesn't use Adobe's Flash plug-in, but has their own.

---

### Post by Robert Finley on 2012-08-11
I have read that Chrome uses it's own flash.  When I initially installed though, I would see a message on various pages that said "Get Adobe Flash" with a link to the site.

Once I install lubuntu-restricted-extras as directed in the lubuntu [documentation]("https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#Need_to_install_Adobe_Flash_Player_or_MP3_codecs"), flash would actually load but would always crash.

I do not have the same versions of Chromium on both sides.

I have:
18.0.1025.168= Lubuntu repositories
22.0.1212.0= Win version downloaded from [website]("http://getchromium.org/").

---

### Post by claracc on 2012-08-11
I recommend to use an adobe flasplayer under 11.2 version, since 11.2.202. can cause crashes in old pcs.

In my ten years old pIII, 1GHZ, 512 Mb ram I have installed adobe flash player 10.3.183.10, you can find old flash releases in [http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html).

You must take into account that it can have security risks.

---

### Post by Robert Finley on 2012-08-11
> **claracc said:**
> you can find old flash releases in [http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html).

Awesome.  Thank you. I will check that out.

---

### Post by Robert Finley on 2012-08-11
> **claracc said:**
>  I have installed adobe flash player 10.3.183.10

I installed the same version and it is working now.  Thank you again for your assistance.

---

### Post by claracc on 2012-08-12
You are very welcome.

Glad you got fixed your problem.
I commited a typo error and really the flash version I have installed in my old pentiumIII is 10.3.183.20.

You can avoid security risks using addons as flashblock or nonscript or adblock (they are firefox addons, I don't know if they are available in chromium)

---

