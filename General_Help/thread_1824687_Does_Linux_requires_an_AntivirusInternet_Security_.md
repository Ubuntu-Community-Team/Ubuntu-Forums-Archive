---
title: "Does Linux requires an Antivirus/Internet Security Suite?"
date: 2011-08-14
forum: General Help
---

### Post by soumyabratapaul on 2011-08-14
I am using Ubuntu 10.04 LTS, and I want to know if it is perfectly safe to browse and download from the internet, on the Linux box? I do not require an antivirus or an internet security suite for protection? Is Linux completely virus protected?

Is there is any antivirus suite, please inform me and please also be kind enough to post a link to it's download or information page.

Thanking you all in advance for all your suggestions.

---

### Post by haqking on 2011-08-14
> **soumyabratapaul said:**
> I am using Ubuntu 10.04 LTS, and I want to know if it is perfectly safe to browse and download from the internet, on the Linux box? I do not require an antivirus or an internet security suite for protection? Is Linux completely virus protected?

Is there is any antivirus suite, please inform me and please also be kind enough to post a link to it's download or information page.

Thanking you all in advance for all your suggestions.


Linux does not suffer from Viruses Like other OS, there are no known viruses in the wild, the main reason using AV on linux is to scan incase you share files with windows users.

It can still suffer from trojans, rootkits etc, but that comes down to vigilence and making sure you stick to the security model and not disabling passwords etc.

Common sense, dont tell your system you want it to do something unless you are sure etc.

In browsers you can still suffer from XSS or CSFR,  other script related issues so use things like NoScript plugin for firefox etc.

Also look at apparmor for profiling your applications and there privelege

See below staring with Bodhi.Zazen overvie3w of Linux Security

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

then here for AV information:

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by dcstar on 2011-08-15
> **soumyabratapaul said:**
> I am using Ubuntu 10.04 LTS, and I want to know if it is perfectly safe to browse and download from the internet, on the Linux box? I do not require an antivirus or an internet security suite for protection? Is Linux completely virus protected?

Is there is any antivirus suite, please inform me and please also be kind enough to post a link to it's download or information page.

Thanking you all in advance for all your suggestions.

Linux's major security issue is dopey users installing software from unverified sources, so take away the major security hole (humans) and Linux will almost be "perfectly safe".

---

### Post by Nathan_M on 2011-08-15
As others have mentioned, there aren't really any significant virus threats out there for home Linux users. Yes, there are security reasons that this is difficult for the virus maker, but security holes are regularly found so it's entirely possible. The main reason there aren't really any viruses is because there are fewer domestic Linux users than Windows users, and they run so many different configurations that it'd be difficult to make a virus spread.

There are anti-virus packages out there, but most Linux users just don't use them. Have a search in Ubuntu Software Installer if you'd like the extra security.

Have a read up on staying safe online though. There are plenty of security threats which are OS-independent, most notably phishing attacks.

---

### Post by varunendra on 2011-08-15
IMHO, a little bit of IT related IQ, common sense and awareness is much more important and powerful than any antivirus, especially when talking about Linux.

As dcstar pointed out, if you use files from only trusted sources, and know what you are doing while connecting to external sources and allowing access to your file-system, you will almost always be secure with linux.

---

