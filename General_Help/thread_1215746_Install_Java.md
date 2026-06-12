---
title: "Install Java"
date: 2009-07-17
forum: General Help
---

### Post by oldtraveler on 2009-07-17
[color=red]SOLVED after a reboot after folloiwng instructions described in #3 and #4 below. [/color]**[COLOR="DarkOrchid"]See post # 14 on next page for the corect solution for Ubuntu 10.04[/COLOR]**.To play Pogo games I need to install Java.  I have downloaded /home/USER/Desktop/jre-6u14-linux-i586.bin, but the only instructions I see require root access which I understand is blocked by Ubuntu.  How can I get java installed?

---

### Post by XCan on 2009-07-17
You could run the file you downloaded by first changing it to executable
```
chmod +x /home/USER/Desktop/jre-6u14-linux-i586.bin
```
and then running it
```
/home/USER/Desktop/jre-6u14-linux-i586.bin
```

However, for simplicity, I strongly recommend that you install the plugin and JRE from the repositories
```
sudo apt-get install sun-java6-jre
sudo apt-get install sun-java6-plugin

```

---

### Post by oldtraveler on 2009-07-17
However, for simplicity, I strongly recommend that you install the plugin and JRE from the repositories
```
sudo apt-get install sun-java6-jre
sudo apt-get install sun-java6-plugin

```[/QUOTE]
After doing this I end up with an open terminal showing

user@userl-desktop:~$ sudo apt-get install sun-java6-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
sun-java6-jre set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
user@user-desktop:~$ sudo apt-get install sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  sun-java6-plugin
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1960B of archives.
After this operation, 102kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse sun-java6-plugin 6-14-0ubuntu1.9.04 [1960B]
Fetched 1960B in 0s (4284B/s)           
Selecting previously deselected package sun-java6-plugin.
(Reading database ... 125100 files and directories currently installed.)
Unpacking sun-java6-plugin (from .../sun-java6-plugin_6-14-0ubuntu1.9.04_i386.deb) ...
Setting up sun-java6-plugin (6-14-0ubuntu1.9.04) ...

[color=red]user@user-desktop:~$ [/color]

Pogo game still says I need Java.

I also tried Synaptic.  Still no go.

---

### Post by oldtraveler on 2009-07-17
It seems that I must treat the above as two commands and do them one at a time.  Then after a re-boot it seems to work.  Thank you.

---

### Post by oldtraveler on 2010-04-20
[COLOR="Red"]**Skip to post #14 below on the next page for the correct solution for Ubuntu 10.04.**[/COLOR]

In Ubuntu 10.04 you must enable an additional repository [http://archive.canonical.com/ubuntu/pool/partner/](http://archive.canonical.com/ubuntu/pool/partner/)  


Open System &#9656; Administration &#9656; Software Sources and select Other 
        Software.

   
Click Add to add a new repository.
        

Enter the APT line for the extra repository. This should be 
        available from the website of the repository, and should look like 
        the following:

        

deb [http://archive.canonical.com/ubuntu/pool/partner/](http://archive.canonical.com/ubuntu/pool/partner/) lucid main


Click Add Source and then click 

       
Close to save your changes.

    
You will be notified that the information about available 
        software is out-of-date. Click Reload.

    


        

Packages from the new repository should now be available in your 
        package manager.

---

### Post by NoVista on 2010-04-20
Now why is it I can go to the web page ok, but after adding the repo I try it via Synaptic and get this error:
Failed to fetch [http://archive.canonical.com/ubuntu/pool/partner/dists/lucid/main/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/pool/partner/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

---

### Post by oldtraveler on 2010-04-20
I am a newbie to Ubuntu so I don't know that I have an answer for you except to ask "Did you follow all of the instructions EXACTLY?"  Also I am on a 64 bit system which may have a bearing. Are you using Ubuntu 10.04 beta?

---

### Post by ubudog on 2010-04-20
You can also install ubuntu-restricted-extras 
```
sudo apt-get install ubuntu-restricted-extras
```

It will install some other useful stuff along with java.

---

### Post by NoVista on 2010-04-20
I'm on my laptop now and get the same error results.
On the laptop, I installed ubuntu extras, (for the heck of it?).
sun-java6 is still no where to be found.
10.04 on both machines.

---

### Post by NoVista on 2010-04-20
I found my answer here, at the bottom of the page >>
[http://www.ubuntu.com/getubuntu/releasenotes/1004](http://www.ubuntu.com/getubuntu/releasenotes/1004)

Adding this repository works >>
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner

---

### Post by oldtraveler on 2010-04-20
> **NoVista said:**
> 

Adding this repository works >>
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
Isn't that what I suggested in post #5 above?

---

### Post by NoVista on 2010-04-21
No.

Worked:
deb [http://archive.canonical.com/](http://archive.canonical.com/)  lucid partner

Didn't work:
[deb ]("http://archive.canonical.com/ubuntu/pool/partner/")[http://archive.canonical.com/ubuntu/pool/partner/](http://archive.canonical.com/ubuntu/pool/partner/)  lucid main

---

### Post by oldtraveler on 2010-05-01
I did better with 10.04 beta than I am with the new 10.04LTS. I still can't get java to work with the LTS edtion. I have installed sun-java6=bin,  san-java6-jre, sun-java6-plugin, sun-java6-source, sun-javadb-client, sun-javadb-common, sun-javadb-core, java-common, javacc, and javahelper.

What am I missing?  Running on 64bit.

---

### Post by scouser73 on 2010-05-01
> **oldtraveler said:**
> I did better with 10.04 beta than I am with the new 10.04LTS. I still can't get java to work with the LTS edtion. I have installed sun-java6=bin,  san-java6-jre, sun-java6-plugin, sun-java6-source, sun-javadb-client, sun-javadb-common, sun-javadb-core, java-common, javacc, and javahelper.

What am I missing?  Running on 64bit.

The best advice for installing both 32 and 64bit versions of Java can be found on this website: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by oldtraveler on 2010-05-01
> **scouser73 said:**
> The best advice for installing both 32 and 64bit versions of Java can be found on this website: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)
Perfect!  I wish that I had had your link 6 hours ago.

Somebody sure made it difficult to get San Java for 10.04 Lucid, but your link provides a clear and understandable way to get the job done.

---

### Post by Razmear on 2010-05-02
Thanks for the info in #14. 
I already had Sun Java installed in 9.10, so in Synaptic
> 
Mark openjdk-6-jre for complete removal. The Icedtea plugin will automatically be marked as well, which is what you want.

Was all I had to do to get Pogo working again in 10.4

eb

---

### Post by Linuxforall on 2010-05-02
Best news is that Oracle has been added to partner repos so Sun Java would be regularly updated to the latest via the right method instead of the manual way. No more tension for Ubuntu users needing Sun Java and worried about updates.

---

### Post by madsc89 on 2010-05-02
Post nr 14 did the trick for me. I've struggeled for some time installing java for both firefox and chromium on my 64 bit system. With the guide ( [http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-64-BIT-UBUNTU](http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-64-BIT-UBUNTU) ) It was done in 5 minutes.

---

### Post by visiondude on 2010-05-03
> **oldtraveler said:**
> Perfect!  I wish that I had had your link 6 hours ago.

Somebody sure made it difficult to get San Java for 10.04 Lucid, but your link provides a clear and understandable way to get the job done.

:D Thanks also for the pointer, I am trying to learn Java 6 at the moment and from updating to 10.04 4 days ago I have been unable to run any codes. Big thanks all round everybody. :popcorn:

---

### Post by oldtraveler on 2010-07-02
I intend to try this post # 9 next time I need to install java.

From another forum:
[http://www.linuxforums.org/forum/linux-newbie/166276-runescape-grey-screen.html#post790231](http://www.linuxforums.org/forum/linux-newbie/166276-runescape-grey-screen.html#post790231)

Perhaps the java installation has been made easy.

---

### Post by oldtraveler on 2010-10-14
Once again Ubuntu fails to acknowledge that we need an easy way to get a version of java that works with pogo games.  I just installed the new ubuntu 10.10 and naturally I am unable to get the needed java plug in for firefox (jre-6u22-linux-x64.bin).

Ultimately got it to work by following the right column of [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java) after downloading jre-6u22-linux-x64.bin

Updated 12.26.10
Same site ([http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)) but used left column section entitiled "INSTALL FROM THE PARTNER REPOSITORY
The first method is the easiest: install JRE from the partner repository. Here you can find a how-to for enabling that repository (number 7).

To begin with, remove OpenJDK and the Icedtea plugin:

System - Administration - Synaptic Package Manager.

Query: openjdk. Don't use the quick search field (it's buggy), but press the Search button in the toolbar of Synaptic.

Mark openjdk-6-jre for complete removal. The Icedtea plugin will automatically be marked as well, which is what you want.

Press the Apply button in the toolbar.

Then do the following in Synaptic Package Manager:
Query: jre

Tick:
sun-java6-jre

Press the Apply button in the toolbar

Repeat this for sun-java6-plugin and for sun-java6-fonts."

---

### Post by oldtraveler on 2011-04-29
With another new Ubuntu - namely 11.04 -- once again java for Pogo games was a problem.  

Solved by doing this:

6. Java runtime environment

Java is a very important app to install, now that many programs need it to run. So type in the terminal:

    sudo add-apt-repository ppa:ferramroberto/java
    sudo apt-get update
    sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

---

### Post by oldtraveler on 2011-12-03
Once again Ubuntu needs to make an easier way to install java; however the above method will work for Ubuntu 11.10 - repeated here:

From a terminal type these commands one at a time

sudo add-apt-repository ppa:ferramroberto/java
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

---

### Post by oldtimer7777 on 2011-12-03
> **oldtraveler said:**
> Once again Ubuntu needs to make an easier way to install java; however the above method will work for Ubuntu 11.10 - repeated here:

From a terminal type these commands one at a time

sudo add-apt-repository ppa:ferramroberto/java
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

That certainly works for me too. 

You can also use the latest JRE 1.7 over here if you feel frisky:

[https://debianhelp.wordpress.com/2011/11/13/how-to-install-sun-java-se-1-7/](https://debianhelp.wordpress.com/2011/11/13/how-to-install-sun-java-se-1-7/)

---

### Post by oldtimer7777 on 2011-12-03
> **oldtraveler said:**
> Once again Ubuntu needs to make an easier way to install java; however the above method will work for Ubuntu 11.10 - repeated here:

From a terminal type these commands one at a time

sudo add-apt-repository ppa:ferramroberto/java
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

That certainly works for me too. 

You can also use the latest JRE 1.7 over here if you feel frisky:

[https://debianhelp.wordpress.com/2011/11/13/how-to-install-sun-java-se-1-7/](https://debianhelp.wordpress.com/2011/11/13/how-to-install-sun-java-se-1-7/)

---

### Post by oldtraveler on 2012-07-18
This is one reason I keep leaving Ubuntu and then come back later thinking that surely by now Ubuntu would have made it easy to get something as universally used as java.

Does any one have a sure fire way to get java in Ubuntu 12.04?  All of the above comments seem to be no longer valid.

---

### Post by QIII on 2012-07-18
Yes.  See the wiki link in my signature.

In the wiki, find the link entitled "Using webupd8.org's strikingly simple method."

---

### Post by oldos2er on 2012-07-18
Closed. Much changes in three years' time. If you need further help oldtraveler, please start a new thread.

---

