---
title: "slow firefox..."
date: 2009-09-13
forum: General Help
---

### Post by che guevara93 on 2009-09-13
my firefox 3.5 is a bit slow while i scroll the page, but opera works just fine...
don't tell me just use the opera...
or some other browser

---

### Post by beastrace91 on 2009-09-13
What version of Ubuntu, 32bit or 64bit, and how do you have FF 3.5 installed? (The sheriko branded one from the repos or the binary package from Mozilla's site.)

~Jeff

---

### Post by josechapamendez on 2009-09-13
I had the same problem and it got solved when I Installed the Shiretoko add-on.

---

### Post by che guevara93 on 2009-09-13
i have 32 bit ubuntu...
i've installed my firefox  via some tar.gz file, i think and a some commands in terminal
i can't find shiretoko???

---

### Post by beastrace91 on 2009-09-13
Installing Sheriko -

```
sudo apt-get install firefox-3.5
```

You should always use apt-get to manage your package(s) when ever possible.

~Jeff

---

### Post by che guevara93 on 2009-09-13
> **beastrace91 said:**
> Installing Sheriko -

```
sudo apt-get install firefox-3.5
```You should always use apt-get to manage your package(s) when ever possible.

~Jeff
you want to say that the way of inatallation was wrong!?
omg...
ok tnx...
i'll try it...
btw. the proper way to  install the flash player in firefox is...?

---

### Post by winotree on 2009-09-13
This [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) worked nicely me and I've never, in two years, had a problem using it.  ;)  However, what **beastrace91 **said is true *because apt-get will insure you get any necessary dependencies installed* with your application.

EDIT - run-on sentence

---

### Post by lovinglinux on 2009-09-13
> **che guevara93 said:**
> i have 32 bit ubuntu...
i've installed my firefox  via some tar.gz file, i think and a some commands in terminal
i can't find shiretoko???

That's not the way things should be done. I'm not saying that you shouldn't install files from tar.gz, but that you shouldn't be running commands without knowing what they do and without writing them down, so you can revert any changes later.

Shiretoko is the development codename of Firefox 3.5. It's the same application, but since FF 3.5 is installed side-by-side with 3.0, the developers didn't replaced it's codename, so users can distinguish them after installation. You can install Shiretoko with the command already mentioned or through the Add/Remove manager. But, is strongly recommended that you first uninstall the Firefox 3.5 that you have installed from the tar.gz file. I don't know how to do that, because I don't know exactly which method of installation you have used. 

> **che guevara93 said:**
> you want to say that the way of inatallation was wrong!?
omg...
ok tnx...
i'll try it...
btw. the proper way to  install the flash player in firefox is...?

Not necessarily. The recommended method of installation is always from the repository, for the reasons already mentioned. But there are [several ways of installing applications in Linux](https://help.ubuntu.com/9.04/add-applications/C/index.html) and when a new application version is not available from the repositories, you probably need an alternative method. Most people that installed Firefox 3.5 with alternative methods were patient enough to wait for repository update. 

The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). There is also a detailed explanation of each installation method provided, comparing the most important differences. So maybe it will help you find which method you have used, so you can revert it, before installing Shiretoko. 

Don't follow multiple tutorials of how to install applications without reverting the changes of each previous method first, otherwise you might have conflicts or even loose data if you don't know what you are doing.

The tutorial above will also help you optimize Firefox to solve the issue with the scrolling page.

> **josechapamendez said:**
> I had the same problem and it got solved when I Installed the Shiretoko add-on.

There is no such thing as Shiretoko add-on.

---

### Post by che guevara93 on 2009-09-13
I'm sorry i forgot...
i installed via **ubuntuzilla**...
yeah thats right, i couldn't remember in moment then you mentioned ubuntuzilla and i remembered...

---

### Post by lovinglinux on 2009-09-13
> **che guevara93 said:**
> I'm sorry i forgot...
i installed via **ubuntuzilla**...
yeah thats right, i couldn't remember in moment then you mentioned ubuntuzilla and i remembered...

So, why bother uninstalling it? Ubuntuzilla allows you to easily update to newer versions as soon as they are released. I'm currently using it, since I was unable to compile 3.5.2 or 3.5.3 myself and didn't want to use 3.5.1 due to security reasons. Besides, installing Shiretoko will probably not solve your performance issue. Follow the optimization tips from my tutorial instead.

Additionally, Shiretoko uses a different folder for storing profiles, while the version installed by Ubuntuzilla uses the same profile folder as FF 3.0. Less things to worry about.

Nevertheless, if you decide to remove it, then run the following command:

```
ubuntuzilla.py -a remove -p firefox
```

---

### Post by che guevara93 on 2009-09-13
tnx man!!!
can u give me the link to your tutorial?

---

### Post by lovinglinux on 2009-09-13
> **che guevara93 said:**
> tnx man!!!
can u give me the link to your tutorial?

Check my signature.

---

