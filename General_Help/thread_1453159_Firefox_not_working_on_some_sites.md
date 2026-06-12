---
title: "Firefox not working on some sites"
date: 2010-04-12
forum: General Help
---

### Post by anafshalom on 2010-04-12
I'm using a 64-bit machine  Ubuntu 9.10, and Firefox 3.5.9 for Ubuntu canonical - 1.0 (Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.9) Gecko/20100402 Ubuntu/9.10 (karmic) Firefox/3.5.9)

This problem has actually been going on since I started using Ubuntu.  Firefox works for most things, but certain sites, many of them are ones you have to log into, but many other sites I log into work just fine.  The first one which did not work was bigcharts.com.  No login necessary. When I try to get a chart (stock) the page reloads with an error that I have to enter a symbol.  On some sites I put in my username and password and the page just seems to reset.

These sites work fine with forefox 3.5.9 on Windows Vista, and work with epiphany on Ububtu.

What's up?

---

### Post by Doctor Mike on 2010-04-13
> **anafshalom said:**
> I'm using a 64-bit machine  Ubuntu 9.10, and Firefox 3.5.9 for Ubuntu canonical - 1.0 (Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.9) Gecko/20100402 Ubuntu/9.10 (karmic) Firefox/3.5.9)

This problem has actually been going on since I started using Ubuntu.  Firefox works for most things, but certain sites, many of them are ones you have to log into, but many other sites I log into work just fine.  The first one which did not work was bigcharts.com.  No login necessary. When I try to get a chart (stock) the page reloads with an error that I have to enter a symbol.  On some sites I put in my username and password and the page just seems to reset.

These sites work fine with forefox 3.5.9 on Windows Vista, and work with epiphany on Ububtu.

What's up?Not sure what's up, but have you tried reinstalling Firefox?"

---

### Post by oleink on 2010-04-13
go to terminal and type "sudo apt-get update"

Then reinstall firefox.
Make sure your full system is up to date through System>admin>update manager

---

### Post by MooPi on 2010-04-13
I have just checked the site your described and the stock charts load and reload seems to work.I'm currently using Firefox 3.5.9 on 64bit. I just disabled java content and the pages went blank, so check to see if your java content is blocked in preferences.

---

### Post by oleink on 2010-04-13
Have you tried anything yet?

---

### Post by anafshalom on 2010-04-13
I update the system regularly, as I am regularly prompted to do so.  I've tried reinstalling firefox a few times ni the past, and it had no effect.

---

### Post by oleink on 2010-04-13
reinstall it via the terminal and post the results

---

### Post by anafshalom on 2010-04-14
> **MooPi said:**
> I have just checked the site your described and the stock charts load and reload seems to work.I'm currently using Firefox 3.5.9 on 64bit. I just disabled java content and the pages went blank, so check to see if your java content is blocked in preferences.

Java is enabled, and JavaScript is enabled.  I also did an update while I was at it.  

Same problem

---

### Post by lovinglinux on 2010-04-14
> **anafshalom said:**
> Java is enabled, and JavaScript is enabled.  I also did an update while I was at it.  

Same problem

Try to reinstall xulrunner.

---

### Post by anafshalom on 2010-04-16
> **lovinglinux said:**
> Try to reinstall xulrunner.

Using Synaptic I purged firefox, and reinstalled--no result. I then after purging went back and manually deleted all firefox and mozilla folders in my root system.  Then I installed it again.  

**Now everything works perfectl**y.  I wonder what the problem was.

Now I'm having a bit of a time reinstalling some of the addons I had.

---

