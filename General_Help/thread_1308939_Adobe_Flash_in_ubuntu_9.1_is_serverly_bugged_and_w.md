---
title: "Adobe Flash in ubuntu 9.1 is serverly bugged and won't install/work"
date: 2009-11-01
forum: General Help
---

### Post by 133794m3r on 2009-11-01
I've tried this about 10 times now. I install it from teh synatpic package manager it, it says it installs. I restart firefox. It shows that it was installed. So i decide to try to install it using the downloader/.deb from adobe. And it tells me "wrong architecture i836. I'm on ubuntu x64_86 so i THOUGHT i had the ability to install i836 debs since in my mind it's just a 32bit deb and i have 32bit support. Which is shown via me having firefox.

This is one more annoying issue i've found with Ubuntu 9.10.

I thought i'd not find any new issues from ubuntu 9.10 as well it is ubuntu and it's never given me "new" problems. Flash used to work on 8.10/9.04. I don't get why it's not working now...

---

### Post by Nburnes on 2009-11-01
[http://ubuntuforums.org/showthread.php?t=1081964](http://ubuntuforums.org/showthread.php?t=1081964)

---

### Post by 133794m3r on 2009-11-01
I don't need the 64bit version of flash. I never said i needed the 64bit version. I'm using Firefox not opera. Firefox is 32bit.  Until firefox goes 64bit, i'm not going to use flash 64bit.

"Reboot Opera,..."

He's using opera. :/ i was talking about flash 32bit. 64bit doesn't help me at all. As it's useless to me.

---

### Post by lavinog on 2009-11-01
> **133794m3r said:**
> I don't need the 64bit version of flash. I never said i needed the 64bit version. I'm using Firefox not opera. Firefox is 32bit.  Until firefox goes 64bit, i'm not going to use flash 64bit.

"Reboot Opera,..."

He's using opera. :/ i was talking about flash 32bit. 64bit doesn't help me at all. As it's useless to me.

Why is your firefox 32bit if you are using 64bit ubuntu?

---

### Post by 133794m3r on 2009-11-01
> **lavinog said:**
> Why is your firefox 32bit if you are using 64bit ubuntu?

Maybe you're new here but i don't know how much you know about firefox. But they don't officially do 64bit. They only release 32bit. And that's b/c flash isn't yet officially supported in 64bit. So firefox is 32bit.

---

### Post by lavinog on 2009-11-01
> **133794m3r said:**
> Maybe you're new here but i don't know how much you know about firefox. But they don't officially do 64bit. They only release 32bit. And that's b/c flash isn't yet officially supported in 64bit. So firefox is 32bit.

```

file /usr/lib/firefox-3.5.4/firefox
/usr/lib/firefox-3.5.4/firefox: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped

```
Mozilla doesn't support 64bit firefox, but 64bit Ubuntu comes with a 64bit compiled firefox.

The flash in the 64bit repo is 32bit because the true 64bit version is in alpha.  The repo version uses a 32bit wrapper.  The wrapper is required for a 64bit system, and if you force the package manager to install a 32bit package, it will not install the wrapper, thus fail.

---

### Post by 133794m3r on 2009-11-01
Why in the world would ubuntu use 64bit firefox in the first place if they have to compile a trunk build or something similar. It's the same with pidgin back when they used to do it.

So your'e saying they "manually compiled" a 64bit pidgin back then?

also i have ti working via the in firefox plugin finder. Didn't try that thing at first but now it's finally woring.

---

### Post by lavinog on 2009-11-02
> **133794m3r said:**
> Why in the world would ubuntu use 64bit firefox in the first place if they have to compile a trunk build or something similar. It's the same with pidgin back when they used to do it.

So your'e saying they "manually compiled" a 64bit pidgin back then?


I am not sure what you mean by "manually compiled."
The ubuntu mozilla team does everything:
[https://wiki.ubuntu.com/MozillaTeam](https://wiki.ubuntu.com/MozillaTeam)

There are various benchmarks that show that firefox 64 runs better than firefox 32 on a 64bit os.  That should be a good enough reason to provide a 64bit firefox.

---

