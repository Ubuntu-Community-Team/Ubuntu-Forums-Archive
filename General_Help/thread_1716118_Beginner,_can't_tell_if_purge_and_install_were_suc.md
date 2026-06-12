---
title: "Beginner, can't tell if purge and install were successful"
date: 2011-03-28
forum: General Help
---

### Post by everything is funny on 2011-03-28
...and if not what to do. I am very new to ubuntu with little command line-type experience. I'm just a user with a laptop on my dorm network, no servers or modems to set up. Running 10.10 64-bit.

So first I wanted to purge firestarter after checking it out and going with ufw. I entered:
```
sudo apt-get remove --purge firestarter
```After that I get:
```
(Reading database ... 118090 files and directories currently installed.)
Removing firestarter ...
Purging configuration files for firestarter ...
Processing triggers for ureadahead ...
Processing triggers for gconf2 ...
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...

```And I don't think terminal showed any more progress after that. I probably should have stopped there and asked but I decided to continue configuring ufw and iptables without waiting, so I don't know if any new developments showed up in the middle of my later configuring (I am slow to understand what code means what as you can see). So my first question is what happened there and what do I need to do?

After deciding ufw and iptables were working well enough I tried to install IPblock using [these instructions]("http://ubuntuforums.org/showthread.php?t=530183"). After entering the command to add the iplist repository, I tried importing the key like described in the link's first option. That didn't seem to work, as I got this:
```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com C6E3D9O5C8BCD56BBO2E6EOB394563111O8B243F
gpg: "C6E3D9O5C8BCD56BBO2E6EOB394563111O8B243F" not a key ID: skipping
```So I went with the link's second route, saving the public key on my desktop and importing it with Software Sources. That seemed to work so I input
```
sudo apt-get update
```Which resulted in plenty of links that I'm guessing you don't need to see, but ended with: 
```
Get:5 http://ppa.launchpad.net maverick/main amd64 Packages [588B]
Fetched 41.3kB in 1s (39.0kB/s)
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 39456311108B243F

```I'm not quite sure what happened but I did something with SS, perhaps this time I imported the public key correctly as I tried updating again and got the same reply minus the GPG error. So then I try installing and after entering "yes" I get:
```
Get:1 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main tzdata all 2011d-0ubuntu0.10.10 [683kB]
Get:2 http://ppa.launchpad.net/ssakar/ppa/ubuntu/ maverick/main iplist amd64 0.29-0ubuntu1 [324kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main openjdk-6-jre-lib all 6b20-1.9.7-0ubuntu1 [6,199kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main tzdata-java all 2011d-0ubuntu0.10.10 [146kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ maverick/main java-common all 0.38 [66.0kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main openjdk-6-jre-headless amd64 6b20-1.9.7-0ubuntu1 [25.6MB]
36% [6 openjdk-6-jre-headless 6,316kB/25.6MB 24%]                   456kB/s 52s^C

```
 And that's it. So the second question is, is this installed correctly and if not what should I do?

I'm sorry if there's too much detail I just don't know what's important and what isn't at this point. Help is much appreciated, thanks.

---

### Post by garvinrick4 on 2011-03-28
```
sudo apt-get install aptitude
```
```
aptitude show firestarter
```
Will show package and if installed:

When you remove something
```
sudo apt-get remove packagename
```
or
```
sudo apt-get purge packagename
```

The purge removes config files also.
and removes package.

If you install a ppa in your sources.list must have a key also.
or get error. Can see keys installed in Software Sources in GUI
```
sudo dpkg --configure -a
```
to fix a broken package.

---

### Post by everything is funny on 2011-03-28
Thanks for replying. I tried getting aptitude and it stopped updating at "Processing triggers for menu ..."

Looking in SS under Authentication for trusted software providers I have one listed as "launchpad ppa for uljanow" which I'm pretty sure is the one that was added after importing the key file...

---

### Post by garvinrick4 on 2011-03-28
What does:
```
sudo apt-get update
```
give you.

---

### Post by everything is funny on 2011-03-28
That worked! thanks. firestarter is gone. I was also able to install ipblock but now I can't update it or start the blocker. 
```
sudo ipblock -s
```
leads to 
```
iplist[9781]: error: can't find level1.gz
```
and
```
sudo ipblock -l
```
shows
```
error: no running iplist instance found
```

I found the GUI for it and tried updating but it produces errors for all of the lists. Their FAQ says their server gets bogged down often and to try again. Hopefully that's the only reason. I'll try later.

---

### Post by fan0o on 2011-03-28
remove to install, you can grep to get info about the package using the following command

ps ax | grep <installed app name>

and make sure that package is loaded

sudo service <name> start

---

