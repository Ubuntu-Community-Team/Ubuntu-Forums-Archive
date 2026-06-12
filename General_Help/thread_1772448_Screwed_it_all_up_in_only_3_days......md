---
title: "Screwed it all up in only 3 days....."
date: 2011-05-31
forum: General Help
---

### Post by johnm99 on 2011-05-31
Just trying Linux for the first time - installed Ubuntu 11.04 - then, I THINK I might have interrupted an installation by starting another one too quickly - not sure - BUT now every time I try to install anything using the Ubuntu Software Centre, I get this message - 

An unhandlable error occured
There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

It then asks to send in an error report - and I did, and see that this is listed as a Critical error with something like 280 people noting it. 

Not sure what to do. Should I just start over- wipe out the install and do it over? Is there a fix? It first happened when I was trying to install Flash. I already had WINE and a few other programs installed OK.

Thanks
John

---

### Post by johnm99 on 2011-05-31
I should add I did a search on this, found and read a dozen or so other posts and got nowhere.....

---

### Post by Rubi1200 on 2011-05-31
Hi and welcome to the forums :-)

Please open a terminal and run the following commands:

```
sudo dpkg --configure -a

sudo apt-get update
```

If errors are reported, copy and past them into a new post here.

Thanks.

---

### Post by Vaphell on 2011-05-31
starting from scratch will be the fastest way i think. Did you set up separate home partition? If not, I strongly recommend that. If for whatever reason system breaks down, you can reinstall its core while leaving user directories intact (including your wine applications which are installed inside user's home). 30 minutes and you are up and running as if nothing happened.

---

### Post by johnm99 on 2011-05-31
Thank you for the advice.

I opened a terminal, and entered those commands - here is what I got with
 " sudo apt-get update"

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0


Thanks
John

---

### Post by linuxinstalledfromhdd on 2011-05-31
The fastest solution would be to freshly install 10.10:

Here is a nice guide to get everything perfect:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

I'm not going to touch 11.04 until they get all the bugs out first. :D

---

### Post by Rubi1200 on 2011-05-31
With all due respect, but suggesting a reinstall for something like this is reckless and completely unnecessary.

@johnm99;

The problem can be solved by taking a look at this thread:
[http://ubuntuforums.org/showthread.php?t=1369015](http://ubuntuforums.org/showthread.php?t=1369015)

Follow the methods suggested by plucky and drs305 and you should be back up and running. Obviously replace with the relevant keys and ppa for your situation.

---

### Post by linuxinstalledfromhdd on 2011-05-31
Maybe it is reckless, and maybe not. It really depends on the end-user, and what they want to do. Maybe they just want a system in a hurry, and simply want have something right now without the hassle.  I don't know. I leave that up to the end user.  If they want to wait around for a posted solution, they are totally free to do that as well.  Everything that users post here are just suggestions, and not the only way to do things, and everyone has their own preferred way of doing things, which I totally respect too btw. When I was new to linux, I just wanted it to work, and I didn't care what I had to do to get it to work right. And the last thing I wanted to do was be involved in development before I even understood how the whole system works either. If someone else is looking for that, then it is best to freshly install a copy of Ubuntu, not the very latest cutting edge version either, and use a step-by-step walkthrough to get the PPAs and everything else installed that you will need the easiest way possible. :D

---

### Post by Rubi1200 on 2011-05-31
We shall have to agree to disagree about this linuxinstalledfromhdd, but at least warn those with other operating systems on the computer that the 10.10 installer can, and will, destroy their other OS unless they use the manual partitioning option.

For more about this, see here:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

especially post # 15

> **[COLOR=Red]Trust me here![/COLOR]** If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! [COLOR=Red]**You will most likely lose the OS and any data contained therein!**[/COLOR]

---

### Post by linuxinstalledfromhdd on 2011-05-31
How do you even know that applies to this particular end-user's situation? What data? They may having nothing on their hard drive except a broken version of Ubuntu that they don't know the first thing about because they are New to Linux altogether, and simply want to get the job done.  The way that I know that is always the most successful way, if all else fails is, do is a fresh installation. Follow a comprehensive walkthrough guide to whatever version you have installed on your computer.  And the one thing that everyone has to do, no matter what kind of OS they are running is, always make sure you got your stuff backed up on a normal basis, maybe even create yourself a nice clone of your system if you are going to really mess around with command line instructions if you don't know precisely what you are doing, or you are a computer technician or network technician.. etc etc. :D

---

### Post by micael3000 on 2011-05-31
-- Sorry I have not read all of the comments.

If you are starting I strongly suggest you to use Ubuntu 10.10 instead of 11.04.
11.04 is alpha quality, still being tested and FULL of bugs...

10.10 will work greatly for you... ;)

---

### Post by coffeecat on 2011-05-31
> **micael3000 said:**
> 
11.04 is alpha quality, still being tested and FULL of bugs...

10.10 will work greatly for you... ;)

I really do wish people would not post this sort of misinformation. It is not alpha and it is not still in testing. I have Natty running on 5 different sytems. It is stable on all of them and as bug-free as I would wish. There is a lot of misleading noise on the forum, mostly hearsay, about Natty. Many who are running it find it to be just fine. I'm posting from it at the moment.

**EDIT**: @johnm99, I suggest you follow Rubi1200's advice.

---

### Post by linuxinstalledfromhdd on 2011-05-31
It's all a matter of personal preference. But no, Natty is still being developed on a daily basis right now. 10.10 isn't anymore.   Correct?

---

### Post by coffeecat on 2011-05-31
> **linuxinstalledfromhdd said:**
> It's all a matter of personal preference. But no, Natty is still being developed on a daily basis. 10.10 isn't anymore.  That's why their is a new release. Correct?

Incorrect.

---

### Post by linuxinstalledfromhdd on 2011-05-31
Then why are people in general, having problems right after installing Natty, but not with previous versions of Ubuntu, if Natty isn't under development?

Just scroll down the list of help requests and read them if you don't accept this.

---

### Post by johnm99 on 2011-05-31
Thanks everyone - I will try the suggestions.

I have my Ubuntu on a partitioned 1TB drive. I am running a backup Windows 7 on one of the 3 partitions on this drive, and the main Windows 7 on another drive. It is connected to a 4TB raid in the computer plus another 8TB in a networked Drobo. 

I have reinstalled Windows so many times I am sick of it. In the 90s I had a Mac network for 7 years that never took one minute of maintenance ever. Then I moved, and because where I moved to wouldn't allow Mac at work, I dove into Windows - every version since 1995. That journey has taught me the pain of a poorly written complex flaky OS. It really is a dreadful OS - even Windows 7 has gotten itself hopelessly corrupted 3 times now in about 2 years. I will have to keep windows going, because my work oriented software will not run on Linux - any version, any emulation setup - that has all been researched by some very knowledgeable engineers I work with - and I am fine with that. But I was kind of thinking if I got set up well, I could avoid Windows except when I have to use that particular software. So, photo editing, and video conversions, torrents etc should be fine. (was kind of hoping to get Photoshop CS5 going but will settle for an earlier version if more stable).

I would like to take the time to learn how to use Ubuntu - it did seem VERY slick on its initial install and is very fast. I just need to get going on what not to do, I suppose. Perfectly willing to make some mistakes, reinstall or whatever is needed to get a feel for it.

I will tinker away, and appreciate all your advice. I also enjoy seeing that people are passionate about Linux, and have their own ways of doing things. Many thanks. I will report back on whether I can fix it or not.

That aside, any advice on a book / video / online resource to get someone like me the "dummy" basics of Ubuntu?

Cheers all

---

### Post by coffeecat on 2011-05-31
> **linuxinstalledfromhdd said:**
> Then why are people in general, having problems right after installing Natty, but not with previous version of Ubuntu, if your reason is that Natty isn't under development?

This is not the place to have a discussion - it is not helping the OP. If you want a discussion, open or join a thread in the Cafe.

But I will say this following and then no more. Natty has been released. It is no longer under active development. There will inevitably be bugfixes and security patches released through regular updates. In this respect it is no different from Maverick, or Lucid for that matter. The difference with Lucid and Maverick is that there are fewer coming through now, only because they have been out longer. But there are still bugfixes filtering through for both of those earlier releases.

And I've been around long enough to be able to set my calendar by the regular twice-yearly howl of protest when a new version of Ubuntu is released. Each new version of Ubuntu is derided as bug-ridden - it isn't. There are always some genuine hardware-related teething troubles for a minority  at first, but this quickly settles down. Believe me - the fuss when Lucid was released was far worse than now with Natty. And now Lucid is touted as the most stable thing there is. So your assertion that problems didn't occur with previous releases is not correct.

---

### Post by Asmodai on 2011-05-31
> **linuxinstalledfromhdd said:**
> Then why are people in general, having problems right after installing Natty, but not with previous version of Ubuntu, if Natty isn't under development?
What makes you think that is the case?
If it seems people are having trouble with Natty right now, then because a lot of people are installing Natty right now and almost no one is installing previous versions.
Likewise, if an existing Ubuntu user upgrades from Maverick to Natty and there are regressions, s/he'll post on the forums about it. If everything goes well like it does in most cases, you won't hear about it.

It's the same story with every release, there are always some regressions and many of those don't ever get fixed by updates within the same release cycle. So there's no point waiting till "all the bugs are fixed", as that will never happen.

> **johnm99 said:**
> 
That aside, any advice on a book / video / online resource to get someone like me the "dummy" basics of Ubuntu?
This might get you started: [http://ubuntu-manual.org/](http://ubuntu-manual.org/)

---

### Post by linuxinstalledfromhdd on 2011-05-31
I have been around long enough to know these things as well. But to say that Maverick has just as many bugs right now as Natty, is incorrect. Yes, more users are installing Natty right now, and so there is a larger sheer number of issues with Natty than other previous releases at the moment.  I know that.  However from my own experience it is best to stick with the previous release to avoid as many of the latest issues as possible, if you just want a system that is up and running ASAP.  That was my suggestion. And I stand by that suggestion since you have given no reason to believe otherwise. I don't like telling people that Natty is the only way to go, and say that they all have bugs, when I know for a fact that previous releases don't have as many bugs as whatever the latest releases always do.

If you want to debate this you take it to the cafe, that's my suggestion.  I'm just defending my position when I'm attacked in a forum where I am helping users out of my own free time.  If you find that I am doing something wrong, you can message me privately from now on. Thank you.

---

### Post by Rasa1111 on 2011-05-31
coffeecat and rubi are making the most sense here.  :P

to John~

Instead of trying to install "flash" on its own..
I suggest you just install ubuntu-restricted-extras, from the software center or through synaptic package manager.  This will install flash, java, all music and video codecs, pretty much everything you'll need, all at once. 

Ive never installed "flash" or "java" or any other codecs on their own..
I always just install restricted extras and everything works perfectly. 

Good luck.

---

### Post by johnm99 on 2011-05-31
Well, installing restricted-extras seems to have worked - the thing I was originally hung up on was trying to install Crossover - I went about it by downloading the file and double clicking on it - which ended up messing things up - I now understand it is better to use the Ubuntu Software Centre - and that you can actually purchase through there. (This is all so I can try to get Outlook and Photoshop to run). So, Crossover has installed nicely.

I did read the thread you referred me to, rubi1200 - but I am afraid I need to do some reading before I understand that advice (I am TOTALLY new to Ubuntu). Which I will do. Until an hour ago I had never heard of a PPA and not sure what a "relevant key" is - but I will try.

Even if I have to do another install from scratch, I am happy to learn as I go. I could even throw on another partition and do a second install........but I will see how this one goes.

---

