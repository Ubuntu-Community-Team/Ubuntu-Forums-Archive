---
title: "POGO.com and Ubuntu 10.04 Lucid Lynx"
date: 2010-05-02
forum: General Help
---

### Post by OldGoat58 on 2010-05-02
I'm certain someone else has figured this out, so forgive me if this old news.

I play games on POGO.com.  After updating from Ubuntu 9.10, Karmic Koala, to Ubuntu 10.04LTS, Lucid Lynx, my games at POGO wouldn't load.  They are all JAVA based.  I used the Ubuntu Software Sources to make sure that the JAVA JRE was in fact installed.  Still the games wouldn't load.

In the "General Help" section of Ubuntu Forums there was a sticky of "Known Issues" in the Lucid Lynx release.  I followed a link there to Launchpad and read some of the posts.  One person mentioned they fixed their problem by disabling the "Icedtea JAVA plugin" in Firefox.  I couldn't figure out how to disable it but I used the Synaptic Package manager to remove it.  

Now when I go to POGO my games load and all is as it was in Karmic.  My question is, did I sacrifice anything by removing the Icedtea plugin?

As always any help will be greatly appreciated.

Thanks!
Mike
Fairless Hills, PA
HP Pavilion dv9810US
AMD Turion 64 X2
3gb DDR2 SODIMM 200 pin Memory
Ubuntu 10.04LTS Lucid Lynx

---

### Post by raul999 on 2010-05-03
Hi,
I have the same issue, can you tell me how exactly you made that it works?
I tried in Firefox Adds-On then Icetea NPR Web-Browser Plugin disable---but that doesn't work for me.

Thx

---

### Post by OldGoat58 on 2010-05-03
I used the Synaptic Package manager to remove the Icedtea.  

Thanks!
Mike
Fairless Hills, PA
HP Pavilion dv9810US
AMD Turion 64 X2
3gb DDR2 SODIMM 200 pin Memory
Ubuntu 10.04LTS Lucid Lynx

---

### Post by raul999 on 2010-05-04
Hallo,
Thank you for your help...this works also for me.

---

### Post by BCtom on 2010-05-05
Hi OldGoat58, me and my friends are having the same problem, we did what you said, removed the Java Icedtea, but the Java Applets load when we tried to play a game, then it stopped, and now it says, "your Java is not installed."

So, two questions:

1. I noticed that there is a second Java-icedtea called, icedtes-6-jre-cacao too along with the icedtea6-plugin, did you un-install them both, or just the one?

2. Could you list all of the java files you are using currently, maybe we could try and mirror what you have so we can get Pogo working for us?

Thanks so much OldGoat58.

Tom

---

### Post by OldGoat58 on 2010-05-05
> **BCtom said:**
> Hi OldGoat58, me and my friends are having the same problem, we did what you said, removed the Java Icedtea, but the Java Applets load when we tried to play a game, then it stopped, and now it says, "your Java is not installed."

So, two questions:

1. I noticed that there is a second Java-icedtea called, icedtes-6-jre-cacao too along with the icedtea6-plugin, did you un-install them both, or just the one?

2. Could you list all of the java files you are using currently, maybe we could try and mirror what you have so we can get Pogo working for us?

Thanks so much OldGoat58.

Tom


Tom,

I'd like to tell you exactly what JAVA files I'm running, but I'm not sure how to find out.  I'm actually fairly computer illiterate, but what I can tell you is, I used the Synaptic Package Manager and removed the "icedtea6-plugin".  I didn't see the 
"icedtea-6-jre-cacao" until you just mentioned it and it is installed on my computer.

I then went to the "Ubuntu Software Center" and searched for "Sun".  That will bring up the "Sun JAVA 6.0 Plugin" and I installed that.  I also searched for "java" and installed a bunch it looks like.  I've battled POGO, JAVA, and Ubuntu since changing to Ubuntu last November.

I attached a screen shot of what JAVA is installed.  I hope it helps you.  

Mike
Fairless Hills, PA ](*,)

---

### Post by BCtom on 2010-05-05
Hi Mike,

Great news I got it going, but I followed this link instead. And I think I can answer your FireFox mystery you were talking about too. 

Have a look at these instructions from Java:

[http://sites.google.com/site/easylinuxtipsproject/java#TOC-Install-JRE-32-bit-](http://sites.google.com/site/easylinuxtipsproject/java#TOC-Install-JRE-32-bit-)

If you type in: > about:plugins in the URL area of your FireFox browser, you should only see, Java 1.6 ..... instead of Icedtea at the very top of that page being displayed. This lists all the plugins being used for FireFox on your system.

I don't think you are loosing anything by giving up icedtea becuase it appears to be only used for the web, and Java6 does that anyway. If you don't see any Java in your FireFox, then you need to at least get the plugins installed, and for that you need to read the above link from the Java/Linux web site.


Cheers, 

Tom

---

### Post by accodata on 2010-05-06
Hi All

Thank you to the people with patience and understanding of what we needed to fix, to be able to play at Pogo.com

It has taken 2 days of frustration, but 30 mins of following this help, I can't thank you enough!!

have a great week!!

Accodata

---

### Post by blazewon22 on 2010-05-30
This thread worked for me as well.  Loving Ubuntu more each day!

---

### Post by earthpigg on 2010-07-04
removed icedtea worked for my mom's setup, thanks.

she will be the one stomping you in canasta with 'geo' in her handle.

---

### Post by Charley Horse on 2010-07-27
No one mentions needing WINE to play Pogo in Ubuntu 10.4.
Is that because WINE is not needed? 
The reason I ask is that checking requirements Pogo on Pogo's site,
only Windows and Macs are mentioned. No mention of Linux.

---

### Post by BCtom on 2010-07-28
> **Charley Horse said:**
> No one mentions needing WINE to play Pogo in Ubuntu 10.4.
Is that because WINE is not needed? 
The reason I ask is that checking requirements Pogo on Pogo's site,
only Windows and Macs are mentioned. No mention of Linux.

No, everything is done with your browser: lots of Flash, and the games are running on a program called Java. Just follow the instructions mentioned earlier on this thread. Install the right Java, get your flash running on FireFox, and you should be set. 

The only reason why you do not see any support for LINUX is that the vast majority of users use Mac and Window$, and they are proprietary operating systems. Pogo does know Ubuntu exists, but they say LINUX/Ubuntu is too small of a group to worry about offering support. 

There is lots of help here, but you need to look at all the threads on the forum, and follow the instructions. It is a bit of a pain at first, but once it's going, Pogo plays just like it does on Window$ and Macs--some say better.

Cheers

---

### Post by Charley Horse on 2010-07-31
BCtom, Thanks for the response. 
I am actually attempting to assist another user in another forum who is now 
playing Pogo on Ubuntu after removing Icedtea. 
Another small problem has popped up. 
QUOTE:  ...when I'm on pogo the slot machine bells go on long  after the play is over. They never stop till I close the window. I've  searched high and low....

Do you or anyone have a suggestion to fix that? Thanks

---

### Post by earthpigg on 2010-08-22
my mom just finished having similar inconsistent behavior with pogo & java stuff. the games would start, but be partially broken.

somehow, icedtea had become installed and java was no longer installed. i don't know if this was due to an update, or my mother clicking around. but that's what you ought to check for. in synaptic, not software center.

---

