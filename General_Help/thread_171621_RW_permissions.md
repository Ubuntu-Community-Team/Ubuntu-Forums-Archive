---
title: "RW permissions"
date: 2006-05-07
forum: General Help
---

### Post by infinitelink on 2006-05-07
Because there are like a billion results for "permission" and all the various combinations of that word and read, write, user, etc. I'm just going to post a new thread (after having search for days before).

I'm running Ubuntu 5.1. I can't write to my other partitions becasue, as I'm told, only the "owner" can write to the file. I'm trying to write to /media/hda2. My username is "infinitelink" and the "owner" is root-John Bradley Bulsterbaum (me). Now, I tried one posts advice: "Properties" (of file)-->permissions-->[drop-down menu to change owner] and nothing, there is no menu. In fact, why does the system set files as owned by root period? Isn't this a horrible design flaw? After all, I'm not the only person with this problem, there are entrie threads, post-after-post, of people with this same problem.

I tried following some unix-guide and entered chmod a+r+w /media/hda2 as root, but I guess that only changes it for root, (i.e. it stays the same in this case). 

How can I change this, and assume I know nothing about linux/unix commdands please, because I don't. Saying "do chmod a..." or a u=rw... won't help. 

If anyone can help me with this, thanks.

John Bradley Bulsterbaum

p.s. I can't believe, though, that this has been so overlooked! And the want to be "edgy" with the next release? How about making a linux system truly user-friendly! There's years more to go. Still needs better defaults, a program-install system where files go in one place, ability to make folders in dialogs (in the directory being viewed), many many guis, for example, to change owners/groups/permissions, and especially DECENT and complete documentation of functions. This list could keep going!

I don't mind learning if it were in any way possible, but I'm finding nothing that is conducive to that effort, and frankly I'm getting fed-up with even Ubuntu, sad if it's supposed to be "friendly." How about hiring-on normal, non-programming, non-geek/nerd, non computer-literate, untrained, unhelped, clueless computer users (i.e. Windows, most of the time, users) and have them tell the team what they can/can't do (without asking "how can I") in basic tasks and *then* building-in functionality from there? Keep the geek-tools (I like some of them too, probably will more when I figure out how to actually use them all), but make it a true user-friendly distro.

: )

---

### Post by aysiu on 2006-05-07
[QUOTE=infinitelink]Because there are like a billion results for "permission" and all the various combinations of that word and read, write, user, etc. I'm just going to post a new thread (after having search for days before).

I'm running Ubuntu 5.1. I can't write to my other partitions becasue, as I'm told, only the "owner" can write to the file. I'm trying to write to /media/hda2. My username is "infinitelink" and the "owner" is root-John Bradley Bulsterbaum (me). Now, I tried one posts advice: "Properties" (of file)-->permissions-->[drop-down menu to change owner] and nothing, there is no menu. In fact, why does the system set files as owned by root period? Isn't this a horrible design flaw? After all, I'm not the only person with this problem, there are entrie threads, post-after-post, of people with this same problem.

I tried following some unix-guide and entered chmod a+r+w /media/hda2 as root, but I guess that only changes it for root, (i.e. it stays the same in this case). 

How can I change this, and assume I know nothing about linux/unix commdands please, because I don't. Saying "do chmod a..." or a u=rw... won't help. 

If anyone can help me with this, thanks.[/quote] It sounds as if it's a Windows partition, and I agree with you on this--why Ubuntu defaults to mounting Windows partition with no read/write access is ridiculous. Either don't mount it at all, or mount it properly. Knoppix has had this functionality for years now--the partitions appear on your desktop, and when you click on them, they mount and open in one click.

In the meantime, follow these instructions:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

> How about making a linux system truly user-friendly! They have. Mepis and PCLinuxOS are it. Linspire comes close, depending on the user. > There's years more to go. No there isn't. Linux distributions will continue to improve for years to come, but right now, they are very usable. > a program-install system where files go in one place, Sounds like [GoBoLinux](http://www.gobolinux.org/). [Syllable](http://www.syllable.org/) is also implementing something similar to what you're talking about. Frankly, I think it's interesting but unnecessary if you install from the repositories. > ability to make folders in dialogs (in the directory being viewed) Um, you can already. > many many guis, for example, to change owners/groups/permissions, Already exists, just not for Windows partitions. Windows partitions don't support Linux permissions. > and especially DECENT and complete documentation of functions. There's plenty of documentation--in fact, it's built right into the installation. See that life preserver on the Gnome panel? > This list could keep going! Yes, and most of it would keep naming things that already exist.

> 
I don't mind learning if it were in any way possible, but I'm finding nothing that is conducive to that effort, and frankly I'm getting fed-up with even Ubuntu, sad if it's supposed to be "friendly." How about hiring-on normal, non-programming, non-geek/nerd, non computer-literate, untrained, unhelped, clueless computer users (i.e. Windows, most of the time, users) and have them tell the team what they can/can't do (without asking "how can I") in basic tasks and *then* building-in functionality from there? Keep the geek-tools (I like some of them too, probably will more when I figure out how to actually use them all), but make it a true user-friendly distro. I only partially agree with you on this. Ubuntu is not a truly geek distro--unlike Gentoo, Slackware, or Linux from Scratch. It is not, however a good first distro for ex-Windows users. I tried it out early on in my Linux adventure, and I was turned off, too, by how un-user-friendly it appeared. Mepis was more my cup of tea when I was first starting out (keep in mind, this was only a year ago).

After I got tired of Mepis, though, I found Ubuntu to be an excellent *second* distro. I'd seriously consider giving Mepis a shot if I were you. Best of luck whatever you do.

---

### Post by infinitelink on 2006-05-07
It's Fat32. I'll try the psychocat instructions in a moment. The partition was created *with* GParted too. 

What I mean by my commons, is that user-friendly is "out-of-the-box." People often counter "Windows this/that," but it's useless because it really does work out-of-box, even if it crashes in 10 minutes, though I know people that have never had a single problem.

If the guis are exist, why aren't they included? What about organization? How about themes/window-settings, destkop backgrounds, splash-pic (log), etc. being under "display"?

What about installing drivers, for instance, one-click? 

The gobo-linux like idea (putting all program files in one directory with each program and its parts) is, of course, windows-like, but without out it there are major problems. Namely, that if I update system-part "a" program "2" breaks while 3-5 are okay...dependency hell. Also, putting each program into a well-defined space means the user can manually find and clean clutter when necessary.

Ubunut, aiming for the stars, needs to think about making well-defined hooks for programs to build onto (for programs to run) and keeping compatibility working. For instance, FF 1.5 isn't officially available for Ubuntu 5.1, I used automatrix, why isn't FF 1.5 availabe? I know it needs to be "built," but one crux of linux is the speed it changes, not necessarily improves (though usually it is), but also breaks itself as this is happening. Hooks Baby! Without them a lot of interested groups just won't accept linux, (I've been reading reports of evaluations of open-source which were commission to determine whether or not it was suitable for use--the main subject was linux). Furthermore, without them, a lot of commercial software firms aren't going to consider the platform either, and they're crucial to its success.

I had linspire, thanks for the advice too, but it wasn't much better. Pay to install free programs? Sure, maybe a few, but not all. Also, it was missing many common tools that without, even my programming friends couldn't figure out how to get things running. One was installing looking-glass, for instance, for the fun of it (I have 2 gigs of ram) and a bunch of tools were missing, becasue he kept typing-in the commands and the basics just weren't there (or accessible).

Oh yeah, thanks again though, toodles. : )

---

### Post by B.Ati on 2006-05-07
I understand your problem, because I have the same feeling most of the time. But when I think it over its because I think as SINGLE USER on MY PC on MY DESK. I want just to use it, all of it, without restriction,  and at the same time to have all the security. But here is the contradiction, it is not only mine if it is connected to net. And a lot of PCs are in offices containing very sensitive data. You just MUST have a system telling what belongs to whom. Like with every other property. You cannot walk into your boss's offices and search his desk,...We are using keys for almost everything. Stop thinking as a single-user (it was okay in the era of MS-DOS) and you will see the problem more clearly. 

Windows sucks with security EXACTLY because when something gets your machine from internet it gets EVERYTHING, it can sit in command post. In *NIX systems it is only a guest in the hall waiting for the USER of the house to decide what to do with it. It cannot EXECUTE until it doesnt have the priviliege to do so. Even if it is executed it can only damage  the USER domain, unless it is run by ROOT.

So the conclusion is that it IS a nuissance if you want to use your HOME computer (like all the locks and keys in our live) but it is necessary. However there are easy ways....
1. Start terminal 
2. Type sudo nautilus ( or the name of your filemanager...)  Voila, you are using the whole system as a ROOT through your filemanager. Just like you would in Windows. No need for CHMOD etc...
3. Right-click with your mouse on the DIRECTORY or FILE whose ownership you want to change
4. At the bottom of the menu chose PROPERTIES
5. You can rename your directory or file here, but wait to see the rest...
6. Click on the third tab -(ownership?, privileges? I cannot tell - because Im using it in my native hungarian :) 
7. You can simply change the owner. Or you can leave the owner but grant Write/Execute privileges to the group, or anybody...

Hope it helped. But be warned, if you make a WINDOWS from your *NIX system, you might lose safety.

---

### Post by kabus on 2006-05-07
[QUOTE=infinitelink]
Ubunut, aiming for the stars, needs to[...]
[/QUOTE]
Maybe you should learn how to use the system before diagnosing its supposed shortcomings.

---

### Post by aysiu on 2006-05-07
[QUOTE=infinitelink]
What I mean by my commons, is that user-friendly is "out-of-the-box." People often counter "Windows this/that," but it's useless because it really does work out-of-box, even if it crashes in 10 minutes, though I know people that have never had a single problem.[/QUOTE] Windows doesn't work out of the box unless it comes pre-installed by some company like Dell. I've installed Windows twice from scratch, and both times it was a nightmare.

I still don't know what you're talking about with those GUI frontends not existing for those particular tasks. They exist. Change permissions, right-click the file or folder. Make a folder, right-click on an empty space and select "new" and then "folder." I don't understand the problem there. You're making up problems that don't exist.

As for the Firefox thing, I think anyone who feels the need to have the absolute latest version of Firefox should have no problem running [this script](http://www.psychocats.net/ubuntu/firefox) or Automatix. Anyone else doesn't care about versions and can definitely wait six months. In fact, a lot of people in my office (who use Windows) are still running Firefox 1.0.4 or 0.9, believe it or not. Most Windows users do not update their software.

And the only time I've run into dependency hell in Ubuntu is when I added in bad repositories (I think accidentally mixed Hoary and Breezy ones once). If you stick with the standard repositories, you should be fine.

Please.

There are actual problems with Ubuntu. You don't need to make up ones that don't exist.

And if you think things are real problems, file bug reports on them.

[What's better than whining on the forums? Making a difference](http://www.ubuntuforums.org/showthread.php?t=78741)

P.S. I noticed you didn't like Linspire, but you haven't tried Mepis or PCLinuxOS. Are you deliberately trying to poo-poo Linux? I told you in the second post that Ubuntu is not a good first distro. I mentioned Linspire just because it's good for a particular group of ex-Windows users. Mepis and PCLinuxOS are "out-of-the-box" friendly *and* cost-free. They both use Synaptic Package Manager to install software, and they don't need Automatix have all the proprietary codecs most users love.

---

### Post by infinitelink on 2006-06-07
I just returned to this thread after a while and found some attempt to help, but very little. The guy who gave me the "maybe you should learn your system..." junk obviously doesn't get user-friendliness in an OS. The "I had to configure Windows" guy was more help, and I appreciated his attempts, but I've also installled Windows many times, from scratch, and it was never difficult, worked perfectly. In fact, I've installed it for many many people, diagnosed it too, it has tools for everything, but eventually it DOES break and become a pain-in-the neck. Linux works great, mostly, *if it's useable.* I've tried using the properties-->permissons methods. I check the boxes and they uncheck themselves. I had a a programmer take a look, the guy is studying engineering for software design and he's a linux programmer: he coudn've fix this. He worked on this for over an hour and gave up.

There are some "duhs" that normal users can just say "this needs to be done," that Linux systems don't seem to ever impliment. For example, the idea of putting all files of a program in one directory. "not necessary with a package manager..." well, yes it is, if you want to manage it without having to track dependency hell. I know that term.  I've re-installed this system twice. I'm about to install dapper, but I can't because I'm on a wireless connection without the ability to download a single file which I can simply point-click to install after I re-install: the problem is that I need to install windows. the nd-whatever tool for a Gui'd ndiswrapper, afterwards to use my wireless card (which, currently, I need the "great" package-manager for, because that thing IS a dependence-hell to deal with), and can't because I can't access the internet without the wireless which I can if I can download the package from the internet through the pm...get the picture?
The suggestions are simplification for the sake of the system's success. Also, a normal user doesn't want the inability to change permissions. Oh well, for those who tried to help instead of taking the all-out defend-linux-at-all-cost geek faschist-attitude, thanks kindly. Oh yeah, and to the comment boy: I would learn about the system if the documentation was worth anything, or better yet, if it existed. I'm all business, in people, not software, so don't give me junk, and I won't give it to you. Grow up little boy. People first. Thanks guys.

---

