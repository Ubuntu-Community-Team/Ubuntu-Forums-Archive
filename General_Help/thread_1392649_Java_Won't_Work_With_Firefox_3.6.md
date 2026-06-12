---
title: "Java Won't Work With Firefox 3.6"
date: 2010-01-28
forum: General Help
---

### Post by ..::| Dave89 |::.. on 2010-01-28
I downloaded Firefox 3.6 from the Mozilla website, and installed Java Runtime and Java Browser Plugin from Ubuntu Software Center, but Java will not work within Firefox, it works with Firefox 3.5.7 installed from the repositories, but I really want to use Firefox 3.6.  I've even tried UbuntuZilla, without any success.  This is annoying as I visit a lot of Java enabled websites.

TIA

---

### Post by nanotube on 2010-01-28
> **..::| Dave89 |::.. said:**
> I downloaded Firefox 3.6 from the Mozilla website, and installed Java Runtime and Java Browser Plugin from Ubuntu Software Center, but Java will not work within Firefox, it works with Firefox 3.5.7 installed from the repositories, but I really want to use Firefox 3.6.  I've even tried UbuntuZilla, without any success.  This is annoying as I visit a lot of Java enabled websites.

TIA

this is a known problem with the sun-java6-plugin package in karmic.
there's a workaround posted on the ubuntuzilla website:
[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Java_plugin_not_showing_up_.28on_Ubuntu_Karmic.29](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Java_plugin_not_showing_up_.28on_Ubuntu_Karmic.29)

---

### Post by drs305 on 2010-01-28
For 64-bit, this command worked for me with FF 3.6 (after java was installed):
```
sudo update-alternatives --install /usr/lib/mozilla/plugins/libjavaplugin.so mozilla-javaplugin.so /usr/lib/jvm/java-6-sun-1.6.0.16/jre/lib/amd64/libnpjp2.so 50
```

---

### Post by scouser73 on 2010-01-28
> **..::| Dave89 |::.. said:**
> I downloaded Firefox 3.6 from the Mozilla website, and installed Java Runtime and Java Browser Plugin from Ubuntu Software Center, but Java will not work within Firefox, it works with Firefox 3.5.7 installed from the repositories, but I really want to use Firefox 3.6.  I've even tried UbuntuZilla, without any success.  This is annoying as I visit a lot of Java enabled websites.

TIA

Hi Dave, follow the instructions on this site for installing the latest version of Java: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by Tourdog on 2010-01-28
Dave89

I just completed the 64 bit (right hand side of the page) Java from the "Sun Java JRE (easy linux tips) project" that is the http that scouser73 posted for you...............   it works perfectly as each step indicates.   I'm using Karmic Koala 9.10, FF 3.61pre   thanks  :)

HTH !

---

### Post by ..::| Dave89 |::.. on 2010-01-28
Neither of those worked for me

---

### Post by scouser73 on 2010-01-28
Did you uninstall the Java that you got from the Ubuntu Software Centre first?

---

### Post by ..::| Dave89 |::.. on 2010-01-28
I removed Java the way it's described in the article @ [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by scouser73 on 2010-01-28
I'd suggest that you look in Synaptic Package Manager and search for any traces of Java and then if found, remove it.  Then you could try that site again.

---

### Post by ..::| Dave89 |::.. on 2010-01-28
Still no success.  I'm going to do a reinstall of Ubuntu (again) then try.

---

### Post by raktarok on 2010-01-28
I also had a similar problem with java and I did this to fix my problem.

Remove the iced-tea plugin if you have installed it.

```
sudo apt-get remove icedtea6-plugin 
```

Then this,

```
sudo apt-get install sun-java6-plugin

sudo ln -s /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so ~/.mozilla/plugins/

```

Note that I am using swiftfox, which is based on firefox 3.6. So this should work for firefox too. Anyway, there's no harm in trying....

And I am using java packages from the repositories..

---

### Post by linusr on 2010-01-28
Java applets work on my machine if FireFox is started from terminal.

Or just displays grey window!

Strange!!! What difference does starting from terminal do?

---

### Post by raktarok on 2010-01-28
That is strange...

Check the launcher that you use to start firefox. What does it have in the command field? Do you launch it from the menu?

Maybe there's a problem with your java installation and the paths aren't set properly? try removing all java related packages and installing it again.

Good luck!

---

### Post by linusr on 2010-01-28
> **raktarok said:**
> That is strange...

Check the launcher that you use to start firefox. What does it have in the command field? Do you launch it from the menu?

Maybe there's a problem with your java installation and the paths aren't set properly? try removing all java related packages and installing it again.

Good luck!

launcher initially had 'firefox %u'. Tried changing to 'firefox' with no luck.

tried openjdk which didn't work either and back to sun jre

---

### Post by raktarok on 2010-01-28
> **linusr said:**
> launcher initially had 'firefox %u'. Tried changing to 'firefox' with no luck.

tried openjdk which didn't work either and back to sun jre

Which version of firefox are you using? Did you try linking the sun's java plugin file to the profile directory, as suggested above?

---

### Post by PRC09 on 2010-01-28
Try post #9 and or #21......


[http://ubuntuforums.org/showthread.php?t=1381226](http://ubuntuforums.org/showthread.php?t=1381226)

---

### Post by linusr on 2010-01-28
> **raktarok said:**
> Which version of firefox are you using? Did you try linking the sun's java plugin file to the profile directory, as suggested above?

Firefox 3.5.7 & sun java plugin.

FF had detected java plugin and listed in about:plugins page.

> sudo ln -s /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so ~/.mozilla/plugins/

above didn't work as well :!:

---

### Post by raktarok on 2010-01-28
@ linusr 
For 3.5.7, the iced tea plugin was working fine for me, but I guess you have already tried it, right? You could try linking the icedtea plugin file to your profile directory, like with sun's plugin, but I am not sure if that will work for you.

Try the instructions posetd in the above link and see if it works.

---

### Post by linusr on 2010-01-28
upgraded to 1.6.0.18 and strangely issue remains..

checked Chrome..it's the same.. Java works if started from terminal

in chrome task manager java plugin is listed and occupies 14M memory but applets don't load!!

confused!!!

---

### Post by ..::| Dave89 |::.. on 2010-01-29
Some progress...  I installed Java as described at [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java) and ran the command sudo ln -s /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so ~/.mozilla/plugins/ as suggested by [raktarok]("http://ubuntuforums.org/member.php?u=694601"), and then installed Java Plugin 1.6.0_15 in Firefox.  Java now works, but is recognized as Update 15, when I uninstalled Update 15 in Synaptic.  Firefox refuses to update the plugin, and Java is recognized as Update 15 in Synaptic.  When I uninstalled Update 15 originally, I only removed the files selected in the attached image, was there something else I had to remove?

[[IMG]http://img29.imageshack.us/img29/986/screenshotsr.th.png[/IMG]](http://img29.imageshack.us/i/screenshotsr.png/)

---

### Post by raktarok on 2010-01-29
> **..::| Dave89 |::.. said:**
> Some progress...  I installed Java as described at [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java) and ran the command sudo ln -s /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so ~/.mozilla/plugins/ as suggested by [raktarok]("http://ubuntuforums.org/member.php?u=694601"), and then installed Java Plugin 1.6.0_15 in Firefox.  Java now works, but is recognized as Update 15, when I uninstalled Update 15 in Synaptic.  Firefox refuses to update the plugin, and Java is recognized as Update 15 in Synaptic.  When I uninstalled Update 15 originally, I only removed the files selected in the attached image, was there something else I had to remove?

[[IMG]http://img29.imageshack.us/img29/986/screenshotsr.th.png[/IMG]](http://img29.imageshack.us/i/screenshotsr.png/)

When I did sudo ln -s /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so ~/.mozilla/plugins/, I was using the file libnpjp2.so from the sun-java6-bin package. But you removed the package sun-java6-bin, right?
So that command should have shown some error? Can you please post the output of this first, so that we can see which plugin file you are using..

```
sudo ls -l ~/.mozilla/plugins/
```

Also, since you installed java in /opt, do this if you have not done it already. This is the same step as suggested in the link above and this should have worked.
```

sudo ln -s /opt/java/32/jre1.6.0_18/plugin/i386/ns7/libjavaplugin_oji.so ~/.mozilla/plugins/
```
You may have to change the part jre1.6.0_18 here, depending on the folder present there. Check the folder /opt/java/32/ to find out what the folder is.
Also, if you decide to do this, make sure you delete the existing java plugin file that could be present in ~/.mozilla/plugins/
```
sudo rm ~/.mozilla/plugins/libnpjp2.so   
```

---

### Post by ratcheer on 2010-01-29
I got the latest Sun Java update working with FF 3.6, Wednesday. So, it is fresh in my mind. It took me most of the day to make it work, because Sun's instructions told me the wrong thing to do.

What you need to do is create a symbolic link to Java file  libnpjp2.so in your Firefox installation's plugins subdirectory. Then, restart Firefox. On my system, the Java file is in /opt/jre-6u18/jre1.6.0_18/lib/i386, but it depends on where you installed Java.

You can confirm that it is working in several ways. 1) Firefox >> Tools >> Add-ons >> Plugins tab; 2) Open page about:plugins in Firefox browser; 3) Visit web page [http://java.com/en/download/installed.jsp](http://java.com/en/download/installed.jsp)

Tim

---

### Post by scouser73 on 2010-01-29
> **ratcheer said:**
> I got the latest Sun Java update working with FF 3.6, Wednesday. So, it is fresh in my mind. It took me most of the day to make it work, because Sun's instructions told me the wrong thing to do.

What you need to do is create a symbolic link to Java file  libnpjp2.so in your Firefox installation's plugins subdirectory. Then, restart Firefox. On my system, the Java file is in /opt/jre-6u18/jre1.6.0_18/lib/i386, but it depends on where you installed Java.

You can confirm that it is working in several ways. 1) Firefox >> Tools >> Add-ons >> Plugins tab; 2) Open page about:plugins in Firefox browser; 3) Visit web page [http://java.com/en/download/installed.jsp](http://java.com/en/download/installed.jsp)

Tim

I know you've installed the latest version of Java, but I'd recommend you bookmark this - [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by ..::| Dave89 |::.. on 2010-01-29
raktarok:

dave89@dave89-desktop:~$ sudo ls -l ~/.mozilla/plugins/
[sudo] password for dave89: 
total 4
lrwxrwxrwx 1 dave89 dave89 61 2010-01-29 19:07 libjavaplugin_oji.so -> /opt/java/32/jre1.6.0_18/plugin/i386/ns7/libjavaplugin_oji.so
lrwxrwxrwx 1 root   root   48 2010-01-29 18:55 libnpjp2.so -> /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so
dave89@dave89-desktop:~$ 

I got this with the command 
sudo ln -s /opt/java/32/jre1.6.0_18/plugin/i386/ns7/libjavaplugin_oji.so ~/.mozilla/plugins/ :


dave89@dave89-desktop:~$ sudo ln -s /opt/java/32/jre1.6.0_18/plugin/i386/ns7/libjavaplugin_oji.so ~/.mozilla/plugins/
ln: creating symbolic link `/home/dave89/.mozilla/plugins/libjavaplugin_oji.so': File exists
dave89@dave89-desktop:~$

---

### Post by raktarok on 2010-01-29
You have two java plugin files in the profile folder, so maybe that's the reason why you are facing that issue.

So do delete the one linked to /usr/lib/java...(that's the older one) and it should work now.

```
sudo rm ~/.mozilla/plugins/libnpjp2.so
```

---

### Post by ..::| Dave89 |::.. on 2010-01-29
I did that, now I've lost all Java capabilities in Firefox.  Tried reinstalling the Java plug-in within Firefox, says it's already installed but there's no entry for Java in about:plugins

---

### Post by ratcheer on 2010-01-29
Just do what I said in post #22. I fooled around with libjavaplugin_oji.so all day, Wednesday. But, Java never worked in Firefox until I linked the current version of libnpjp2.so

Tim

---

### Post by ..::| Dave89 |::.. on 2010-01-30
Oh I see, I must have missed that in post  #22, solved my problem straight away!  Thank for everyones help!

---

### Post by ratcheer on 2010-01-30
You are welcome.

Tim

---

### Post by nanotube on 2010-01-30
by the way, the workaround described on the ubuntuzilla website does exactly the same thing - places a link to the libnpjp2.so from java into /usr/lib/mozilla/plugins... 

the libjavaplugin_oji.so uses an old plugin interface that no longer works with ff3.6.

---

### Post by ratcheer on 2010-01-30
Then Sun needs to update their installation instructions to say to use one plugin if your FF is such-and-such or older, or the other plugin if your FF is newer. I spent hours trying to solve that problem.

Tim

---

### Post by nanotube on 2010-01-30
> **ratcheer said:**
> Then Sun needs to update their installation instructions to say to use one plugin if your FF is such-and-such or older, or the other plugin if your FF is newer. 

yes, indeed it does.

---

### Post by Pjotr123 on 2010-02-01
In the meantime, I've updated the instruction on my website, for users of Firefox 3.6: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Just for fun, I've tried using [COLOR="Blue"]libnpjp2.so[/COLOR] in Firefox 3.5, instead of [COLOR="Blue"]libjavaplugin_oji.so[/COLOR]. 

It appears to work fine.... So maybe I could remove all references to [COLOR="Blue"]libjavaplugin_oji.so[/COLOR] in my how-to. I'm not sure though, if [COLOR="Blue"]libnpjp2.so[/COLOR] will work in Firefox 3.0.

---

### Post by LegendarySandwich on 2010-02-01
> **Pjotr123 said:**
> In the meantime, I've updated the instruction on my website, for users of Firefox 3.6: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Just for fun, I've tried using [COLOR=Blue]libnpjp2.so[/COLOR] in Firefox 3.5, instead of [COLOR=Blue]libjavaplugin_oji.so[/COLOR]. 

It appears to work fine.... So maybe I could remove all references to [COLOR=Blue]libjavaplugin_oji.so[/COLOR] in my how-to. I'm not sure though, if [COLOR=Blue]libnpjp2.so[/COLOR] will work in Firefox 3.0.
Thanks for that site, I had the exact same problem :D

Just one question though: since it is installed manually, will it update all by itself, or will I have to manually update it?

---

### Post by raktarok on 2010-02-01
> **LegendarySandwich said:**
> Thanks for that site, I had the exact same problem :D

Just one question though: since it is installed manually, will it update all by itself, or will I have to manually update it?

You will have to update it manually. But there are probably some ppas with new java package maintained regularly. You could try searching for them.

---

### Post by linusr on 2010-02-05
> **linusr said:**
> Firefox 3.5.7 & sun java plugin.

FF had detected java plugin and listed in about:plugins page.

above didn't work as well :!:

I had to delete java plugin in folders,

```
/usr/lib/mozilla/plugins
/usr/lib/xulrunner-addons/plugins
```

then link
```
ln -s /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so ~/.mozilla/plugins/libjavaplugin.so
```

---

### Post by crjackson on 2010-02-07
I'm sure there is a more elegant way to do all this in a terminal session, but this works for me every time.

[http://buck-nasty.blogspot.com/2010/02/installing-firefox-36-and-java-618.html]("http://buck-nasty.blogspot.com/2010/02/installing-firefox-36-and-java-618.html")

---

