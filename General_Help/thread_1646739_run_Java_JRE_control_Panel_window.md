---
title: "run Java JRE control Panel window"
date: 2010-12-16
forum: General Help
---

### Post by snaj on 2010-12-16
I am a bit green in Ubuntu Linux. I installed Java JRE and when I check using Java website I get the confirmation that it is indeed installed. I am unable to run the Java control panel window. Please assist

---

### Post by lykeion on 2010-12-16
How do you mean "unable to run". You should be able to launch Sun Java 6 Plugin Control Panel from System > Preferences.

---

### Post by snaj on 2010-12-16
> **lykeion said:**
> How do you mean "unable to run". You should be able to launch Sun Java 6 Plugin Control Panel from System > Preferences.


When i check on system>preferences, it is not listed in the menu

---

### Post by lykeion on 2010-12-16
Do you have Sun Java installed or is it OpenJDK ? What version does the Java website report that you have? 
Version 6 Update 20 --> OpenJDK
Version 6 Update 22 --> Sun Java

Or you could do this in a terminal (Applications > Accessories > Terminal) with this command:
```
java -version
```Java Control Panel is only available with Sun Java. 

But why exactly do you need the control panel?

---

### Post by Irony on 2010-12-16
Go to **Places > Search for files** and type

```
controlpanel
```

Then add that to your main menu by going to **System > Preferences > Main menu**

---

### Post by snaj on 2010-12-16
> **lykeion said:**
> Do you have Sun Java installed or is it OpenJDK ? What version does the Java website report that you have? 
Version 6 Update 20 --> OpenJDK
Version 6 Update 22 --> Sun Java

Or you could do this in a terminal (Applications > Accessories > Terminal) with this command:
```
java -version
```Java Control Panel is only available with Sun Java. 

But why exactly do you need the control panel?


This is the result i get:

java -version
The program 'java' can be found in the following packages:
 * gcj-4.4-jre-headless
 * openjdk-6-jre-headless
 * cacao
 * gij-4.3
 * jamvm
 * kaffe
Try: sudo apt-get install <selected package>
java: command not found

---

### Post by lykeion on 2010-12-16
Well in first post you stated that you had installed Java, but from that output I can tell you haven't.

Before I'll show you how to install Java I'd like to know why do you need the Java control panel?

---

### Post by snaj on 2010-12-16
> **lykeion said:**
> Well in first post you stated that you had installed Java, but from that output I can tell you haven't.

Before I'll show you how to install Java I'd like to know why do you need the Java control panel?

I am visiting a website that requires Java JRE to be installed because the content in the website. I was in chat with support of that website who asked me to  open java control panel, go settings and click on a clear button

---

### Post by lykeion on 2010-12-16
From a terminal (Applications > Accessories > Terminal) enter these commands to install Sun Java JRE and browser plugin:

1. Enable partner repository (change lucid -> maverick if using that):
```
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"
```
2. Update repostories:
```
sudo apt-get update
```
3. Remove OpenJDK (you can ignore error messages about not being installed):
```
sudo apt-get remove openjdk-6-jre icedtea6-plugin
```
4. Install Sun Java:
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

To make the browser plugin take effect you might have to restart your browser.
You can start Sun Java 6 Plugin Control Panel from System > Preferences.

---

### Post by snaj on 2010-12-16
> **lykeion said:**
> From a terminal (Applications > Accessories > Terminal) enter these commands to install Sun Java JRE and browser plugin:

1. Enable partner repository (change lucid -> maverick if using that):
```
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"
```2. Update repostories:
```
sudo apt-get update
```3. Remove OpenJDK (you can ignore error messages about not being installed):
```
sudo apt-get remove openjdk-6-jre icedtea6-plugin
```4. Install Sun Java:
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```To make the browser plugin take effect you might have to restart your browser.
You can start Sun Java 6 Plugin Control Panel from System > Preferences.

Thank you for your continued support.

I am using ubuntu version 9.10 which i believe is karmic koala.

When i run the commands as you have given them i get:

sudo apt-get install sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate

---

### Post by lykeion on 2010-12-16
Karmic, okay, I was assuming you are using Lucid or Maverick. For Karmic Sun Java should be available in the main repositories.
EDIT: Seems like it's in the multiverse repositories for Karmic.

When you did step 1 to enable partner repositories, did you change to karmic? Else you'll do best to remove that entry from your sources:
System > Administration > Software Sources > Other Software Tab
You'll see a list of the entries in the form like this: [COLOR="Red"]<URI>[/COLOR] [COLOR="Blue"]<distribution>[/COLOR] [COLOR="SeaGreen"]<components>[/COLOR]
Example:
[COLOR="Red"]http://archive.canonical.com/ubuntu[/COLOR] [COLOR="Blue"]karmic[/COLOR] [COLOR="SeaGreen"]partner[/COLOR]

If you have any entry with other distributions than karmic you should uncheck them.

Switch to Ubuntu Software Tab and make sure this line is checked:
Software restricted by copyright or legal issues (multiverse)

Click Close and then Reload.

Then try step 4 again.

---

### Post by snaj on 2010-12-17
I was working behind a proxy and believe it is the one that was blocking me off. I connected using open Internet connection and USING Step 4 installed the plugins successfully.

Much thanks

---

### Post by d0nut on 2011-06-28
> **lykeion said:**
> From a terminal (Applications > Accessories > Terminal) enter these commands to install Sun Java JRE and browser plugin:

1. Enable partner repository (change lucid -> maverick if using that):
```
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"
```
2. Update repostories:
```
sudo apt-get update
```
3. Remove OpenJDK (you can ignore error messages about not being installed):
```
sudo apt-get remove openjdk-6-jre icedtea6-plugin
```
4. Install Sun Java:
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

To make the browser plugin take effect you might have to restart your browser.
You can start Sun Java 6 Plugin Control Panel from System > Preferences.

When i do the above, the finals screen i get in the terminal is the Pacage configuration screen.  it lets me scroll through to see the terms of the agreement but im unsure how to get past this point for it to continue installing.  at the bottome is something that looks like it might be an <Ok> button you'd click on in windows...but obv cant do that in the terminal.

If I try to exit the terminal, it says  *"There is still a process running in this terminal. Closing the terminal will kill it."*
So I'm not sure how to get this process to complete.  **Plz help!**

---

### Post by daftlad on 2011-06-28
> **d0nut said:**
> When i do the above, the finals screen i get in the terminal is the Pacage configuration screen.  it lets me scroll through to see the terms of the agreement but im unsure how to get past this point for it to continue installing.  at the bottome is something that looks like it might be an <Ok> button you'd click on in windows...but obv cant do that in the terminal.

If I try to exit the terminal, it says  *"There is still a process running in this terminal. Closing the terminal will kill it."*
So I'm not sure how to get this process to complete.  **Plz help!**


Just press the tab key until the OK box is highlighted and press enter

---

### Post by d0nut on 2011-06-28
awesome ty

---

### Post by pbanerjee on 2011-12-02
Thanks **lykeion.**[B]
[COLOR=Black][/COLOR][/B]

---

