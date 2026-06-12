---
title: "How to change default directory in graphical mode?"
date: 2010-04-23
forum: General Help
---

### Post by dannysauer on 2010-04-23
So, I noticed that sometime in the last couple of releases, every terminal I open up under KUbuntu opens up in my ~/Documents folder.  This is really irritating, because I'm not on a Windows machine.  I have an organizational scheme already, and using folders with capital letters is not something my Unix old-timer mind enjoys.  Capital letters are reserved for variables and Windows compatibility. :)

But I digress.

When searching around, I find a bunch of people suggesting that I stick a "cd $HOME" or similar in my .profile, or my .bashrc, or whatever.  That's ugly, and is masking the actual problem.  This is a clean install, and no one has changed my profile (also, "Documents" doesn't appear in any of the shell init files).  I figured I'd try to find the actual problem.  If I start the "run program" dialog, and run "pwd > /tmp/file", I find that the CWD that KDE is running under is ~/Documents - so all of the resultant terminals are doing the right thing by starting in the current working directory.  Ugh.

So who decided to change the CWD to ~/Documents somewhere during KDE initialization?  I'd like to send them a "present" - they should ignore the ticking and the extra packing tape...  And how do I undo their evil, evil change? :)

---

### Post by Untitled_No4 on 2010-04-23
I'm not sure if I understand your problem, but maybe you can find your answer in System Settings -> About Me -> Paths.

---

### Post by dannysauer on 2010-04-23
Perhaps it'd help if I describe the problem in terms of a scenario. :D

I install a fresh build of KUbuntu on a system, and create a user.
I Start the machine up, and log in to KDE as that user.
I go to the K menu, and navigate to "applications" -> "utilities" and start up the terminal emulator.
When the terminal starts, the initial working directory is "~/Documents" - not $HOME.

This is in contradiction to the behavior expected using any other login method (console, ssh, or usually ftp) on this system - or on most any UNIX or Unix-y system which has ever been remotely popular.  It's also a change sometime in the last couple of releases, but I don't exactly remember when as I've only fairly recently switched back to KDE from Gnome or Windowmaker... :)

I guess I should file this inconsistency as a bug, but mostly I'm just interested in fixing it on my machine.  Some usability weenie wanting to make things more friendly probably has a good reason for setting CWD to ~/Documents on X login - more than likely so people who don't know what they're doing will automatically save stuff in their Documents folder regardless of app.  So it probably won't change just because I'm a grumpy old man (no, I'm not really that old - but I feel like it sometimes).  But I still want it to change on my system. :D

I suppose I could change the DOCUMENTS variable to $HOME and see if that magically makes it work, but that seems like it'd probably make a mess of something else somewhere...  Anyone have thoughts on what I'll blow up by making Documents my homedir?  Is some boneheaded app gonna accidentally wipe out all of the dotfiles in there someday if I make that change?

---

### Post by Untitled_No4 on 2010-04-23
Since I don't have Terminal Emulator under Utilities, I'm assuming you mean Konsole.

When I open Konsole it opens in my home folder and not in Documents, as it has always been.

Perhaps check the properties of the menu item you're running by right clicking on the Kmenu icon, selecting Menu Editor and highlight the item. On the right then click on Advanced and check what's under Work path.

---

### Post by dannysauer on 2010-04-23
The work path is empty.  And no, I don't have Konsole, for some reason. :)  I have xfce4-terminal and konsole both installed, but I only have an entry in my K menu for the xfce terminal.  Which is weird (I also don't have an entry for gnome-termional, though they're all on my system).

I suppose I should note that I'm running lucid, and that I actually installed from the mythbuntu media, then put the kubuntu-desktop package on top of that.  But that shouldn't matter in a sane world... :D

Now I'm gonna have to get VMWare Server set back up and try a clean KUbuntu install just to make sure I'm not a crazy person...

---

### Post by agnes on 2010-04-23
> Anyone have thoughts on what I'll blow up by making Documents my homedir?  You could edit *~/.config/user-dirs.dirs* 
See [here]("http://ubuntuforums.org/showthread.php?t=631711").
Should work for KDE too, it also uses xdg. 
That would not hurt your system any way.

---

### Post by dannysauer on 2010-04-23
Thanks. :)  I do know *how* to do it, though - I'm just curious if anyone knows that it'll have potentially bad side effects when other programs make assumptions about that being a subfolder of $HOME rather than actually being $HOME.  EG, some program assumes it's ok to compress everything in there, or clean up old files, or get stuff from one level above, etc.  Good programmers wouldn't do that, but I've been a sysadmin long enough to know that there are a lot of non-good programmers out there. ;)

---

### Post by khughitt on 2010-04-30
I'd also be interested in knowing how the terminals know to use $HOME/Documents as the initial directory. I'm running Kubuntu 10.04 and interestingly, when I open up a konsole window it starts in $HOME, however, when I open up a terminator window, it starts in $HOME/Documents.

Changing the system "Documents" directory would be a bit indirect, and I'd much rather figure out the root cause.

I checked /etc/profile and /etc/bash.bashrc but didn't see anything in there.

Any ideas?

---

### Post by cIdde on 2010-05-14
Hi all,

same problem here. I am an intensive user of xterm and am experiencing the same problem. All bash sessions in the xterms try to start in $HOME/Dokumente in my case. Hey, I don't even have this bloody stupid directory in my home folder. I've had my own sceme for decades and won't change that now just because of such a stupid *bug*. So, all the xterms started in an invalid directory and threw error messages about that. Annoying!!!

Thanks for the hint about changing ~/.config/user-dirs.dirs. I did that and it helped. But just like dannysauer, I think that this is a bit like removing the symptom, but not the cause.

So, still anyone with a deeper insight into what happens, when you start an xterm in KDE, who can clarify the problem?
It seems like it has something to do with the package xdg-user-dirs, but how does that work and how can one change the behavior. Xterms should not start in the XDG_DOCUMENTS_DIR directory.

---

### Post by melikamp on 2010-09-13
Hi!

I will write ~ for the full path to my home directory, for brevity.

This very thing happened to me recently, even though I am on Slackware 13.1. A few days ago my KDE session suddenly decided that my home is in ~/Documents. Unfortunately, I cannot pinpoint the reason. Console and WindowMaker logins go into ~ as usual, but anything starting in KDE would be in Documents. I tested with Alt-F2 and starting programs via shortcuts. I do not use the folder Documents for anything, and even if I did, I don't understand why it has to be the default starting point for the shell. I went into System Settings, About Me, Paths (thanks Untitled_No4), and replaced Documents path ~/Documents with ~. Now KDE starts in ~. That alone is enough to convince me that it is a bug.

I noticed that konsole starts from ~ regardless of where you run it from, so I think that is how the bug may have crept in. I use xterm, which honestly starts in the current directory.

---

### Post by efAston on 2011-01-08
.

---

### Post by Theredbaron1834 on 2012-05-13
I know this is a bit old, but I was really bugged by this, and figgered it out. So here goes.

Ok, here is how to fix it, graphically, with no "badness".

If you have the icon pinned, right click, icon settings, application, work path. There is a little folder there you can click and just go to the folder you want.

If it is in the item menu, right click on the launcher, click edit application, and go to the term you want to "fix". Go to advanced, and work path is right there. Same as above, click the folder and choose the working dir you want.

---

### Post by lisati on 2012-05-13
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=217836&stc=1&d=1336885280[/IMG]

---

