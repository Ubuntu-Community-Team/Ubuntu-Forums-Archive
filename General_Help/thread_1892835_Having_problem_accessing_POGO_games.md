---
title: "Having problem accessing POGO games"
date: 2011-12-08
forum: General Help
---

### Post by kelpie_canada on 2011-12-08
I can log into POGO and access the home page but when I try to access any of the games I get the following error message.

The connection was reset. The connection to the server was reset while the page was loading.

It doesn't matter which game I try to open I get the same message.

Can someone help me??

---

### Post by bollix47 on 2011-12-08
Pogo games use a lot of java and flash.

Do you have ubuntu-restricted-extras installed?

If not you can add them through Synaptic Package Manager or via terminal using the command:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by killermist on 2011-12-08
Has it worked before, and this is a recent problem (possibly a server issue on their end), or is this something you've never gotten to work?

---

### Post by sammiev on 2011-12-08
Works great here. I use [JRE Java]("http://sites.google.com/site/easylinuxtipsproject/java") and the latest flash.

---

### Post by kelpie_canada on 2011-12-09
I checked and it is already installed.

---

### Post by kelpie_canada on 2011-12-09
> **killermist said:**
> Has it worked before, and this is a recent problem (possibly a server issue on their end), or is this something you've never gotten to work?

It was working before. Although when I upgraded to Lucid 10.04 the last time I lost the ability to access a lot of games. But this latest problem is recent.

---

### Post by kelpie_canada on 2011-12-09
> **sammiev said:**
> Works great here. I use [JRE Java]("http://sites.google.com/site/easylinuxtipsproject/java") and the latest flash.

JRE Java is already installed and I checked to see if I had the latest flash and I do. I don't know what else to check.

---

### Post by sammiev on 2011-12-09
Just tried it here on 2 laptops. Both are having troubles today with pogo. Check java and flash, both are the latest. Will look into it again .

---

### Post by sammiev on 2011-12-09
> **kelpie_canada said:**
> JRE Java is already installed and I checked to see if I had the latest flash and I do. I don't know what else to check.

OK, all works fine. My troubles was that I forgot to drop my firewall with pogo.

---

### Post by kelpie_canada on 2011-12-09
> **sammiev said:**
> OK, all works fine. My troubles was that I forgot to drop my firewall with pogo.

How do you drop the firewall?

---

### Post by sammiev on 2011-12-09
If you never activated your firewall then no changes are required. I have my outgoing set to deny and I choose which ports will be opened. As default all outgoing is open.

---

### Post by kelpie_canada on 2011-12-10
> **sammiev said:**
> If you never activated your firewall then no changes are required. I have my outgoing set to deny and I choose which ports will be opened. As default all outgoing is open.

I don't know if the firewall has been activated. How do I find out and how do I change it if it is?

---

### Post by sammiev on 2011-12-10
I attached a screen shot of my firewall running. To disable you just have to switch it to off so it allows outgoing.

---

### Post by kelpie_canada on 2011-12-10
> **sammiev said:**
> I attached a screen shot of my firewall running. To disable you just have to switch it to off so it allows outgoing.

Where do I go to find the firewall? Is it in Firefox or in my computer. I am not very computer literate.

---

### Post by sammiev on 2011-12-10
I would say you do not have any special outgoing settings as you would of had to add them yourself. Here is how I edit mime but you will likely not have this screen if you never activated it in the first place. I would say your problem is with your flash or jre java. What verion of flash and jre java are you using. Please leave a screen shot. 

My menu for my firewall found in systems.

---

### Post by kelpie_canada on 2011-12-11
> **sammiev said:**
> I would say you do not have any special outgoing settings as you would of had to add them yourself. Here is how I edit mime but you will likely not have this screen if you never activated it in the first place. I would say your problem is with your flash or jre java. What verion of flash and jre java are you using. Please leave a screen shot. 

My menu for my firewall found in systems.

I know that I am being bothersome. I took a screen shot of both Java and Adobe but I am not sure how to post them here.

---

### Post by sammiev on 2011-12-11
Press New Reply and select the paper clip. Find the attachment and hit upload. :) Then just post over reply. Are you using adblock plus or no script?

---

### Post by kelpie_canada on 2011-12-11
Are you using adblock plus or no script? I don't know what this is. I am going to be 60 on my next birthday and ubuntu is my first computer. But here are the screen shots.

[ATTACH]208920[/ATTACH]

[ATTACH]208921[/ATTACH]

---

### Post by sammiev on 2011-12-11
> **kelpie_canada said:**
> Are you using adblock plus or no script? I don't know what this is. I am going to be 60 on my next birthday and ubuntu is my first computer. But here are the screen shots.

[ATTACH]208920[/ATTACH]

[ATTACH]208921[/ATTACH]

Your JRE java is way tooooo old. 

Try [this]("http://sites.google.com/site/easylinuxtipsproject/java"). :)

---

### Post by kelpie_canada on 2011-12-13
> **sammiev said:**
> Your JRE java is way tooooo old. 

Try [this]("http://sites.google.com/site/easylinuxtipsproject/java"). :)

I went to the java page and followed the instructions. I deleted the old plug-in and downloaded the new version but when I go to the terminal and follow the instructions my computer just keeps repeating no such file exists. Now that I have downloaded the new version how do I get the computer to execute and install it?

---

### Post by sammiev on 2011-12-13
Which version are you after, the 32bit or 64bit? Also Do Not download the RPM one. Then after you download it follow the instructions I provided in my last post. :)

---

### Post by kelpie_canada on 2011-12-18
I think my system is 64bit. What do I do with the download?[ATTACH]209326[/ATTACH]

---

### Post by sammiev on 2011-12-18
Go into your system info screen and it will tell you if you installed the 64 bit system then and if so place the saved file in your Download directory and follow the instructions I supplied in the other post. If you have the 32 bit OS then download the 32 bit version and do the same.

Updated: Noticed the newer version of java so I downloaded and used the instructions I posted in an earlier post and it works great. The instructions are for java Version 6 Update 30. Not Java 7.

---

### Post by kelpie_canada on 2011-12-19
Is this the place that I need to be? I am not sure if it is 32 or 64bit it doesn't really say much. Where do I find my Download Directory?

[ATTACH]209351[/ATTACH]

---

### Post by sammiev on 2011-12-19
You are running 10.04 and have 1 Gib of memory, so likely you are running 32 bit but that's just a guess. Go into system settings and select system info.

In Terminal type "cd Downloads" to switch directories.

---

