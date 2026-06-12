---
title: "Continuing update issues..."
date: 2009-11-21
forum: General Help
---

### Post by CoolBreeze47 on 2009-11-21
Hi everyone

First of all, sorry for the misunderstanding this morning regarding the bit of well-intended chiding I received (ie; "CoolBreeze46"). Not to get into a lot of personal issues but at the time I joined the forum this morning I was going through some pretty severe prescription drug withdrawal plus a lot of other even more personal issues so I imagine I might have been a bit overly-sensitve as my brain was pretty scrambled and I wasn't thinking to clearly to say the least. Anyway, no hard feelings and I appreciate the replies via my thread and PM's I received with respect to my problem :D

However, after an entire week and despite taking all of the suggestions, instructions, checking and double-checking, I am still unable to receive updates either via the Synaptic package manager or sudo apt-get update/upgrade. I don't know whether there is an issue with the repos, the package manger itself or if there are simply no updates to be had. Almost always (and especailly with new releases) the updates usually (but not always) come every day or so...sometimes nearly every day.

I'm stumped on this one. Ubuntu on two laptops and one desktop and no updates for a week. Seems a bit odd but who knows.

---

### Post by mechro on 2009-11-22
Looking at my Jaunty system I've found that **apt** keeps its log files in **var/log/apt**. The latest **term.log** file shows all package installation and update activity from 1 November till today.

So if you do...

```
gksudo gedit /var/log/apt/term.log
```

...you might get some more clues to your problem (Text search for "replacement" highlights the update stuff). There must be a problem because nobody has said that there haven't been any updates.

Be well. I also wrote you a PM but I'm not sure it was sent. Despite my post count I'm quite new here myself and am not yet up to speed on the fangly dangly bits in my forum user control panel.

Tony

---

### Post by CoolBreeze47 on 2009-11-22
Using the Software Sources tool, I located another server/repo in the U.S. and then went directly to their FTP archive to determine when the last update was provided. The date shown was Nov. 18, 2009. That was 4 days ago so I should have received that update and yet I have not received ANY updates in 8 days.

Next, I made that repo my default and ran the update manager. Everything appeared to run smoothly but still no updates. This is really getting strange. Obviously, the security updates are important and it would also be kind of nice to be able to get the bug fixes and feature updates as well.

gksudo gedit /var/log/apt/term.log

The command above simply brought up a history of past updates but indicated no errors or any other unusual activity.

Any more ideas because I'm completely stumped :confused:

---

### Post by CoolBreeze47 on 2009-11-22
Anyone?. I'm pulling my hair out on this one...

---

### Post by CoolBreeze47 on 2009-11-22
:frown:

---

### Post by Uncle Spellbinder on 2009-11-22
There have been threads on other parts of the forum about servers being down. For 3 days I couldn't update or install anything. 

Just wait. That's what I did.

---

### Post by CoolBreeze47 on 2009-11-22
Yes but I've already tried a number of servers from the sources list and no joy. Also, I can understand 3 days but 8?. Finally, everything runs as smooth as silk and if there is an issue with a particular server, you would expect to get an error message (as I always do).

I guess about the only thing I can do is wait. And Hope.

---

### Post by CoolBreeze47 on 2009-11-23
Tried a few other things yesterday as well. Here it is 9 days and still no updates. I'm not trying to keep a running log here, just hoping that someone in the know will drop in and tell me what's going.

---

### Post by QLee on 2009-11-23
[QUOTE=CoolBreeze47] ... and then went directly to their FTP archive to determine when the last update was provided. The date shown was Nov. 18, 2009. That was 4 days ago so I should have received that update and yet I have not received ANY updates in 8 days.[/QUOTE]

Since you looked at the site, and thus could see the version numbers, what piece of software installed on your system did not upgrade?


[QUOTE=CoolBreeze47]gksudo gedit /var/log/apt/term.log

The command above simply brought up a history of past updates but indicated no errors or any other unusual activity.[/QUOTE]

Yes, and it would show you what the last upgrade was too. 

Since you could check the version numbers of your installed software you should be able to determine what software installed on your system didn't upgrade. I realise that checking manually like that would be a pain but ... Just to be sure, you're not thinking about a piece of software that you installed outside of a package manager are you?

Most of what I asked about should be obvious from the Synaptic GUI. Since you said you did an update, Synaptic should show the installed version and the latest version and if you use the Custom Filter, "Upgradeable", you should see a list of packages for which there is a newer version.

Maybe I missed something in what you were describing.

---

### Post by CoolBreeze47 on 2009-11-23
I've been through and am aware of these things and have spent a great deal of time comparing, testing, examining logs, using "fancy" terminal commands, etc. Like I said, I'm using a vanilla install so everything is set to the defaults and for the last three years I've been using Ubuntu, I've never seen this much of a delay in updates.

After 9 days however, I finally got 3 updates for Nautilus. None of these updates fixed the 5 serious issues in Nautilus so I'm not exactly sure what the update was for but the fact that there were any updates at all at least tells me that the "system" is working.

I'm thinking about switching to Linux Mint when v8 is released. I realize it's based on Ubuntu but a friend has been using it for some time and has no issues with updating or Nautilus errors. Either that or straight Debian.

Thanks for all the replies. I'll sit back and see what happens. Hope everyone here has a nice Holiday and take care.

- Cool Breeze

---

### Post by QLee on 2009-11-24
[QUOTE=CoolBreeze47]I've been through and am aware of these things and have spent a great deal of time comparing, testing, examining logs, using "fancy" terminal commands, etc. Like I said, I'm using a vanilla install so everything is set to the defaults and for the last three years I've been using Ubuntu, I've never seen this much of a delay in updates.[/QUOTE]

Well, keep in mind that the system only upgrades packages that you have installed, there could be "updates"(upgrades) to some packages, which would mean the repository would have some upgrades but if there weren't any for what you have installed, none would come down to your system.

[QUOTE=CoolBreeze47]After 9 days however, I finally got 3 updates for Nautilus. None of these updates fixed the 5 serious issues in Nautilus so I'm not exactly sure what the update was for but the fact that there were any updates at all at least tells me that the "system" is working.[/QUOTE]

Yes, after you have verified your sources.lst, seen no errors when you apt-get update and the package manager you choose to use shows nothing to update, trust the system. (I think this is where people often say, "use the FORCE, Luke", as a quote from an old movie)

I don't remember seeing any questions about Nautilus but, I think it is working for most users.

[QUOTE=CoolBreeze47]I'm thinking about switching to Linux Mint when v8 is released. I realize it's based on Ubuntu but a friend has been using it for some time and has no issues with updating or Nautilus errors. Either that or straight Debian.[/QUOTE]

It appears that you also haven't been having any upgrade issues, just that there weren't any available for your system.

Either of those operating systems might be good choices for you, only you can determine that. If you go with Debian, I suggest Lenny ("stable"), it won't have the newest features but you would probably not like the volatility of the unstable branch which would be more similar to Ubuntu with the newer features of software.

---

