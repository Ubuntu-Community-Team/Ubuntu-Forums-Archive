---
title: "Cups 1.1.x on Dapper?"
date: 2006-06-10
forum: General Help
---

### Post by Devari on 2006-06-10
Hi everyone,

I've got a little problem here. I have a Samsung ML-2010 printer, which unfortunately uses a closed-source driver. The only way to use the driver is through the Linux Print Package software that Samsung ships with the printer. Unfortunately, the LPP software ONLY works with Cups 1.1.x - Dapper's upgrade to 1.2 simply won't work. The software, unfortunately, is quite old (GTK 1.2!), and doesn't seem to have much hope of being CUPS 1.2 compatible.

I use SUSE myself (used Kubuntu 5.04, but ditched it after a less-than-stellar Breezy dist-upgrade mucked things up), but I did convince my Dad to switch to Linux and suggested he choose either SUSE or Kubuntu. He decided on Kubuntu, based on the advantages and disadvantages of each that I outlined. That in itself is no problem, except that he wants to use the Samsung printer through the network! The SMB sharing from my end is absolutely no problem - the Windows 98 computer with the proper driver loves it, and, when using the open ML-4500 driver, he can print. However, the ML-4500 driver has wacked out alignment and the such, not being meant for this printer.

I'm quite sure that the problem is solely with CUPS. When I accidentally had a repository with CUPS 1.2 in my apt-rpm sources.list on SUSE, it completely broke the Linux Print Package. A quick downgrade later, and all was happy.

So, I am wondering - is it possible to install Cups 1.1.x on Dapper? Will the Breezy packages work? We did try that on another computer, back in one of the Dapper flights, and it decided to remove a whole bunch of packages! This may have been a dependency issue that has been resolved - we haven't tried that with the full release yet. Does anyone have any clue if someone will release proper cups 1.1.x packages for Dapper? Will a manual install be necessary? Anyone got any ideas? :)

I noticed that a number of people have had trouble with their Samsung printers on Dapper, and I'm almost completely sure the CUPS issue is the problem. So, if I can find the answer to my question, hopefully a number of other people can be helped as well! :D

Thanks!

(Sorry for the different spellings of cups/CUPS/Cups throughout my message. I guess I'm too lazy to be consistent! ;) )

---

### Post by fuji8bit on 2006-07-07
Sorry, this is not a post to help, I'm just commiserating. :)

I, too am working (or not working) with a Samsung ML-2010 printer on Dapper, and the CUPS 1.2 libraries are killing me.

I think the Dapper folks jumped the gun on including 1.2, since it seems to have broken a lot of working 1.1 installations.  It also seems like changing the CUPS library shouldn't invoke all the dependencies that Dapper has.  

I have found a solution to the 2010 problem for local printing (basically use a hacked PPD file), but my wife's iBook can't connect and print to it, making it (for my purposes) a deal-killer.

So if anyone knows how to get CUPS 1.1 on Dapper, please let us know.  I'm ready to go back to Debian (shudder).

---

### Post by sean on 2006-07-08
Hi,

I likewise am stuck with being unable to print using Dapper and a Samsung ML-2010.  It all worked fine with Breezy.

Sean

> **Devari said:**
> Hi everyone,

I've got a little problem here. I have a Samsung ML-2010 printer, which unfortunately uses a closed-source driver. The only way to use the driver is through the Linux Print Package software that Samsung ships with the printer. Unfortunately, the LPP software ONLY works with Cups 1.1.x - Dapper's upgrade to 1.2 simply won't work. The software, unfortunately, is quite old (GTK 1.2!), and doesn't seem to have much hope of being CUPS 1.2 compatible.

I use SUSE myself (used Kubuntu 5.04, but ditched it after a less-than-stellar Breezy dist-upgrade mucked things up), but I did convince my Dad to switch to Linux and suggested he choose either SUSE or Kubuntu. He decided on Kubuntu, based on the advantages and disadvantages of each that I outlined. That in itself is no problem, except that he wants to use the Samsung printer through the network! The SMB sharing from my end is absolutely no problem - the Windows 98 computer with the proper driver loves it, and, when using the open ML-4500 driver, he can print. However, the ML-4500 driver has wacked out alignment and the such, not being meant for this printer.

I'm quite sure that the problem is solely with CUPS. When I accidentally had a repository with CUPS 1.2 in my apt-rpm sources.list on SUSE, it completely broke the Linux Print Package. A quick downgrade later, and all was happy.

So, I am wondering - is it possible to install Cups 1.1.x on Dapper? Will the Breezy packages work? We did try that on another computer, back in one of the Dapper flights, and it decided to remove a whole bunch of packages! This may have been a dependency issue that has been resolved - we haven't tried that with the full release yet. Does anyone have any clue if someone will release proper cups 1.1.x packages for Dapper? Will a manual install be necessary? Anyone got any ideas? :)

I noticed that a number of people have had trouble with their Samsung printers on Dapper, and I'm almost completely sure the CUPS issue is the problem. So, if I can find the answer to my question, hopefully a number of other people can be helped as well! :D

Thanks!

(Sorry for the different spellings of cups/CUPS/Cups throughout my message. I guess I'm too lazy to be consistent! ;) )

---

### Post by visperas on 2006-07-11
hi, i was working whith kubuntu berzy and my Samsung 1520 perfect until the new version. With dapper i cant, in local.

_**[fuji8bit]**_
*_I have found a solution to the 2010 problem for local printing (basically use a hacked PPD file)_*

What do you mean with this??, its possible configure a samsung printer in dapper for local?. thanks

---

### Post by .t. on 2006-07-11
You could always try getting the old source, and rebuilding CUPS. However, I'd not know how to go about getting the source (Google), nor whether this would break your system. Even so, this is a solution.

---

### Post by nanotube on 2006-07-11
with apt-get, or aptitude, (or probably even synaptic), it is possible to force a specific version for a package (look in synaptic options, or try "man aptitude", for specifics). 
don't know how well it will work, but it's a possibility.

---

### Post by tagra123 on 2006-08-27
Here's a workaround until it gets fixed:


[http://ubuntuforums.org/showthread.php?p=1428724#post1428724](http://ubuntuforums.org/showthread.php?p=1428724#post1428724)

---

### Post by xbruceyx on 2006-09-06
I just recently purchased a Samsung ML-2010 laser printer. This is how I got it to work.

[http://www.ubuntuforums.org/showthread.php?t=65111&page=4&highlight=samsung+ml-2010]("http://www.ubuntuforums.org/showthread.php?t=65111&page=4&highlight=samsung+ml-2010")

---

