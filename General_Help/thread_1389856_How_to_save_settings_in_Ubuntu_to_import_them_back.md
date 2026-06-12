---
title: "How to save settings in Ubuntu to import them back on reinstallation"
date: 2010-01-24
forum: General Help
---

### Post by linotechie on 2010-01-24
I've installed the latest version of Ubuntu on one of my systems. I need to wipe it out and replace it with another OS for testing. After a week or so I'll reinstall Ubuntu.

I've customized the looks and feel of Ubuntu desktop and have changed many other settings at a number of places. Is there a way so I can save my settings (like the desktop background, the screen saver settings, colors, terminal window settings including its fonts etc., and others) in a file or a set of files which can then be imported directly when I'd reinstall Ubuntu? Any help would be appreciated. Thanks in advance.

[CENTER]:popcorn:
[/CENTER]

---

### Post by Jackzor on 2010-01-24
Well.. Number one thing would be the home folder. Lol Thats all I know about backing up ubuntu.

---

### Post by Jackzor on 2010-01-24
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

Do plenty of reading about this before you try it. I haven't heard of it I just figured the best thing for you would be to make a custom install disc that has all of your settings already there and I googled it.


This is what I got and I skimmed the page.

---

### Post by linotechie on 2010-01-24
I do not wish to make a custom installation disk since I believe the content and the settings can remain at distant places separately. That way, the customization set would be quite small and can easily be exchanged with others too. The users would also have the option to apply or leave out the specific settings. So I'd prefer to save the settings alone, like via some theme file or something similar for desktop looks etc. Only I don't know how to do that if possible.

I've searched a lot and have seen people directed to the website [http://ubuntuforums.org/](http://ubuntuforums.org/) for solution time and again. Therefore I made one account and posted the problem here. I searched this site also, but a matching question was not found so far.

Exactly where in the "home/" folder are the settings present? It will be insightful if someone can point out. There's no point saving the unnecessary files that would come back unchanged upon reinstallation. And please tell me for sure if the settings are stored nowhere else. Thanks.

---

### Post by Jackzor on 2010-01-24
> **linotechie said:**
> I do not wish to make a custom installation disk since I believe the content and the settings can remain at distant places separately. That way, the customization set would be quite small and can easily be exchanged with others too. The users would also have the option to apply or leave out the specific settings. So I'd prefer to save the settings alone, like via some theme file or something similar for desktop looks etc. Only I don't know how to do that if possible.

I've searched a lot and have seen people directed to the website [http://ubuntuforums.org/](http://ubuntuforums.org/) for solution time and again. Therefore I made one account and posted the problem here. I searched this site also, but a matching question was not found so far.

Exactly where in the "home/" folder are the settings present? It will be insightful if someone can point out. There's no point saving the unnecessary files that would come back unchanged upon reinstallation. And please tell me for sure if the settings are stored nowhere else. Thanks.

Well Your desktop layout.. I have no idea. But your themes you can just save them the way that are and back up that theme file. FOr example go to System/Preferences/Appearances and save the current theme

---

### Post by nmccrina on 2010-01-24
I would just save EVERYTHING in your home folder. All your settings are in the hidden files and folders (the ones that begin with a dot), but rather than trying to find which setting is in which file grabbing the lot of them would be simpler. Then on the reinstall delete the new stuff and put everything back.

---

### Post by linotechie on 2010-01-24
Thanks to both of you for this bit of information. Now I'll be able to save my theme and my other settings. I'm quite new to Linux and Ubuntu and have never installed any software on it. I've been using it since last 3 days. Your instructions seem straightforward and easy. I'll try them out as soon as I get to the system :)

---

### Post by Ginsu543 on 2010-01-24
To make this process easier, it is helpful to keep your /home folder on a separate partition from your / folder. When you reinstall your OS, you can simply tell the partitioning program in the installation process not to format the /home partition. The installer will then install the new operating system with the old /home folder intact. This way you don't have to copy/paste everything back from your /home folder.

PS: Having said all this, I *still* keep a copy of my /home folder saved on another hard drive, just in case. :P

---

### Post by Jackzor on 2010-01-24
> **linotechie said:**
> Thanks to both of you for this bit of information. Now I'll be able to save my theme and my other settings. I'm quite new to Linux and Ubuntu and have never installed any software on it. I've been using it since last 3 days. Your instructions seem straightforward and easy. I'll try them out as soon as I get to the system :)

To aviod this completely.. Depending on your reasons for testing the "other os" you should Check into Virtualbox for ubuntu.

If you need a link or anything post back and I'll get it for you or you can just google it.

Just in case you do not already know what VBox is, it gives you the ability to install a complete Operating system inside what you already have for free. And it will dedicate some of your ram and processing power to the other os and let you test/play around with something else inside of ubuntu without having to format or anything. It will create a virtual harddrive for you and everything.

---

### Post by Jackzor on 2010-01-24
> **Ginsu543 said:**
> To make this process easier, it is helpful to keep your /home folder on a separate partition from your / folder. When you reinstall your OS, you can simply tell the partitioning program in the installation process not to format the /home partition. The installer will then install the new operating system with the old /home folder intact. This way you don't have to copy/paste everything back from your /home folder.

PS: Having said all this, I *still* keep a copy of my /home folder saved on another hard drive, just in case. :P

This is not a good idea from what I have heard if you are installing different linux distros that will use the same home folder.

---

### Post by linotechie on 2010-01-25
I can understand an additional backup of the settings is always useful. So, how would the installer know that my "home/" folder is in another partition during a new installation? How would it pick it up automatically during the new install? And won't it overwrite it? Thanks.

@Jackzor Dear Jackzor, I'm trying out Ubuntu as a guest OS on one of the Windows XP SP3 systems. And yesterday I heard the new version Helena of Mint has codecs built-in (this is the new OS I'm gonna try out). Ubuntu doesn't play my multimedia files and asks me to install software for them - a process I read at so many places not suitable for the beginners like me. I'll check Mint out and if it offers all the functionality plus the built-in codecs, I'll choose that as my Linux distro instead. But if Ubuntu was better, I'd return to it. That's why I thought of saving the settings. BTW, thanks for the suggestion.

---

### Post by Ginsu543 on 2010-01-25
You're right, I hadn't thought of that. I guess the safest way to try different OSes is to install them on a separate hard drive. That way, you don't have the two OSes accessing the same /home folder. That is the way I have my machine set up, so it didn't even enter my mind that the two OSes will be accessing the same /home folder.

Having a separate /home folder is still a good idea if you are reinstalling or upgrading the same distro.

---

### Post by linotechie on 2010-01-25
@Ginsu543 Can I change the location of the "home/" folder once the OS is installed? If so, how? Your previous suggestion is still useful to my case since I'd be installing only one Linux OS on that hard drive at a time. Thanks.

---

### Post by Jackzor on 2010-01-25
> **linotechie said:**
> @Ginsu543 Can I change the location of the "home/" folder once the OS is installed? If so, how? Your previous suggestion is still useful to my case since I'd be installing only one Linux OS on that hard drive at a time. Thanks.

Installing the codecs and all the things you need to play your media is very simple. All you will need to do is copy paste command into the terminal. It may look scary but you really don't even have to read it. Lol.

Infact someone correct me if I'm wrong.. He can open the ubuntu software center and search ubuntu-restricted-extras and install that?

---

### Post by linotechie on 2010-01-25
I don't like to enter a command I don't understand what it's doing. Your suggestion was meant to be helpful but unfortunately it's not something suitable for me. I'll try to find the meaning of the commands and once I understand them properly, then only I'll enter them. Thank you for the encouragement. I've posted a question on how to install software at the link below. Hope someone could guide me.

[http://ubuntuforums.org/showthread.php?p=8723909#post8723909](http://ubuntuforums.org/showthread.php?p=8723909#post8723909)

---

### Post by Darktrax on 2010-09-13
Simply saving *everything* is likely going to cause trouble.
There are many hidden files and whole directory structures in your home folder that contain scripts and settings that may well be inappropriate for the "new" version.

I always keep a partition for "home" data that is separate, but I don't name it "/home" - I call it something else. I allow any installation to keep its /home in its own root directory. The "other" one can be accessed from any new version installation, or even a totally different distro, without upsetting the many configurations that would be mangled by simply overwriting.

That said, it seems easier to copy across email archives and browser settings etc. from a Windows installation that a previous Ubuntu. Try going from 8.10 straight to a 10.04 on another partition! There *might* be an easy recipe, but I don't yet know it.

---

### Post by linotechie on 2010-09-13
Hmmm... I was so confused and frustrated by the software installation and Internet connecting processes (many attempts failed) I gave up on Linux for some time now. After some time (a few months) I'll come back to try it again. The main problem is one of the inability to download the software installation file on one computer and then install it on another which is offline. I consider this redundant having to download something every time it needs to be installed. Why cannot I save something I've downloaded for future use? Is it sane to ask someone with a 5 KBPS connection to download half a GB of data every time a piece of big software need be installed? Anyway that was off-topic. Thanks for the suggestion. I'll try to make use of this thread in future when I'll be trying Ubuntu again.

[CENTER]):P
[/CENTER]

---

### Post by theozzlives on 2010-09-13
> **linotechie said:**
> Hmmm... I was so confused and frustrated by the software installation and Internet connecting processes (many attempts failed) I gave up on Linux for some time now. After some time (a few months) I'll come back to try it again. The main problem is one of the inability to download the software installation file on one computer and then install it on another which is offline. I consider this redundant having to download something every time it needs to be installed. Why cannot I save something I've downloaded for future use? Is it sane to ask someone with a 5 KBPS connection to download half a GB of data every time a piece of big software need be installed? Anyway that was off-topic. Thanks for the suggestion. I'll try to make use of this thread in future when I'll be trying Ubuntu again.

[CENTER]):P
[/CENTER]


I don't know where you get 5Kb/sec from. Modems ages ago were 2400 bits/sec, then went to 14.4 Kb/sec. now modems are 56K. That's all outdated! Broadband is VERY affordable, mine runs at 5 MB/sec. So it's not unreasonable that you get with the rest of the world and go broadband.

It's also easy to keep your settings, just make a separate /home partition. I've used mine from 7.10 to 10.04 and everything worked fine.

---

### Post by oldfred on 2010-09-13
this is where everything is downloaded.

Location of downloaded debs
/var/cache/apt/archives/

You may want to look at aptonCd
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

APTonCD is a tool with a graphical interface which allows you to create  one or more CDs or DVDs (you choose the type of media) with all of the  packages you've downloaded via APT-GET or APTITUDE, creating a removable repository that you can use on other computers.

---

### Post by linotechie on 2010-09-13
@theozzlives Yes braodband is the trend. I do have that connection at the office, but there are few places where all one can get is a mobile modem connection and that's what I have at home. I wanted to download the software-installer from the office computer and use it to install the apps at the home computer. Your suggestion to get a broadband is appreciated, but it's simply not available at the location of my home; so not a fault on my side.

@oldfred Wow, now that's something that could really be helpful. Why didn't you find this thread earlier? ;) I'll sure try this method on my next visit to Ubuntu. SourceForge is already one of my favorite Open Source sites (though for an entirely different reason - It features loads of Windows software and their source code, extremely useful). Thanks for your sweet suggestion. :D

---

