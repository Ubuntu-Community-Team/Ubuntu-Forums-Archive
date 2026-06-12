---
title: "How do I get the sound to work on this page....."
date: 2010-10-27
forum: General Help
---

### Post by donut123 on 2010-10-27
This web page....the Java works fine...the sound does not work.
I am using Ubuntu !0.10...it worked in 10.04 but not now.

[http://njagyouth.org/](http://njagyouth.org/)

---

### Post by irv on 2010-10-27
> **donut123 said:**
> This web page....the Java works fine...the sound does not work.
I am using Ubuntu !0.10...it worked in 10.04 but not now.

[http://njagyouth.org/](http://njagyouth.org/)

It must be the website I don't have sound either.

---

### Post by donut123 on 2010-10-27
> **irv said:**
> It must be the website I don't have sound either.
Hello Irv...no it is not the website becuase the sound works in Windows XP...so it could not be the site.
It usualy works.
I tried it with the Alpha Ultimate Edition...a couple of months ago...it did not work in there either.
And this is !0.10...a similar platform. Almost the same only this is the Final ...so it should work.
See if you can find an answer.
Thank you

---

### Post by irv on 2010-10-27
There is a problem with the design of the webpage, here is a sniped of the code. There are using a java scrip and the design might not work in Linux. I don't believe it is a problem with 10.10 or any linux based OS but the code.
```
<param name=[COLOR="Red"]"para_sound"[/COLOR]	value="2">

      <!--<![endif]-->
        <!-- MSIE (Microsoft Internet Explorer) will use inner object -->
        <object classid="clsid:8AD9C840-044E-11D1-B3E9-00805F499D93"
                codebase="http://java.sun.com/update/1.5.0/jinstall-1_5_0-windows-i586.cab"
                height="266" width="494" >
          <param name="code" value="jhanabi" />
          <param name="para_bits" 	value="10000">
		  <param name="para_max"  	value="300">
		  <param name="para_blendx"	value="90">
		  <param name="para_blendy"	value="50">
<param name=[COLOR="Red"]"para_sound"[/COLOR]	value="2">

          <strong>
            This browser does not have a Java Plug-in.
            <br />
            <a href="http://java.sun.com/products/plugin/downloads/index.html">
              Get the latest Java Plug-in here.
            </a>
          </strong>
        </object>
      <!--[if !IE]> close outer object -->
      </object>

      <!--<![endif]-->

</td>

```

---

### Post by donut123 on 2010-10-28
> **irv said:**
> There is a problem with the design of the webpage, here is a sniped of the code. There are using a java scrip and the design might not work in Linux. I don't believe it is a problem with 10.10 or any linux based OS but the code.
```
<param name=[COLOR=Red]"para_sound"[/COLOR]    value="2">

      <!--<![endif]-->
        <!-- MSIE (Microsoft Internet Explorer) will use inner object -->
        <object classid="clsid:8AD9C840-044E-11D1-B3E9-00805F499D93"
                codebase="http://java.sun.com/update/1.5.0/jinstall-1_5_0-windows-i586.cab"
                height="266" width="494" >
          <param name="code" value="jhanabi" />
          <param name="para_bits"     value="10000">
          <param name="para_max"      value="300">
          <param name="para_blendx"    value="90">
          <param name="para_blendy"    value="50">
<param name=[COLOR=Red]"para_sound"[/COLOR]    value="2">

          <strong>
            This browser does not have a Java Plug-in.
            <br />
            <a href="http://java.sun.com/products/plugin/downloads/index.html">
              Get the latest Java Plug-in here.
            </a>
          </strong>
        </object>
      <!--[if !IE]> close outer object -->
      </object>

      <!--<![endif]-->

</td>

```


Ok so should we just turn our head because Linux does not work properly?
Or try to find an answer?
I mean if it were connected to the e mail client...how fast would it be fixed?
The code means nothing to me...what if it said doo doo and ca ca?
I not trying to be rude Im only saying ...I guess it will never be solved on why 
the sound for Linux does not work on Java script pages.

---

### Post by irv on 2010-10-28
> **donut123 said:**
> Ok so should we just turn our head because Linux does not work properly?
Or try to find an answer?
I mean if it were connected to the e mail client...how fast would it be fixed?
The code means nothing to me...what if it said doo doo and ca ca?
I not trying to be rude Im only saying ...I guess it will never be solved on why 
the sound for Linux does not work on Java script pages.

It is not the fault of Linux, but the one who designed the webpage. Java scripts work with Linux if it is coded right. The only one who can fix the problem is the programmer who made the page. If he wants it to work with any Linux OS then he better make sure it work on all OS's. I design web pages and I make sure they work on many OS's before I publish them and I use Jave scripts.

---

### Post by donut123 on 2010-10-28
> **irv said:**
> It is not the fault of Linux, but the one who designed the webpage. Java scripts work with Linux if it is coded right. The only one who can fix the problem is the programmer who made the page. If he wants it to work with any Linux OS then he better make sure it work on all OS's. I design web pages and I make sure they work on many OS's before I publish them and I use Jave scripts.
Ok look...here is another site...the sound should work...right?
[http://www.maylin.net/Fireworks.html](http://www.maylin.net/Fireworks.html)
I had the sound for one blast...then it stopped...what do you make of it?
And here............
[http://www.95isalive.com/java/fireworks.htm](http://www.95isalive.com/java/fireworks.htm)
And it turns the sound completely off...and takes a while to return.

---

### Post by irv on 2010-10-28
> **donut123 said:**
> Ok look...here is another site...the sound should work...right?
[http://www.maylin.net/Fireworks.html](http://www.maylin.net/Fireworks.html)
I had the sound for one blast...then it stopped...what do you make of it?
And here............
[http://www.95isalive.com/java/fireworks.htm](http://www.95isalive.com/java/fireworks.htm)
And it turns the sound completely off...and takes a while to return.

I tried both links in Ubuntu and Windows 7. I could get no sound on either link in Ubuntu, but it did work in Windows 7. I am starting to rethink this problem. It might be in the Linux Java plugin. To be honest, I am not really sure if the problem is in the code. I looked at the code in the other two links and they look like the sound should work. Maybe a new thread should be started to see if others are having problems with sound on other Java sites. It would be nice to know if anyone has a Java site with sound working now. I may look into this further when I have more time.

---

### Post by donut123 on 2010-10-28
> **irv said:**
> I tried both links in Ubuntu and Windows 7. I could get no sound on either link in Ubuntu, but it did work in Windows 7. I am starting to rethink this problem. It might be in the Linux Java plugin. To be honest, I am not really sure if the problem is in the code. I looked at the code in the other two links and they look like the sound should work. Maybe a new thread should be started to see if others are having problems with sound on other Java sites. It would be nice to know if anyone has a Java site with sound working now. I may look into this further when I have more time.
OK ..great! Thats what I was talking about.
I dont know how to go about getting Linux...or someone to look into it.
I am mostly a user.
I use Ultimate Edition...its 2.8..however it runs off of 10.10 Ubuntu base.
i had the sound for these sites working in 2.7...however there was a problem with any media player being on...the sound would shut down..in the Java...only worked alone...no media player on.
The guys on Ultimate Edtion forum dont know either! :(
Lets try to work on it...:P
I will be here until Sunday...then I will be out of town...I dont have a laptop..but i think I can use some ones. 
I will be around...
Thanks Irv .

---

### Post by irv on 2010-10-28
> **donut123 said:**
> OK ..great! Thats what I was talking about.
I dont know how to go about getting Linux...or someone to look into it.
I am mostly a user.
I use Ultimate Edition...its 2.8..however it runs off of 10.10 Ubuntu base.
i had the sound for these sites working in 2.7...however there was a problem with any media player being on...the sound would shut down..in the Java...only worked alone...no media player on.
The guys on Ultimate Edtion forum dont know either! :(
Lets try to work on it...:P
I will be here until Sunday...then I will be out of town...I dont have a laptop..but i think I can use some ones. 
I will be around...
Thanks Irv .
Your welcome, and I seem to have the same problem. Finding time to dig deeper into this problem. I was on the road today, and did get some time on the Internet in a coffee shop, but life sometimes gets to busy.
Later

---

### Post by irv on 2010-10-29
We are not the only Linux users having problem with sound in Java Applets. Arch Linux users are also having problem. Found this post on there forum.
[https://bbs.archlinux.org/viewtopic.php?id=105733]("https://bbs.archlinux.org/viewtopic.php?id=105733")
And this problem excised back in 2007, [http://ubuntuforums.org/archive/index.php/t-492285.html ]("http://ubuntuforums.org/archive/index.php/t-492285.html")
Also there are posts on the firefox forum. (2006)
[http://forums.mozillazine.org/viewtopic.php?t=386579&highlight=runescape+sound]("http://forums.mozillazine.org/viewtopic.php?t=386579&highlight=runescape+sound")

I guess I would have to say this problem is widespread and over time. I don't think the answer to this problem is going to be easy.

---

### Post by donut123 on 2010-10-29
> **irv said:**
> we are not the only linux users having problem with sound in java applets. Arch linux users are also having problem. Found this post on there forum.
[https://bbs.archlinux.org/viewtopic.php?id=105733](https://bbs.archlinux.org/viewtopic.php?id=105733)
and this problem excised back in 2007, [http://ubuntuforums.org/archive/index.php/t-492285.html ]("http://ubuntuforums.org/archive/index.php/t-492285.html")
also there are posts on the firefox forum. (2006)
[http://forums.mozillazine.org/viewtopic.php?t=386579&highlight=runescape+sound](http://forums.mozillazine.org/viewtopic.php?t=386579&highlight=runescape+sound)

i guess i would have to say this problem is widespread and over time. I don't think the answer to this problem is going to be easy.
[size=6]wow ![/size]

---

### Post by irv on 2010-10-29
After doing more searching I am seeing things like:
> Some Java sites/games like Runescape use a IE only settings(?) resulting in no sound in Firefox. 
I also check my Java verison I am running just for the record. Here is what I have:
I typed in a terminal:
```
java -fullversion
```
and saw:
> java full version "1.6.0_20-b20"

I then typed:
```
jave -version
```
and saw:
> OpenJDK Runtime Environment (IcedTea6 1.9.1) (6b20-1.9.1-1ubuntu3)
OpenJDK Server VM (build 17.0-b16, mixed mode)

I am running IcedTea Java Plugin
[ATTACH]173880[/ATTACH]
This is my start in finding out why sound is not working in Java scripts.
I do have a question if someone has sound in firefox and java scripts working. If you do could you post your setting? and what you are using?

---

### Post by donut123 on 2010-10-29
> **irv said:**
> After doing more searching I am seeing things like:

I also check my Java verison I am running just for the record. Here is what I have:
I typed in a terminal:
```
java -fullversion
```and saw:

I then typed:
```
jave -version
```and saw:

I am running IcedTea Java Plugin
[ATTACH]173880[/ATTACH]
This is my start in finding out why sound is not working in Java scripts.
I do have a question if someone has sound in firefox and java scripts working. If you do could you post your setting? and what you are using?
Nice work Irv....I still havent gotten an answer for it on Ultimate Edition Australia. 
They usually are great with fixes. Icedtea does not work well with me.
I always get my plugin from Ultimatix. It usually works good. Last time the sound worked but noet with any media player on.
I try to find some clues also.
Thanks Irv...nice work !

---

### Post by donut123 on 2010-10-29
Ok Irv...I tried Java this and Java that...and I tried alot of things...and still nmo sound.
I dont know !:sad:

---

### Post by donut123 on 2010-10-30
Hi Irv...I found this out
Here is something..it sayss we have the wrong Java..it may be the root of the problem.

[http://www.java.com/en/download/installed.jsp?jre_version=1.6.0_15&vendor=Sun+Microsystems+Inc.&os=Linux&os_version=2.6.35-22-generic](http://www.java.com/en/download/installed.jsp?jre_version=1.6.0_15&vendor=Sun+Microsystems+Inc.&os=Linux&os_version=2.6.35-22-generic)

---

### Post by irv on 2010-10-30
> **donut123 said:**
> Hi Irv...I found this out
Here is something..it sayss we have the wrong Java..it may be the root of the problem.

[http://www.java.com/en/download/installed.jsp?jre_version=1.6.0_15&vendor=Sun+Microsystems+Inc.&os=Linux&os_version=2.6.35-22-generic](http://www.java.com/en/download/installed.jsp?jre_version=1.6.0_15&vendor=Sun+Microsystems+Inc.&os=Linux&os_version=2.6.35-22-generic)

I've downloaded this version, and it didn't work either, and I got some other errors with it so I went back to IcedTea which is a temporary fork of OpenJDK. 
[ATTACH]173983[/ATTACH]

---

### Post by irv on 2010-10-30
When I made the last post, I notices that Icetea Java plugin was not installed, so I installed it. When I tried the fireworks applet it keep freezing up. So I uninstall Icetea and it started to work again. I went and tried the other links you posted and they worked also. But with no sound. I shut down firefox and started it up and when to the links again. I had sound for 4 or 5 fireworks and then it quick working again. So I tried restarting firefox again and this time I could only get sound on two of the fireworks and it quick again. There is something very flaky with this. 

I have the "OpenJDK Java 6 Runtime" installed because I need other applacations. Here is what it tell me.

> Full Java runtime environment - needed for executing Java GUI and Webstart programs. Using Hotspot JIT. The packages are built using the IcedTea build support and patches from the IcedTea project.

I believe I need to have IcedTea install also, but if I install it, I have problem with the applets you posted.

I feel I am digging a hole and it is getting hard to get out of.
I think I am going to leave it alone for awhile.

---

### Post by rogprov on 2010-10-30
For a long while I've had no luck getting the Java sound in Firefox and 10.04 and 10.10 to work here:
[http://websdr.ewi.utwente.nl:8901/](http://websdr.ewi.utwente.nl:8901/)
Works fine in XP :(

---

### Post by Rodney9 on 2010-10-30
When I try the first site - [http://njagyouth.org/](http://njagyouth.org/) - it logs me out.

---

### Post by donut123 on 2010-10-30
Hello Irv...and guests.
Irv...the Java is worse with Icedtea..it wont work at all.
I always install the plugin from Ultimatix...its just this time the sound
wont work.
The sound was working in 2.7 Ultimate Edtion..wich 
is the Ubuntu 10.04 base.
I have 2.8 now...it is the 10.10 Ubuntu base.
So something is wrong with the Ubuntu base.

---

### Post by irv on 2010-10-30
> **rogprov said:**
> For a long while I've had no luck getting the Java sound in Firefox and 10.04 and 10.10 to work here:
[http://websdr.ewi.utwente.nl:8901/](http://websdr.ewi.utwente.nl:8901/)
Works fine in XP :(

I tried the link and I have sound on this site.

---

### Post by irv on 2010-10-30
Ok, Here is the plugin I am using now.
[ATTACH]174004[/ATTACH]

---

### Post by donut123 on 2010-10-30
OK..so how does ones get it?
I havent been able to see that one

---

### Post by irv on 2010-10-30
> **donut123 said:**
> OK..so how does ones get it?
I havent been able to see that one

I believe this is it:
Removed URL.
Edit: don't use this one it is outdated.

---

### Post by donut123 on 2010-10-30
Hey Irv...it wont install on mine.

---

### Post by rogprov on 2010-10-31
> **irv said:**
> I tried the link and I have sound on this site.

... could you please give a source for the Java plug-in you have installed? 

Thanks.

Edit

Okay I've checked and have the same version running but no sound here - the mystery continues .... :(

---

### Post by Omnomnom on 2010-10-31
Well for me it crashed firefox. I will try it with Chromium too.

---

### Post by Omnomnom on 2010-10-31
I heard a slight sound in chromium, just for a tenth of a second, but that's it.

---

### Post by donut123 on 2010-10-31
Yes ..here is what I am using...Screenshot...
Its the latest Java

---

### Post by irv on 2010-10-31
> **donut123 said:**
> Yes ..here is what I am using...Screenshot...
Its the latest Java
I have the same, so far it is the only one I can get working except with no sound on the links you posted. I can get sound on other sites like the last one that was posted. [URL="http://websdr.ewi.utwente.nl:8901/"]http://websdr.ewi.utwente.nl:8901/
[/URL]

---

### Post by jebradley on 2010-11-03
> **rogprov said:**
> For a long while I've had no luck getting the Java sound in Firefox and 10.04 and 10.10 to work here:
[http://websdr.ewi.utwente.nl:8901/](http://websdr.ewi.utwente.nl:8901/)
Works fine in XP :(
I'm having problems with the same page.

But, I know it will work on Ubuntu 10.10, because I have it working on my laptop. I just can't figure out what's the problem on my desktop. Other sound works fine. I'm beating my head against the wall.

---

### Post by jebradley on 2010-11-03
I should have posted a bit more. The page, [http://websdr.ewi.utwente.nl:8901](http://websdr.ewi.utwente.nl:8901) initally would crash my firefox browser. I played around with the different versions of java, and got it to load without crashing the browser, but the little window reported a java applet with a different version that the java that I was running. I installed the sun-java-6-plugin and deleted the icedtea plugin, and sound worked after that (on my laptop). Unfortunately the results were not repeatable on my desktop.

---

### Post by irv on 2010-11-03
> **jebradley said:**
> I should have posted a bit more. The page, [http://websdr.ewi.utwente.nl:8901](http://websdr.ewi.utwente.nl:8901) initally would crash my firefox browser. I played around with the different versions of java, and got it to load without crashing the browser, but the little window reported a java applet with a different version that the java that I was running. I installed the sun-java-6-plugin and deleted the icedtea plugin, and sound worked after that (on my laptop). Unfortunately the results were not repeatable on my desktop.

This would mean there is a variable here that needs to be known. If it works on one machine and not another then the question is: Is it hardware or software or a combination of both?

---

### Post by rogprov on 2010-11-05
Unfortunately the University of Twente radio site has closed temporarily so further testing is on hold ....  :(

---

### Post by bfowles on 2011-02-13
I am running Ubuntu 10.10 on an ACER netbook and had the same issue where all the WEBSDR sites could be seen but not heard. After routing around it was suggested to install the SUN JAVA JRE which I did but still no sound, I then found ...

[http://www.dh1tw.de/websdr-java-ubuntu-linux-how-to-make-it-work](http://www.dh1tw.de/websdr-java-ubuntu-linux-how-to-make-it-work)

.. and ran the following two commands.

sudo apt-get purge openjdk-6-jdk
sudo apt-get purge icedtea6-plugin

.poof! now all sounds are working on several of the sites I have tried, hope this helps someone out there.

73's

---

