---
title: "After a while, LibreOffice Writer gets SLOW?"
date: 2012-05-26
forum: General Help
---

### Post by ladasky on 2012-05-26
I have a new and unusual problem which I believe may have started when I upgraded to Ubuntu 11.10, but which may have occurred later.  

When I first boot up my computer and start LibreOffice Writer, everything seems fine.  After about two hours of switching back and forth between various applications, I start to notice slow scrolling.  Shortly after that, I have a noticeable lag in response to typing, and pop-up menus take up to a second to appear.

Every other application that I have open continues to operate normally.

The largest file that I am editing in LibreOffice Writer is a bit under 100 kilobytes.  It is text only, no attached graphics or anything fancy like that.

I read somewhere that the memory management settings for LibreOffice can be a bit conservative (I'll hunt down the link again if anyone cares).  I have selected Tools > Options > LibreOffice > Memory, and I've adjusted the Graphics cache settings upwards.  I increased the "Use for LibreOffice" to 50 MB, and the "Memory per object" setting to 10.0 MB.  This does not appear to have an effect.

My system configuration:
AMD 6-core CPU, 8 GB RAM, NVidia GTX 460 GPU, Ubuntu 11.10 x64.  All fairly recent hardware and software, as you can see.

If I look at the System Monitor, CPU loading and memory use do not appear to be a problem.  None of the CPU cores are registering much more than 10% use at any given moment.  I'm only using 2 GB of my 8 GB of RAM, and my 8 GB swap partition is completely unused.

Quitting and restarting LibreOffice Writer can sometimes restore normal response -- but other times, not.

Any suggestions?  Thanks.

---

### Post by ladasky on 2012-05-26
Following up to myself...

I just tried leaving LibreOffice Calc open to a spreadsheet in parallel with having a word-processing document open in Writer.  Both Calc and Writer start experiencing performance lags at the same time.

So the problem may be common to all LibreOffice components.

LibreOffice details: version 3.4.4 OOO340m1 (Build:402).

---

### Post by holycow131415 on 2012-05-26
Sounds like one of those weird things that may start happening because of upgrading instead of clean installing. You arent on the newestt ubuntu so maybe movin on up again will solve it.

---

### Post by ladasky on 2012-05-27
> **holycow131415 said:**
> Sounds like one of those weird things that may start happening because of upgrading instead of clean installing. You arent on the newestt ubuntu so maybe movin on up again will solve it.

Actually, I just went through a massive reinstallation process, because of some _[problems with NVidia]("http://ubuntuforums.org/showthread.php?p=11895731#post11895731")_ graphics hardware and drivers.  In that process I eventually ended up starting with a fresh installation of the OS, which overwrote everything expect my **/home** directory.  I briefly tried Ubuntu 12.04, but _[I couldn't even get it to boot]("http://ubuntuforums.org/showthread.php?p=11918328#post11918328")_.

---

### Post by idoitprone on 2012-05-27
> **ladasky said:**
> Actually, I just went through a massive reinstallation process, because of some _[problems with NVidia]("http://ubuntuforums.org/showthread.php?p=11895731#post11895731")_ graphics hardware and drivers.  In that process I eventually ended up starting with a fresh installation of the OS, which overwrote everything expect my **/home** directory.  I briefly tried Ubuntu 12.04, but _[I couldn't even get it to boot]("http://ubuntuforums.org/showthread.php?p=11918328#post11918328")_.

perhaps purge your some of your profile configuration fiiles

which are file that start with dot in your home dir
or
try this ppa to see if it persist

[https://launchpad.net/~libreoffice/+archive/ppa]("https://launchpad.net/%7Elibreoffice/+archive/ppa")

---

### Post by wilee-nilee on 2012-05-27
Here is my settings, runs fairly quickly, but I never write big papers or use much, but text, I acquired these adjustments from the ubuntu geek site a while back when openoffice was the default. Turning off the java in the app helps as well.
[ATTACH]218807[/ATTACH]

---

### Post by idoitprone on 2012-05-28
> **wilee-nilee said:**
> Here is my settings, runs fairly quickly, but I never write big papers or use much, but text, I acquired these adjustments from the ubuntu geek site a while back when openoffice was the default. Turning off the java in the app helps as well.
[ATTACH]218807[/ATTACH]

you should rename the file with your settings to test out that if youe settings are causing the problems

---

### Post by ladasky on 2012-06-09
Thanks for all of your suggestions.  Unfortunately, none of them seemed to work for me.  But I've investigated my problem in a little more detail, and I have recognized one condition which sets it off consistently.

I've _[started a new thread]("http://ubuntuforums.org/showthread.php?t=2000212")_, with a more specific title.  The problem does not appear to be with LibreOffice specifically, but some interaction between LibreOffice and the fact that I am switching back and forth between two accounts.

---

