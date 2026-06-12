---
title: "Solution for LogMeIn using firefox 64"
date: 2010-02-14
forum: General Help
---

### Post by GOVATENT on 2010-02-14
Not sure if anyone saw this, but while googleing around I was able to confirm what I thought was causing firefox 64 to not allow me to use logmein. The problem is Adobe's great flash. (yet again another reason to dislike adobe) If you disable the flash plugin in firefox, logmein will work just fine in 64 bit java. I am using sun java btw. Just figured that I did not see anyone make this recommendation so I figured I would make a post about it.

---

### Post by megamaced on 2010-02-15
Doesn't the LogMeIn Linux Browser Plugin Preview work in 64-BIT Firefox?

[https://secure.logmein.com/US/labs/](https://secure.logmein.com/US/labs/)

---

### Post by markackerman8@gmail.com on 2010-04-09
Jalelieuia finally after 2 years with linux logmein is working with my 64-bit ubuntu!!

just goto
[http://community.logmeinrescue.com/t5/Labs-Betas-and-Tech-Previews/64-bit-Linux-Support/td-p/23423/page/2](http://community.logmeinrescue.com/t5/Labs-Betas-and-Tech-Previews/64-bit-Linux-Support/td-p/23423/page/2)

yahoooo!!!!!!

---

### Post by thomas.smekal on 2010-04-14
What was your solution? The first entry on the linked page reports a false positive. The only "solution" that could be considered working but not really a solution, is to run XP in VBox. Was that the solution you used? If not, would you care to elaborate?

---

### Post by thomas.smekal on 2010-04-14
GOVATENT's solution on the other hand works just fine. Another thumbs down for Flash

---

### Post by markackerman8@gmail.com on 2010-04-14
For the record I was able to run logmein on Ubuntu 10.04 64-bit, but it has since for some reason unknown to me stopped logging into the guest with a ssh error.  I assume it is a beta problem with Ubuntu or logmein.

I will copy and paste the 2 posts from [http://community.logmeinrescue.com/t5/Labs-Betas-and-Tech-Previews/64-bit-Linux-Support/td-p/23423;jsessionid=44FB214811E916313EE547C61B3F8622](http://community.logmeinrescue.com/t5/Labs-Betas-and-Tech-Previews/64-bit-Linux-Support/td-p/23423;jsessionid=44FB214811E916313EE547C61B3F8622), that worked for me.

2nd Post do First/
Hey Everyone.  I got this to finally work on 64bit Ubuntu 9.10 Karmic.  It's very easy.

1)  Go to Synaptic Package Manager
2)  Install the Java Libraries as indicated Below:
       a)  sun-java6-bin        Sun Java(TM) Runtime Environment (JRE) 6 (architecture dependent files)
       b)  sun-java6-jre         Sun Java(TM) Runtime Environment (JRE) 6 (architecture independent files)
       c)  sun-java6-plugin    The Java(TM) Plug-in, Java SE 6
       d)  java-common        Base of all Java packages
3) Close all FireFox Browsers before downloading and installing
4) After install, reopen your browser and all should work fine remote controlling.
 
1st Post do Second/
So, I know that this topic was considered solved with the 64-bit Java plugin suggestion.  But I'd like to add another suggestion to this thread as I just ran into this problem even with the java plugin installed (it looks like the version installed by the sun-java6-plugin package from ubuntu 9.10 is installing a 64-bit JRE/Plugin that's incompatible with the current version of logmein).  So what I did, was I downloaded the 32-bit version of this plugin and installed it by using nspluginwrapper (the same procedure typically used for flash support in 64-bit linux).  If you download the .tar.gz version, you should find an .so file.

After you download that file you have to follow the following instructions:

1) untar the file: (e.g. tar xvf ./logmein-client-1.0.387-1.tar.gz)

2) make sure you have it in a directory that you can reference and store for future use (I have mine in ~/Source/logmein-client-1.0.387-1/libractrl.so)

3) make sure you have nspluginwrapper installed (in ubuntu 9.10, if you don't, you should be able to type "sudo apt-get install nspluginwrapper" to get this to work)

4) run the following command as root or sudo: "sudo nspluginwrapper -i ~/Source/logmein-client-1.0.387-1/libractrl.so"

5) restart firefox



If anyone has success with Ubuntu Lucid 64-bit, please post any tips, thanks.  It was working for me for 1 week!  Now I have install XP in Virtualbox which I must say has been a fun alternative (Virtualbox has come a long has over the past year1)

Good Luck, and I hope this helps

---

