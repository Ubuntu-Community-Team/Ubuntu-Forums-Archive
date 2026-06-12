---
title: "AverMedia TV Hybrid + FM PCI card does not work"
date: 2006-04-27
forum: General Help
---

### Post by aio on 2006-04-27
Hello.
First of all excuse my bad english.
I´ve got an AverMedia TV Hybrid + FM PCI card since three mounh ago or so. I was waiting for drivers for Linux cause I emailed AverMedia about my problem with this card running under Ubuntu amd they told me I had to wait a couple of mounth to get the drivers. And finally they did the work they promissed to me and I could download and install drivers for Linux from AverMedia webpage. There are three drivers for Linux and I  really don´t know which one to install. I found them here.

[http://www.avermedia.com/cgi-bin/support_driverbympdpro.asp?category=TV%20Card&category2=Hybrid&proname=AVerTV%20Hybrid%20FM%20PCI&modelno=A16AR](http://www.avermedia.com/cgi-bin/support_driverbympdpro.asp?category=TV%20Card&category2=Hybrid&proname=AVerTV%20Hybrid%20FM%20PCI&modelno=A16AR)

I am runnig Ubuntu Linux and it goes quite good. The only trouble is this one I report you. Th eproblem with HPScanJet5P is solved and iy runs too with sane :D 
¿Could you please help me to watch tv?

Thanks a lot.

---

### Post by aio on 2006-04-27
Well, I have proceeded to install one of the drivers for AverMediaTV card and then installation instructions tell me that I have to install xine in order to watch tv. So I installed Xine, but then instructins go on saying this:

[B]XINE needs a channel configuration to properly tune to TV channels. 
 The following example shows you how to generate such channel config.
 Take Taiwan DVB-T services for example, do the following after driver is
 loaded:

 $ ./dvbscan dvb-t/tw-Taipei | tee channels.conf

 dvb-t/tw-Taipei is a initial data file that describes the transponder
 parameters for DVB-T services in Taiwan. Use appropriate file under dvb-t
 directory according to your country/area. If no appropriate file can be
 found for your country/area or you believe the file is incorrect, please
 refer to [http://www.linuxtv.org/](http://www.linuxtv.org/) for help. The tool "dvbscan" and files
 under dvb-t/ are provided by Linux-DVB community and therefore AVerMedia
 have no way of supporting these utilities.

 This step, if successful, will generate the file "channels.conf". Copy this
 file to xine config directory:

 $ cp channels.conf ~/.xine/.[/B]



So I don´t know where to write this:
 $ ./dvbscan dvb-t/tw-Taipei | tee channels.conf


Can anyone help me?
Of course, I can´t watch tv.:???: 
Thanks a lot.

---

### Post by kombipom on 2006-06-06
Hi,

Whenever anybody says type they mean type into the terminal (Applications->Accessories->Terminal).  The $ is the prompt the terminal shows when it is ready for you to type in a command.  The rest of the line is the command itself (actually two commands).  

Some questions:
1. Are you in Taipei?  
2. If you type "ls" (without quotes) at the prompt does the returned text include "dvbscan"? 
3. Does any of this make sense?
4. Which driver did you install as none of them seem to be Ubuntu (or even Debian)?

---

