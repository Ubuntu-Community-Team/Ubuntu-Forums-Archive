---
title: "Firefox 10 won't upload anymore"
date: 2012-02-07
forum: General Help
---

### Post by dgermann on 2012-02-07
Hi--

Just the other day upgraded to Firefox 10.0 via ppa. Can no longer upload.

System: Ubuntu 10.04 LTS
Browser: FireFox 10.0
NoScript: 2.2.9
Where I have tried uploading: Facebook, using both regular uploader and basic uploader; Dropbox, using both regular uploader and basic uploader.

Facebook complained about Flash, if I remember correctly.
Dropbox gives an Error (500) and NoScript pops up a yellow box on top that reads: "NoScript filtered a potential cross-site scripting (XSS) attempt from [[https://www.dropbox.com]](https://www.dropbox.com]). Technical details have been logged to the Console."

The NoScript Console entry which I think might be the one reads:

>     Error: [Exception... "Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) [nsIURI.host]" nsresult: "0x80004005 (NS_ERROR_FAILURE)" location: "JS frame :: file:///usr/lib/firefox-10.0/extensions/ubufox@ubuntu.com/components/ufoxHTTPListener.js :: <TOP_LEVEL> :: line 64" data: no]
    Source File: file:///usr/lib/firefox-10.0/extensions/ubufox@ubuntu.com/components/ufoxHTTPListener.js
    Line: 64

Since this is happening generally on uploads, I am wondering if this is a problem with FF? Could it be a problem with Appamor?

I have tried disabling NoScript and still cannot upload to these sites. I also have these extensions on FF, and have tried disabling them in sequence and still no joy: BetterPrivacy 1.68; HTTPS-Everywhere 1.2.2; Ubuntu Firefox Modifications 0.9.3.

I was able to upload to both of these before the upgrade.

Thanks for any help you can give me!

---

### Post by lovinglinux on 2012-02-08
From the errors, looks like a problem with Ubuntu Firefox Modifications extension.

Try Firefox in safe mode:

```
firefox -safe-mode
```

Have you tried to upload to other sites? I don't know about Dropbox, but Facebook loves to break things with their updates.

---

### Post by dgermann on 2012-02-08
lovinglinux--

Thanks!

Just tried safe mode, and no joy on either Facebook or dropbox.

Then I tried Epiphany Browser (2.30.2) from this same computer to upload and had no problem on Facebook.

Does this suggest any clues? What might I try next?

Thanks!

---

### Post by lovinglinux on 2012-02-10
> **dgermann said:**
> lovinglinux--

Thanks!

Just tried safe mode, and no joy on either Facebook or dropbox.

Then I tried Epiphany Browser (2.30.2) from this same computer to upload and had no problem on Facebook.

Does this suggest any clues? What might I try next?

Thanks!

Only suggests the problem is localized.

Well, you could try a clean profile.

```
firefox -P
```

---

### Post by dgermann on 2012-02-11
lovinglinux--

Thanks!

Actually, the problem looks like it was apparmor. See this thread: [http://ubuntuforums.org/showthread.php?p=11681491&posted=1#post11681491]("http://ubuntuforums.org/showthread.php?p=11681491&posted=1#post11681491"), posts 52 & 53.

That apparmor thing has been a nemesis for me! I almost want to disable it!

Thanks for giving me hand holding, lovinglinux!

---

### Post by lovinglinux on 2012-02-11
> **dgermann said:**
> lovinglinux--

Thanks!

Actually, the problem looks like it was apparmor. See this thread: [http://ubuntuforums.org/showthread.php?p=11681491&posted=1#post11681491]("http://ubuntuforums.org/showthread.php?p=11681491&posted=1#post11681491"), posts 52 & 53.

That apparmor thing has been a nemesis for me! I almost want to disable it!

Thanks for giving me hand holding, lovinglinux!

That is the first time I see an AppArmor problem related to upload. Usually it prevents Firefox from downloading. Good to know.

It wouldn't be wise to recommend disabling the AppArmor profile for Firefox, but you need to balance security and usability. If thing is driving you crazy, then don't use it. I don't use it for that reason.

---

### Post by dgermann on 2012-02-11
lovinglinux--

Well, if you as a developer do not use it, that says a lot!

Not sure what good it does me at all. In any case, I read that it used to be shipped with the firefox profile disabled.

Probably wouldn't be so bad if I could find someplace which explained that crazy syntax they use, and what it is trying to do. The Ubuntu community page for it does not explain it at all, just gives a cookbook for turning it on and off totally or by profile. One of those pages which, if you know all the stuff that's there already, it explains it well, but if you're in the dark when you first come there, you are in the dark when you leave! ;)

Even when I ask for status, it gives a bunch of code, instead of saying whether anything is in enforce or complain, like it used to do! Not friendly.

---

### Post by lovinglinux on 2012-02-13
> **dgermann said:**
> lovinglinux--

Well, if you as a developer do not use it, that says a lot!

Not sure what good it does me at all. In any case, I read that it used to be shipped with the firefox profile disabled.

Probably wouldn't be so bad if I could find someplace which explained that crazy syntax they use, and what it is trying to do. The Ubuntu community page for it does not explain it at all, just gives a cookbook for turning it on and off totally or by profile. One of those pages which, if you know all the stuff that's there already, it explains it well, but if you're in the dark when you first come there, you are in the dark when you leave! ;)

Even when I ask for status, it gives a bunch of code, instead of saying whether anything is in enforce or complain, like it used to do! Not friendly.

As far as I know, Firefox profile comes disabled by default. At least I never had to disable it on my system.

Only you can decide if AppArmor is for you or not. AppArmor restricts what the application can do on your system. It is particularly important to block zero-day attacks, which means those threats nobody is aware of yet. People who doesn't use AppArmor to restrict Firefox, usually use NoScript to prevent rogue scripts from running. It is not a replacement, but another layer of security.

Check this thread: [http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

bodhi.zazen is the AppArmor guru in the forums.

Use this command to get the status:

```
sudo apparmor_status
```

It will list all the profiles in enforce and complain mode.

---

### Post by dgermann on 2012-02-13
lovinglinux--

I thought I too had read that the firefox profile came disabled, but not on my system for some reason. One day it just showed up. That was my first post to bodhi.zazen a couple years ago (you responded to me way back then--held my hand till bodhi.zazen showed up--thanks!) Even an upgrade to FF the last couple days offered to give me a new profile!

Thanks very much for the link to the tutorial. I think it will be helpful.

The undecipherable stuff came when I used the command ```
sudo service apparmor status | grep firefox 
```
Yours gives much better info! Thanks!

Thanks, lovinglinux!

---

### Post by lovinglinux on 2012-02-13
*sudo service apparmor status* and *sudo apparmor_status* give me the same result and it is readable.

```
apparmor module is loaded.
14 profiles are loaded.
14 profiles are in enforce mode.
   /sbin/dhclient
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-thumbnailer
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/lightdm/lightdm-guest-session-wrapper
   /usr/lib/telepathy/mission-control-5
   /usr/lib/telepathy/telepathy-*
   /usr/sbin/mysqld-akonadi
   /usr/sbin/mysqld-akonadi///usr/sbin/mysqld
   /usr/sbin/mysqld-digikam
   /usr/sbin/mysqld-digikam///usr/sbin/mysqld
   /usr/sbin/tcpdump
0 profiles are in complain mode.
2 processes have profiles defined.
2 processes are in enforce mode.
   /usr/lib/telepathy/mission-control-5 (1872) 
   /usr/lib/telepathy/telepathy-* (1924) 
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.
```

---

### Post by dgermann on 2012-02-14
lovinglinux--

Thanks!

Actually, after I posted I discovered that they both gave the same results. But what I get seems unreadable to me:
```
doug@doug2:~$ sudo apparmor_status |grep firefox
[sudo] password for doug: 
   /usr/lib/firefox-10.0/firefox{,*[^s][^h]}
   /usr/lib/firefox-10.0/firefox{,*[^s][^h]}//firefox_java
   /usr/lib/firefox-10.0/firefox{,*[^s][^h]}//firefox_openjdk
   /usr/lib/firefox-9.0.1/firefox-*bin
   /usr/lib/firefox-9.0.1/firefox-*bin//firefox_java
   /usr/lib/firefox-9.0.1/firefox-*bin//firefox_openjdk
   /usr/lib/firefox-10.0/firefox{,*[^s][^h]}//firefox_openjdk//null-29
   /usr/lib/firefox-10.0/firefox{,*[^s][^h]}//firefox_openjdk//null-2a

```

---

