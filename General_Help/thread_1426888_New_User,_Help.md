---
title: "New User, Help?"
date: 2010-03-10
forum: General Help
---

### Post by KasRoth on 2010-03-10
I'm an extremely green user here. And I just got off a call with the tech support that lasted over an hour and left me wanting to wipe this new mini and buy another OS. I want to give this a chance, but I like having a lot of control over my system. I can't seem to download firefox or update their version at all. 

I understand coding and programming to a point, but the whole OS seems so unfriendly to me at this point. 

Basically I want to be able to download whatever I want to the desktop and update my firefox via the help menu. It's not my complete use computer, it is just for classes and notes. I'm also having a horrible time getting it to run Matlab for school.

Any help at all would be appreciated. I saw the "Updating firefox" post, but I couldn't get the coding to read properly, it wouldn't recognize what "deb" command is.

---

### Post by Ozymandias_117 on 2010-03-10
> **KasRoth said:**
> I'm an extremely green user here. And I just got off a call with the tech support that lasted over an hour and left me wanting to wipe this new mini and buy another OS.

Are you saying you bought a new mini with Ubuntu already on it? Or you're interested in trying Ubuntu.

> **KasRoth said:**
> Basically I want to be able to download whatever I want to the desktop and update my firefox via the help menu. It's not my complete use computer, it is just for classes and notes. I'm also having a horrible time getting it to run Matlab for school.

I don't understand what you mean by "I want to be able to download whatever I want to the desktop"

If Firefox 3.5.8 really isn't good enough and you need 3.7 you can open a terminal and type 
```
sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
sudo apt-get update
sudo apt-get install firefox-3.7
```
This will give you the most bleeding edge release of Firefox, but, it may be buggy. Unless you have a reason you need it, you would be better sticking with the stable releases. (Which you get by either going to System -> Administration -> Update Manager or typing "sudo apt-get dist-upgrade" from a terminal.

Sorry, no idea about Matlab... You could try Wine.

---

### Post by KasRoth on 2010-03-10
Thanks. Yes, I got the "Hefty" or "Hardy" edition on my laptop already. I'm used to a certain level of control with my desktop and I'm just a bit irked by the greyout on the "check for updates" in firefox. Thanks for the code lists. It's more for future reference on my part. 

I got the mini just for taking notes in my courses alongside the graph work. It came loaded with a lot more than I expected and it's taking longer for me to get it set up just the way I like. So far, it's not so bad, I need to twiddle with it more.

---

### Post by snowpine on 2010-03-10
Hi Kasroth, the Dell Minis come preinstalled with a special "Dellbuntu" remix that is kind of like a "lite" version of Ubuntu. If you are a "power user" and you have a Dell Mini 9 or Mini 10v, you might prefer running the regular version of Ubuntu 9.10 (the current version) following the tutorials at [http://ubuntumini.com](http://ubuntumini.com) (8.04 after all is the April 2008 release, which is why its applications are a bit outdated.)

I strongly recommend learning about the concept of a "repository". Rather than upgrading applications individually (such as through the Firefox Help menu), you upgrade all of your applications at once using the "package manager." This ensures that you get only the most stable and trusted software for your Ubuntu release, from a central software source (repository). In my opinion, package management is the very best feature of Linux. :)

Good luck, and let me know if you have any questions about the Dell Mini!

ps Matlab is commercial software and I would hope its price includes technical support to get it installed and running on your new computer. ;)

---

### Post by KasRoth on 2010-03-10
> **snowpine said:**
> 

I strongly recommend learning about the concept of a "repository". Rather than upgrading applications individually (such as through the Firefox Help menu), you upgrade all of your applications at once using the "package manager." This ensures that you get only the most stable and trusted software for your Ubuntu release, from a central software source (repository). In my opinion, package management is the very best feature of Linux. :)

Good luck, and let me know if you have any questions about the Dell Mini!

ps Matlab is commercial software and I would hope its price includes technical support to get it installed and running on your new computer. ;)

Yes, my Dell mini came loaded with ubuntu. I was... extremely unprepared for it, as I was expecting Windows 7.  I currently have Vista on my larger laptop and it didn't take me long to turn off all the securities and make it do exactly what I want to. 

This OS is proving to be a challenge for me to adjust exactly the way I want it. 

Do you have any good links to this "repository"? I've always done most all of my updates selectively and by hand. I just am a control freak and love to be able to dictate exactly what I put on and do with my computer at any given time. I've been reading sites for most of the day and just find myself confused at this point. 

Well matlab I get access to for free for my courses in college (Free being the moot point, considering the course price). I just need to get it to download properly. 

I admit that I wasn't a fan of Linux the first time I tried it, I found windows to be more intuitive, though I'm willing to give it another shot.

---

### Post by snowpine on 2010-03-11
> **KasRoth said:**
> Do you have any good links to this "repository"? I've always done most all of my updates selectively and by hand. I just am a control freak and love to be able to dictate exactly what I put on and do with my computer at any given time. I've been reading sites for most of the day and just find myself confused at this point. 

No problem, to update your system with the latest versions from the 8.04 repository, just go to System->Administration->Update Manager. 

And here are good how-tos on installing new applications from the repository (and other trusted sources):

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

(please note that because you have the Dell version instead of "regular" Ubuntu, some of the specific details might be a little different)

Finally a few good resources for further reading:

[https://help.ubuntu.com/community/DellMini9](https://help.ubuntu.com/community/DellMini9)
[http://mydellmini.com](http://mydellmini.com)
[http://ubuntumini.com](http://ubuntumini.com)

ps if you decide you don't like Ubuntu, certain Dell Mini models are capable of running Windows or Mac OSX; see the mydellmini forums/guides for more info.

---

