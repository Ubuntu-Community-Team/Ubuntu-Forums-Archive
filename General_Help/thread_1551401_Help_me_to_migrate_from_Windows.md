---
title: "Help me to migrate from Windows"
date: 2010-08-12
forum: General Help
---

### Post by hathiphnath on 2010-08-12
Hi all!

I tried migrating from Windows XP to Mac OS X several months ago and this resulted in an astounding failure. I was amazed how integral the *taskbar* was to my desktop experience. As a result, I tried other alternatives to Window XP, including Windows 7 while having had sporadic Ubuntu dealings for a few years now. I'm also considering getting more acquainted with BSD, but in the terms of developing and features, I don't think it can compare to Ubuntu desktop environment at the moment.

In short, XP doesn't cut it for me anymore and I'm planning on getting new PC with September the 1st discounts that will hopefully pop up. Also, I'm seriously considering purchasing a bundled Windows 7 licence with it... which, as you all know, isn't quite cheap.

While I compared the price of Windows 7 to the overall likely cost of the new PC, I realised that Windows itself aside, I use almost no paid software, although a bunch of closed source free ones. So, I tried to compile a more or less comprehensive list of what has stopped me from migrating to Ubuntu so far.

With your help, I hope to find open-source alternatives to  replace the closed-source apps that I've come to see as invaluable.

For starters, software issues. If you read "no alternative" think of it as followed by "that I know of".

- no "save as .rtf" option in the pidgin conversation window (I say "pidgin" not "IM app" as pidgin IS my preferred IM app on linux; I know it logs conversations automatically, but saving a selection of them as .rtf's is an ESSENTIAL feature I need on top of that)
- no alternative to [_stardock/objectdock + stack docklet_]("http://www.youtube.com/watch?v=XFqfdqYhTWM") (I don't use it as primary app launcer as this guy in the video, but to quickly access images from pre-defined folders, so, displaying the thumbnails is essential; if this explanation is confusing, tell me so, and I'll make a video to explain)
- no alternative to [_Format Factory_]("http://www.formatoz.com/") (after discovering FF, converting audio/video files was FINALLY not a pain anymore! I'd hate it to be a pain *again*)
- no alternative to [_Tag&Rename_]("http://www.softpointer.com/tr.htm") (this is the only paid app I was talking about)
- no (real) alternative to [_IrfanView_]("http://www.irfanview.com/") (I don't want to launch up GIMP for every minor cropping)
- no alternative to [_VirtualDub_]("http://www.virtualdub.org/") 

After using Windows 7, I found several features that I would not migrate without:
- integrated search in the Explorer's upper right corner (it searches the both the file names and file contents in the *active folder* (and subfolders) and you can easily give parameters for both, say... filename:keyword1 keyword2 "searched expression in addition to the previous two keywords"; simple, flexible, I love it!)
- click'n'drag rearrangable taskbar (you're used to the browser being the leftmost window on the taskbar, but closed it accidentally? while it appears rightmost when you relaunch the app, you can easily drag it around on the taskbar and freely pick a spot on where you want it to be)
- snap the window to cover half a screen ([_just excellent!_]("http://www.youtube.com/watch?v=MzQQcdw1qmY"))
- searchable start menu and launching apps as you've searched them, needing never to touch the mouse (is such thing available for GNOME?)

Misc notes:
- I own an iPod and I love the album cover based interface of iTunes, if only it was less bloated. didn't like RythmBox when I last tried to use it, but since it supposedly has iPod support now, I'm giving it another shot
- Transmission isn't IMO a aviable alternative to uTorrent, but I guess I could live with that
- I also liked the Snipping Tool for taking screenshots? Anything alike for linux out there?

I think you guys can nail *most* of these issues. Prove me wrong and nail them *all*! :)

---

### Post by 3Miro on 2010-08-12
Moving to a new system always requires going through a learning period, since you are a power user, this period will be longer and harder. There is no way for you to get to use a new system without a few somewhat painful months of learning new apps and features (but go ahead and prove me wrong ;) )

Here is a more detailed answer:

- on the windows 7 features:
From what I hear, it will be best for you to try KDE. Many of the windows 7 features that you list are not in Gnome or are somewhat harder to set up. KDE looks a lot like windows and will be much easier for you. Kubuntu (as in Ubuntu + KDE) is probably not the best KDE distro, but I have used it in the past and it worked fine for me. You can also take standard Ubuntu and install KDE on it so you can have both KDE and Gnome on one place.

- on the misc features
I don't use iTunes so I don't know. I don't see Transmission as being inferior to uTorrent in any way, however, if you are using KDE you should use ktorrent, which in terms of interface is almost a uTorrent clone (or uTorrent is clone of ktorrent since the KDE app comes first). As for snipping tool, you can play around with the default tool for snapshots, I am not sure exactly what features it has and what you need.

- on .rtf files: I would check to see what Open Office and AbiWord can do, but basically I don't know.
- on the dock features: Gnome has Awn and Cairo dock, KDE has fancy apps, look them up to see what features they have and what you need.
- on Format Factory: look up ffmpeg and mencoder, those are command line tool, however, I am sure they can do prety much everything FF can.
- Tag and Rename looks a lot like EasyTAG (at least form the screenshots), I like EasyTAG and besides that there are many other tag editing programs in Ubuntu.
- as for IrfanView and VirtualDub, you have to wait for a replay from someone who knows.

You should note that some windows programs will may run well in wine and/or VirtualBox. Neither one is a "silver bullet", but they can help with many features.

If you are looking for a Ubuntu computer in the USA, you should check System76, they do have a good selection, great support and you are guaranteed that your system will be 100% compatible with Ubuntu.

---

### Post by dabl on 2010-08-12
I'm going give you a couple of things:

1. Two bits of advice
2. Some links to useful information that will help you make your choices.

First, your post says "migrate", but after reading it, I think you're on a mission to "replicate" your Windows environment.  That's not gonna work.  If you are working on a theory that you can save $150 on an OS license, and still have all your Windows software working as you are accustomed to having it on your Windows system, then you are doomed to fail.  **Linux is not Windows**.

Second, there is a Windows translation package, named "wine", that will run lots of common windows applications.  But, it has its limits -- gaming graphics will not be as glorious and responsive as on a native Windows installation, in most cases, and complex applications (specialized databases, for example) don't all work correctly on wine.  So, you could do a trial installation of Ubuntu, and then install wine, and try out your Windows apps on it and see how they work.

Now, here is some useful information for you:

[http://www.libervis.com/wiki/index.php?title=Table_of_Equivalent_Software](http://www.libervis.com/wiki/index.php?title=Table_of_Equivalent_Software)

[http://www.linux.ie/newusers/alternatives.php](http://www.linux.ie/newusers/alternatives.php)

[http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)

---

### Post by hathiphnath on 2010-08-12
> **3Miro said:**
> Moving to a new system always requires going through a learning period, since you are a power user, this period will be longer and harder. There is no way for you to get to use a new system without a few somewhat painful months of learning new apps and features (but go ahead and prove me wrong ;) )Of course it won't be easy, but I'm not getting there unless I try ;)

> **3Miro said:**
> From what I hear, it will be best for you to try KDE. Many of the windows 7 features that you list are not in Gnome or are somewhat harder to set up. KDE looks a lot like windows and will be much easier for you. Kubuntu (as in Ubuntu + KDE) is probably not the best KDE distro, but I have used it in the past and it worked fine for me. You can also take standard Ubuntu and install KDE on it so you can have both KDE and Gnome on one place.I have only vaguely touched the KDE and it did not appeal to me as much as GNOME, but that may have been a first glance issue. But what's lacking in kubuntu? Are there better distros available? And in if yes, better in what regard? I'm looking at ubuntu right now as I've had many positive experiences with the community in the past and it seems to be developed the hardest, and with most resources.

> **3Miro said:**
> - on .rtf files: I would check to see what Open Office and AbiWord can do, but basically I don't know.With this, you missed my point. I want to be able to *save* an IM conversation to a separate file if I need to, without digging in the log files.

> **3Miro said:**
> If you are looking for a Ubuntu computer in the USA, you should check System76, they do have a good selection, great support and you are guaranteed that your system will be 100% compatible with Ubuntu.I'm in Eastern Europe, but thanks anyway :)

I'll start trying the suggestions out once I get some more responses that hopefully cover the whole spectrum of my issues.

---

### Post by hathiphnath on 2010-08-12
> **dabl said:**
> First, your post says "migrate", but after reading it, I think you're on a mission to "replicate" your Windows environment.  That's not gonna work.  If you are working on a theory that you can save $150 on an OS license, and still have all your Windows software working as you are accustomed to having it on your Windows system, then you are doomed to fail.  **Linux is not Windows**.Did I really come off being that rigid? I don't expect any of my Windows software to work on ubuntu. That's why I'm asking the community to help me find alternatives, which I would probably not be able to find myself for the lack of my experience on the platform.

That said, I *do* have some expectations to the GUI beyond it simply being functional, and so I'm stating things that I've come to see as essential. There are so many customisation tricks out there (compiz for example) that I've never heard of. How can people suggest me solutions or alternatives if I don't make clear what my expectations are?

In other words, if searching from a specific folder was a impossible under OS X, a hassle under XP and a breeze under 7, I see nothing wrong in stating that if I migrate to some other platform, I also expect the search to be a breeze, and then defining what I mean by it :)

> **dabl said:**
> Second, there is a Windows translation package, named "wine", that will run lots of common windows applications.Yes, I know of wine, and in my experience it's a huge hassle. I'd prefer an alternative application and missing some features any time over wine.

> **dabl said:**
> Now, here is some useful information for you:Thanks for the links!

---

### Post by 3Miro on 2010-08-12
> **hathiphnath said:**
> 
I have only vaguely touched the KDE and it did not appeal to me as much as GNOME, but that may have been a first glance issue. But what's lacking in kubuntu? Are there better distros available? And in if yes, better in what regard? I'm looking at ubuntu right now as I've had many positive experiences with the community in the past and it seems to be developed the hardest, and with most resources.


Which version of KDE did you try. KDE 3.5 is the obsolete version and it is not much different from Gnome, KDE 4.x is the new version and it is the one you should be using. KDE was developed almost concurrently with Vista and many of the so called "new" features of windows 7 have been in KDE 4.2 and 4.3 long before. KDE 4.x also comes with features, such as searchable menus, right out of the box.

Ubuntu is a Gnome-centric distro, which means that apps and features are tested exclusively for Gnome. With KDE, there is always a chance that something will not run right off hand. The biggest issue that I have seen comes from the sound. KDE and Gnome use different sound systems that are not fully compatible and sometimes it happens that if you open couple of programs in KDE one of them will lose the sound. I am not sure how much of that has been cleaned in the new Kubuntu 10.04 with KDE 4.4.

Other KDE distros are OpenSusa, Mandriva, Mint and Sabayon. Ubuntu has the largest repository database, most users and largest community, it is also the only distro that tries to assume that the users don't know absolutely anything about computers, so it good for beginners. My advice is to stick with Ubuntu and its variants at least for now, but you can also look around if you want.

---

### Post by dabl on 2010-08-12
> **hathiphnath said:**
> Did I really come off being that rigid? 

I didn't mean "rigid" in a bad way.  :)

It sounds like you have some well-developed work flows, using your Windows applications, and you are very efficient by following your existing methods, and you fear to lose efficiency by having to change methods.  That's normal and natural -- actually it is a good instinct.

I made the migration to Linux (in my personal life, not my office life) about 4 years ago.  As it happens, there is a Windows software package that does a very important job for me, that has no equivalent in Linux.  It is a special-purpose (genealogy) database built on MS Visual FoxPro.  So, after trying wine and finding it inadequate, after buying a Win4Lin license and finding it also inadequate, I eventually discovered VMware Player and learned to use that very effectively. The latest version of VMware, 3.0.x, is far more user-friendly and powerful than it was 3 or 4 years ago.  On my hardware and using my Windows application when I was still dual-booting, I did some benchmarking, and found that my application actually ran 95% as fast on VMware as it did on a native Win XP installation.  So it is a small performance penalty to run it on VMware Player, under Linux. But of course, you still need a valid Windows license to install it on a VM.  (I'm presently running Win 7 Pro on my VM).

Some of your workflows, for example the saving of Pidgin logs in .rtf format, are so specialized that I'm doubtful that you're going to find an exact replacement in a Linux package.  If those specialized workflows are critical to your efficiency, then maybe you should re-evaluate the move to Linux, and/or consider putting a Windows OS on a VM and running them that way.

---

### Post by hathiphnath on 2010-08-12
> **dabl said:**
> Some of your workflows, for example the saving of Pidgin logs in .rtf format, are so specialized that I'm doubtful that you're going to find an exact replacement in a Linux package.I know the .rtf-saving issue is the most specific and perhaps even silly, but I figured that since there are so many extensions out there, there's no harm in asking. I have no idea how hard it would be implement either. It could be a couple lines of code, or it could be several days of hard work for all I know. Maybe there's a good IM client I've missed that has that feature?

> **dabl said:**
> If those specialized workflows are critical to your efficiency, then maybe you should re-evaluate the move to Linux, and/or consider putting a Windows OS on a VM and running them that way.That's what I'm weighing here. If I've not found proper linux alternatives by the time I'll buy the PC, I'll probably get the 7.

*Edit:* Oh, and any specific reason of preferring VMware Player over VirtualBox?

---

### Post by hathiphnath on 2010-08-12
> **3Miro said:**
> Which version of KDE did you try.It mush have been 4.x, and I recall it being much more cluttered with all kinds of drawers on the desktop and whatnot. GNOME had a much cleaner and more comprehensive look IMO.

> **3Miro said:**
> The biggest issue that I have seen comes from the sound. KDE and Gnome use different sound systems that are not fully compatible and sometimes it happens that if you open couple of programs in KDE one of them will lose the sound.So it happens randomly? I mean, not being an issue you can fix and be done with it? That sounds scary, but I'll try it out.

---

### Post by dabl on 2010-08-12
> **hathiphnath said:**
> 
*Edit:* Oh, and any specific reason of preferring VMware Player over VirtualBox?

Yeah, it's the one I know how to use.  LOL

OK, I did try VBox once, and it was really easy to set up.  Then I learned that the version I had did not support the USB interface, which I need. Turned out there were/are two versions of it, one open-source and one not, OSE or not, yadda yadda yadda -- it got more complicated than I cared or needed to deal with. VMware Player "just works" for me, and so I've stuck with it.  If you start out with VBox, (and make sure you've got the flavor you need), then it's probably just as satisfactory for your Windows OS and apps.

On the .rtf logs thing, I would suspect that a fairly simple process exists to convert .txt files to .rtf format.  I've never looked into it, but I agree .rtf is a great format for handling docs that need to preserve their carriage returns and margins and such, and still retain an "application-neutral" characteristic when you don't know which word processor will be used to open the doc.

EDIT:  This could be part of the answer: [http://www.nllgg.nl/Ted/](http://www.nllgg.nl/Ted/)

or maybe this:  [http://sourceforge.net/projects/latex2rtf/](http://sourceforge.net/projects/latex2rtf/)

---

### Post by hathiphnath on 2010-08-12
> **dabl said:**
> VMware Player "just works" for me, and so I've stuck with it.But don't you need VMware Workstation to set the VM up?

---

### Post by dabl on 2010-08-12
> **hathiphnath said:**
> But don't you need VMware Workstation to set the VM up?

Absolutely not -- the free VMware Player is all you need (and your Windows installation CD).

---

### Post by Vaphell on 2010-08-12
pidgin logs are a bunch of html or plaintext files located in ~/.purple/logs, it should be quite easy to write a script to merge some/all files into 1 and then convert it to something. I tested html->latex->rtf path (gnuhtml2latex, latex2rtf) and it somewhat works, though text formatting of the result is not perfect in OO. Logs treat hyperlinks as plaintext so you won't get active links in the result. I think it could be coded around.

---

### Post by dino99 on 2010-08-12
ive definitively removed windoz from my system since 2005 and use wine (winehq) to run the few exe around, thats all

---

### Post by NIT006.5 on 2010-08-12
> **hathiphnath said:**
> 
That's what I'm weighing here. If I've not found proper linux alternatives by the time I'll buy the PC, I'll probably get the 7.


While I don't have answers to any of your specific issues, this is just my humble 5 cents, based on my own migration experience.

I was a devoted Windows user for many years and dreaded the switch to Linux, which I was "pressured" into by changes in our company's policy at the time. Eventually I stopped arguing and made the move because I had to. I definitely lost a lot of the features that I thought were essential at the time, and it was possibly the most frustrating three months of my life, particularly while trying to be productive and efficient while learning a totally new environment. 

However, it didn't take long for me to get over what I had "lost". Why? Because I had discovered so much more on a Linux platform, that I found I didn't care about those things any more! I may not have had the same features that I treasured so much on Windows, and it's taken a while to get there, but I can now do things much more efficiently and quickly than I ever could before, thanks to the inherent flexibility of Ubuntu and open source apps. Since you mentioned compiz previously, this is actually a prime example for me. My last job forced me back into a Windows environment and I was absolutely lost without the additional functionality.

So while I can't put my finger on each and every point that makes Ubuntu so much better for me, I hope that it might help hearing it from someone who really struggled initially with the migration, but would now never go back. Ever! And while I had "messed around" with Linux desktops before, I only really and truly discovered how awesome Ubuntu was after I was forced to use it in a live environment.

In summary, I would really, really encourage you not to just base your decision on these "essentials" because I do believe you'll find even more features on Ubuntu that will, with time, become even more essential :) 

However, I know that not everyone ended up as happy as I am on Ubuntu, and maybe it's not for everyone. And there's a very slim chance that I've become biased :D So this is just my passion talking, and I apologise if I've gone off topic. O:)

---

### Post by hathiphnath on 2010-08-12
> **Vaphell said:**
> pidgin logs are a bunch of html or plaintext files located in ~/.purple/logs, it should be quite easy to write a script to merge some/all files into 1 and then convert it to something. I tested html->latex->rtf path (gnuhtml2latex, latex2rtf) and it somewhat works, though text formatting of the result is not perfect in OO.The .rtf issue seems to cause inordinate confusion, so, I'll be more specific. One of my hobbies is role-playing, but since my g-roup has spread all around the country, we play via IM. When the session is over, I choose "save" from the Windows Live messenger file menu, and save that game log into a different location. This serves mainly three purposes:

1) I can write key information about the activities and in-game date into the file name, making it easy to find stuff in case I need to reference it in the future
2) If the keywords fail me, I can just search the game folder, not the *whole archive* of my IM history, making the process much faster and more accurate
3) Being .rtf files, they can be read more easily than plain text files and unlike with .html, typos can easily be fixed

There! :)

---

### Post by Zorgoth on 2010-08-12
I don't do much audio stuff so I can't really say anything about tag and rename.  But I believe Amarok will handle tags for you.

Stardock gets utterly powned by cairo-dock, and you can also look at avant-window-navigator and docky.

There are a *lot* of image editors for Ubuntu, of which GIMP is the most complicated (and advanced).  Search the repositories and you should find one.

Converting sound files is easy enough in audacity anyway, and I saw something called soundconverter in the repository that seems good.

For video conversion, I don't know specifically.  Format Factory 2.x *does* work well under Wine apparently, and if you want a simpler frontend you could use PlayonLinux or Crossover (that one's proprietary).  Is Video Converter 3.0 any good?

I am not really a big multimedia guy, but honestly I doubt that you will not find toold comparable to what you need for Linux.  However, if you expect to find tools to do everything exactly the same way with the same interface, that's not going to happen.  Windows and Linux are simply different, and there is a learning curve between them.  Personally, I could say Windows has no real equivalent to Nautilus,cairo-dock, or compiz and so I could never use it.  But I did use it for most of my life.

I would recommend trying out Ubuntu and learning your way around.  Only you are capable of really determining whether Ubuntu or Windows will suit your purposes better.  btw, I've never used it, but maybe you would like to look into Ubuntu Studio?

---

### Post by 3Miro on 2010-08-12
> **hathiphnath said:**
> 
So it happens randomly? I mean, not being an issue you can fix and be done with it? That sounds scary, but I'll try it out.

It is semi-random, for example, I couldn't play sound from Mplayer while Amarok was open and paused. This was annoying more than anything else. The only solution that I could find was to close Amarok, though sometimes I would have to reboot the sound system (it is an easy one line in the terminal).

This was in 9.04 and 9.10, which means that it might have been fixed in 10.04 and/or going to be fixed in 10.10.

Also, for the way KDE looks, KDE is the most customizable environment that is available right now. This means that the thing will look like what you want it to look like. The default KDE 3.x interface was what I would call cluttered, however, the default 4.x is pretty much what you get from default Windows 7. Of course in KDE, there is no reason for the default to last for more than 10 seconds.

---

### Post by Zorgoth on 2010-08-12
> **hathiphnath said:**
> The .rtf issue seems to cause inordinate confusion, so, I'll be more specific. One of my hobbies is role-playing, but since my ***** has spread all around the country, we play via IM. When the session is over, I choose "save" from the Windows Live messenger file menu, and save that game log into a different location. This serves mainly three purposes:

1) I can write key information about the activities and in-game date into the file name, making it easy to find stuff in case I need to reference it in the future
2) If the keywords fail me, I can just search the game folder, not the *whole archive* of my IM history, making the process much faster and more accurate
3) Being .rtf files, they can be read more easily than plain text files and unlike with .html, typos can easily be fixed

There! :)

The person you were replying to was explaining how to do just that basically.  The only difference is that you don't use "save as," but a shell script to convert the files.  The command line is only scary if you let it be :D; for me I do a large part of basic filesystem operations from the command line, not because I can't do them from the GUI (in fact it is usually easier in the GUI than it is in Windows), but because the command line gives me better control, and because writing one command with something like "find -name 'something' -exec 'whatever'", particularly with autocompletion, is much, much faster than navigating with a point-and-click GUI.

---

### Post by hathiphnath on 2010-08-12
> **NIT006.5 said:**
> I was a devoted Windows user for many years and dreaded the switch to Linux, which I was "pressured" into by changes in our company's policy at the time. (...) However, it didn't take long for me to get over what I had "lost". Why? Because I had discovered so much more on a Linux platform, that I found I didn't care about those things any more!I can totally understand that, but I want to keep doing the same things with my computer that I've always done. Most probably I can re-learn the method, but I don't want that to increase my workload. If the change of OS means I must stop doing things I like, or doing those things becomes a hassle, there's hardly any point in changing the platform at all.

> **Zorgoth said:**
> I would recommend trying out Ubuntu and learning your way around.  Only you are capable of really determining whether Ubuntu or Windows will suit your purposes better.  btw, I've never used it, but maybe you would like to look into Ubuntu Studio?Of course. I'm just sniffing around and taking recommendations at the moment. I'd probably not have thought of downloading Kubuntu at all if I'd not made this thread, for example, but it seems it's more than just a different GUI.

Thanks for the other suggestions! I'll try them out once Kubuntu finishes downloading.

> **Zorgoth said:**
> The person you were replying to was explaining how to do just that basically.  The only difference is that you don't use "save as," but a shell script to convert the files.  The command line is only scary if you let it be :DI must have misread him, sorry. Still, I have my doubts about saving the contents of an active IM window to an .rtf file being a trivial task from a command line, but perhaps not? How would you do it?

---

### Post by Zorgoth on 2010-08-12
My guess would be that you would want to pick up the most recent log from your hard drive or something like that.  I can't use an IM at work, so I may post more in the evening :D

---

### Post by hathiphnath on 2010-08-12
> **Zorgoth said:**
> My guess would be that you would want to pick up the most recent log from your hard drive or something like that.  I can't use an IM at work, so I may post more in the evening :DNow, going hunting for log files is the exact thing I'd *not* want to do, but I'd appreciate the input in any case!

For the record, under Windows I do it like this for the active window:

alt+f & s *choose file location* *type file name* enter

And as the conversation progresses, an additional "alt+f & s" when I want to overwrite the old file with new information

If you could find something comparable for pidgin (haven't tried the kmess and other KDE stuff yet), it would be AWESOME! :)

---

### Post by Zorgoth on 2010-08-12
> **hathiphnath said:**
> Now, going hunting for log files is the exact thing I'd *not* want to do, but I'd appreciate the input in any case!

For the record, under Windows I do it like this for the active window:

alt+f & s *choose file location* *type file name* enter

And as the conversation progresses, an additional "alt+f & s" when I want to overwrite the old file with new information

If you could find something comparable for pidgin (haven't tried the kmess and other KDE stuff yet), it would be AWESOME! :)

I'm not saying you manually get the most recent log file; the script would do that.  The nice thing about the command line is that it is trivial to automate tasks.

---

### Post by Vaphell on 2010-08-12
basic idea would be a script that takes buddy_id as a parameter, date possibly being another (to ignore older stuff)

you'd simply copy the id in pidgin, paste it to terminal window as a script parameter (middle click works). The script would find a proper dir with matching name inside .purple/logs/<protocol>/<your_account_id>/ and merged the content of all the files present inside into 1 automatically. On that created file you can perform any transformations you want or even better - you can simply pass it to Open Office Writer to open it and there you can save as any of the supported formats and you have access to all the bells and whistles of a full-blown document editor right off the bat.
required pieces:
1. ```
find ~/.purple/logs -name <buddy_id>
``` to find dir with conversations (you can try it)
2. something to glue html/txt together into one file <file.txt/html>, txt being a trivial case, html somewhat more annoying (unless there is a tool that can do that without hassle)
edit: merging html files as is, with total disregard to recurring <html> and <body> tags doesn't cause any problems in OpenOffice
3. ```
ooffice <file.txt/html>
```

Not as convenient as simple rightclicking on a buddy name and selecting customized option in context menu but it works or at least it should. Always one can dive into the art of writing pidgin plugins and follow same steps as above, but without the terminal :-)

---

### Post by Vaphell on 2010-08-12
rough version of script:
```
#!/bin/sh

dir=`find ~/.purple/logs/ -name "$1"`
for file in $dir/*.html
do
  cat $file >> $1_full.html
done
ooffice $1_full.html
rm $1_full.html

```

buddyid as a parameter
it's not elegant or anything, i am noobish at bash :)

---

### Post by hathiphnath on 2010-08-12
So, it basically joins all the log files in a certain folder and opens them in openoffice?

---

### Post by Zorgoth on 2010-08-12
Something that might be useful potentially is a command-line utility I found in the repositories called enscript that can turn plain text into RTF using a set of rules.  It is designed to export source code with proper syntax highlighting and indentation, which I think is probably pretty similar to what you want to do.

---

### Post by Vaphell on 2010-08-12
yep, basically it is all that script does :) $1 is first parameter of the script, whatever you typed there is put in place of $1.
find looks for a proper dir
for loop repeats for each file in that dir - append content to the end of temporary buddyid_full.html
when finished, run ooffice and after that delete temporary file.

Zorgoth's stuff sounds nice too.

As you can see you can build your own tools and you don't have to be a master haxxor to do some basic stuff, i used to know something about programming in bash, but i forgot almost everything and wrote that example with the help of google :-)

---

### Post by hathiphnath on 2010-08-12
> **Vaphell said:**
> yep, basically it is all that script does :)I tried to explain what I wanted, but you've completely misunderstood me. Let's imagine the following IM chat:

> **hathiphnath says:** 
Good evening, Zorgoth!
Mind if I invite Vaphell?
**Zorgoth says:** 
Go ahead.

[SIZE="1"]Vaphell has been invited to the conversation.[/SIZE]

**Vaphell says:**  
Hi guys!
**hathiphnath says:**
Great to have you both around.
You see all this chat we've been having?
**Zorgoth says:**
Sure.
**Vaphell says:**  
Not from the very beginning, but yes.
**hathiphnath says:**
THIS is the part I want to be saved to a separate .rtf file.
From the moment I said "Good evening, Zorgoth!" to this very line I'm writing right now.
*Saves the conversation to "tech tips" folder as "Pidgin modding.rtf"*
**Zorgoth says:**
You mean, you want to save ONLY what we can see in the window right now?
And this is not to include... conversation we had in the morning, for example?
**hathiphnath says:**
Precisely.
**Vaphell says:**  
Do you want to save the rest of the conversation we're having as well?
I mean, the one we've been having after you saved the file.
**hathiphnath says:**
I might, but I'm not sure yet.
Hm, yes, it's related enough. So, I want to keep the rest as well.
*Overwrites the previous .rtf file*
*And then the conversation drifts off to how we can't wait for the 5th season of Dexter to begin already*

And this quoted text *actions not included* is also what I expect to see when I open the "Pidgin modding.rtf" file

It will be logged automatically by pidgin anyway, but since I thought the conversation was of the highest importance, I've ALSO saved a copy to my "tech tips" folder and if I need the recall the details of this specific conversation six months from now, I can look into the "tech tips" folder and forego the need to search the archive covering the past six years, where I might have talked to Zorgoth and Vaphell on many occasions, perhaps even daily :)

---

### Post by Vaphell on 2010-08-13
it crossed my mind that you may be talking about conferences. It complicates a little but it's still doable

```

#!/bin/sh

echo "Buddy name(s): "
read buddies
echo "hours: "
read hrs
lastmins=$(($hrs*60))

outfile="log_full.html"
tmpdir="log_temp"

arr=$(echo $buddies)
regexp=""
for buddy in $arr
do
  pattern="<b>${buddy}:</b>"
  regexp="${regexp}(${pattern})|"
done
regexp=$(echo ${regexp%\|})
echo $regexp

counter=0
mkdir $tmpdir
cd $tmpdir
for dir in `find ~/.purple/logs -type d`
do
  echo Scanning $dir
  if grep -qE -e "$regexp" $dir/*; then
    echo "Log files found"
    for file in `find $dir -type f -mmin -"$lastmins"`
    do
      counter=$counter+1
      cp $file .
    done    
  fi
done

if [ $counter = 0 ]; then
  echo "Warning - no logs found"
  cd ..
  rm -r $tmpdir
else
  echo "Generating output file..."
  for file in `ls *.html`
  do
    cat $file >> $outfile
  done
  sed -i 's/<br\/>/<br>/g' $outfile
  cd ..
  echo "Opening in OOffice..."
  ooffice $tmpdir/$outfile
  sleep 5
  rm -r $tmpdir
fi

```

what it does:
- it asks for space delimited buddy names (names with spaces may cause trouble)
- it asks how many last hours it should take into account (hrs should be precise enough)
- it finds all files with occurences of listed buddy names (but not in message bodies) not older than n hrs (converted to minutes). Pattern determines how the buddy name looks in conversation log - in my case it was <b>NAME:</b>
- it copies the files into single temp directory and then glues them together into single html file. File is passed to open office and then temp is deleted

unpolished edges:
- logs are very fragmented (each killing of the conv window starts new file) and the script looks for occurence of buddy name, so if some log file has only part of greater conversation when buddy was silent, that piece won't be found. Workaround would be to find all directories where files with occurences are and then check the timestamp on every file in these directories - i simply couldn't figure out how to do that with next to no effort, but it can be done with slightly more coding.
- script does farm every file with a buddy name because when you start conversation 1v1 and then invite more people, files are likely to be scattered around the logs dir and there is no foolproof way to decide if a given file should count or not (beginning in buddy dir, the rest in generic conference dir). Script will be as smart as the amount of additional logic you want to put into the script.
- the lines of the conversation are not separated by newline because it ignores legit <br/> tag. Simple replace <br/> with <br> would fix that. Output file in html format looks really nice if firefox.
Either way you get a single file, you can do whatever you want with it. Test the script to see if it works well with your data. I have only 2 3line long conference files :)

edit:
upgraded script to include files with no buddy occurence when name occurs in other files within the same directory.
changed 'broken' <br/> tags to <br> so OO stops to ignore them

---

### Post by hathiphnath on 2010-08-13
I still don't get where should I insert this script, sorry :oops:

---

### Post by schreber on 2010-08-13
If you like Virtual Dub on Windows you might want to take a look at [Avidemux]("http://fixounet.free.fr/avidemux/") you can find it in software center. It does a pretty good job and seemingly does a little more than VD does on Windows by default.

---

### Post by Vaphell on 2010-08-13
if you put it in the main directory of your home, it will be available without any navigation but you can put it anywhere - you'll have to take care of a proper path though

create a file named whatevernameyouwant.sh, open it with gedit, paste the code, save it
open terminal
type
**chmod +x whatevernameyouwant.sh** (to mark it as an executable file)
and then run it with
**./whatevernameyouwant.sh** (.=current dir, terminal starts in your home by default, in case of different location you need to provide proper path)
tapping tab key autocompletes names, so you don't have to type whole name every time, 2 or 3 first letters should be enough

you can also create a launcher on your panel (right click, add custom launcher) and put that script as a terminal program to execute ( ~/whatevernameyouwant.sh , ~=your home dir)

if it's successful, you should get Open Office window with the compilation of logs that matched the criteria

---

### Post by hathiphnath on 2010-08-15
I appreciate the input on the .rtf script, but this goes waaay beyond the effort I'm willing to spend on the task each time I want to save a conversation :(

For one, I have no desire to keep track on how long a conversation has been going on for me to be able to save it. Secondly, the scrip seems not to work. I put the both buddy names in and then even if I account for the last 24 hours, nothing pops up. Or at least I can't find the generated file anywhere. I'm using GNOME, maybe that's the reason.

And in any case, I discovered that the conference chat in Pidgin is waaay off from what I thought it would be. I expected it to be... similar to WLM, y'know, but pidgin requires that you create a "chat room", which makes the whole thing unusable for me. Sorry, as I said, I've used ubuntu only sporadically.

Now, I tried my otherwise next best choice, emesene, and conference chats seem to work fine there. But while pidgin has the option to save to .html and not to .rtf, emesene does not offer any direct saving at all. I made a plugin/feature request on their boards, but who knows whether that's actually implemented.

On the other notes, I'm experiencing a bunch of other problems as well. For example, yWriter won't support umlauts under ubuntu, while they work just fine under windows.

As for CairoDock, Docky and AWN all "pwning" ObjectDock, this didn't seem to be so. The only dock having my desired "stack" feature was AWN, or at least I couldn't find it in the other two. And in AWN, I did not manage to a) stop it automatically picking up open apps (I only want it to include items I myself have put there) and b) I astonishingly failed to make it hide. If I've missed a feature, please do explain.

---

### Post by Zorgoth on 2010-08-15
Cairo-dock definitely has stack, if you are talking about the OS X feature.  Are you using cairo-dock 2.2?

And AWN and docky dont pown objectdock - just cairo-dock :)

---

### Post by hathiphnath on 2010-08-15
Ah, yes it did, but I did not find a way to point the stack to a folder. I want the stack to display the contents (more precisely, the image thumbnails) of certain folder. The contents of the said folder would change regularly and updating the stack by hand as Cairo requires would simply not do. :(

My cairo-dock is from the repositories: 2.1.3

---

### Post by Zorgoth on 2010-08-15
The "Folders" applet provides th efunctionality you want.

Both Kopete and amsn will allow you to save chats, but I don't think you can choose the format.  My guess is though that if you save them all to a particular directory, then a plain text -> rtf or other easy to edit/read format would be pretty trivial (as a single command, even a hotkey, could instantly convert every log file in a directory, once you have the rtf script set up).  I don't think you're going to find a messenger right now that makes it as easy as MSN does though...

---

### Post by Zorgoth on 2010-08-15
Kopete's format seems like pretty complkicated html, but a good script could do it.  It would take a while to write though.  I'll look at amsn when I am done with this chat.

---

### Post by Zorgoth on 2010-08-15
The amsn is a very nice plain text format it looks like.  It should be easy to convert to rtf, or even just to work with as plain text.

Personally I am not a big fan of amsn in general, but maybe you will be,

---

### Post by hathiphnath on 2010-08-15
The last time I used aMSN it was very slow and ugly, but I'll check it out again.

---

### Post by Zorgoth on 2010-08-15
By the way, to get the latest cairo-dock:

sudo apt-add-repository ppa:cairo-dock-team/weekly

then reload your package information, and cairo-dock 2.2 should show up as an upgrade in your package manager.

Note that this will be a beta version - however 2.2 is a big step over 2.13.

---

