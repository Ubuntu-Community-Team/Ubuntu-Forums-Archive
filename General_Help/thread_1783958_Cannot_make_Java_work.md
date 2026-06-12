---
title: "Cannot make Java work"
date: 2011-06-16
forum: General Help
---

### Post by frank cox on 2011-06-16
I have installed and unstalled Sun Java in Natty  and not once has a window popped up from Sun . In terminal it says it installed but when I check in Software Manager the only thing under java as far as installed software is ubuntu restricted.
I have tried it this way:

sudo add-apt-repository ppa:ferramroberto/java
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

And with several other similar methods but I cannot do anything on line such as search for drivers at Dell or HP. If anyone can give me the solution I would be most grateful. It is to the point now where I will have to nuke Natty and go back to 10.04 .

---

### Post by scouser73 on 2011-06-16
Hi Frank, here's the tutorial I use to install the latest version of Java, it does work and is really simple to follow. All that's needed is to copy and paste the commands into the Terminal.

[[COLOR="Red"]**Easy Linux Tips: Install Java**[/COLOR]]("https://sites.google.com/site/easylinuxtipsproject/java")

---

### Post by gandaran on 2011-06-16
> **frank cox said:**
> I have installed and unstalled Sun Java in Natty  and not once has a window popped up from Sun . In terminal it says it installed but when I check in Software Manager the only thing under java as far as installed software is ubuntu restricted.
I have tried it this way:

sudo add-apt-repository ppa:ferramroberto/java
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

And with several other similar methods but I cannot do anything on line such as search for drivers at Dell or HP. If anyone can give me the solution I would be most grateful. It is to the point now where I will have to nuke Natty and go back to 10.04 .
if you have the ubuntu-restricted-extras package installed then you will also have openjdk-java installed and its that one the system is using, having both javas installed either you have to set which one the system uses or just remove the icedtea-plugin then the system will use the sun-java-plugin if its really installed.

---

### Post by frank cox on 2011-06-16
> **gandaran said:**
> if you have the ubuntu-restricted-extras package installed then you will also have openjdk-java installed and its that one the system is using, having both javas installed either you have to set which one the system uses or just remove the icedtea-plugin then the system will use the sun-java-plugin if its really installed.

I went into software manager and typed in iced-tea and removed all the open source java that was there .
Still cannot do anything with Java
Thanks

---

### Post by gandaran on 2011-06-16
> **frank cox said:**
> I went into software manager and typed in iced-tea and removed all the open source java that was there .
Still cannot do anything with Java
Thanks
post the full output of 
```
sudo apt-get install sun-java6-plugin
```
just to check if any problem with install

---

### Post by The Cog on 2011-06-16
What are you trying to do with java?

What does it say when you type this command on the command line?> java -version

---

### Post by frank cox on 2011-06-16
> **scouser73 said:**
> Hi Frank, here's the tutorial I use to install the latest version of Java, it does work and is really simple to follow. All that's needed is to copy and paste the commands into the Terminal.

[[COLOR=Red]**Easy Linux Tips: Install Java**[/COLOR]]("https://sites.google.com/site/easylinuxtipsproject/java")
]
Failed to fetch [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/tiheum/equi/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/tiheum/equi/ubuntu/dists/natty/main/source/Sources)  404  Not Found

---

### Post by frank cox on 2011-06-16
> **The Cog said:**
> What are you trying to do with java?

What does it say when you type this command on the command line?

Download drivers etc. Without Java you cannot use Dell or HP's website.

It says:

java-version: command not found

---

### Post by wildmanne39 on 2011-06-16
> **frank cox said:**
> Download drivers etc. Without Java you cannot use Dell or HP's website.

It says:

java-version: command not found

Hi, what are you trying to do at dell and hp site? there is not much there you can do with ubuntu because all drivers there are for windows. Java should be just a simple install using software center. I use the link to get java and everything I need related to multimedia, it takes care of all of it.
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by frank cox on 2011-06-17
In order to search for drivers you must have Java.
I have tried method after method and not once did I see the window from Sun .

---

### Post by wildmanne39 on 2011-06-17
> **frank cox said:**
> In order to search for drivers you must have Java.
I have tried method after method and not once did I see the window from Sun .Hi, what drivers are you needing ubuntu has almost all drivers already installed and you do not use window drivers on ubuntu, unless as a very last resort with ndiswrapper. That is almost never needed.

---

### Post by wildmanne39 on 2011-06-17
> **frank cox said:**
> In order to search for drivers you must have Java.
I have tried method after method and not once did I see the window from Sun .Hi, what drivers are you needing ubuntu has almost all drivers already installed and you do not use window drivers on ubuntu, unless as a very last resort with ndiswrapper. That is almost never needed. Also look in my previous post and there is a link to install all things including java for multimedia. You have to accept the agreement when the download of java starts from that link.

---

### Post by frank cox on 2011-06-21
I am not stupid , I am aware that dell and hp do not have linux drivers , at least not many.
I use Ubuntu but most of my customers use windows, hence the need to access dell and hp .
I will try the methods you suggested, I use puppy linux at the house because I cannot get broadband there.

---

### Post by frank cox on 2011-06-23
Is there anyone who can help me with this? I am at the point now where I will have to nuke natty . Today I needed a usb driver for an ocv drive on win 98 and I know where to get it but it might as well be on mars .

---

