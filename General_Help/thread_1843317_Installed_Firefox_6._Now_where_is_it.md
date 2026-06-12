---
title: "Installed Firefox 6. Now where is it?"
date: 2011-09-13
forum: General Help
---

### Post by Advait on 2011-09-13
Hi All,

See attached pic. Yesterday I installed FireFox 6 on my 10.10 machine. I was using it and it worked fine. But today when I try to execute double click and OPEN the "firefox-bin" file in the FireFox 6 folder nothing happens. When I click on the FireFox shortcut (top left) it goes for FF 3.6.22. How can I execute FF 6? Do I have to uninstall 3.6? When I go to Applications -> Internet the FF link there starts up version 3.6, not version 6. 

Thanks,

Tom

---

### Post by sanderd17 on 2011-09-13
What output do you get if you run the firefox-bin file in the terminal?

---

### Post by mike555 on 2011-09-13
You should have installed Firefox through package manager after adding PPA for mozilla ....   [https://launchpad.net/~mozillateam/+archive/firefox-stable](https://launchpad.net/~mozillateam/+archive/firefox-stable)

---

### Post by SoFl W on 2011-09-13
Which version runs when you type "Firefox" from the command line? (Terminal)  As Mike said above, you should have added the PPA.

---

### Post by haqking on 2011-09-13
> **mike555 said:**
> You should have installed Firefox through package manager after adding PPA for mozilla ....   [https://launchpad.net/~mozillateam/+archive/firefox-stable]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable")

+1

also when in doubt
```

whereis <appname>
```

willl show all possible instances of the app and where they are

```
which <appname>
```

will show the one used by defualt

---

### Post by mikewhatever on 2011-09-13
It looks like you've just downloaded the .tar.bz from Mozilla and extracted it, which makes the 'I installed FireFox 6' extremely misleading.
I'd second the PPA method as mentioned above.

---

### Post by Advait on 2011-09-13
> **sanderd17 said:**
> What output do you get if you run the firefox-bin file in the terminal?

OK, I did that. Just says "command not found". Any ideas? Please remember I know almost nothing about the command line. Thanks!

---

### Post by Advait on 2011-09-13
> **SoFl W said:**
> Which version runs when you type "Firefox" from the command line? (Terminal)  As Mike said above, you should have added the PPA.

"Firefox" on the command line brings up FF version 3.6.22, not version 6. Any ideas? Thanks!

---

### Post by Advait on 2011-09-13
> **mikewhatever said:**
> It looks like you've just downloaded the .tar.bz from Mozilla and extracted it, which makes the 'I installed FireFox 6' extremely misleading.
I'd second the PPA method as mentioned above.

Actually I definitely did install FireFox 6. It ran right after install and when I checked the version it was definitely "6.02". And the FF screen looked very different and similar to my Windows FF 6.02. Please advise how to locate and run 6.02 version. Thanks!

---

### Post by Advait on 2011-09-13
> **mike555 said:**
> You should have installed Firefox through package manager after adding PPA for mozilla ....   [https://launchpad.net/~mozillateam/+archive/firefox-stable]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable")

OK, I tried to install using ppa but it involves the command line. I do not know how to use the command line. Here's part of what I got: Any ideas? Thanks

Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                                                                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                                                                               
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                                                                                     
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                                                                               
  404  Not Found
Fetched 65.4kB in 9s (6,878B/s)                                                                                                        
W: Failed to fetch [http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
advait@advait-laptop:~$

---

### Post by Advait on 2011-09-13
> **SoFl W said:**
> Which version runs when you type "Firefox" from the command line? (Terminal)  As Mike said above, you should have added the PPA.

OK, can you give me step by step instructions on how to do this? Please remember I don't know how to use the command line. Thanks

BTW, I have already installed FF 6.02. I know it's installed because I used it and checked the version #. Please, how can I find it? Please remember I do not know how to navigate directories using the command line. Way too complicated!

---

### Post by mikewhatever on 2011-09-14
Since you insist on having installed it, so be it. According to the screenshot, it's in your home folder, and you can create a launcher. Right click on the desktop (or panel), select 'Create Launcher':

```
Type: Application

Name: Firefox6

Command: "/home/advait/FireFox 6/firefox/firefox"

Comment: 
```

---

### Post by psrdotcom on 2011-09-14
You have to replace the existing firefox executable with the extracted firefox executable.

To do the please do
$ sudo apt-get remove firefox

after that you can extract and run the ./install.sh 

Firefox Folder Location:
It will located in /etc/firefox-6.x .. you can find the firefox folder ..

---

### Post by uRock on 2011-09-14
To install via CLI do the following,

Add the PPA with,```
sudo add-apt-repository ppa:mozillateam/firefox-stable
```Tell the system to search for updates, then to install them with,```
sudo apt-get update && sudo apt-get upgrade
```Or you can skip this second command by opening and running Update Manager.

---

### Post by sanderd17 on 2011-09-14
> **Advait said:**
> OK, I did that. Just says "command not found". Any ideas? Please remember I know almost nothing about the command line. Thanks!

Sorry, I though you had some CLI experience.

You should first Change your Directory (cd) to where the firefox-bin file is

```

cd /home/user/path/to/the/firefox/directory

```

Afterwards, you can run the file with

```

./firefox-bin

```

---

### Post by Advait on 2011-09-14
> **psrdotcom said:**
> You have to replace the existing firefox executable with the extracted firefox executable.

To do the please do
$ sudo apt-get remove firefox

after that you can extract and run the ./install.sh 

Firefox Folder Location:
It will located in /etc/firefox-6.x .. you can find the firefox folder ..

Which directory do I need to be in when I run "sudo apt-get remove firefox"? Doesn't matter? Thanks.

---

### Post by Advait on 2011-09-14
> **psrdotcom said:**
> You have to replace the existing firefox executable with the extracted firefox executable.

To do the please do
$ sudo apt-get remove firefox

after that you can extract and run the ./install.sh 

Firefox Folder Location:
It will located in /etc/firefox-6.x .. you can find the firefox folder ..

I don't understand "after that you can extract and run the ./install.sh". What do you mean by "extract"? What do I "extract" and how do I do it? What commands do I need to run? Thanks.

---

### Post by Advait on 2011-09-14
> **psrdotcom said:**
> You have to replace the existing firefox executable with the extracted firefox executable.

To do the please do
$ sudo apt-get remove firefox

after that you can extract and run the ./install.sh 

Firefox Folder Location:
It will located in /etc/firefox-6.x .. you can find the firefox folder ..

Is there any way I can get my FF 6.02 running without all this very confusing command line stuff?

---

### Post by 3rdalbum on 2011-09-14
> **Advait said:**
> Is there any way I can get my FF 6.02 running without all this very confusing command line stuff?

Find the "firefox" file inside the folder you downloaded.
Open a terminal and just drag that file into the terminal. Click on the terminal window again to bring it to the front, and press Enter.

That should do it. If there's any error messages, please post them here.

---

### Post by Advait on 2011-09-14
> **3rdalbum said:**
> Find the "firefox" file inside the folder you downloaded.
Open a terminal and just drag that file into the terminal. Click on the terminal window again to bring it to the front, and press Enter.

That should do it. If there's any error messages, please post them here.

Yay! It worked! Thanks! I nominate you for "Ubuntian of the Day".

It brought up FF6.02. Perfect. Anyway to automate this procedure so I don't have to manually drag the file to a terminal window every time I want to run FF 6.02?

Now how do I delete FF 3.6.22 without also deleting FF 6.02? 

Cheers!

---

### Post by sanderd17 on 2011-09-14
Maybe you should read a bit about command line: [Here]("http://linuxcommand.org") you have all basics you need.

For the rest, just know that launchers use a command like one you would type in your terminal. If you edit a launcher, you will see that command.

---

### Post by Advait on 2011-09-14
> **sanderd17 said:**
> Maybe you should read a bit about command line: [Here]("http://linuxcommand.org") you have all basics you need.

For the rest, just know that launchers use a command like one you would type in your terminal. If you edit a launcher, you will see that command.

I've been using Ubuntu for about a year now. I rarely have to use the command line; only when I'm installing or upgrading some program. If I read up on the command line it would definitely be totally forgotten the next time I had to use the command line (and memorizing arcane commands is not my idea of fun). In terms of wider adoption by the average user, every time a user *has* to use the command line to do something, that represents a failure in Ubuntu, IMHO. The command line is great and I really admire people who know how to use it. But as long as basic actions *require* usage of the command line, Ubuntu will never be widely adopted. But maybe the Ubuntu community is not interested in wider adoption; I don't know. I would have totally abandoned Ubuntu after 3 days were it not for the great Ubuntu forums. I *need* Ubuntu in order to securely browse to my financial accounts. That's the only reason I put myself thru the occasional torture of spending hours trying to figure out how to do something in Ubuntu that would take minutes in Windows. Well, I actually like learning this techie stuff, but I simply don't have time for it. Too many other priorities! Thank goodness for the great people on the Ubuntu forums! You've always been patient with my many newbie questions. Thanks!

Tom (feeling secure)

---

### Post by haqking on 2011-09-14
> **Advait said:**
> I've been using Ubuntu for about a year now. I rarely have to use the command line; only when I'm installing or upgrading some program. If I read up on the command line it would definitely be totally forgotten the next time I had to use the command line (and memorizing arcane commands is not my idea of fun). **In terms of wider adoption by the average user, every time a user *has* to use the command line to do something, that represents a failure in Ubuntu, IMHO. The command line is great and I really admire people who know how to use it. But as long as basic actions *require* usage of the command line, Ubuntu will never be widely adopted**. But maybe the Ubuntu community is not interested in wider adoption; I don't know. I would have totally abandoned Ubuntu after 3 days were it not for the great Ubuntu forums. I *need* Ubuntu in order to securely browse to my financial accounts. That's the only reason I put myself thru the occasional torture of spending hours trying to figure out how to do something in Ubuntu that would take minutes in Windows. Well, I actually like learning this techie stuff, but I simply don't have time for it. Too many other priorities! Thank goodness for the great people on the Ubuntu forums! You've always been patient with my many newbie questions. Thanks!

Tom (feeling secure)

The command line exists because it remains the same across different versions of a Distro.  For example in 8.04, 9.04, 11.04, Xubunut,lubunut,Kubuntu all the interfaces are different and so steps for doing something change.

Terminal you type the same thing in and works the same (for the most part)

In ubuntu

sudo apt-get install packagename

is different for GUI in each interface or steps to get there.

Ubuntu and other distros would certainly fail if they removed the terminal or need to use it.  Linux is a console based OS with GUI added on, GUI is a luxury, CLI is where the power and real tools are.

```
ls 
``````
cat /proc/cpuinfo
``````
whereis appname
``````
which appname
```
etc etc

is the same in Unix or Linux whatever the distro pretty much, try achieveing all those with exactlty the same steps in every desktop environment/GUI

---

### Post by uRock on 2011-09-14
> **Advait said:**
> I've been using Ubuntu for about a year now. I rarely have to use the command line; only when I'm installing or upgrading some program. If I read up on the command line it would definitely be totally forgotten the next time I had to use the command line (and memorizing arcane commands is not my idea of fun). In terms of wider adoption by the average user, every time a user *has* to use the command line to do something, that represents a failure in Ubuntu, IMHO. The command line is great and I really admire people who know how to use it. But as long as basic actions *require* usage of the command line, Ubuntu will never be widely adopted. But maybe the Ubuntu community is not interested in wider adoption; I don't know. I would have totally abandoned Ubuntu after 3 days were it not for the great Ubuntu forums. I *need* Ubuntu in order to securely browse to my financial accounts. That's the only reason I put myself thru the occasional torture of spending hours trying to figure out how to do something in Ubuntu that would take minutes in Windows. Well, I actually like learning this techie stuff, but I simply don't have time for it. Too many other priorities! Thank goodness for the great people on the Ubuntu forums! You've always been patient with my many newbie questions. Thanks!

Tom (feeling secure)

The firefox in your current repo gets security patches.

---

### Post by sanderd17 on 2011-09-14
As said above, all packages in the repos get security updates, so nobody has to install something that isn't in the software center.

If you do want to install something in the software center, please allow us to use the command line instead of taking screenshots (which cost a lot of work and bandwidth) and afterwards noticing that you use another interface and that our screenshots are worthless for your.

Using Linux, wanting to do more advanced stuff, and not wanting to use the command line? That's just like changing from DOS to win95 and not wanting to use the mouse.

Really, you don't need the command line for most things (including this one), but it's just a lot easier.

---

