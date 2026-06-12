---
title: "Firefox, Ubuntu 10.04, GoToMyPC"
date: 2010-06-16
forum: General Help
---

### Post by rashby3 on 2010-06-16
Does anyone reading this use GoToMyPC to access a PC from Ubuntu?

GoToMyPC is installed on my work PC.

For two years I have accessed my work PC from my Ubuntu Linux laptop using the GoToMyPC Universal Viewer in FireFox.

I recently upgraded to Ubuntu 10.04. The next time I tried to use GoToMyPC it told me I needed a Java-enabled web browser.

I found a web page at linuxtree.blogspot.com on "How to Enable Firefox Java plugin on Ubuntu 10.04."

It said to do the following: 

step 1 : Go to terminal and type

sudo apt-get install openjdk-6-jre icedtea6-plugin

step 2: Restart the browser

I did the above, and also went to a Java tester page at java.com that told me "Your Java is working."

The next time I started the GoToMyPC universal viewer in FireFoxm it seemed to start okay, asked me for my PC's password as usual and seemed to accept it, but when it got to the point of displaying my PC's desktop, it just displayed a black screen. I tried a few more times and got the same results.

Does anyone have any suggestions?

I have upgraded Ubuntu a few times in the past without disabling GoToMyPC.

Is this icedtea plugin something new with 10.04? Is there an alternative java plugin that might work better?

I have not had to specifically install a java plugin after my previous upgrades, as far as I remember.

The linuxtree page said "sun-java6 packages are no longer included in the default repositories." So, what I am wondering is this: Is the icedtea plugin an alternative to a sun-java6 plugin, or is it the sun-java6 plugin?

Thanks very much.

---

### Post by wojox on 2010-06-16
Beats me but here's how to install [Sun's Java]("http://wojox.homelinux.org/?p=78")

---

### Post by rashby3 on 2010-06-17
Thanks very much, wojox.

That worked (after I also removed the icedtea6 plugin).

---

### Post by dejal on 2010-06-23
Thank wojox, I had the same problem (I also used icedtea6).   When gotomypc's window came up I was getting the left half of my work computer.

---

### Post by tripower on 2010-07-03
Well I am running 10.04 (64bit) and I can't get the universal viewer going at all.

---

### Post by tripower on 2010-07-05
bump

---

### Post by kiwiboyus on 2010-07-06
> **tripower said:**
> Well I am running 10.04 (64bit) and I can't get the universal viewer going at all.

Hi there, 

I work for Citrix Online and the Universal Viewer will work in Firefox on Ubuntu 64bit if you follow the steps listed above and install the openjdk-6-jre and icedtea6-plugin through the Software Center. After installing Java support and re-launching Firefox you can click connect for your Host, you will see a new page mentioning the Universal Viewer and may need to tell Firefox to allow pop ups from gotomypc.com If it fails to load the first time (usually because of the pop-up blocker), just reload the page and try again.

Thanks,

---

### Post by tripower on 2010-07-08
> **kiwiboyus said:**
> Hi there, 

I work for Citrix Online and the Universal Viewer will work in Firefox on Ubuntu 64bit if you follow the steps listed above and install the openjdk-6-jre and icedtea6-plugin through the Software Center. After installing Java support and re-launching Firefox you can click connect for your Host, you will see a new page mentioning the Universal Viewer and may need to tell Firefox to allow pop ups from gotomypc.com If it fails to load the first time (usually because of the pop-up blocker), just reload the page and try again.

Thanks,


I tried several times and it doesn't work.

---

### Post by tripower on 2010-07-15
Bump.

---

### Post by kiwiboyus on 2010-07-16
Hi,

Not sure why it isn't working for you, you could try removing java and reinstalling it, also make sure java is enabled in FF including in the Add Ons area. Or, if you're not opposed to running Wine on you system follow this guide and use the Windows native viewer: [http://glenndcitrix.wordpress.com/2010/07/07/gotomypc-and-linux/](http://glenndcitrix.wordpress.com/2010/07/07/gotomypc-and-linux/)

---

### Post by jrusidoff on 2010-08-27
Well, I know this says "solved" but it is still not solved for me.  I have done everything here, installed Sun Java, ditched icedtea, ditched Sun Java, re-installed the'native' java for Ubuntu.  I am running 10.04 LTS.  I had it working at home earlier, but after some updates it no longer works!  Is there anything I am missing?
Thanks!

---

