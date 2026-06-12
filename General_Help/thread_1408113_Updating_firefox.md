---
title: "Updating firefox"
date: 2010-02-16
forum: General Help
---

### Post by TheDarkSix on 2010-02-16
Having a hardtime its a .tar.bz2 

google gives mixed results...Uhm some please please - Yes i am a COMPLETE noob sorry

also i was using the default 3.5.3 that installed with xubuntu...is my system compromised because i visited a lot of websites and sites now exploit firefox MORE than ie

More exploits exist for firefox more than EVER and it SURPASSES internet explorer so i am just paranoid to death

I seriously got damaged by windows and gradually recovering

---

### Post by Richard1979 on 2010-02-16
> **TheDarkSix said:**
> sites now exploit firefox MORE than ie

No they don't.
And I think getting a virus to work under Linux without the user noticing would be *impossible*.

Anyway the commands you need are:
```

bunzip2 file.tar.bz2
tar xf file.tar
```

---

### Post by x33a on 2010-02-16
If you are planning on compiling firefox, then using a ppa would be a better option.

This is a ppa for firefox stable:

[https://launchpad.net/~mozillateam/+archive/firefox-stable]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable")

> **Richard1979 said:**
> 
No they don't.
And I think getting a virus to work under Linux without the user  noticing would be *impossible*.
+1

> Anyway the commands you need are:
```

bunzip2 file.tar.bz2
tar xf file.tar
```

or 
```
tar xvjf file.tar.bz2
```

---

### Post by SeaJayEmm on 2010-02-16
Its virtually impossible to get a virus in Linux. No worries there, so need for an antivirus.

---

### Post by lovinglinux on 2010-02-16
See the [COLOR="Sienna"]**Installing Other Versions**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by TheDarkSix on 2010-02-17
> **Richard1979 said:**
> No they don't.
And I think getting a virus to work under Linux without the user noticing would be *impossible*.

Anyway the commands you need are:
```

bunzip2 file.tar.bz2
tar xf file.tar
```

 Richard1979 is there an easier way? i dont know how to compile things  I downloaded the firefox to my downloads and i have no idea how to make the terminal go about installing it...sorry

---

### Post by Pjotr123 on 2010-02-17
Stick with your current Firefox: it's secure and you're safe. And it will be kept secure by Canonical, during the life cycle of your Ubuntu version (for 18 months after release).

Some background information about Linux security:
[http://sites.google.com/site/easylinuxtipsproject/security](http://sites.google.com/site/easylinuxtipsproject/security)

Relax and enjoy your Ubuntu. :-)

P.S.: My Firefox was updated to 3.5.8 today... By the Ubuntu Update Manager. Yours was, too, I suppose. So: no worries, mate. :-)

---

### Post by wojox on 2010-02-17
> **TheDarkSix said:**
> Richard1979 is there an easier way? i dont know how to compile things  I downloaded the firefox to my downloads and i have no idea how to make the terminal go about installing it...sorry

Download the latest stable release from the ppa's: [http://wojox.homelinux.net/?p=67](http://wojox.homelinux.net/?p=67)

---

### Post by t0p on 2010-02-17
Where did you get this firefox archive from?  What exactly is in it?

There's no real need for you to upgrade your Firefox.  If you really want to upgrade, we'll all be happy to help you.  But your current version (3.5.x) is not somehow vulnerable to attack or anything.  As long as you install the security updates suggested by Update Manager, you're perfectly safe from attack.  So stop being so paranoid!  Firefox (and the rest of the software in the Ubuntu OS) is perfectly safe.

---

### Post by hissyfut on 2010-02-17
you don't need no stinkin ppa!

if you want to try to latest without changing the old ubuntu version.... but BEFORE you do the following, best to  back up your mozilla personal directory in case you do something wrong......
assuming you are in your home user directory.....

tar cvfj mymozillabackup.tar.bz2 .mozilla

download the latest binary.
[http://www.mozilla.com/en-US/firefox/](http://www.mozilla.com/en-US/firefox/)

tar xvfj firefox-xxx.tar.bz2

move the firefox directory just created to somewhere.

create a folder somewhere to contain a new profile.....
mkdir testnewfirefox

run the new firefox with a profile...
/path/to/somewhere/firefox/ firefox -profile "/path/to/testnewfirefox"

If you don't specify the -profile part, then the firefox will overwrite your old .mozilla files, and possibly screw up your world! Hence the reason to back up your old settings first. Consider this highly dangerous and might make your computer explode! just kidding, it is really simple.

---

### Post by hissyfut on 2010-02-17
> **TheDarkSix said:**
> 
also i was using the default 3.5.3 that installed with xubuntu...is my system compromised because i visited a lot of websites and sites now exploit firefox MORE than ie

More exploits exist for firefox more than EVER and it SURPASSES internet explorer so i am just paranoid to death


if you have links to this information, there is sure people who would be interested. can you post a link?

---

### Post by 26venger on 2010-02-17
> **SeaJayEmm said:**
> Its virtually impossible to get a virus in Linux. No worries there, so need for an antivirus.

why is it so difficult to install a virus on linux? Is it due to the fact that the virus wouldnt be able to install itself because of the strict file permessions linux has?

---

### Post by x33a on 2010-02-17
> **26venger said:**
> why is it so difficult to install a virus on linux? Is it due to the fact that the virus wouldnt be able to install itself because of the strict file permessions linux has?

Better read these:

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by 26venger on 2010-02-18
wow, thanks alot x33a those links contained a wealth of info

---

### Post by TheDarkSix on 2010-02-21
I see 2 firefox's in update manager, one is a meta package and the other is just 3.5.8+ and much larger than meta package...

Also the current version of firefox installed with ubuntu/xubuntu has flaws according to mozilla's website

[MFSA 2009-51]("http://www.mozilla.org/security/announce/2009/mfsa2009-51.html")     Chrome privilege escalation with FeedWriter
     [MFSA 2009-50]("http://www.mozilla.org/security/announce/2009/mfsa2009-50.html")     Location bar spoofing via tall line-height Unicode characters
     [MFSA 2009-49]("http://www.mozilla.org/security/announce/2009/mfsa2009-49.html")     TreeColumns dangling pointer vulnerability
     [MFSA 2009-47]("http://www.mozilla.org/security/announce/2009/mfsa2009-47.html")     Crashes with evidence of memory corruption (rv:1.9.1.3/1.9.0.14)

---

