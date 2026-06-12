---
title: "LibreOffice is slow to initialize in Ubuntu 10.10"
date: 2011-01-19
forum: General Help
---

### Post by bdweiner on 2011-01-19
After I double click it's shortcut it takes LibreOffice Writer 35 seconds to come up fully. I've reinstalled it, played with the memory settings, no change. If I turn on quickstarter it works fine but as many people have noted, you have to turn quickstarter off before you shutdown otherwise the system hangs.

I would like LibreOffice to initialize within 10 seconds and be able to do a shutdown by just clicking shutdown. Anybody have any answers?

Thank you.

---

### Post by IWantFroyo on 2011-01-19
Is anything other than LibreOffice slow?

---

### Post by IWantFroyo on 2011-01-19
Is anything other than LibreOffice slow?

---

### Post by endotherm on 2011-01-19
> **bdweiner said:**
> After I double click it's shortcut it takes LibreOffice Writer 35 seconds to come up fully. I've reinstalled it, played with the memory settings, no change. If I turn on quickstarter it works fine but as many people have noted, you have to turn quickstarter off before you shutdown otherwise the system hangs.

I would like LibreOffice to initialize within 10 seconds and be able to do a shutdown by just clicking shutdown. Anybody have any answers?

Thank you.
I'm afraid that the performance you speak of is mroe the rule than the exception. my box just took about 20s to open the spreadsheet app. 

OO/LO are mostly java powered, so perhaps using the oracle java runtime may help.
[https://sites.google.com/site/easylinuxtipsproject/java](https://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by Olaf123 on 2011-01-29
I too noticed that LibreOffice that I just installed from the ppa starts dreadfully slow: 22 seconds. I found this: if I disconnect from the network it is blazingly fast (less then 3 seconds)!!. This means it is trying to access something over the Internet. I don't know what yet.

---

### Post by Spyderkid on 2011-01-29
You might want to wait till LibreOffice is on Ubuntu properly and fully supported which I think it will on the next release which is in March or May i think

For now perhaps stick which OpenOffice?

---

### Post by speedwell68 on 2011-01-29
TBH the current version of LibreOffice seems to be about as fast the last version of OpenOffice was.

---

### Post by lykeion on 2011-01-29
Just switched to LibreOffice and though I haven't timed it, I actually think it's a little bit faster to startup than OO.
I'm using LibreOffice 3.3.0 on Ubuntu Lucid with Sun Java 6.

---

### Post by Vaphell on 2011-01-29
if it's anything like OO.org you may check if there is an option to disable java environment in preferences and turn java off. It should shave few seconds off.

[http://download.openoffice.org/common/java.html](http://download.openoffice.org/common/java.html)
> Java is required for complete OpenOffice.org functionality. Java is mainly required for the HSQLDB database engine (used by our database product Base) and to make use of accessibility and assistive technologies. Furthermore some wizards rely on Java technology. If you do not require these features, then you do not need to have Java installed for running OpenOffice.org.

So what does this imply for me? Base (the database component) relies completely on Java technologies to run, but other programs (like Writer, Calc and Impress) only need Java for special functionality. We do recommend that you have a Java Runtime Environment on your system, and therefore our default installation offering includes a JRE (which adds about 15MB to the total download size).

---

### Post by TenPlus1 on 2011-01-29
LibreOffice 3.3.0 starts up in 7 seconds on my setup (2ghz, 2gb, xubu 10.10) and seems to be pretty fast...  I have Java enabled in the LO preferences and it is using java-common...

---

### Post by drewsus on 2011-01-29
LibreOffice starts very fast for me. <5 seconds.
2.6 GHz Core 2 Duo
2 GB RAM

---

### Post by koukourikos on 2011-02-06
> **bdweiner said:**
> After I double click it's shortcut it takes LibreOffice Writer 35 seconds to come up fully. I've reinstalled it, played with the memory settings, no change. If I turn on quickstarter it works fine but as many people have noted, you have to turn quickstarter off before you shutdown otherwise the system hangs.

I would like LibreOffice to initialize within 10 seconds and be able to do a shutdown by just clicking shutdown. Anybody have any answers?



> **Olaf123 said:**
> I too noticed that LibreOffice that I just installed from the ppa starts dreadfully slow: 22 seconds. I found this: if I disconnect from the network it is blazingly fast (less then 3 seconds)!!. This means it is trying to access something over the Internet. I don't know what yet.

This is a problem that came from openoffice so the solution remains the same.
[http://www.linuxquestions.org/questions/linux-software-2/double-clicking-on-open-office-files-leads-to-very-slow-opening-808048/]("http://www.linuxquestions.org/questions/linux-software-2/double-clicking-on-open-office-files-leads-to-very-slow-opening-808048/")

---

### Post by Olaf123 on 2011-02-16
Sorry,

I was away for a while. Thanks for the solution. I will try this weekend. It became really annoying to wait so long.

Olaf

---

### Post by Olaf123 on 2011-02-26
Just tried it with 3.3.1. Works like a charm =D>

---

