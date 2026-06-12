---
title: "Firefox still running at shutdown"
date: 2011-12-29
forum: General Help
---

### Post by daldude on 2011-12-29
Many times when I go to shut down after running Firefox for for a long time and going to several sites Linux will say that Firefox is still running even though I closed it or in other words it does the same thing Windows is famous for doing, having some porly programmed apps still running in memory but not accessible or available to the user and you get the message that the program is not responding and have the option to end it now or wait or cancel shutdown.

So when this happens with Firefox in Linux I simply select Shutdown Anyway and then it kills Firefox and shuts down properly. If I don't use Firefox much and only go to a few site and then close it I don't get the shutdown problem.
Does anyone else have this problem and if so how do you fix it? It does not seem do any harm to Linux because it shuts down properly without errors or crashing but it's just an annoyance but I think it does cause Firefox to not remember any changes you do to it because every time  I try to add the Print Icon to the tool bar it goes away after I restart Firefox.:frown:

I have Linux 10.04 64 bit LTS

---

### Post by Erik1984 on 2011-12-29
It's a well known bug in 10.04 with the 3.6.x version of FF. My 'solution' is to open a terminal and type "pkill firefox". [https://bugs.launchpad.net/ubuntu/lucid/+source/firefox/+bug/875538](https://bugs.launchpad.net/ubuntu/lucid/+source/firefox/+bug/875538)

---

### Post by pretty_whistle on 2011-12-29
> **Euroman said:**
> It's a well known bug in 10.04 with the 3.6.x version of FF. My 'solution' is to open a terminal and type "pkill firefox". [https://bugs.launchpad.net/ubuntu/lucid/+source/firefox/+bug/875538](https://bugs.launchpad.net/ubuntu/lucid/+source/firefox/+bug/875538)
pkill firefox kills firefox, doesn't it?

---

### Post by Erik1984 on 2011-12-29
> **pretty_whistle said:**
> pkill firefox kills firefox, doesn't it?

That's right, it won't really help the TS as he already knows how to shut down ff. But that's just how I handle it until there is a real fix. And apparently, according to Launchpad, there is no such fix yet (please correct me if I'm wrong there!). Only workarounds like installing a newer version of FF from a PPA.

---

### Post by guestolo on 2011-12-29
I don't have the problem, using 11.10
Sounds like the user here resolved the issue, as did others
with this workaround
[http://ubuntuforums.org/showpost.php?p=11394760&postcount=12](http://ubuntuforums.org/showpost.php?p=11394760&postcount=12)

I would backup bookmarks, even take a screenshot of saved passwords if need be if you want to try this route

NOTE: Ensure Firefox isn't running when removing firefox and restarting after modifying about:config entries

---

### Post by Bobhuber on 2011-12-29
Why don't you backup your profile and bookmarks and install a newer version of FF ??
Anything 9.0+ will make you wish you had done it a long time ago.The speed increase is amazing.

---

### Post by daldude on 2011-12-29
Or you could simply open system monitor and kill it from there just click on firefox.bin and then click on the end process button. That is what I do when I try to re open Firefox and it tells me it is already running.

---

