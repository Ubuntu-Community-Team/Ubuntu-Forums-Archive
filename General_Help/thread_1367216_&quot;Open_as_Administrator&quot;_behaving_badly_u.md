---
title: "&quot;Open as Administrator&quot; behaving badly under Karmic?"
date: 2009-12-29
forum: General Help
---

### Post by tgeer43 on 2009-12-29
I'm surprised that I haven't seen this mentioned in these forums or elsewhere on the web.

I've installed 'nautilus-gksu' in Karmic just like I always do when installing Ubuntu. In previous releases when selecting 'Open as administrator' on a folder the resulting new nautilus window would open with the nautilus profile settings of root. This is nice when you have multiple nautilus windows open as you can easily see which ones are root by the different icons and other nautilus settings. It's the same for Karmic but now my _entire_ _session_ becomes that of root (desktop, background, etc.) and the only way to revert back to my normal profile is to log off/on. Entering 'gksu-nautilus' at the command line gives the same result. Quite annoying and counter-productive, to say the least.

Am I missing a new Karmic setting or something else? Barring that, is there a better/quicker way to revert back to my normal user profile?

Any help would be greatly appreciated as I've rooted around quite a bit (no pun intended) but haven't turned up a solution yet.

tgeer

---

### Post by tgeer43 on 2010-01-05
Well, the only GUI way that I found to circumvent this problem was to uninstall gksu-nautilus and use a regular nautilus script to open files/folders as root. I still don't know if the problem resides in the gksu-nautilus package or in Karmic itself. Since my resolution is more of a workaround than a fix, I'm not marking this thread as solved.

The complete lack of responses here leads me to believe that the problem is not widespread and may in fact have something to do with my particular installation/configuration but I can't for the life of me think of what it might be.

tgeer

---

### Post by jamesisin on 2010-01-05
I don't use that specific package (gksudo-nautilus).  Can't you just gksudo nautilus when you need a specific window?

---

### Post by tgeer43 on 2010-01-05
> **jamesisin said:**
> I don't use that specific package (gksudo-nautilus).  Can't you just gksudo nautilus when you need a specific window?
I mis-typed a couple of times in my first post. The correct package name is 'nautilus-gksu'. And when I said:
> Entering 'gksu-nautilus' at the command line gives the same result. I meant 'gksudo nautilus', so I have tried that. It still changes my entire profile to that of root and there's no easy way that I know of to switch back to my regular profile. And besides, if I'm going to enter a CLI command to open a nautilus window as root, I might as well just enter the entire command, eg. sudo cp /etc/grub.d/00_header /etc/grub.d/00_header.bak.

Thanks for the suggestion, though.

tgeer

Tom

---

### Post by jamesisin on 2010-01-05
Well, you could merely type gksudo nautilus into gnome-do...

Have you tried running gksudo nautilus after removing (purging) nautilus-gksudo?

---

### Post by tgeer43 on 2010-01-05
> **jamesisin said:**
> Well, you could merely type gksudo nautilus into gnome-do...I don't run gnome-do but I don't think that would be any different than typing it at the command line or into the 'Run Application' panel applet dialog box. Correct me if I'm wrong.
> **jamesisin said:**
> Have you tried running gksudo nautilus after removing (purging) nautilus-gksudo? Yes, unfortunately I have.

I just took a look at the 'Browse as root' nautilus script that I'm successfully using now. The command contained therein reads: > gksu -u root "nautilus --no-desktop $NAUTILUS_SCRIPT_CURRENT_URI"So it appears that the --no-desktop option is the key. According to the nautilus man page: > --no-desktop
Do not manage the desktop — ignore the preference set in the preferences dialog.tgeer

---

### Post by jamesisin on 2010-01-05
I think gnome-do is the best application launcher to date.  A single keystroke starts it and then I type something until I recognize what I'm after.  If I type out a command (like gksudo nautilus) and hit enter it's the same as having first opened the command line and then typed it out.  I use it for just about anything now.  Way better than Spotlight and better than Windows-R.  And I probably am not yet fully exploiting it.  (Use the Glass Frame theme as the others don't follow the behavior I am talking about.)

I agree with you about the --no-desktop.  Sounds suspicious.

---

### Post by 3rdalbum on 2010-01-05
The "--no-desktop" bit is the key. Alternatively, you can run:

```
gksudo gconf-editor
```

And then change the setting so that Nautilus (as root) doesn't manage the desktop.

---

### Post by tgeer43 on 2010-01-05
> **jamesisin said:**
> I think gnome-do is the best application launcher to date.  A single keystroke starts it and then I type something until I recognize what I'm after.  If I type out a command (like gksudo nautilus) and hit enter it's the same as having first opened the command line and then typed it out.  I use it for just about anything now.  Way better than Spotlight and better than Windows-R.  And I probably am not yet fully exploiting it.  (Use the Glass Frame theme as the others don't follow the behavior I am talking about.)

I agree with you about the --no-desktop.  Sounds suspicious.
Thanks for the info on gnome-do. I'm already quite familiar with it (having tried it in the past) and I know that it's widely regarded as the best app of its kind. However, I currently have no real need for it. That may sound a bit odd but if you saw that way that I have my system set up you would understand. Every menu and application that I normally access is already at my fingertips via panel launchers and applets and I rarely have to type anything unless I choose to work from the command line. There's nothing on my desktop as I have nautilus set up to _not_ manage the desktop. For those few apps that I use only infrequently there's always the main menu or the 'Run Application' panel applet. 

And besides, we already established the fact that it would not help in this case because it's no different than typing the same command from the command line which unfortunately doesn't work. :(

tgeer

---

### Post by mbeach on 2010-01-05
> **3rdalbum said:**
> 
And then change the setting so that Nautilus (as root) doesn't manage the desktop.

trying to understand a similar issue over at:
[http://ubuntuforums.org/showthread.php?t=1372619](http://ubuntuforums.org/showthread.php?t=1372619)

thinking that they may have seen the same sort of thing happening. 

Which setting controls **root** allowing desktop management - what is the path to the setting in gconf-editor? Is it something other than Apps -> Nautilus -> Preferences -> show desktop?

---

### Post by tgeer43 on 2010-01-05
> **mbeach said:**
> trying to understand a similar issue over at:
[http://ubuntuforums.org/showthread.php?t=1372619](http://ubuntuforums.org/showthread.php?t=1372619)

thinking that they may have seen the same sort of thing happening. 

Which setting controls **root** allowing desktop management - what is the path to the setting in gconf-editor? Is it something other than Apps -> Nautilus -> Preferences -> show desktop?That is indeed the correct key. The difference is that by running gconf-editor as root (gksudo gconf-editor), root's profile is edited instead of the current user's.

Many thanks to 3rdalbum who pointed this out in post #8 of this thread. I ran gconf-editor as root and unchecked Apps -> Nautilus -> Preferences -> show desktop then reinstalled nautilus-gksu and now the 'Open as adminstrator' right-click context menu item works like it did for me by default in earlier versions of Ubuntu. The current user's desktop is left undisturbed throughout the root nautilus session.

The thread that you referenced does look like it's very closely related since they both have to do with the desktop and root nautilus sessions. But whereas mine involved obvious switching of the desktop to that of root's, his desktop does not change. Although he can see his 'missing' files in a root nautilus session, the missing desktop icons are still not present. Nevertheless, his solution turned out to be the same except that he had to edit Apps -> Nautilus -> Preferences -> show desktop as the current user rather than as root like I had to do. Same key - different user.

You know, I really don't mind little issues like this as I never fail to learn something new about this amazing OS.

tgeer

---

### Post by jamesisin on 2010-01-05
Nice resolution.  Unexpected.  I like it.

I'd be interested to see your desktop arrangement if you are willing to attach a screen shot (or send one to me).

---

### Post by tgeer43 on 2010-01-06
> **jamesisin said:**
> Nice resolution. Unexpected. I like it.

I'd be interested to see your desktop arrangement if you are willing to attach a screen shot (or send one to me).
I don't know how 'nice' the final resolution was but I agree that it was unexpected and I definitely like it too since it put an end to something that had been bugging me since I installed Karmic about two months ago. I really started to try to resolve it only about two weeks ago and I can only take partial credit for it. I did uncover the ***--no-desktop*** thing but it was 3rdalbum that came up with the real solution in post #8 above.

As for a screenshot - sure, here's one attached that I had to scale down to meet the forum's file size limitations. Native resolution is actually 1440x900. There's really not much to look at since I don't allow nautilus to manage the desktop, hence no desktop icons. In fact, my top and bottom panels are normally set to 'autohide' so I had to temporarily reveal them for the screenshot or else there wouldn't be anything to look at except one of my desktop backgrounds.

[ATTACH]142656[/ATTACH] [SIZE=1]Click on thumbnail for larger view.[/SIZE]

Anyway, here's how it works and the reason that I don't see a need for running a separate application launcher like gnome-do:

[SIZE=4][COLOR=Blue]_TOP PANEL_[/COLOR][/SIZE][COLOR=Blue]:[/COLOR]
The left section contains the 'Run Application' applet as well as launchers for 13 of my most used applications and scripts. They are (from left to right): Terminal, Root Terminal, Firefox, Xmms, Skype, Deluge, Gimp, Toggle Webcam As Desktop Background, Frequency Scaling, Gedit, Toggle Conky, System Monitor, and PlayOnLinux.

The middle section contains drop-down menus corresponding to the following sections in the Start Menu: Preferences, Administration, Accessories, Games, Graphics, Internet, Office, Other, Sound & Video, and System Tools.

The right section is just a few odds & ends: Find Files, Terminate Misbehaving Application, Indicator Applet, and Shutdown.

[SIZE=4][COLOR=Blue]_BOTTOM PANEL_[/COLOR][/SIZE][COLOR=Blue]:[/COLOR]
Left section: Start Menu, Shortcut to Home Folder, and Workspace Switcher.

The entire middle section is the Window List (you can see my Ubuntu Forums Firefox session there).

Right section: Weather Applet, Blueman, Networking, Battery Indicator, Volume Control, BlueProximity, System Clock, and Trash Applet.

That's it! - very simple but highly functional and efficient. I used to (particularly in my Windows days) like to have a bunch of nifty looking icons on the desktop but in my old age I really prefer the uncluttered, minimalistic look. I find it to be more productive and easier on the eyes. By the way, that desktop background is a picture of my current girlfriend (what a bitch!) :wink:

So as you can now see, there's very little that I can't do directly from the panels without the need for using the Start Menu, much less a dedicated launcher application. Everything's there when I need it and hidden when I don't.

If you (or anyone else) would like any info on my Frequency Scaling, Toggle Conky, or Toggle Webcam As Desktop Background scripts, just say so. They're all very simple yet effective. I've also put together a nifty little system maintenance script (cleanup.sh) which, with only a couple of keystrokes cleans a whole bunch of stuff from my system. I have it set to run periodically via a cron task and I also run it manually before making a system backup. Oh, yeah - that reminds me. I also wrote a script that consists of a single (albeit very long) line of code that with a single mouse click makes a compressed tar archive of my entire installation and stores it on a separate drive for quick and easy restoration of the system in the event of major catastrophe. It has saved my bacon on more than one occasion and takes less than 10 minutes to back up the entire system (minus music, pictures, and videos which are archived separately). No need for a stand alone backup program when Ubuntu comes with everything needed to do the job effectively.

But I'm getting *very* off-topic here as well as exceedingly long winded so goodbye for now!

tgeer

---

### Post by jamesisin on 2010-01-06
I'm heading out now, but let's talk on IM about some of these scripts.

---

