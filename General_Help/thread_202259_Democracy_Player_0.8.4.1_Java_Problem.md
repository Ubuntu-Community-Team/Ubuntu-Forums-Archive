---
title: "Democracy Player 0.8.4.1 Java Problem"
date: 2006-06-23
forum: General Help
---

### Post by Sabot on 2006-06-23
I justed downloaded the new democracy Player and it would not run. It kept crashing with an error on the command line that said: 

INTERNAL ERROR on Browser End: JavaPluginFactory5 init - no agent?

The solution to this problem is to install Java 5.0.  Here are the instructions from linuxtopia

How do I install the J2SE Runtime Environment (JRE) 5 (1.5) with Firefox plugin?
	
1.Make sure the multiverse repository is enabled. (See How do I add Universe and Multiverse?)

2.Go to [http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp) and click on &#8220;Download JRE 5.0 Update 7&#8221;. Ensure you do not choose the link with the NetBeans bundle.

[Note] 	
At the time of this writing J2SE is at version 5.0 Update 7. This is subject to change. If you do not see this version on Sun's website, download the newest version displayed.

3. You must first accept the licence, then click on &#8220;Linux self-extracting file&#8221; (jre-1_5_0_04-linux-i586.bin). Save this file to your hard drive.
   
4. Install the java-package package with Synaptic.

Miscellaneous - Text Based (multiverse) > java-package

5. Make the downloaded file executable. At the command line, change to the directory where you downloaded the file, and type

chmod +x  jre-1_5_0_07-linux-i586.bin

6. To install JRE, run the downloaded file. Type

fakeroot make-jpkg jre-1_5_0_07-linux-i586.bin

sudo dpkg -i sun-j2re1.5_1.5.0+update07_i386.deb

---

### Post by whatrucrazy on 2006-06-24
thanks sabot, just tried this fix and it works perfectly!
gotta wonder about this, bit of a screw up eh? the download area on the democracy player site wasn't working when i tried the ubuntu link too, so dunno what's going on.

anyway, this fix isn't too much work and the app is ok so its worth it.
ps- not sure if you need to re-install the data and the player files after this fix, i did it anyway and was all good, so if anyone is still having issues try that.

---

### Post by nevin on 2006-11-18
yes it worked!
after i changed my java, i tried to install the democracy player in the ubuntu add/remove thing, but it did not work, so i had to install it from their website
but works perfectly now.

this linux update is really coming together... i just had to do a fresh install.

---

