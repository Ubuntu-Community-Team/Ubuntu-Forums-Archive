---
title: "installing java"
date: 2010-12-17
forum: General Help
---

### Post by zhity on 2010-12-17
how do you install java on ubuntu?? with windows its a matter of clicking buttons... i read the instructions for linux, downloaded the filefrom sun. but the installation instructions are gobblygook

---

### Post by lykeion on 2010-12-17
The preferred way to install applications (a.k.a packages) in Ubuntu is to use a package manager, like Ubuntu Software Center.

Simple click-and-install instructions to install the Java browser plugin:
1. Start Ubuntu Software Center (found in the Applications menu)
2. In the search textfield at top right enter "java plugin" and install the IcedTea Java Plugin. 

This will install the open-source version of the Java plugin. If you for some reason need to install the proprietary version from Sun/Oracle, you need to enable the partner repository (if you're using Lucid or Maverick) or the multiverse repository (if you are using older versions of Ubuntu).

If the open-source version works for you there is *really no need* to install proprietary Sun Java plugin.

---

### Post by The_Eggert on 2010-12-17
I'm assuming you're installing the latest version of java:
When you have downloaded the file from Java.com, first make it executable (replace "FILENAME" with the actual filename.. ;).
From a terminal write:
```

chmod +x FILENAME.bin

```

With that done, move the .bin to the desired install folder:
```

sudo mv /PATH/TO/JAVA-BINARY/FILENAME.bin /DESIRED/INSTALL/PATH
*[COLOR="Red"]Eg. "sudo mv /home/lars/Downloads/jre-6u23-linux-x64.bin /usr/loacl/bin/java/[/COLOR]*

```

Then navigate to the install folder in the terminal and type
```
./FILENAME.bin
```

This is the first time I'm providing any acctual help here..So do tell me if I need to specify something :P

---

### Post by gdiloren on 2010-12-17
> **zhity said:**
> how do you install java on ubuntu?? with windows its a matter of clicking buttons... i read the instructions for linux, downloaded the filefrom sun. but the installation instructions are gobblygook
I refer you to this thread [http://ubuntuforums.org/showthread.php?t=1645237&highlight=update+java](http://ubuntuforums.org/showthread.php?t=1645237&highlight=update+java)
Just change 22 to actual version 23 but as been said in the thread the java you got on your pc provided by Ubuntu is already ok.;)

---

### Post by Peanuts123 on 2010-12-18
Simply go to applications>software center and install java. If you like you can install the original or the icetea version as i did and i am playing games on facebook and watching youtube videos now

---

### Post by asmoore82 on 2010-12-18
[SIZE="3"]Big +1[/SIZE] for the IcedTea Java Plugin.

The more complete answer is that Java is always in a state of upheaval.
There's Java 6 vs. Java 7 vs. Java Mobile vs. OpenJDK vs. GCJ vs. Android.
Choosing one over the other is a decision. Whenever a situation seems simpler
on other OS's, it just means that someone has made decisions for you.

---

### Post by zhity on 2010-12-22
installed the icedtea java plugin... it does NOT work with yahoo games. i made an exception for the popup blocker for this site. applet pops up but does not load game...

---

### Post by zhity on 2011-03-25
still no solution here. 3 months now. the iced tea java does not work on some applications, ie yahoo games in the old version and also person .com on the web cams. so some more detailed instructions on installing sun java from anyone here would be great. im still using ubuntu more and more these days but things like this keep me going back to windows.

---

### Post by scouser73 on 2011-03-26
**1** - Go to **System** [COLOR="Red"]>[/COLOR] **Administration** [COLOR="red"]>[/COLOR] **Software Sources**
**2** - Click on the tab labelled **Other Sources**
**3** - Tick the box named **Canonical Partners**
**4** - Click **Close**
**5** - Click **Reload**
**6** - Now go to **System** [COLOR="red"]>[/COLOR] **Administration** [COLOR="red"]>[/COLOR] **Synaptic Package Manager**
**7** - In the search field type **Java**, and the **Sun Java JRE** will be listed
**8** - Click the box to select it and also install the **Java Plugin**
**9** - Click **Apply** and Sun Java JRE & the Java Plugin will be installed
**10** - You can now remove the other Java that is installed

---

### Post by Dry Lips on 2011-03-28
I wanted to use my net bank using Chromium, but the 
default OpenJDk Java6 didn't work. So I tried the Icedtea-plugin,
 but alas, still no luck... Finally I tried what Scouser73 
suggested. To my surprise  it didn't work, so I then installed
 Opera, where everything did work perfectly. (I didn't 
want to use firefox for this, as I use NoScript, and a 
couple of cookie-blockers, which don't always work too
 well with those kind of places...)
 
 So what boggles me is whether or not chromium was the 
real problem; perhaps Icedtea would have worked if I'd
 used another browser in the first place...  :confused:
 
**scouser73**
> **7** - In the search field type **Java**, and the **Sun Java JRE** will be listed
**8** - Click the box to select it and also install the **Java Plugin**
**9** - Click **Apply** and Sun Java JRE & the Java Plugin will be installed
**10** - You can now remove the other Java that is installed     
 To be more specific:  
 
 - sun-java6-jre
 - sun-java6-plugin
 
 Then remove:
 &#8220;OpenJDK Java6 Runtime&#8221; from the Ubuntu Software Center.

---

