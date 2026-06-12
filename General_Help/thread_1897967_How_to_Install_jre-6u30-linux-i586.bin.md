---
title: "How to Install jre-6u30-linux-i586.bin"
date: 2011-12-20
forum: General Help
---

### Post by Richiegs on 2011-12-20
I am using Ubuntu 10.04 and I need to update Java to 6.30 or something. I downloaded it from Java website. Because it is not in Debian format, I have no idea how to install it correctly. I would appreciate anyone who could offer me suggestions on how to install Java correctly. Thank you in advance

---

### Post by raja.genupula on 2011-12-20
open your terminal and cd to that directory where java file located.
then do this 

sudo chmod +x filename.bin
./filename.bin

file name means your java file name

---

### Post by Richiegs on 2011-12-20
> **raja.genupula said:**
> open your terminal and cd to that directory where java file located.
then do this 

sudo chmod +x filename.bin
./filename.bin

file name means your java file name

But how do I find out which directory Java is located?

---

### Post by gandaran on 2011-12-20
> **Richiegs said:**
> But how do I find out which directory Java is located?
where is the downloads go to?

---

### Post by Richiegs on 2011-12-20
> **gandaran said:**
> where is the downloads go to?

/usr/lib/jvm
However, after I changed the directory  and typed "sudo chmod +x jre-6u30-linux-i586.bin", it said "chmod
: cannot access" & "jre-6u30-linux-i586.bin: no such file or directory"

I don't know what I did wrong.

---

### Post by QIII on 2011-12-20
I'd stop what you are doing for a bit.  There is a very easy, step-by-step tutorial for installing and uninstalling Sun Java.  I'm on my mobile right now, so I can't post the url.  Google for the terms 

Easy linux tips java

Make sure your browser is set to download to your Downloads (note case) directory in /home.

A word of warning: At one point the instructions said to uninstall OpenJDK.  Don't.  That will bork other stuff.  If he still says to uninstall OpenJDK, just skip that part.  But DO uninstall IcedTea, which is the open source version of the browser plugin.

---

### Post by gandaran on 2011-12-20
> **Richiegs said:**
> /usr/lib/jvm
However, after I changed the directory  and typed "sudo chmod +x jre-6u30-linux-i586.bin", it said "chmod
: cannot access" & "jre-6u30-linux-i586.bin: no such file or directory"

I don't know what I did wrong.
move the file to your home user directory then execute the install commands, from the user directory is not necessary to cd the terminal as the terminal opens on user settings,
thinks to do first first, right click the bin file » properties » permissions » mark allow executing file and don't forget to use sudo on the install command, it's easy to install the .bin file if you do it correctly.

---

### Post by Karlchen on 2011-12-20
Hello, Richiegs.
> I am using Ubuntu 10.04 and I need to update Java to 6.30 or something. I downloaded it from Java website. Because it is not in Debian format, I have no idea how to install it correctly.Please, use this step by step instruction [**Oracle (Sun) Java JRE for Ubuntu, Linux Mint and Debian**]("http://sites.google.com/site/easylinuxtipsproject/java#TOC-INSTALL-MANUALLY").
Note that there are actually two separate instructions: one applying to Ubuntu 64-bit and Java 64-bit and one applying to Ubuntu 32-bit and Java 32-bit, though of course the steps are pretty similar.

Personally I have extracted the steps to install the 32-bit Java Runtime Environment from the article and modified/enhanced them to match my environment perfectly. Works like a charm.

HTH,
Karl

---

### Post by QIII on 2011-12-20
Danke sehr, Karlchen!

Was on my mobile ane couldn't post the url.

I make much of my living developing in Java for Linux platforms, which is why I suggested the detailed and straight forward tutorial.

---

### Post by AgentZ86 on 2011-12-20
nice but where the heck is the terminal in ubuntu 11.10

I can't find it anywhere

--ok got it alt+ctrl+T ok

so it extracted it and is this all there is to it ? 

How about the path or link to the plugin ?

---

### Post by QIII on 2011-12-20
If you are using Unity, click on the Ubuntu symbol in the upper left.  Start typing "terminal"

---

### Post by QIII on 2011-12-20
> **QIII said:**
> If you are using Unity, click on the Ubuntu symbol in the upper left.  Start typing "terminal"

Are you using the tutorial at the url provided?

I love accidentally quoting myself when typing on my mobile!

---

### Post by AgentZ86 on 2011-12-20
Ok so i put into the home directory and it extracted and said Done

So how to get it working, it does not appear to install a plugin
I mean it looked like it was installing / or extracting and says Done

But yet no functioning plugin working at this point


P.S I installed the x64 version would this make a difference or should I be using the i586 version ? 



Please advise
Thanks

---

### Post by AgentZ86 on 2011-12-20
Ok I think I got it working, thanks

---

### Post by QIII on 2011-12-20
If you are still around, would you do the following in the terminal and let us know what it says?

```
java -version
```

And then type 

```
about:plugins
```

in FF if you are using it?

---

### Post by AgentZ86 on 2011-12-20
> **QIII said:**
> If you are still around, would you do the following in the terminal and let us know what it says?

```
java -version
```

And then type 

```
about:plugins
```

in FF if you are using it?

Yep

Java
> java version "1.6.0_30"
Java(TM) SE Runtime Environment (build 1.6.0_30-b12)
Java HotSpot(TM) 64-Bit Server VM (build 20.5-b03, mixed mode)
agent86@agent86-S2865:~$ 

and FF

> Java(TM) Plug-in 1.6.0_30

    File: libnpjp2.so
    Version: 
    The next generation Java plug-in for Mozilla browsers.

For me what I did was follow the instructions from your link / and for 64bit version which is on the right side of that page

But prior to that I actually had also saw that you suggested to uninstall icetea plugin, but not the OpenJDK so I had already did that

So from the install link basically all went well and the parts about removing icetea just error and said nothing to uninstall since I had already uninstalled it from the ubuntu center

So now it appears ok


Thanks

---

### Post by Richiegs on 2011-12-21
I moved the new java file to the home folder and then typed " sudo ./jre-6u30-linux-i586.bin" in the terminal. The terminal said "done", but it didn't display the java agreement afterward. What did I do wrong?

---

### Post by gandaran on 2011-12-21
> **Richiegs said:**
> I moved the new java file to the home folder and then typed " sudo ./jre-6u30-linux-i586.bin" in the terminal. The terminal said "done", but it didn't display the java agreement afterward. What did I do wrong?
run any graphical java application then it should show the agreement window first.

---

### Post by AgentZ86 on 2011-12-21
> **Richiegs said:**
> I moved the new java file to the home folder and then typed " sudo ./jre-6u30-linux-i586.bin" in the terminal. The terminal said "done", but it didn't display the java agreement afterward. What did I do wrong?

Read Post No# and click the link which has instructions for you

You did exactly what I did at first and simply unpacked it

These instructions are for 32bit to the left of the page and 64bit to the right of the page

And Don't uninstall the OpenJDK as some suggested, only uninstall IceTea plugin

Follow the instructions at the link on post no#8 and you will be up and running

Happy hacking

---

### Post by Richiegs on 2011-12-21
> **AgentZ86 said:**
> Read Post No# and click the link which has instructions for you

You did exactly what I did at first and simply unpacked it

These instructions are for 32bit to the left of the page and 64bit to the right of the page

And Don't uninstall the OpenJDK as some suggested, only uninstall IceTea plugin

Follow the instructions at the link on post no#8 and you will be up and running

Happy hacking

Do I need to uninstall the original Java from Synaptic Package Manager first?

---

### Post by Richiegs on 2011-12-21
I moved it to the home folder, but one post suggested to move it to the download folder of home directory. I am confused. Which folder should I move Java to?

---

### Post by Richiegs on 2011-12-21
I wonder which directory I should install Java to.

---

### Post by gandaran on 2011-12-21
> **Richiegs said:**
> I moved it to the home folder, but one post suggested to move it to the download folder of home directory. I am confused. Which folder should I move Java to?
this was just o run the install command, did you see on the terminal output where java was going to be installed? the package should install java to the package set default directory.

---

### Post by Richiegs on 2011-12-21
> **gandaran said:**
> this was just o run the install command, did you see on the terminal output where java was going to be installed? the package should install java to the package set default directory.

It just installed Java in the home directory. After DONE, it did not show me the agreement page from the terminal. I followed the installation instructions from Java web site.

---

### Post by gandaran on 2011-12-21
> **Richiegs said:**
> It just installed Java in the home directory. After DONE, it did not show me the agreement page from the terminal. I followed the installation instructions from Java web site.
okay sorry about that, I just tried installing the same package and in fact it installs to home directory, it wasn't like this before it would install java to /opt by default so you have to run the install command from the same directory where you want java to be.
also java installed in home should work without problems (for firefox plugin run the link command) to but it's annoyning having it here.
[http://java.com/en/download/help/linux_install.xml#selfextracting](http://java.com/en/download/help/linux_install.xml#selfextracting)

---

### Post by Richiegs on 2011-12-22
> **QIII said:**
> I'd stop what you are doing for a bit.  There is a very easy, step-by-step tutorial for installing and uninstalling Sun Java.  I'm on my mobile right now, so I can't post the url.  Google for the terms 

Easy linux tips java

Make sure your browser is set to download to your Downloads (note case) directory in /home.

A word of warning: At one point the instructions said to uninstall OpenJDK.  Don't.  That will bork other stuff.  If he still says to uninstall OpenJDK, just skip that part.  But DO uninstall IcedTea, which is the open source version of the browser plugin.

I followed the instructions in Easy Linux Tips Java and was able to install jre-6u30-linux-i586.bin. Thank you so much!

---

### Post by rjf1 on 2011-12-22
The instructions told how to install the plugin into Firefox -- how do you install it into Chrome/Chromium? TIA

---

### Post by Richiegs on 2011-12-22
> **rjf1 said:**
> The instructions told how to install the plugin into Firefox -- how do you install it into Chrome/Chromium? TIA

It seems only Firefox needs this special step. Other browsers work fine so far.

---

### Post by uteck on 2011-12-23
Here are the steps I took to convert the latest Java .bin file into a .deb so that I could add that to my repo to update my systems with.

1. Download latest version of Java from: [http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp)
Make sure to get &#8220;Linux (self-extracting file) &#8220;  or x64 for 64 bit systems, but not ones with RPM in the name.
2. Convert it to a Debian package;
Install the &#8220;java-package&#8221; application to make the conversion
run &#8220;fakeroot make-jpkg jre-6u30-linux-i586.bin&#8221; as a normal user, not root as that can mess up your settings.
3. This will produce a file called sun-j2re1.6_1.6.0+update30_i386.deb, but it will not install properly since it will be looking to configure some old Netscape settings which do not exist in new versions of Java.
4. Make a directory to extact the new .deb file into, &#8220;mkdir jre-6u30&#8221;
5. Extract it using &#8220;dpkg-deb -x sun-j2re1.6_1.6.0+update30_i386.deb jre-6u30&#8221;
6. Extract control file &#8220;dpkg-deb -e sun-j2re1.6_1.6.0+update30_i386.deb jre-6u30/DEBIAN&#8221;
7. Inside the DEBIAN directory you just extracted, edit the postinst file.
Remove the Netscape section to prevent the installer from looking for it since it does not exist and crashes the installer.
The normal Java plugin does not work properly and needs a helper file to load.  At the end of the postint file, above EXIT 0, add these lines;
#Fix broken pligin
rm $mozilla_dir/libnpjp2.so
ln -s /usr/lib/j2re1.6-sun/lib/i386/libnpjp2.so $mozilla_dir

For the SDK the path is;
ln -s /usr/lib/j2re1.6-sun/jre/lib/i386/libnpjp2.so $mozilla_dir
8. Build the new Debian pakage
Make build directory, mkdir build
dpkg-deb -b jre-6u30 build
Inside the build directory will be a new sun-j2re1.6_1.6.0+update30_i386.deb file that will install without errors and configure a working plugin.

---

