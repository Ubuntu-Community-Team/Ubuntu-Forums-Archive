---
title: "All applications crashing - Firefox, Thunderbird, Opera, OpenOffice"
date: 2010-07-13
forum: General Help
---

### Post by elibunt on 2010-07-13
For a couple of weeks, I have had constant crashes of all my applications on Lucid:
[LIST]
[*]Thunderbird 3.1 (updated since crashing started using Ubuntuzilla)
[*]Firefox 3.6.6 (updated since crashing started using Ubuntuzilla) - also crashes in safe mode
[*]OpenOffice 3.2
[*]Opera 9.63
[/LIST]
Most frequently it is Firefox and Thunderbird crashing, because they're the applications I use most. (Also F-Spot has crashed, but F-Spot frequently crashed before all this, so may not be related). 

Sometimes applications will run for a few hours and then crash (either suddenly close or freeze, it varies). Other times the application crashes before it even opens, and I just get the Mozilla crash reporter. If an application won't start at all, it will usually start if I restart the computer, but may crash again soon afterwards. There is no obvious pattern to when it crashes - sometimes on starting, sometimes when I click something, sometimes when I'm not even at the computer and I just come back to find it crashed.

My husband (a programmer) has run Memtest on my machine, which found no problems. He is also running lucid on the same hardware apart from the monitors, and has the same versions of OpenOffice, Thunderbird and Firefox except for extensions, but has not had any problems. 

A warning that shows on the terminal if Firefox crashes in safe mode, is:

WARNING: pipe error: Broken pipe: file /builds/slave/linux_build/build/ipc/chromium/src/chrome/common/ipc_channel_posix.cc, line 627
WARNING: pipe error (3): Connection reset by peer: file /builds/slave/linux_build/build/ipc/chromium/src/chrome/common/ipc_channel_posix.cc, line 404

This is strange because I did not, when that warning first appeared, have Chromium installed (although I did have Picasa). My husband installed Chromium on my machine after seeing the warning, hoping it might help somehow, and Chromium is running okay so far but other applications are still crashing. 

Any advice would be much appreciated. I might get my husband to file a bug report, but it would help if I could clarify the nature of the problem first.

---

### Post by robsoles on 2010-07-13
What are the chances of trying something else altogether - can these items run without crashes from a LiveCD?

You can run a few of the apps you mentioned without having to install (at least to some extent) so as to test if it they are themselves a problem or not.




Can you remember an update getting halfway through and the machine being unplugged or anything nasty like that?

Does anything reported in terminal from following command look 'bothersome'?
```
sudo apt-get update
```

(post output if it mentions problems/errors)

---

### Post by elibunt on 2010-07-13
My husband has a live CD somewhere, so I can try that when he gets home. 

Regarding updates, there is sometimes a problem with the updates icon in the panel (hope I'm using the correct terms here) showing a red circle with a white line across it and an error warning. I was getting around that by right clicking on the circle, and selecting "check for updates" then installing them, which has seemed to work and the red circle goes away.

I have just tried sudo apt-get update, and got the following error message:[INDENT]Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_lucid_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
[/INDENT]After doing this, the red circle warning appeared again, and hovering over it gives the following error message (copied manually as carefully as I can):[INDENT]' Error: Opening the cache (E:Problem parsing dependency Depends, E:Error occurred while processing gnome-desktop-environment (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_lucid_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.)'This usually means that your installed packages have unmet dependencies
[/INDENT]Does that mean anything to you?

> **robsoles said:**
> What are the chances of trying something else altogether - can these items run without crashes from a LiveCD?

You can run a few of the apps you mentioned without having to install (at least to some extent) so as to test if it they are themselves a problem or not.




Can you remember an update getting halfway through and the machine being unplugged or anything nasty like that?

Does anything reported in terminal from following command look 'bothersome'?
```
sudo apt-get update
```(post output if it mentions problems/errors)

---

### Post by robsoles on 2010-07-14
Am at work so can't spend long time posting...

Try:
```
sudo aptitude -f reinstall gnome-desktop-environment
```

If it doesn't seem to indicate that it will download too many bytes for you and other alarming stuff isn't mentioned then press 'y' and give it a whirl - if the output from that command does seem very hairy then please post it back to this thread in your next reply.

---

### Post by elibunt on 2010-07-14
Tried 

sudo aptitude -f reinstall gnome-desktop-environment

but got the following error message:[INDENT]Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_lucid_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_lucid_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

[/INDENT]

---

### Post by elibunt on 2010-07-14
Just got a call from my husband and told him where we'd got to. He suggested I post a copy of the contents of sources.list in case it helps, so here it is:
[INDENT]deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
# deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free # disabled on upgrade to jaunty
# deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) testing non-free # disabled on upgrade to jaunty

# deb [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main # disabled on upgrade to lucid
[/INDENT]

---

### Post by robsoles on 2010-07-14
When I get home (about another 4 or 5 hours from 'as I post this') I can try more radical stuff in a VM to try to find a solution for you but in the meantime perhaps I can contemplate your answer to question: Did trouble start immediately you upgraded to Lucid?

(I might be able to do more here at work if I am creative enough!)

---

### Post by elibunt on 2010-07-14
I don't think it started immediately. My husband says he upgraded me soon after lucid came out, which was back in April, and I haven't had the problem that long.

---

### Post by robsoles on 2010-07-14
OK, I worried it was a little too radical while I was at work and couldn't test it in a 'harmless' situation but now I have tested the following in a VM and it really does appear harmless.

Please try
```
sudo rm /var/lib/apt/lists/*
```It will ask for your password and when it is finished it will report back:

rm: cannot remove '/var/lib/apt/lists/partial': Is a directory

(It's not harmless if we remove 'partial' directory so it's good 'rm' on it's own won't remove it!)

This being the case, please try
```
sudo apt-get update
```again - post me the output of that command again.

If at the 'rm' step above you get different output from what I suggest then please post that into this thread as well!

---

### Post by elibunt on 2010-07-14
All went as you said, no error message this time, just the following: 

Fetched 11.7MB in 1min 17s (150kB/s)                                           
Reading package lists... Done

Should I now run sudo apt-get upgrade?

Thanks heaps for your help by the way.

---

### Post by robsoles on 2010-07-14
> **elibunt said:**
> All went as you said, no error message this time, just the following: 

Fetched 11.7MB in 1min 17s (150kB/s)                                           
Reading package lists... Done

...

Beauty, I was still mildly worried after trying it in a couple of different VMs here at home!

> **elibunt said:**
> ...

Should I now run sudo apt-get upgrade?

...

Yep, but if it bombs then post me the output from running the command and also have another try at my suggested command in post #4 in this thread.

> **elibunt said:**
> ...

Thanks heaps for your help by the way.

Very welcome, I love doing it or I probably wouldn't - sometimes I get to practice old knowledge but mostly I learn something new everytime I reach out to help anybody really!

---

### Post by elibunt on 2010-07-14
I ran sudo apt-get upgrade fine, then I tried sudo aptitude -f reinstall gnome-desktop-environment again and got the message:

[INDENT]Segmentation faultsts... 4%
[/INDENT]I'm off to bed now - it's after midnight here - so if you have anything else for me to try, I'll give it a go in the morning. Thanks again and goodnight!

---

### Post by robsoles on 2010-07-14
Good Morning (:))

Would you please post the output of the following commands into your next reply:

```
sudo aptitude -v why gnome-desktop-environment

sudo aptitude -v show gnome-desktop-environment
```

(mmmh, now I better make my bedtime plans or it will become after midnight here as well and I will still be up!!)

---

### Post by elibunt on 2010-07-14
Good morning! The output of both those commands is the same:

Segmentation fault

---

### Post by robsoles on 2010-07-14
Oh poop.

I've found that the things I do on my systems don't get that package installed for me and I've got a 
pretty desktop etc so hopefully it is safe to uninstall because that is what I am now going to advise - 

probable case scenario: It doesn't uninstall but reports this 'Segmentation fault' again

best case scenario: just uninstalls and we find everything now works and we don't have to do any thing else

worst case scenario: it uninstalls but for some reason the world ends on us!

If you are 'game' enough:
```
sudo aptitude -f remove gnome-desktop-environment
```
(for anyone watching: that '-f' switch is supposedly about "aggressively fixing broken packages" and not 'force' when using this command!)

And if that completes successfully then try some of the apps - push them a bit, if they run brilliantly then don't rush into reinstall but if they are still crud or something is worse then reinstall using the 'fixit' switch again:
```
sudo aptitude -f install gnome-desktop-environment
```

Of course, if 'remove' fails and it says something more than that blasted 'Segmentation fault' I will be keen to know what the output is!

---

### Post by elibunt on 2010-07-14
I haven't tried removing and reinstalling gnome desktop environment yet, because so far my computer hasn't crashed today. Is it possible that something we've tried already might have fixed the problem? Of course, I mentioned that sometimes I do get a few hours without crashes, so this might be just such an interlude, but perhaps I should just keep using the computer and see what happens?

---

### Post by robsoles on 2010-07-14
Absolutely a fair thing to do **BUT** that segmentation fault regarding the gnome-desktop-environment will eventually get around to biting you in the back again, if it isn't dealt with, even if it does wait for another dist-upgrade to do it.

That 'fault' may randomly bite you any time you update, install or uninstall anything from your PC.

If you decide to wait and see and it lasts long enough to make you satisfied it will be a while before it bites you again then please come and mark this thread solved - when you get bitten by the fault again you might try those 'remove' and 'install' instructions I posted and start a new thread if they fail on you.

---

### Post by elibunt on 2010-07-15
I don't like the sound of waiting for something to bite! I will do the remove and install, but I've been busy this afternoon and my husband suggests I should boot into the terminal first, so I'll do that shortly and report back.

---

### Post by robsoles on 2010-07-15
I'll be less worried about it biting you if we basically make it bite now while we are thinking of it.

Hopefully the 'remove' and 'install' commands given before will just flow through but no matter how good it goes make sure you take a snapshot (copy & paste to somewhere, including this thread, or quite literally get camera out and photograph from display) of all the programs it says it will remove when you run the 'remove' command...

It may list some thing(s) that won't automatically be put back in by the 'install' command I have advised to execute after the 'remove' but we can put them back ourselves if we have a list of them.

---

### Post by elibunt on 2010-07-15
Sounds like good advice, thanks, I'll do that. In between cooking the dinner I've been trying to find out how to boot into the terminal.  I'm not finding a quick answer, so can you tell me how? Or do I not really need to do that?

---

### Post by robsoles on 2010-07-15
Shouldn't really need to do it - when I started playing in Linux you could use 'shutdown' to get into a single user maintenance mode but, as with all my favorite things, somebody changed it so you don't/can't anymore.

see this thread [http://ubuntuforums.org/showthread.php?t=1510133&page=1](http://ubuntuforums.org/showthread.php?t=1510133&page=1)

I reiterate: for our purpose you shouldn't need it and you have to restart with whatever problems may have been introduced by commands issued in it to get back to a browser etc to be able to access the forums again!

---

### Post by elibunt on 2010-07-15
I did the remove step, and got the following output:

[INDENT]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done[/INDENT]

I then tried to open Firefox to post in this thread, and it promptly crashed! (By the way, I forgot to mention that the crashes started again soon after my post #18.) I tried Opera, and it crashed too. So I'm now trying Chromium. Should I now go ahead with the install step, or has the remove not worked properly?

---

### Post by robsoles on 2010-07-15
Try the remove step again but drop the '-f', I have a sneaking suspicion that either the '-f' conflicts with the idea of 'remove' or gnome-desktop-environment isn't really installed on your machine!

If next attempt at remove makes it look like it was removed then turn around into the install (**with '-f' included**) step straight away, otherwise we stop barking up that tree and I start getting you to post snippets of certain log files off your machine from times around the crashes.

---

### Post by elibunt on 2010-07-15
Tried it without the -f, but I think the output was the same:

[INDENT]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
[/INDENT]

---

### Post by robsoles on 2010-07-15
Ok, LOL - looks much more like that sucker simply isn't installed so YAY!!! :)


Um, one more thing to do:
```
sudo apt-get dist-upgrade
```Don't execute immediately, read the two package names that are listed (I am expecting two packages in list) - consult with hubby and/or post names of packages it says it will update here if it makes you nervous otherwise just commit and press 'y'

Will give us some more info if something about it fails - if nothing about it fails I think I will walk you through uninstalling each of the 'crashing' programs and reinstalling them (using -f switch) to see if we can get away without even having to look at the logs.

In uninstalling and reinstalling these packages the expectation is to keep all your settings and data - these would only be removed if we used a command I am not even going to mention (unless you ask!)


2nd edit: Actually, I will just post easy way to get package names for use in terminal and point out other (hopefully) helpful bits in a post I will start composing now - that way you (elibunt) and anyone who comes looking afterward may benefit more (sooner).

---

### Post by robsoles on 2010-07-15
To get the package name of a program you are using just find it in 'System'->'Administration'->'Synaptic Package Manager', if you are able to use 'apt-get' or 'aptitude' on it then it will be listed here.

When you use the package name to uninstall it using the following command all user data and settings should be retained _**unless**_ you go out of your way to get rid of them using another technique I will just barely point out below.

```
sudo apt-get remove this-or-that-package-name
```
into terminal should result in you (1) having to enter your password if you haven't used sudo and entered it in the last while, (2) in being shown what will be removed, including dependent packages, should you agree and (3) having to agree by press 'y' [Enter] before action takes place.

It should be possible to just reinstall it and use it without any special commands:
```
sudo apt-get install this-or-that-package-name
```

But if issuing that command gets you a broken situation then reissuing the 'remove' version of the command and then
```
sudo aptitude -f install this-or-that-package-name
```
Has a pretty good chance of fixing it without need for more indepth tinkering.


If you want your data and settings (for given package alone) scrubbed then
```
sudo apt-get purge this-or-that-package-name
```
should suffice but to be sure it all gets scrubbed thoroughly it is best to identify (carefully) the directories it uses in your home folder and make sure they got emptied if not removed - tinkering at this level can blow up in your face but if you can verify that you are only touching folders/files that the program in question made in YOUR OWN home directory then all should turn out peachy for a nice reinstall and fresh (re)start.

---

### Post by elibunt on 2010-07-15
I did the dist-upgrade last night. There was only one package - gwibber. My husband then upgraded Opera to version 10.6 and also removed a beta version of Virtual Box that he installed on my machine a couple of months ago, which he guiltily thinks might have something to do with all the trouble I've been having. (He was using my machine at the time to test a Mac version of his open source statistics package. He didn't want to use his own machine because it was too risky!) So far no crashes today, but I won't know for a while if the problem's fixed. I'll report back.

---

### Post by elibunt on 2010-07-15
Firefox just crashed. Using a tip from a friend, I entered dmesg | grep error in the terminal, and got the following output:

[INDENT][ 6041.255474] operapluginwrap[2559]: segfault at 0 ip (null) sp bfe044ec error 4 in libX11.so.6.3.0[110000+119000]
[ 6041.265659] operapluginwrap[2562]: segfault at 0 ip (null) sp bfaf765c error 4 in libgcc_s.so.1[110000+1d000]
[ 6041.292233] operapluginwrap[2565]: segfault at 0 ip (null) sp bfb9ae1c error 4 in libc-2.11.1.so[110000+153000]
[ 6041.299416] operapluginwrap[2567]: segfault at 0 ip (null) sp bf8e407c error 4 in libm-2.11.1.so[110000+24000]
[ 6041.319789] operapluginwrap[2570]: segfault at 0 ip (null) sp bfd23abc error 4 in libm-2.11.1.so[110000+24000]
[ 6041.324433] operapluginwrap[2571]: segfault at 0 ip (null) sp bfbf794c error 4 in libstdc++.so.6.0.13[110000+e9000]
[ 6041.364862] operapluginwrap[2573]: segfault at 0 ip (null) sp bff8062c error 4 in libxcb.so.1.1.0[110000+18000]
[ 6041.379840] operapluginwrap[2575]: segfault at 0 ip (null) sp bfb0c3fc error 4 in libX11.so.6.3.0[110000+119000][/INDENT]

This operapluginwrap showed up once before, which was the reason we upgraded Opera last night.

I only use Opera when Firefox fails, meaning there's much less to lose in the way of settings and extensions, so perhaps I should make Opera the first package to remove and install. Does that sound sensible, or is the operapluginwrap something to deal with more directly?

---

### Post by elibunt on 2010-07-15
I just googled "operapluginwrap error" and the top result suggested the cause of the segfaults was a bug in Flash. I do have Flash installed, and my husband says it is evil and the source of lots of problems, though necessary for lots of things. He also surmised the problem could be an interaction between Flash and Adblock Plus 1.2.1, which I have installed in Firefox and would not want to do without. Does this extra information suggest a different solution?

---

### Post by robsoles on 2010-07-15
Trouble with a few of the logs is that they use time marks that require translating (or none at all) and then you have to translate them (or guess from events happening around them if there is none) to figure out what time 'this log entry' was made and whether or not it is relevant to our problem.

If you look at my post #[**26**]("http://ubuntuforums.org/showpost.php?p=9592313&postcount=26") above you should see that the first way I suggest to remove a package should be harmless to your settings and so forth so it shouldn't matter which order you do them in - I'd love it if you pick off each one as it crashes on you and post back error (or confusing) messages from executing the 'remove' command back to this thread.

Do it to Opera first if you like but if you avoid the 'purge' option it really shouldn't be more than reinstalling plugins that are system wide rather than addons which are stored in your home directory.

---

### Post by elibunt on 2010-07-15
I've removed and installed Opera. There were no error messages, just some unknown media types. I'm not sure if you saw my post #29, because I sent it just before your post #30. Wondering if I should do something about Flash.

---

### Post by robsoles on 2010-07-16
Flash is a necessary evil, I agree with your hubbie about that. Those log entries don't help a great deal and there is a lot of noise on the internet regarding flash stuffing some or other thing up.

I saw #29 before I made #30, I decided to stride on because it is just so unlikely to effect one of your big four: OpenOffice (I mean that OpenOffice has no dependency on flash nor web-browsers at all to get it's job done - not that I've come across anyway!)


Push Opera around a little, if it doesn't actually crash then it's as fixed as you need it for purpose of using it as a web-browser. If it appears fixed then try the next program, replace it with a fresh copy of itself (un & re install)

If you open a terminal and pop following command in then you'll get to watch log entries being made as you try stuff in the programs and you'll be able to see whether or not they relate to a real crash or just minor hiccups that you don't even really notice.
```
sudo tail -f /var/log/dmesg
```(A more interesting log to follow like this may be /var/log/messages though).

EDIT: Actually, just checked and where I've been using 'sudo' since they convinced me to stop logging into my server(s) as root it isn't necessary to 'follow' (-f) a log.

---

### Post by elibunt on 2010-07-17
The log files haven't revealed anything much - sometimes nothing at all when Firefox has crashed. Today we ran a thorough check of the hard drive, and tried using a network cable rather than the wireless card. I also removed Flash - a friend told us it's the first crash that matters on each startup, and I think the Open Office crashes have always followed other crashes, so even though Flash wouldn't crash Open office directly, I gather that if Flash has caused a segfault then that in turn might cause the Open Office crash? When I first tried to remove Flash, I got the following message:

[INDENT]Segmentation fault
(Reading database ... 230858 files and directories currently installed.)
Removing adobe-flashplugin ...
Segmentation fault
dpkg: error processing adobe-flashplugin (--remove):
 subprocess installed pre-removal script returned error exit status 139
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 adobe-flashplugin
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/INDENT]However, after an update and upgrade, which tried to complete the Flash installation and resulted in a crash alert, Flash removed okay and no crashes since. But not long enough to draw any conclusions. I'll see what happens tomorrow.

---

### Post by robsoles on 2010-07-17
I will be (apologetically) surprised if you get a good result across the board by removing flash but I suppose it is worth pursuing even if only to rule it out.

Most of the when programs crash and get closed/killed they go by themselves - if they aren't going by themselves they usually put you in a position where you can tell fairly easily that you need to reboot your computer before you'll get a decent run out of certain things on it. Of course there are exceptions to rules but I have crashed flash stuff repeatedly without anything else in the system needing attention thereafter.

If it were my system or a system I was administrating directly (at work I am the IT admin...) then I would just make a backup of all associated user data and just uninstall and reinstall each program that exhibits the bad behavior and pursue error messages given in uninstall and install processes and then error messages from a fresh install made with no errors reported.

Anyway, I remain subscribed to your thread - every time either one of us posts to it we bump it back to the top of the thread list in it's forum so it has another chance of attracting attention of others with at least different, if not entirely better, advice to try perhaps :)

---

### Post by elibunt on 2010-07-18
Okay, I had a crash this morning, but at least as you say I've ruled Flash out.

I've just removed openoffice.org*. The only possibly interesting things (but probably not) in the output were:

[INDENT]dpkg: warning: while removing openoffice.org3, directory '/opt/openoffice.org3/share/uno_packages/cache' not empty so not removed.
dpkg: warning: while removing openoffice.org3, directory '/opt/openoffice.org3/share/uno_packages' not empty so not removed.
dpkg: warning: while removing openoffice.org3, directory '/opt/openoffice.org3/share' not empty so not removed.
dpkg: warning: while removing openoffice.org3, directory '/opt/openoffice.org3' not empty so not removed.
[/INDENT]and

[INDENT]Removing openoffice.org-filter-binfilter ...
file:///usr/lib/openoffice/basis3.2/program/libbf_migratefilterli.so
revoke component 'file:///usr/lib/openoffice/basis3.2/program/libbf_migratefilterli.so' from registry '/var/lib/openoffice/basis3.2/program/services.rdb' succesful!
[/INDENT]

---

### Post by lidex on 2010-07-18
If you have Log File Viewer installed, it will give you a mass of information. The package is 'gnome-system-log'. Run via 'System>Administration>Log File Viewer'.

gnome-desktop-environment is not in a default ubuntu install, gnome-desktop data is however as well as ubuntu-desktop.

Have you tried logging in as a different user?

---

### Post by robsoles on 2010-07-18
Have you reinstalled any openoffice items yet?

I am looking into the '/opt/openoffice.org3' entries you show in your post to see if it is an obvious 'value-add' to go out of our way to move or delete them.

---

### Post by robsoles on 2010-07-18
I don't have this 'openoffice.org3' folder on my PC(s) so I need to find it on yours before I can tell you commands to move it somewhere we can keep it safe while we install OO Word Proc and whichever other components of the OO package you really want using the '-f' switch for each one.

Please give me output from
```
sudo find -name '*openoffice.org3*'
```

EDIT: Just noticed lidex posted while I was procrastinating over post #37 - I think they just read page #1 and didn't notice we had another 3 pages in your thread here elibunt **BUT** their idea of logging in as someone else is one I usually try in not too dissimilar circumstances and I have to admit it is a good idea - give it a whirl, make a new user account and make it as powerful as you like then try to crash these things using that account. (Let's pursue getting openoffice installed with 'fixit' flag supplied first if you haven't already reinstalled but otherwise...)

---

### Post by elibunt on 2010-07-18
I didn't see your latest post, robsoles, before starting installation of openoffice.org. It still has about 15 minutes to go. Should I let it complete or stop it somehow?

---

### Post by robsoles on 2010-07-18
Sorry, didn't catch up with post soon enough and apparently it has finished(?) - put a little while into getting this copy of openoffice to crash (unless you quit without me :)) and if it does make a new user account and see if you can crash any of the programs still crashing with the new user.

Did Opera crash again after reinstall? You didn't specify which program crashed since that post.

---

### Post by elibunt on 2010-07-18
(Regarding the installation, I didn't use the -f because I hadn't seen post #38.) The installation for openoffice.org was still in process (somewhere over 61%). I had pasted some lines from the message files into gedit and was trying to copy them into this message when gedit crashed (suddenly closed) and at the same time the installation stopped abruptly. The message from the terminal was:

[INDENT]Fetched 68.9MB in 28min 18s (40.6kB/s)                                         
Failed to fetch [http://ubuntu.mithril-linux.org/archives/pool/main/o/openoffice.org/openoffice.org-core_3.2.0-7ubuntu4.1_i386.deb](http://ubuntu.mithril-linux.org/archives/pool/main/o/openoffice.org/openoffice.org-core_3.2.0-7ubuntu4.1_i386.deb)  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
[/INDENT]
The last few crashes have been Firefox. I have not reinstalled Opera yet because I can do without it for now, I only need it if Firefox is unusable. 

Lidex: thanks for that method of viewing log files. I had a look and found it records more useful time entries. There were no messages about a Firefox crash I'd had around 20:35, but there were a few lines amongst the reboot messages just afterwards that might perhaps be relevant (copied from the gedit file without it crashing this time):

[INDENT]Jul 18 20:39:57 ubuntu kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.

Jul 18 20:39:57 ubuntu kernel: [    0.188105] ACPI Warning: Incorrect checksum in table [OEMB] - C5, should be C0 (20090903/tbutils-314)

Jul 18 20:39:57 ubuntu kernel: [   21.803813] nvidia: module license 'NVIDIA' taints kernel.
Jul 18 20:39:57 ubuntu kernel: [   21.803816] Disabling lock debugging due to kernel taint
[/INDENT]Interestingly, the log file viewer window itself crashed when I clicked on messages1, but when I reopened the log file viewer and tried clicking on messages1 again it worked fine (and yes, I found out they were just older messages).

So that's two more things to add to the list of applications that have crashed (if it's correct to call them applications): gedit and log file viewer.

I do have gnome-desktop-data - should I try removing that??

---

### Post by robsoles on 2010-07-18
Yes, I forgot about the GUI log viewer and the fact that it translates that other time stamp for us.


Maybe your system can benefit from an update to the BIOS firmware but that isn't a sure thing - maybe it can benefit from getting into BIOS settings and select "Load Failsafe Defaults" or whatever simile of that is found and then save and reboot, again not a sure thing though!


I think you will be better off at this point to restart your openoffice install using '-f' option in the terminal - I have the impression you know the packages required, post back if I'm wrong about that and I'll have a closer look and give you the line to execute IMHO.


EDIT: Don't try to do anything much while installation is downloading and taking place, we want to see if using '-f' makes anything that is relied on 'across the board' happens to get replaced.

Once installed (or perhaps even before installing) make a new user on this machine, a new administrator privileged one, and try the failing packages with that user. (And perhaps re-try failed install process using new user as well...)

---

### Post by elibunt on 2010-07-18
Before I try installing OpenOffice again, you asked in post #38 for the output of sudo find -name '*openoffice.org3*', so here it is, if it is not too late:[INDENT]./.local/share/applications/openoffice.org3-draw.desktop
./.local/share/Trash/info/openoffice.org3-draw.desktop.trashinfo
./.local/share/Trash/files/OOO300_m9_native_packed-1_en-US.9358/DEBS/openoffice.org3-dict-fr_3.0.0-9_i386.deb
./.local/share/Trash/files/OOO300_m9_native_packed-1_en-US.9358/DEBS/openoffice.org3-draw_3.0.0-9_i386.deb
./.local/share/Trash/files/OOO300_m9_native_packed-1_en-US.9358/DEBS/openoffice.org3-writer_3.0.0-9_i386.deb
./.local/share/Trash/files/OOO300_m9_native_packed-1_en-US.9358/DEBS/openoffice.org3-en-us_3.0.0-9_i386.deb
./.local/share/Trash/files/OOO300_m9_native_packed-1_en-US.9358/DEBS/openoffice.org3-math_3.0.0-9_i386.deb
./.local/share/Trash/files/OOO300_m9_native_packed-1_en-US.9358/DEBS/openoffice.org3_3.0.0-9_i386.deb
./.local/share/Trash/files/OOO300_m9_native_packed-1_en-US.9358/DEBS/desktop-integration/openoffice.org3.0-debian-menus_3.0-9354_all.deb
./.local/share/Trash/files/OOO300_m9_native_packed-1_en-US.9358/DEBS/openoffice.org3-dict-es_3.0.0-9_i386.deb
./.local/share/Trash/files/OOO300_m9_native_packed-1_en-US.9358/DEBS/openoffice.org3-impress_3.0.0-9_i386.deb
./.local/share/Trash/files/OOO300_m9_native_packed-1_en-US.9358/DEBS/openoffice.org3-dict-en_3.0.0-9_i386.deb
./.local/share/Trash/files/OOO300_m9_native_packed-1_en-US.9358/DEBS/openoffice.org3-base_3.0.0-9_i386.deb
./.local/share/Trash/files/OOO300_m9_native_packed-1_en-US.9358/DEBS/openoffice.org3-calc_3.0.0-9_i386.deb
./.local/share/Trash/files/openoffice.org3-draw.desktop
./.gnome2/panel2.d/default/launchers/openoffice.org3-calc-1.desktop
./.gnome2/panel2.d/default/launchers/openoffice.org3-writer.desktop
./.gnome2/panel2.d/default/launchers/openoffice.org3-writer-1.desktop
[/INDENT]As for openoffice packages, for remove I used openoffice.org*, and for install I used openoffice.org but it didn't seem to include Writer (word-processor), so I'd be happy to take advice on that. I mainly need Writer and Calc, and a British English dictionary.

---

### Post by robsoles on 2010-07-18
All output above is with command executed from your home directory and I entirely can't blame you - I didn't specify to 'cd /' first but lets forget it for now.

IMHO best line to execute in terminal is
```
sudo aptitude -f install openoffice.org-calc openoffice.org-writer
```

this is based on (probably poor) assumption that you are only using spreadsheet and word processing really - to get an idea of the package names for the other major bits please open synaptic package manager in 'system'-'administration' and type 'openoffice' into the search bar, scroll down the major package components are actually lower down on the list.

Just listing the major package components you want in our line of terminal code should get you all the 'dependency' bits and pieces but I'll just help you work through it till we've got everything you want!

It is getting late there (11.00pm I think) and I want an early night so please don't hesitate to post again tonight but forgive me if I don't get back to you till morning!

---

### Post by elibunt on 2010-07-18
You were right which packages I need at the moment, as you see from my edits just before I received your post, plus British English dictionary. 

I tried sudo aptitude -f install openoffice.org-calc openoffice.org-writer
but got the following output:
[INDENT]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Segmentation fault
[/INDENT]From the log file viewer:

Jul 18 23:10:36 ubuntu kernel: [ 3922.154648] __ratelimit: 12 callbacks suppressed
Jul 18 23:10:36 ubuntu kernel: [ 3922.154654] aptitude[1962]: segfault at ee9c000c ip 081d5dcc sp bf907520 error 5 in aptitude[8048000+20b000]


An early night (ie before midnight) would be sensible for me too - the kids start back at school/kindy tomorrow after two weeks' holiday, so I have to stop my night owl ways.

---

### Post by robsoles on 2010-07-18
Peeped before beddies - mmmh, maybe we are attacking the wrong animals right now, let's refresh your copy of aptitude, try again and then if it fails again we'll personally kill it's cache (straight after I testing 'personally killing it's cache' in a VM!)

```
sudo apt-get purge aptitude

sudo apt-get -f install aptitude
```

If that goes through looking like we've made a fresh copy of aptitude on your machine then retry that openoffice installer command!

(Good morning!)

---

### Post by scouser73 on 2010-07-18
I've seen a couple of people that have had problems with Ubuntuzilla, my advice would be to remove Ubuntuzilla and install Firefox and Thunderbird manually using the following instructions.

**_Installing Mozilla Firefox_**

Download the **.tar.bz2** file from

[[COLOR="Red"]**Mozilla Firefox**[/COLOR]]("http://www.mozilla-europe.org/en/firefox/")


**1** - Extract the **.tar.bz2** file

**2** - Enter **gksudo nautilus** in terminal

**3** - Go to the folder **/opt**

**4** - Copy & paste the Firefox file that you extracted to **/opt**

**5 -** Enter these commands into **Terminal** > **sudo -i**

*Enter your password if asked.*

> **cd /opt**
> **chown -R username filename**

[COLOR="Red"]**Obviously the username refers to you, and the filename to the file**[/COLOR]

**6** - Go to **System > Preferences > Main Menu**

**7** - In Main Menu, click on **New Item**

**8** - In the **Name** field enter **Firefox**

**9** - In the **Command** field enter **/opt/firefox/firefox**

**10** - In the **Comment** field enter **Firefox**

[[IMG]http://img121.imageshack.us/img121/7329/screenshot2c.png[/IMG]](http://img121.imageshack.us/img121/7329/screenshot2c.png/)


**_Installing Mozilla Thunderbird_**

Download the **.tar.bz2** file from

[[COLOR="Red"]**Mozilla Messaging: Thunderbird 3.1**[/COLOR]]("http://www.mozillamessaging.com/en-GB/thunderbird/all.html")


**1** - Extract the **.tar.bz2** file

**2** - Enter **gksudo nautilus** in terminal

**3** - Go to the folder **/opt**

**4** - Copy & paste the Thunderbird file that you extracted to **/opt**

**5 -** Enter these commands into **Terminal** > **sudo -i**

*Enter your password if asked.*

> **cd /opt**
> **chown -R username filename**

[COLOR="Red"]**Obviously the username refers to you, and the filename to the file**[/COLOR]

**6** - Go to **System > Preferences > Main Menu**

**7** - In Main Menu, click on **New Item**

**8** - In the **Name** field enter **Mozilla Thunderbird Mail/News**

**9** - In the **Command** field enter **/opt/thunderbird/thunderbird**

**10** - In the **Comment** field enter **Mozilla Thunderbird Mail/News**

[[IMG]http://img121.imageshack.us/img121/7329/screenshot2c.png[/IMG]](http://img121.imageshack.us/img121/7329/screenshot2c.png/)

---

### Post by robsoles on 2010-07-18
> **scouser73 said:**
> I've seen a couple of people that have had problems with Ubuntuzilla, my advice would be to remove Ubuntuzilla and install Firefox and Thunderbird manually using the following instructions.

...

POSITIVE: Could fix firefox & thunderbird

NEGATIVE: If it fixes your problem then it will break you out of getting automatic updates for both of them.


I have become positive that your copy of aptitude is broken and that is definitely not a good thing. Please don't skip on replacing it for future convenience sake.

---

### Post by elibunt on 2010-07-19
I purged and installed aptitude this morning (over twelve hours ago), was then able to successfully install openoffice, and have not had any crashes today! (yet) Still could be just another interlude, but I'll wait to see if I get further problems before trying anything further such as removing Ubuntuzilla.

---

### Post by robsoles on 2010-07-19
Glad to hear about aptitude replacement and (so far) nice run with openoffice.

Has UbuntuZilla crashed since install or has been fairly stable by comparison of others?

---

### Post by elibunt on 2010-07-19
Wouldn't you know it, Firefox crashed about two minutes after I sent that last post, even though it had been running happily all day. I wasn't too surprised, though, because I didn't expect that fixing aptitude would fix the problems with Firefox and Thunderbird crashing, even though it was a necessary step.

I don't think Ubuntuzilla has crashed exactly - it has always gone smoothly when using it to update Firefox or Thunderbird - but it also runs checks in the background to see if updates are needed, and the log files might show that Ubuntuzilla has had some problems performing these checks. For example, at 8:54 yesterday morning (probably just after start-up so might be affected by that):

[INDENT]Jul 18 08:54:14 ubuntu UBUNTUZILLA: wget --tries=20 --read-timeout=60 --waitretry=10 -q -nv -O - [http://ubuntuzilla.sourceforge.net/updates/ubuntuzillalatestreleaseinfo.txt](http://ubuntuzilla.sourceforge.net/updates/ubuntuzillalatestreleaseinfo.txt)
Jul 18 08:54:14 ubuntu UBUNTUZILLA: Failed to retrieve Ubuntuzilla update info. Detailed error information follows.
Jul 18 08:54:14 ubuntu UBUNTUZILLA: Process returned code 4
Jul 18 08:54:14 ubuntu UBUNTUZILLA: []
Jul 18 08:54:16 ubuntu UBUNTUZILLA: wget --tries=20 --read-timeout=60 --waitretry=10 -q -nv -O - [http://ubuntuzilla.sourceforge.net/updates/ubuntuzillalatestreleaseinfo.txt](http://ubuntuzilla.sourceforge.net/updates/ubuntuzillalatestreleaseinfo.txt)
Jul 18 08:54:16 ubuntu UBUNTUZILLA: Failed to retrieve Ubuntuzilla update info. Detailed error information follows.
Jul 18 08:54:16 ubuntu UBUNTUZILLA: Process returned code 4
Jul 18 08:54:16 ubuntu UBUNTUZILLA: []
Jul 18 08:54:18 ubuntu UBUNTUZILLA: wget --tries=20 --read-timeout=60 --waitretry=10 -q -nv -O - [http://ubuntuzilla.sourceforge.net/updates/ubuntuzillalatestreleaseinfo.txt](http://ubuntuzilla.sourceforge.net/updates/ubuntuzillalatestreleaseinfo.txt)
Jul 18 08:54:18 ubuntu UBUNTUZILLA: Failed to retrieve Ubuntuzilla update info. Detailed error information follows.
Jul 18 08:54:18 ubuntu UBUNTUZILLA: Process returned code 4
Jul 18 08:54:18 ubuntu UBUNTUZILLA: []
Jul 18 08:54:20 ubuntu UBUNTUZILLA: wget --tries=20 --read-timeout=60 --waitretry=10 -q -nv -O - [http://ubuntuzilla.sourceforge.net/updates/ubuntuzillalatestreleaseinfo.txt](http://ubuntuzilla.sourceforge.net/updates/ubuntuzillalatestreleaseinfo.txt)
Jul 18 08:54:20 ubuntu UBUNTUZILLA: Failed to retrieve Ubuntuzilla update info. Detailed error information follows.
Jul 18 08:54:20 ubuntu UBUNTUZILLA: Process returned code 4
Jul 18 08:54:20 ubuntu UBUNTUZILLA: []
Jul 18 08:54:22 ubuntu UBUNTUZILLA: wget --tries=20 --read-timeout=60 --waitretry=10 -q -nv -O - [http://ubuntuzilla.sourceforge.net/updates/ubuntuzillalatestreleaseinfo.txt](http://ubuntuzilla.sourceforge.net/updates/ubuntuzillalatestreleaseinfo.txt)
Jul 18 08:54:22 ubuntu UBUNTUZILLA: Failed to retrieve Ubuntuzilla update info. Detailed error information follows.
Jul 18 08:54:22 ubuntu UBUNTUZILLA: Process returned code 4
Jul 18 08:54:22 ubuntu UBUNTUZILLA: []
Jul 18 08:54:24 ubuntu UBUNTUZILLA: Error downloading latest release info. Trying again, hoping for a different mirror.
Jul 18 08:54:24 ubuntu UBUNTUZILLA: last message repeated 4 times
Jul 18 08:54:24 ubuntu UBUNTUZILLA: Failed to retrieve Ubuntuzilla update info. This may be due to transient network problems, so try again later. Exiting.
[/INDENT]Today, each series of Ubuntuzilla entries at 12:00, 16:00 and 20:00, ended in the following way:

[INDENT]Jul 19 12:00:06 ubuntu UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 132, in getSystemOutput
Jul 19 12:00:06 ubuntu UBUNTUZILLA:     return result[0]
Jul 19 12:00:06 ubuntu UBUNTUZILLA: IndexError: list index out of range
[/INDENT]
Anyway, should I go ahead and remove Ubuntuzilla? And should I then remove Thunderbird and Firefox before installing as scouser73 explained? Or should I remove them and install using sudo aptitude -f install as robsoles suggested earlier?

Or should I leave those for now and do something about BIOS, or try booting with a live CD (still haven't tried that, would take a day or more to know if it made a difference), or try logging in as another user? All suggestions from further back, but in the light of what's happened since, which is the best to try first?

---

### Post by robsoles on 2010-07-19
What with being robsoles I am probably a bit biased!!!

Have a go at logging in as different user - that was a better suggestion than some would merit (*and also not something I started!!!)

Try my '-f' fix next and give it a little a while (if aptitude was corrupted by something then why shouldn't these others be?) - uninstall UbuntuZilla and then use '-f' installer line in terminal.
(PART OF LATTER EDIT: ) remove UbuntuZilla as proposed by scouser73 but pursue fresh install using '-f' in install line of Canonical's standard packages!

When that blows up in your face have a bash at what scouser73 suggested if it doesn't intimidate you at all but skip it if it worries you - ask more questions and make robsoles (or any rsole) think harder if unsure!!!!

---

### Post by RJARRRPCGP on 2010-07-19
> **elibunt said:**
> 
Most frequently it is Firefox and Thunderbird crashing, because they're the applications I use most. (Also F-Spot has crashed, but F-Spot frequently crashed before all this, so may not be related). 

Sometimes applications will run for a few hours and then crash (either suddenly close or freeze, it varies). Other times the application crashes before it even opens, and I just get the Mozilla crash reporter. 

Likely a hardware problem. Bad caps or a bad PSU can cause these symptoms.

[http://badcaps.net](http://badcaps.net)

Some symptoms you reported are also common if your processor is overclocked too much.

---

### Post by robsoles on 2010-07-19
> **RJARRRPCGP said:**
> Likely a hardware problem. Bad caps or a bad PSU can cause these symptoms.

[http://badcaps.net](http://badcaps.net)

Some symptoms you reported are also common if your processor is overclocked too much.

To check for bad capacitors on your motherboard take a look at the device in the picture on the page at [http://www.solarbotics.com/products/cp4700uf/](http://www.solarbotics.com/products/cp4700uf/) and observe the flat top of the cylindrical package - if the ones on your motherboard are bulging on top then replacing them is called for.

I might say though that I find motherboards with failing caps either have difficulty booting at all or if they make it through booting they either freeze or restart at what appears to be random intervals - I've been wrong before though I really haven't seen caps do this.

I am the IT and Production manager for a small electronics company and I've been playing with PCs for 25 years, I haven't seen a power supply cause specific programs to crash but I suppose there is some slim chance this could be happening if it is all programs you try to run. 

I would really expect the PC to randomly die in a general fashion and for the kernel to be reported in errors - **Have you got a multimeter elibunt?** There are a few pages on the internet that walk the user through testing a power supply and there is bound to be a video on youtube - I'll dig it up if you want to test your PS and you can't find a guide you are sure of.


I think that if OpenOffice crashes on you today it is well worth getting a LiveCD and trying to work off that for at least a couple of hours (or however long it took OpenOffice off your hard drive to crash) using a memory stick to store/access your work rather than your HDD.

If it crashes while running off the LiveCD then it is more likely to be your hardware but if it doesn't then there is a step we can take to fix your copies of things on the HDD and if we keep plodding along we are bound to find and finally take that step.

(No doubt some impatient person will next post that you should just reinstall the whole OS -  probably me in a couple more pages ;))

---

### Post by elibunt on 2010-07-19
I decided to remove and install the last two crashing applications before trying either the live CD or logging in as another user, because those steps could take at least a day of computer use (without ready access to the files I need to make that time productive) to test them properly, since I sometimes get a few hours or even like yesterday twelve hours without crashes anyway (although other times I'll get crashes within a few minutes of starting).

I've removed Ubuntuzilla and Firefox, and installed Firefox from the terminal using -f. I then installed Flash again (since it hadn't seemed to make any difference), removed Thunderbird and installed thunderbird-locale-en-gb using -f. All went smoothly, so we'll see what happens.

Earlier this morning though, after Firefox crashed while I was away from the computer (so I don't know the exact time but could have been 9:32), I checked the log file viewer and found the following message (the only message other than startup messages):

[INDENT]    Jul 20 09:32:46 ubuntu kernel: [ 1828.747630] __ratelimit: 12 callbacks suppressed
    Jul 20 09:32:46 ubuntu kernel: [ 1828.747636] slideshow[1848]: segfault at 8000000 ip 006fbcc6 sp b775ed00 error 4 in libglib-2.0.so.0.2400.1[6a2000+c8000]
[/INDENT]
Is that segfault significant at all?

I don't have a multimeter, but I have a friend who might have one perhaps.

---

### Post by lidex on 2010-07-20
See  this thread:
[http://ubuntuforums.org/showthread.php?t=1393931](http://ubuntuforums.org/showthread.php?t=1393931)

---

### Post by robsoles on 2010-07-20
> **lidex said:**
> See  this thread:
[http://ubuntuforums.org/showthread.php?t=1393931](http://ubuntuforums.org/showthread.php?t=1393931)

I followed that thread and a thread which was linked from that thread - these things relate to libglib but I don't see a direct correlation between them and the problems you started with elibunt.


Where you start 'Earlier this morning though, ...' it isn't clear if you are saying firefox crashed before or after you replaced it - can you please clarify that and whether or not you've had fresh crashes since the '-f' install or whether you were just asking this due to a crash on the 'pre' replacement one.


I suspect a faulty module and maybe it is libglib BUT the errors noted in the other threads talk about network connectivity problems and otherwise a lot of nautilus bits seg-faulting - rather than rolling libglib back to an earlier version in your situation it might be better refreshing the copy of it on your system.

Remember how aptitude was broken? I think the problem module is simply broken in the same way - binary became dodgy at some point or another and just replacing it will fix it the same as aptitude.

---

### Post by elibunt on 2010-07-20
Still crashing, will keep this short because it keeps crashing before I can finish. Will update properly tomorrow.

---

### Post by robsoles on 2010-07-20
Pretty sure libglib-2.0.so.0.2400.1 is part of following package so please post back the output from following command
```
sudo aptitude -f reinstall libglib2.0-dev
```

although replacing '2.0-dev' with '*' will possibly make it more sure to replace the package that really has libglib-2.0.so.0.2400.1

If that fixes the crashes I will be most pleased but it could still be worthwhile to look into updating your BIOS firmware, select 'failsafe defaults' in BIOS and check your M/B for fat caps if it is older than about 3 years.

---

### Post by robsoles on 2010-07-20
Just reviewed a few bits and pieces of this thread and am reminded of gnome-desktop-environment

I think I was probably wrong and a little research has shown me how harmless it would be if I was right, and how beneficial it might be if I was wrong, for you to **also** try this chestnut again:
```
sudo aptitude -f reinstall gnome-desktop-environment
```

If it's actually installed afterall then it will be replaced with a fresh copy of itself and if it isn't installed aptitude will say so in output.

---

### Post by elibunt on 2010-07-20
Before I act on your last couple of posts, my updater is having problems again, to do with a corrupted archive, but I've changed the source file and still have the problem: 
[INDENT]' Error: BrokenCount > 0' This usually means that your installed packages have unmet dependencies.
[/INDENT]
Synaptic identifies the broken package as libfreetype6-dev, installed version 2.3.11-1ubuntu2. Trying sudo apt-get upgrade through the terminal gives the following:

[INDENT]You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libfreetype6-dev: Depends: libfreetype6 (= 2.3.11-1ubuntu2) but 2.3.11-1ubuntu2.1 is installed
E: Unmet dependencies. Try using -f.
[/INDENT]
Does that mean I should run 'sudo apt-get -f install libfreetype6-dev'? Also, around the time I got the corrupted archive there was the following log file message:

[INDENT]Jul 21 11:10:50 ubuntu kernel: [ 9664.728195] __ratelimit: 12 callbacks suppressed
Jul 21 11:10:50 ubuntu kernel: [ 9664.728200] dpkg-preconfigu[2629]: segfault at bee7efcc ip 080bff91 sp bee7efd0 error 6 in perl[8048000+12c000]
[/INDENT]I also note that even though I've removed Ubuntuzilla, I still got the following log file message:

[INDENT]Jul 21 12:00:01 ubuntu kernel: [ 2596.929050] padlock: VIA PadLock not detected.
Jul 21 12:00:01 ubuntu UBUNTUZILLA: /bin/sh: /usr/local/bin/ubuntuzilla.py: not found
Jul 21 12:00:01 ubuntu UBUNTUZILLA: /bin/sh: /usr/local/bin/ubuntuzilla.py: not found
[/INDENT]

---

### Post by robsoles on 2010-07-20
> **elibunt said:**
> ...

Does that mean I should run 'sudo apt-get -f install libfreetype6-dev'? Also, around the time I got the corrupted archive there was the following log file message:

...


Yes, but also run the other two synaptic commands I gave in those two other posts - they cannot make anything worse but they can repair plenty!


Please tell me how you installed ubuntuzilla and then how you removed it - looks like it has left stuff behind that may (or may not) need cleaning up after.


EDIT: Also probably worthwhile perhaps
```
sudo aptitude -f reinstall dpkg
```

I'm going to try what I see as a bit of a radical experiment in one of my VM installations of Lucid (in about 6 hours when I get home from work). If it works out I have thought of a shortcut to getting all the problem packages replaced on your system without actually having to identify them - still worth a look at 'failsafe defaults' and 'fat caps' ideas!

---

### Post by elibunt on 2010-07-20
I ran 'sudo apt-get -f install libfreetype6-dev' and that's fixed the broken package problem. Then ran 'sudo aptitude -f reinstall dpkg' but I'm not sure if it worked properly or not:
[INDENT]Preparing to replace dpkg 1.15.5.6ubuntu4.1 (using .../dpkg_1.15.5.6ubuntu4.1_i386.deb) ...
Unpacking replacement dpkg ...
Processing triggers for man-db ...
E: Sub-process /usr/bin/dpkg received a segmentation fault.
A package failed to install.  Trying to recover:
Setting up dpkg (1.15.5.6ubuntu4.1) ...

Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
[/INDENT]Then ran 'sudo aptitude -f reinstall libglib*' but got the message 
[INDENT]Couldn't find any package whose name or description matched "libglib*"
[/INDENT]so tried 'sudo aptitude -f reinstall libglib2.0-dev' and that went smoothly.

Also ran 'sudo aptitude -f reinstall gnome-desktop-environment' and got the message that it is not currently installed. (But remember I do have gnome-desktop-data.)

I can't actually remember how I installed Ubuntuzilla because I followed instructions from a webpage, but I removed it using 'sudo apt-get remove Ubuntuzilla'. I may have installed it the same way as my husband, although I think I did it first, but he recorded his way as follows:

[INDENT]1) in terminal run:
echo -e "\ndeb  [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all  main" | sudo tee -a /etc/apt/sources.list > /dev/null
2) then run:
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com  C1289A29
3) and:
sudo apt-get update
4) Download ubuntuzilla deb from here:   [http://sourceforge.net/projects/ubuntuzilla/](http://sourceforge.net/projects/ubuntuzilla/)
[/INDENT]       One idea my husband has had is to put my hard drive into his computer and let me try it out for a few hours. Would stop him getting any work done for a while, but shouldn't run any risk of damaging his setup, right? If I don't get a crash it doesn't mean anything because a few hours  would not be long enough. But if I do get a crash, then it must be software not hardware.

My husband set BIOS to default last night, and also checked the temperature and voltage readings plus added the hardware sensor applet to the panel.

---

### Post by robsoles on 2010-07-21
> **elibunt said:**
> I ran 'sudo apt-get -f install libfreetype6-dev' and that's fixed the broken package problem. Then ran 'sudo aptitude -f reinstall dpkg' but I'm not sure if it worked properly or not:
[INDENT]Preparing to replace dpkg 1.15.5.6ubuntu4.1 (using .../dpkg_1.15.5.6ubuntu4.1_i386.deb) ...
Unpacking replacement dpkg ...
Processing triggers for man-db ...
E: Sub-process /usr/bin/dpkg received a segmentation fault.
A package failed to install.  Trying to recover:
Setting up dpkg (1.15.5.6ubuntu4.1) ...

Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

...

Perhaps re-run the command and see if it does it again or if it doesn't mention errors in second run.


> **elibunt said:**
> ...

Then ran 'sudo aptitude -f reinstall libglib*' but got the message 
[INDENT]Couldn't find any package whose name or description matched "libglib*"
[/INDENT]so tried 'sudo aptitude -f reinstall libglib2.0-dev' and that went smoothly.

Also ran 'sudo aptitude -f reinstall gnome-desktop-environment' and got the message that it is not currently installed. (But remember I do have gnome-desktop-data.)

... 

run it again with gnome-desktop-data, should only replace what you have with a fresh copy which eliminates something I suspect.

> **elibunt said:**
> ...

I can't actually remember how I installed Ubuntuzilla because I followed instructions from a webpage, but I removed it using 'sudo apt-get remove Ubuntuzilla'. I may have installed it the same way as my husband, although I think I did it first, but he recorded his way as follows:

[INDENT]1) in terminal run:
echo -e "\ndeb  [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all  main" | sudo tee -a /etc/apt/sources.list > /dev/null
2) then run:
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com  C1289A29
3) and:
sudo apt-get update
4) Download ubuntuzilla deb from here:   [http://sourceforge.net/projects/ubuntuzilla/](http://sourceforge.net/projects/ubuntuzilla/)

...

Ok, let's ignore it for now (looks like two alternative methods in one set of instructions to me!), we'll get back to it if we can't just walk around it.


> **elibunt said:**
> ...

One idea my husband has had is to put my hard drive into his computer and let me try it out for a few hours. Would stop him getting any work done for a while, but shouldn't run any risk of damaging his setup, right? If I don't get a crash it doesn't mean anything because a few hours  would not be long enough. But if I do get a crash, then it must be software not hardware.

My husband set BIOS to default last night, and also checked the temperature and voltage readings plus added the hardware sensor applet to the panel.

Don't pursue this idea about HDD to his PC for now, that could introduce issues to your setup regarding hardware if your PCs aren't physically a very very close match.

Good about BIOS to default, rules out another thing. Good about voltage and temperature checks. Rule out fat caps for me please.


EDIT: <snip>

---

### Post by elibunt on 2010-07-21
Okay, I've run 'sudo aptitude -f reinstall gnome-desktop-data', all went  smoothly. 
My husband had a look this evening and said the caps look  okay. 
And I've just run 'sudo aptitude -f reinstall dpkg' again, no  problems this time. 

No crashes since my post #63, but I'll let you know  if/when it crashes again. 

By the way, my husband's computer IS a  very very close match to mine (except for the wireless network card and  we've already eliminated that as the problem by trying a cable, and  also one of my USB ports is broken), because we bought identical  computers at the same time. Our monitors and keyboards are different,  but he would just be letting me try out his box with my hard drive and  the rest of my setup.

---

### Post by robsoles on 2010-07-21
Cool, but doesn't seem to me like we can 'value add' by breaking hubbie's time up on his PC.

I am another hour or more from trying the radical test in my VM that I mentioned in an earlier post but I might say that info I've managed to gather whilst serving my employer makes me think I will say it isn't worth trying.

Cool if we've nailed it - <snip>shouldn't post drunk</snip> we'll just have to keep BASHing it if not.

---

### Post by robsoles on 2010-07-21
I carried out the experiment - it did what I expected, which was to show me it wasn't worth pursuing.

None of my users, business or personal (family & work that rely on me for their 'happiness') have put themselves in a position for needing the Ubuntu equivalent of "Repair selected ??????? installation" so I am not entirely sure of Ubuntu simile at this point - researching next time I am not so inebriated and will post nearest equiv I can find unless you declare that problem really is gone (rather hoping circumstances of your last post continue freely!) or something else makes us decide not to pursue it!

---

### Post by elibunt on 2010-07-21
Something is still not right. No actual crashes (although I've been away from my computer most of the day), but my updater is having problems again. Here are the log file messages:
[INDENT]Jul 22 10:46:57 ubuntu kernel: [ 7284.415018] update-manager[2221]: segfault at 2554e46c ip 06c8a885 sp bfd09200 error 4 in libapt-pkg-libc6.10-6.so.4.8.0[6c52000+c8000]
Jul 22 10:46:59 ubuntu kernel: [ 7286.707929] update-manager[2226]: segfault at 253f046c ip 05fbc885 sp bf9ab9d0 error 4 in libapt-pkg-libc6.10-6.so.4.8.0[5f84000+c8000]
Jul 22 10:47:34 ubuntu kernel: [ 7321.341779] update-manager[2230]: segfault at 2543046c ip 06c24885 sp bfbfa010 error 4 in libapt-pkg-libc6.10-6.so.4.8.0[6bec000+c8000]
Jul 22 10:47:56 ubuntu kernel: [ 7343.427847] update-manager[2234]: segfault at 253d546c ip 053d9885 sp bf9e07c0 error 4 in libapt-pkg-libc6.10-6.so.4.8.0[53a1000+c8000]
Jul 22 10:48:03 ubuntu sudo: pam_sm_authenticate: Called
Jul 22 10:48:03 ubuntu sudo: pam_sm_authenticate: username = ...
Jul 22 10:48:03 ubuntu sudo: Passphrase file wrapped
Jul 22 10:48:10 ubuntu kernel: [ 7357.024120] synaptic[2239]: segfault at 2616546c ip 00e0d885 sp bf83bf00 error 4 in libapt-pkg-libc6.10-6.so.4.8.0[dd5000+c8000]
Jul 22 10:48:13 ubuntu kernel: [ 7359.892055] apt-check[2263]: segfault at 2687546c ip 00e0e885 sp bfc10110 error 4 in libapt-pkg-libc6.10-6.so.4.8.0[dd6000+c8000]
Jul 22 10:48:25 ubuntu kernel: [ 7372.236488] update-manager[2266]: segfault at 2541646c ip 03c6c885 sp bfd7a1d0 error 4 in libapt-pkg-libc6.10-6.so.4.8.0[3c34000+c8000]
Jul 22 10:48:27 ubuntu kernel: [ 7374.289937] update-manager[2270]: segfault at 2545b46c ip 089be885 sp bfc050a0 error 4 in libapt-pkg-libc6.10-6.so.4.8.0[8986000+c8000]
Jul 22 10:48:33 ubuntu kernel: [ 7379.837284] update-manager[2274]: segfault at 254e946c ip 06d6b885 sp bfc56990 error 4 in libapt-pkg-libc6.10-6.so.4.8.0[6d33000+c8000]
[/INDENT]I tried sudo apt-get update (fine) and sudo apt-get upgrade, but got:
[INDENT]Reading package lists... Done
Segmentation faulty tree... 50%
[/INDENT]The log file messages when I tried the upgrade were:
[INDENT]Jul 22 15:44:42 ubuntu kernel: [25149.794620] synaptic[2638]: segfault at 2608d46c ip 00b11885 sp bfd43bb0 error 4 in libapt-pkg-libc6.10-6.so.4.8.0[ad9000+c8000]
Jul 22 15:44:47 ubuntu kernel: [25154.740758] apt-check[2661]: segfault at 267b346c ip 00c3d885 sp bfbaeb70 error 4 in libapt-pkg-libc6.10-6.so.4.8.0[c05000+c8000]
Jul 22 15:44:59 ubuntu kernel: [25166.417667] synaptic[2665]: segfault at 2623346c ip 00255885 sp bfd439f0 error 4 in libapt-pkg-libc6.10-6.so.4.8.0[21d000+c8000]
Jul 22 15:45:26 ubuntu kernel: [25193.735216] update-manager[2671]: segfault at 2546646c ip 074ed885 sp bfbf91e0 error 4 in libapt-pkg-libc6.10-6.so.4.8.0[74b5000+c8000]
Jul 22 15:45:34 ubuntu kernel: [25201.657544] update-manager[2676]: segfault at 2555c46c ip 07854885 sp bfe2e440 error 4 in libapt-pkg-libc6.10-6.so.4.8.0[781c000+c8000]
Jul 22 15:45:51 ubuntu kernel: [25218.723834] synaptic[2681]: segfault at 2614846c ip 00acc885 sp bfea26e0 error 4 in libapt-pkg-libc6.10-6.so.4.8.0[a94000+c8000]
Jul 22 15:45:57 ubuntu kernel: [25224.746306] apt-check[2703]: segfault at 2682946c ip 009fb885 sp bf8a4960 error 4 in libapt-pkg-libc6.10-6.so.4.8.0[9c3000+c8000]
Jul 22 15:45:58 ubuntu kernel: [25225.138285] synaptic[2707]: segfault at 2629346c ip 00895885 sp bff7fa70 error 4 in libapt-pkg-libc6.10-6.so.4.8.0[85d000+c8000]
Jul 22 15:46:13 ubuntu sudo: pam_sm_authenticate: Called
Jul 22 15:46:13 ubuntu sudo: pam_sm_authenticate: username = ....
Jul 22 15:46:13 ubuntu sudo: Passphrase file wrapped
Jul 22 15:46:37 ubuntu kernel: [25264.776440] apt-check[2732]: segfault at 2686e46c ip 00b45885 sp bfd1f240 error 4 in libapt-pkg-libc6.10-6.so.4.8.0[b0d000+c8000]
Jul 22 15:47:16 ubuntu kernel: [25303.718650] apt-get[2735]: segfault at 2709546c ip 00148885 sp bfea2bb0 error 4 in libapt-pkg-libc6.10-6.so.4.8.0[110000+c8000]
[/INDENT]

---

### Post by robsoles on 2010-07-22
Please tell me output from following sequence of commands if errors appear to occur:
```
sudo aptitude -f reinstall apt

sudo apt-get update

sudo apt-get upgrade

```

---

### Post by elibunt on 2010-07-22
sudo aptitude -f reinstall apt:[INDENT]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REINSTALLED:
  apt 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 10 not upgraded.
Need to get 1,810kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
Get:1 [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid-updates/main apt 0.7.25.3ubuntu9 [1,810kB]
Fetched 1,810kB in 13s (131kB/s)                                                
Segmentation fault
dpkg: parse error, in file '/var/lib/dpkg/available' near line 31763 package 'python-gtksourceview2':
 field name `!This' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
Segmentation fault
Segmentation fault
[/INDENT]sudo apt-get update:[INDENT]
[List of packages]
Reading package lists... Done
[/INDENT]sudo apt-get upgrade:[INDENT]Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  krb5-multidev libgssapi-krb5-2 libgssrpc4 libk5crypto3 libkadm5clnt-mit7
  libkadm5srv-mit7 libkdb5-4 libkrb5-3 libkrb5-dev libkrb5support0
10 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,012kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid-updates/main libkrb5-dev 1.8.1+dfsg-2ubuntu0.2 [35.9kB]
Get:2 [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid-updates/main krb5-multidev 1.8.1+dfsg-2ubuntu0.2 [102kB]
Get:3 [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid-updates/main libk5crypto3 1.8.1+dfsg-2ubuntu0.2 [96.3kB]
Get:4 [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid-updates/main libgssapi-krb5-2 1.8.1+dfsg-2ubuntu0.2 [120kB]
Get:5 [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid-updates/main libkrb5-3 1.8.1+dfsg-2ubuntu0.2 [350kB]
Get:6 [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid-updates/main libkrb5support0 1.8.1+dfsg-2ubuntu0.2 [42.4kB]
Get:7 [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid-updates/main libgssrpc4 1.8.1+dfsg-2ubuntu0.2 [75.1kB]
Get:8 [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid-updates/main libkdb5-4 1.8.1+dfsg-2ubuntu0.2 [58.9kB]
Get:9 [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid-updates/main libkadm5srv-mit7 1.8.1+dfsg-2ubuntu0.2 [71.8kB]
Get:10 [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) lucid-updates/main libkadm5clnt-mit7 1.8.1+dfsg-2ubuntu0.2 [58.8kB]
Fetched 1,012kB in 6s (147kB/s)                                                
Segmentation fault
(Reading database ... 225219 files and directories currently installed.)
Preparing to replace libkrb5-dev 1.8.1+dfsg-2ubuntu0.1 (using .../libkrb5-dev_1.8.1+dfsg-2ubuntu0.2_i386.deb) ...
Unpacking replacement libkrb5-dev ...
Preparing to replace krb5-multidev 1.8.1+dfsg-2ubuntu0.1 (using .../krb5-multidev_1.8.1+dfsg-2ubuntu0.2_i386.deb) ...
Unpacking replacement krb5-multidev ...
Preparing to replace libk5crypto3 1.8.1+dfsg-2ubuntu0.1 (using .../libk5crypto3_1.8.1+dfsg-2ubuntu0.2_i386.deb) ...
Unpacking replacement libk5crypto3 ...
Preparing to replace libgssapi-krb5-2 1.8.1+dfsg-2ubuntu0.1 (using .../libgssapi-krb5-2_1.8.1+dfsg-2ubuntu0.2_i386.deb) ...
Unpacking replacement libgssapi-krb5-2 ...
Preparing to replace libkrb5-3 1.8.1+dfsg-2ubuntu0.1 (using .../libkrb5-3_1.8.1+dfsg-2ubuntu0.2_i386.deb) ...
Unpacking replacement libkrb5-3 ...
Preparing to replace libkrb5support0 1.8.1+dfsg-2ubuntu0.1 (using .../libkrb5support0_1.8.1+dfsg-2ubuntu0.2_i386.deb) ...
Unpacking replacement libkrb5support0 ...
Preparing to replace libgssrpc4 1.8.1+dfsg-2ubuntu0.1 (using .../libgssrpc4_1.8.1+dfsg-2ubuntu0.2_i386.deb) ...
Unpacking replacement libgssrpc4 ...
Preparing to replace libkdb5-4 1.8.1+dfsg-2ubuntu0.1 (using .../libkdb5-4_1.8.1+dfsg-2ubuntu0.2_i386.deb) ...
Unpacking replacement libkdb5-4 ...
Preparing to replace libkadm5srv-mit7 1.8.1+dfsg-2ubuntu0.1 (using .../libkadm5srv-mit7_1.8.1+dfsg-2ubuntu0.2_i386.deb) ...
Unpacking replacement libkadm5srv-mit7 ...
Preparing to replace libkadm5clnt-mit7 1.8.1+dfsg-2ubuntu0.1 (using .../libkadm5clnt-mit7_1.8.1+dfsg-2ubuntu0.2_i386.deb) ...
Unpacking replacement libkadm5clnt-mit7 ...
Processing triggers for man-db ...
dpkg: error processing man-db (--unpack):
 subprocess installed post-installation script killed by signal (Segmentation fault)
Errors were encountered while processing:
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)

Also, just before running these I noticed a couple of webpages showing "Adobe flash plugin has crashed" and the log file message:

Jul 22 16:03:54 ubuntu kernel: [26301.140619] synaptic[2752]: segfault at 2000010 ip 080b1267 sp bfd52270 error 4 in synaptic[8048000+af000]
Jul 22 16:15:33 ubuntu kernel: [27000.205035] slideshow[2830]: segfault at 1b7929c ip 004e503a sp b760ad94 error 4 in ld-2.11.1.so[4dc000+1b000]

The log file messages around the time I ran the above code were:

Jul 22 16:38:49 ubuntu kernel: [28396.252522] dpkg-preconfigu[2912]: segfault at 10a66314 ip 080a2748 sp bf895400 error 4 in perl[8048000+12c000]
Jul 22 16:38:49 ubuntu kernel: [28396.253601] dpkg-preconfigu[2906]: segfault at 10a66314 ip 080a2748 sp bf895400 error 4 in perl[8048000+12c000]
Jul 22 16:38:50 ubuntu kernel: [28397.026403] dpkg[2920]: segfault at 4000000 ip 0805fc61 sp bfc7b820 error 4 in dpkg[8048000+5c000]
Jul 22 16:38:50 ubuntu kernel: [28397.028398] aptitude[2897]: segfault at 28fc7d14 ip 08092e78 sp bfb67780 error 4 in aptitude[8048000+20b000]
Jul 22 16:38:53 ubuntu kernel: [28400.461007] apt-check[2921]: segfault at 5a000000 ip 005ad90e sp bfbd05a0 error 4 in libapt-pkg-libc6.10-6.so.4.8.0[575000+c8000]
Jul 22 16:39:18 ubuntu kernel: [28425.461882] apt-check[2941]: segfault at ee0f4584 ip 002c4c6b sp bfa92980 error 5 in libapt-pkg-libc6.10-6.so.4.8.0[262000+c8000]
Jul 22 16:39:43 ubuntu kernel: [28450.484318] apt-check[2961]: segfault at 12000000 ip 00955cb2 sp bfcc8010 error 4 in libapt-pkg-libc6.10-6.so.4.8.0[91d000+c8000]
Jul 22 16:40:08 ubuntu kernel: [28474.933984] dpkg-preconfigu[2968] general protection ip:80f4a75 sp:bfaa08f0 error:0 in perl[8048000+12c000]
Jul 22 16:40:12 ubuntu kernel: [28479.678290] frontend[3070] general protection ip:80f4a75 sp:bfd23000 error:0 in perl[8048000+12c000]

[/INDENT]

---

### Post by imagifier on 2010-07-22
Interesting, I'm also having the same problem. Been happening for a few days now.

---

### Post by robsoles on 2010-07-22
mmmh, should have remembered this from the one time I took the 'recovery' mode on startup - try this (both of you!)

restart your PC and while it is booting press and hold shift as soon as the hard drive becomes active after POST

Your boot menu will be displayed, select the option that includes 'recovery mode' in it's title.

A menu should come up which includes an option to 'repair broken packages' - take this repair option and when that process finishes and you are booted around to your desktop again try some stuff out and post back how good or bad that makes it for you!!!

---

### Post by robsoles on 2010-07-22
> **imagifier said:**
> Interesting, I'm also having the same problem. Been happening for a few days now.

I'd recommend reading through the thread and finding the bits about checking your hardware and applying those as well.

---

### Post by elibunt on 2010-07-23
Still crashing. A friend who's good with computers visited yesterday and tried recovery mode - using the escape key rather than the shift key. The menu came up but with a corrupted memory display, and it was impossible to navigate the menu. He tried connecting the keyboard with a PS2 adaptor, but made no difference. The five most recent kernels had corrupted memory display. The two oldest kernels would navigate to "repair broken packages" but he said there were no broken packages. He then recreated the swap file and ran a test on the hard drive cache. 

Still crashing this morning, so we rang our friend and his guess is hardware, perhaps the graphics card but first my husband's going to try swapping the RAM (even though it passed Memtest). We think we now have a quicker way to test, by seeing whether it displays correctly in recovery mode rather than just waiting for a crash.

---

### Post by robsoles on 2010-07-23
Sounds fairly convincing that it's your hardware but popping your HDD into hubbie's machine and retrying the recovery option off the GRUB boot menu may reveal it even better.

If the files involved in recovery mode are 'skewered' on the hard drive then they will look a mess on hubbie's PC as well - if the recovery files are skewered then it's again no guarantee that your hardware has the problem - difficulty is that hardware can lead to broken files and broken files can lead to more broken files as well!


Have you tried booting and running off a LiveCD for a couple of hours? You could put some of your work on a memory stick and try to work on it using OpenOffice off the LiveCD or you could just surf the internet - this gives your hardware (minus HDD) a (hopefully) fair chance of revealing if it is the problem after all.

---

### Post by elibunt on 2010-08-06
Just a quick update. Short version - it was almost certainly the motherboard/PSU/CPU. 

Long version - I couldn't get a live CD to work on my computer, I just got the following message: The installer encountered an irrecoverable error. A desktop session will now be run so that you may investigate the problem or try installing again." The live CD worked fine on my husband's main PC and also his laptop though. He also ran checks on the CD and it passed.

I then tried my hard drive in hubby's computer for a couple of hours and it went fine, apart from recovery mode which was still impossible to navigate for the most recent kernels. For over a week now, I've been running my hard drive on a borrowed machine, and have had no problems. So it seems pretty clear it must be my hardware. Since the voltages were okay and replacing the graphics card or RAM didn't help, I guess it is probably the motherboard and/or CPU. So I have reluctantly accepted I'll just have to buy a new computer, although I can transfer the RAM, graphics card, sound card & hard drive. (Well actually, hubby will get a new computer and I'll get his. He's not exactly unhappy about this!) 

I'll mark this solved if (when) a new computer does fix the problem.

---

### Post by robsoles on 2010-08-08
Thanks for the lesson - I wish I had pursued this idea I had in post #2 to this thread: How does it go from the LiveCD?

It's annoying that with my hands on your PC personally I would have probably wasted less than 5 minutes finding the root of the problem where this is page #8 - I am pretty drunk now or I would just be (*what I currently see as dumb but tomorrow will wish I didn't post about) biting my tongue some more right now!

---

### Post by elibunt on 2010-08-08
Yeah, don't you love hindsight? Around post #51, when I wondered which of several options I should try next and brought up your live CD suggestion again, I think we were both assuming it would take a couple of hours to test the live CD, so it was just one of several things to try. 

When the live CD wouldn't run at all, and just gave a cryptic error message, that wasn't really what we'd expected. It's possible that bad hardware is the only reason a good live CD would give that message, I don't know, but anyone getting that message would probably want to do some more checks anyway before tossing out their computer. For me, it was testing my hard drive for a lengthy time on two lots of different hardware that really clinched it. 

I've learned heaps along the way, so thanks again for all your help. I'm sure that others with tricky hard-to-nail-down problems will find plenty of things from this thread to try out.

---

