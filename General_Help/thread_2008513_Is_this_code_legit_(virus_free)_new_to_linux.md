---
title: "Is this code legit? (virus free) new to linux"
date: 2012-06-22
forum: General Help
---

### Post by SRJL on 2012-06-22
Hello i followed an online tutorial to install the latest java. 

Could someone please take a glance at this code to see if it is actually doing what it claims it is.

Thanks alot for your time 


  	 	 	 	 	 	   **[COLOR=#000000][SIZE=4][B]HOW-TO FOR 64 BIT UBUNTU**[/SIZE][/COLOR][/B]

 ** [COLOR=#000000][SIZE=3][B]Remove the browser plug-in of the old version**[/SIZE][/COLOR][/B]

 [COLOR=#000000][SIZE=3]First you'll want to remove the browser plug-in of the old JRE or openJDK (if you have it). [/SIZE][/COLOR][COLOR=#000000][SIZE=3]***Only the browser plug-in needs to be removed!***[/SIZE][/COLOR][COLOR=#000000][SIZE=3] Otherwise unwanted side effects may occur. 

When the old JRE has been installed manually in [/SIZE][/COLOR][COLOR=#0000ff][SIZE=3]/opt/java[/SIZE][/COLOR][COLOR=#000000][SIZE=3], see the [/SIZE][/COLOR][instruction at the bottom of this column (under the header Removal)]("https://sites.google.com/site/easylinuxtipsproject/java#TOC-Removal1")[COLOR=#000000][SIZE=3].

When you don't have an old JRE, you probably have openJDK and the IcedTea browser plug-in. The IcedTea browser plug-in (icedtea-6-jre-cacao) should be removed; openJDK itself can remain on your hard disk. 

Like this:

Click on Ubuntu Software Center (the shopping bag) in the side panel.
Query: [/SIZE][/COLOR][COLOR=#0000ff][SIZE=3]icedtea[/SIZE][/COLOR][COLOR=#000000][SIZE=3].

Remove only the [/SIZE][/COLOR][COLOR=#0000ff][SIZE=3]IcedTea Java-plug-in[/SIZE][/COLOR][COLOR=#000000][SIZE=3]. Leave OpenJDK itself on your hard disk.

Press the [/SIZE][/COLOR][COLOR=#0000ff][SIZE=3]Remove [/SIZE][/COLOR][COLOR=#000000][SIZE=3]button.[/SIZE][/COLOR]
 


 **[COLOR=#000000][SIZE=3][B]Get JRE**[/SIZE][/COLOR][/B]

 [COLOR=#000000][SIZE=3]Get the right file from the Java website: [/SIZE][/COLOR][http://www.java.com]("http://www.java.com/")[COLOR=#000000][SIZE=3]

For 64-bit you want [/SIZE][/COLOR][COLOR=#000000][SIZE=3]***Linux x64***[/SIZE][/COLOR][COLOR=#000000][SIZE=3]. The name of this file ends on [/SIZE][/COLOR][COLOR=#0000ff][SIZE=3].tar.gz[/SIZE][/COLOR][COLOR=#000000][SIZE=3]. Do not pick [/SIZE][/COLOR][COLOR=#000000][SIZE=3]***Linux x64 RPM***[/SIZE][/COLOR][COLOR=#000000][SIZE=3] (file name ends on [/SIZE][/COLOR][COLOR=#0000ff][SIZE=3]x64.rpm[/SIZE][/COLOR][COLOR=#000000][SIZE=3]), because RPM is not built for Ubuntu, but for other Linux distro's.

[/SIZE][/COLOR][COLOR=#000000][SIZE=3]***Note:***[/SIZE][/COLOR][COLOR=#000000][SIZE=3] Store the file in the folder Downloads. So in [/SIZE][/COLOR][COLOR=#0000ff][SIZE=3]/home/your-user-name/Downloads[/SIZE][/COLOR][COLOR=#000000][SIZE=3]. Firefox puts downloaded files there by default, but not all web browsers do it like that.  [/SIZE][/COLOR]

[COLOR=#000000][SIZE=3]For example: user John should place the file in[/SIZE][/COLOR][COLOR=#000000] [/COLOR][COLOR=#0000ff][SIZE=3]/home/john/Downloads[/SIZE][/COLOR][COLOR=#000000][SIZE=3]. When in doubt, check it. 

This is important for the terminal commands that you'll execute later on; otherwise they won't be correct.[/SIZE][/COLOR]
 


 **[COLOR=#000000][SIZE=3][B]Install JRE (64-bit)**[/SIZE][/COLOR][/B]

 [COLOR=#000000][SIZE=3]***Note:***[/SIZE][/COLOR][COLOR=#000000][SIZE=3] the terminal commands in this how-to possibly refer to an older version of JRE. When there's a newer version, you can simply adapt the file names in the terminal commands.

[/SIZE][/COLOR][COLOR=#000000][SIZE=3]***This how-to has been written for JRE 7 update 5 (64 bit version).***[/SIZE][/COLOR][COLOR=#000000][SIZE=3]


1. Create a new subfolder in the folder [/SIZE][/COLOR][COLOR=#0000ff][SIZE=3]opt[/SIZE][/COLOR][COLOR=#000000][SIZE=3], by means of a command.

Click on the grey Ubuntu logo (Dash home). Query: [/SIZE][/COLOR][COLOR=#0000ff][SIZE=3]terminal[/SIZE][/COLOR][COLOR=#000000][SIZE=3]. 
Click on Terminal.

Type (use copy/paste: rapidly click three times on the blue line, in order to select the entire line).
[/SIZE][/COLOR][COLOR=#0000ff][SIZE=3]sudo mkdir -p -v /opt/java/64[/SIZE][/COLOR][COLOR=#000000][SIZE=3]

Press Enter.

Type your password. You won't see anything, not even dots, this is normal.
Press Enter.


2. Now go to the Downloads folder and unpack the compressed JRE file that you just downloaded, with the following combined command.

Type (copy/paste):[/SIZE][/COLOR]
[COLOR=#0000ff][SIZE=3]cd Downloads && tar xvzf ~/Downloads/jre-7u5-linux-x64.tar.gz[/SIZE][/COLOR][COLOR=#000000][SIZE=3]

Press Enter.


3. Move the unpacked contents of the JRE file into the system folder that you created in step 1, with the following command.

Type (copy/paste):[/SIZE][/COLOR]
[COLOR=#0000ff][SIZE=3]sudo mv -v ~/Downloads/jre1.7.0_05 /opt/java/64

[/SIZE][/COLOR][COLOR=#000000][SIZE=3]Press Enter.[/SIZE][/COLOR]
 ** [COLOR=#000000][SIZE=3][B]Inform the system and make the new JRE the default**[/SIZE][/COLOR][/B]

 [COLOR=#000000][SIZE=3]4. Now you'll want to tell the system, that there's a new Java version available.

Type (copy/paste):[/SIZE][/COLOR]
[COLOR=#0000ff][SIZE=3]sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/64/jre1.7.0_05/bin/java" 1[/SIZE][/COLOR][COLOR=#000000][SIZE=3]

Press Enter.

[/SIZE][/COLOR][COLOR=#000000][SIZE=3]***Note:***[/SIZE][/COLOR][COLOR=#000000][SIZE=3] are you updating from a previous Java version, which you have removed manually? Then you'll need to execute the above command twice, because you'll get an error message the first time.
[/SIZE][/COLOR][COLOR=#000000][SIZE=3]

5. Tell the system, that the new Java must be the default.

Type (copy/paste):[/SIZE][/COLOR]
 [COLOR=#0000ff][SIZE=3]sudo update-alternatives --set java /opt/java/64/jre1.7.0_05/bin/java

[COLOR=#000000]Press Enter.[/COLOR][/SIZE][/COLOR]
 **[COLOR=#000000][SIZE=3][B]Install the Firefox plugin**[/SIZE][/COLOR][/B]

 [COLOR=#000000][SIZE=3]6. Installing the Firefox plugin is simple. First execute the following command, in order to create a certain folder (if it doesn't exist already).

Type in the terminal (copy/paste):[/SIZE][/COLOR]
[COLOR=#0000ff][SIZE=3]mkdir -v ~/.mozilla/plugins[/SIZE][/COLOR][COLOR=#000000][SIZE=3]

Press Enter.

If it exists already, you'll see a notification of that.


7. Now remove the IcedTea plugin, if it has been installed.

Type (copy/paste):[/SIZE][/COLOR]
[COLOR=#0000ff][SIZE=3]sudo apt-get remove icedtea-6-plugin && sudo apt-get remove icedtea-7-plugin

[/SIZE][/COLOR][COLOR=#000000][SIZE=3]Press Enter.

If it's not there to begin with, you'll get a notification of that.

8. Remove an older version of the Java plugin.

Type (copy/paste):[/SIZE][/COLOR]
[COLOR=#0000ff][SIZE=3]rm -v ~/.mozilla/plugins/libnpjp2.so

[/SIZE][/COLOR][COLOR=#000000][SIZE=3]Press Enter.

If it's not there to begin with, you'll get a notification of that.

9. Now you can install the plugin, by creating a symbolic link (you tell Firefox, where the plugin is located).

Type (copy/paste):[/SIZE][/COLOR]
 [COLOR=#0000ff][SIZE=3]ln -s /opt/java/64/jre1.7.0_05/lib/amd64/libnpjp2.so ~/.mozilla/plugins/

[COLOR=#000000]Press Enter.[/COLOR][/SIZE][/COLOR]
 **[COLOR=#000000][SIZE=3][B]Final check**[/SIZE][/COLOR][/B]

 [COLOR=#000000][SIZE=3]10. Now close and restart Firefox. Check whether everything has succeeded. Type in the url bar of Firefox [/SIZE][/COLOR][COLOR=#000000][SIZE=3]***(not in the terminal!)***[/SIZE][/COLOR][COLOR=#000000][SIZE=3]:

[/SIZE][/COLOR][COLOR=#0000ff][SIZE=3]about:plugins[/SIZE][/COLOR][COLOR=#000000][SIZE=3]

Press Enter.

And scroll down, until you see something approximately similar to this:
[/SIZE][/COLOR][COLOR=#0000ff][SIZE=3]Java(TM) Plug-in 1.7.0_05[/SIZE][/COLOR][COLOR=#000000][SIZE=3]

You can also use this website:
[/SIZE][/COLOR][http://java.com/en/download/installed.jsp](http://java.com/en/download/installed.jsp)[COLOR=#000000][SIZE=3]
[/SIZE][/COLOR][COLOR=#000000][SIZE=3][B]
[/B][/SIZE][/COLOR]

---

### Post by PhantomTurtle on 2012-06-22
Looks fine, but you can just use the webupd8 ppa to install Java, its a lot easier. You read the instructions here if you want - [http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html]("http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html"). If you don't want to read it just open terminal and issue the following commands,

```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```
Then you should have Java 7 installed, if you want to check which version is installed run,
```
java -version
```

It should return with some like this,
```
java version "1.7.0_04"
Java(TM) SE Runtime Environment (build 1.7.0_04-b20)
Java HotSpot(TM) Server VM (build 23.0-b21, mixed mode)
```

EDIT: I forgot to mention that I have used this ppa and it is safe and works fine.

---

### Post by sammiev on 2012-06-22
Looks like your looking at this [site]("https://sites.google.com/site/easylinuxtipsproject/java"). I use this setup all the time as I do not like ppa's on my system from other site. If it is you are good to go. :)

---

### Post by oldos2er on 2012-06-23
You could have just posted the link instead of all that text; but yes, I can vouch for [cavsfan's]("http://ubuntuforums.org/member.php?u=889820") site.

---

