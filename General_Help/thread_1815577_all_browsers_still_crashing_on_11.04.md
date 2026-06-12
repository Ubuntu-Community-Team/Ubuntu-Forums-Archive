---
title: "all browsers still crashing on 11.04"
date: 2011-07-31
forum: General Help
---

### Post by ottosykora on 2011-07-31
I am still in progress of testing 11.04 on my HP probook 6550b. This is basically rather current and standard intel based notebook with M520/2.4ghz and intel HD graphic i5.

11.04 runs on it either with unity or classic, but regardless of which gui I use, browsers do crash all the time. Tried firefox with default extensions, then seamonkey and then chromium. Nothing works really.

I am not able to run any search in this forum for example, this will make any of the browsers crash.

The kernels I tried are standard 32bit as well as -pae variety.

Everything seemed to be more stable on real 64bit ubuntu, but number of software does not work here, so not real alternative.

Any experience with browsers permanently crashing on 11.04?

Example of crash readout of the firefox:

Add-ons: [email]globalmenu@ubuntu.com:1.0.2,langpack-de@firefox.mozilla.org:4.0,langpack-en-GB@firefox.mozilla.org:4.0,langpack-en-US@firefox.mozilla.org:4.0,langpack-en-ZA@firefox.mozilla.org:4.0,langpack-es-AR@firefox.mozilla.org:4.0,langpack-es-CL@firefox.mozilla.org:4.0,langpack-es-ES@firefox.mozilla.org:4.0,langpack-es-MX@firefox.mozilla.org:4.0,langpack-pt-BR@firefox.mozilla.org:4.0,langpack-pt-PT@firefox.mozilla.org:4.0,langpack-zh-CN@firefox.mozilla.org:4.0,ubufox@ubuntu.com[/email]:0.9,{972ce4c6-7e08-4474-a285-3208198ce6fd}:4.0
BuildID: 20110419185614
CrashTime: 1312133360
EMCheckCompatibility: true
FramePoisonBase: 00000000f0dea000
FramePoisonSize: 4096
InstallTime: 1312130779
ProductName: Firefox
SecondsSinceLastCrash: 130
StartupTime: 1312133315
Theme: classic/1.0
Throttleable: 1
URL: [http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)
Vendor: Mozilla
Version: 4.0

---

### Post by mike555 on 2011-07-31
You might try not using (disable) globelmenu in firefox and see......... 
  or try using "classic Ubuntu" desktop and see if your still having crashes ....

---

### Post by ottosykora on 2011-08-01
well tried all obvious

changed to classic and classic(no effects) then disabled globalmenu... still all the same.

then crash reports started with all the language addons...
disabled all those one by one too...
still crashing 
removed one by one all addons and extensions...
still crashing
mozillas unusable completely, cant even read this forum here

chromium , well can read, but when it comes to something more complex like search, then it does crash too

when I restore 10.10 from backup, all works fine, so it is something connected with 11.04, as chromium crashes too

Further indication: tried to install flash, but this does crash immediately too (flash itself) 

Tried to install skype, installed ok, started ok, but crashed and whole os got frozen few seconds after connection to test was started

Tried on standard and -pae kernels, no difference

---

### Post by fermin on 2011-12-20
Did you solve this? I have the same problem with Ubuntu 11.10 and had it on 11.04 before on the same machine. The problem persisted even after a fresh install of 11.10 in my old Pentium 4 machine. Any new ideas? I know it is not the network because I have other machines working with same software in the same network, so it must be software-hardware interaction related.

---

