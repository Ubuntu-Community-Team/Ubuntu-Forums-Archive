---
title: "npviewer.bin sucks"
date: 2011-01-29
forum: General Help
---

### Post by steve7777777 on 2011-01-29
** npviewer.bin** sucks CPU usage

I noticed on the panel that CPU temps were 12 C higher than normal. I then found that Processor 3 (I have an AMD quad processor) was at 90% when the system was idle. After killing the npviewer.bin process cpu usage returned to normal. This did not cause crash, freeze-ups or other problems.

This was discussed in 2008:
[http://ubuntuforums.org/showthread.php?t=647961&highlight=npviewer](http://ubuntuforums.org/showthread.php?t=647961&highlight=npviewer)

and Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/438086](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/438086)

I'm running Ubuntu 10.10 64bit.

Anyone else have problems with this bug? Not a huge deal but a little annoying.

---

### Post by RJ12 on 2011-01-29
That is the process for the Adobe Flash Plugin. Do you have any browsers running and using flash content?

---

### Post by Wolf-Ekkehard on 2011-05-16
Same issue here - npviewer.bin pegs one of my cores even long AFTER my browser (Chrome) has been showing the flash movie.  The darn thing appears not to be terminated properly after its job is done.  The problem is easy to spot: fan speed increases audibly as the chip heats up.  Killing npviewer.bin fixes that - but not the code that doesn't terminate npviewer.bin properly, of course.  So I have to do it after every time I use the flash player.

Do other browsers show the same problem, i.e. is it a browser problem or an npviewer.bin problem?

Running Kubuntu 10.10 64 bit.

---

### Post by gefalu2008 on 2011-10-05
I have a similar problem with npviewer. Using Firefox 7.01, Ubuntu 11.04 (64 bit), Intel Core2 Quad.

---

### Post by logan85 on 2011-10-06
I had the same problem, and installing flashblock solved the problem.

---

### Post by Vaphell on 2011-10-06
uninstall 32bit version of flash and go with native 64bit which doesn't have to use npviewer (it is related to wrapper that allows 32bit flash to run on 64bit system).
Flash-aid addon for firefox can do that for you or you can go to adobe website to download and install manually.

---

### Post by carlosOvni on 2012-01-28
Yeah, same thing here. I was watching a video and when I tried to stop it, it didn't and freezed firefox completely ](*,), only with a *kill process*, the browser returned to normal.  Maybe this is a substitution of *plugincontainer.exe* in Windows?
I'm also using Ubuntu 10.10 64bit.

---

### Post by Vaphell on 2012-01-28
the question is: do you use 32 or 64bit plugin?

---

### Post by carlosOvni on 2012-01-30
I *was* using 32bit plugin, uninstalled it, installed 64bit and now a new name for the "same" plugin named *plugin-container* is running, just like in window$, difference is that is smoother.

---

### Post by jbird21 on 2012-02-07
how do I check the version & change  it?
thanks in advance

currently using ubuntu 11.04 64bit

---

### Post by Vaphell on 2012-02-07
try this firefox addon
[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)
it will ask which version you want, in case of 64bit it will create a script to uninstall old/conflicting packages and install version from adobe.com instead.

---

### Post by jbird21 on 2012-02-07
thanks, i'll try that, unfortunately I am unable to download that at the moment, (some connection error at Mozilla) will try again later

---

### Post by jbird21 on 2012-02-08
I have been unable to install that addon, is there another way to check which version of flash i'm using? 

tia, jay

---

