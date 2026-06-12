---
title: "Questions about Banshee"
date: 2006-06-17
forum: General Help
---

### Post by aysiu on 2006-06-17
So, in Breezy, I used JuK because AmaroK was way too slow on my computer.

In Dapper, AmaroK sped up, and I was happy with it. Then I switched back to Gnome from KDE, and I kind of like using a native music player, so I used Rhythmbox for a while.

Now, since finding out about the DAAP plugin for sharing music with iTunes, I'm now using Banshee as my main music player.

A couple of questions about Banshee, though:

1. **Why does it create a folder called ~/Music?** This seems rather intrusive and annoying. I hope it creates it only the first time you launch it, because I've gone ahead and deleted that folder. I keep my music in ~/music (lowercase *m*), and I'm sure every person has her own way of organizing her own music.

This reminds me too much of Windows' annoying automatically-created folders: My Documents, My Music, My Pictures, etc. My eBooks. Geez.

2. **Can it be minimized to the notification area?** Both JuK and AmaroK can be minimized to the system tray, and it makes them less intrusive. Sure, I can always move Banshee to another workspace, but that's just annoying--it also doesn't let me see what song is playing unless I hover my mouse over the notification area icon. I'd like to have it so that when I close the Banshee window, it just goes to the notification area and stays there.

3. **Is there a way to make it stop?** I guess Banshee's a lot like iTunes this way. Maybe I'm just old-fashioned, but I like the idea of sometimes stopping the music, not just pausing. Electronically, is there a difference, apart from pausing just remembering where you left off?

4. **Has anyone gotten the File System Monitor plugin to actually work?**: In Rhythmbox, when I closed it and re-opened it, it would automatically scan my music folder and add new songs. In Banshee, theoretically, the File System Monitor plugin does this... except that it doesn't. Is it just me? I've had to go to Music > Import Music to get the new songs to show up.

5. **Is there a way to create dynamic or "smart" playlists?**

Any help would be much appreciated. Thanks in advance.

---

### Post by aysiu on 2006-06-18
Bump.

---

### Post by aysiu on 2006-06-19
Shameless second bump.

---

### Post by asimon on 2006-06-19
Sorry, I am no banshee user and can only answer one of your questions.
> 
5. **Is there a way to create dynamic or "smart" playlists?**

There is a plugin for smart playlists in development. See the [Plugins page](http://patches.ximian.com/Plugins). It's part of a plugin package for Banshee which isn't released yet.

---

### Post by aysiu on 2006-06-19
Thanks for the info. I guess I'll wait on that for now: >  Official External Plugins

It is important to note that this is a completely separate module from Banshee that provides plugins. This module has not yet been released and is only available from Banshee Subversion:

svn co svn://svn.banshee-project.org/trunk/banshee-official-plugins

Additionally, the Podcasting and Smart Playlists plugins requires Banshee from CVS/HEAD (what will be the 0.11.x series). All other plugins in this module will work with Banshee 0.10.10 and higher.

    * Podcasting - Mike Urbanski has released the Podcast plugin and abock has invited into the 0.11.x series. 

    * Mini Mode - Allows controlling Banshee through a simplified interface. Coming in the 0.11.x series. 

    * Music Recommendations - Recommends new artists, tracks and albums based on the playing artist using Last.FM 

    * Smart Playlists - Allows for smart playlists based on song metadata. Requires recent Banshee CVS. 

    * Internet Radio - Listen to internet streaming radio. 

---

### Post by panurge77 on 2006-06-19
On suse you get banshee by default. On ubuntu you get rhythmbox. They just look exactly the same. I never knew there was a difference...:roll:
But when on Suse it would minimize to the tray, if I remember correctly

---

### Post by aysiu on 2006-06-19
No ideas on how to implement the "minimize to tray" option in Ubuntu, though?

---

### Post by panurge77 on 2006-06-19
Errr, no. Sorry, but I'm on rhythmbox still. But now that thought of it. Does it appear at the tray? Because actually rhythmbox wont go to the tray if you press minimize or close buttons, it only minimizaes to the tray if you click on the tray icon when its open...

---

### Post by aysiu on 2006-06-19
Oh! That's a trick I didn't know. Thanks. I just tested it for Rhythmbox. Let me see if it works for Banshee.

**Edit**: Works for Banshee, too. Only problem with this is that it doesn't display what song is playing when I've switched songs. Still... a neat trick to know. Thanks again.

---

### Post by panurge77 on 2006-06-19
I think the trick works for everything that goes into the tray.. or almost everything... hehe. It works for firestarter and amsn, but not for system monitor... that's all i have at the tray now

---

### Post by aysiu on 2006-06-20
Well, I've gone back to Rhythmbox. My wife and I don't have that much of a need to share music, to be honest. It's a cool feature I'll keep in mind for future reference, but the lack of library refresh, the lack of smart playlists, and the occasional random crashing (which I haven't mentioned before in this thread), has just made me want to ditch Banshee.

Back to Rhythmbox. Thanks to Panurge77 for answering at least one of my questions.

---

### Post by panurge77 on 2006-06-22
You might want to know that rhythmbox is also supporting the saure funccionality, as you can see from their homepage:

Optional requirements for additional functionality

    * DBus 0.35 - allow other applications to control and query Rhythmbox
    * HAL 0.2 - Removable media (e.g. portable audio player) support
    * libgpod - enhanced iPod support
    * Avahi 0.5 or Howl - DAAP music sharing
    * libsoup 2.2 - DAAP music sharing and AudioScrobbler/Last.fm support
    * libnotify 0.2.1- Notification bubbles for track changes, podcast downloading and other events
    * libmusicbrainz 2.1.0 - Audio cd information lookup

What bugs me is that after I moved to unnoficial 9.4.1 the tray icon is not transparent anymore :(

---

### Post by aysiu on 2006-06-22
When I enable music sharing in Rhythmbox, it can't be seen from anywhere--not my wife's iTunes or even my other Ubuntu computer's Rhythmbox.

---

### Post by panurge77 on 2006-06-22
Hmm. I never tried. I use nicotine for sharing the goodies :D

---

### Post by jan on 2006-06-22
What is Banshee??? ;)

---

### Post by asimon on 2006-06-22
[QUOTE=jan]What is Banshee??? ;)[/QUOTE]
Either [this](http://banshee-project.org/Main_Page) or [this](http://en.wikipedia.org/wiki/Banshee). ;-)

---

### Post by sha_man on 2006-06-26
[QUOTE=aysiu]
1. **Why does it create a folder called ~/Music?** This seems rather intrusive and annoying. I hope it creates it only the first time you launch it, because I've gone ahead and deleted that folder. I keep my music in ~/music (lowercase *m*), and I'm sure every person has her own way of organizing her own music.
[/QUOTE]

just set your own in the *preferences* ;)

---

### Post by aysiu on 2006-06-26
[QUOTE=sha_man]just set your own in the *preferences* ;)[/QUOTE]
It doesn't matter if I set my own folder in preferences. It still creates its own folder called ~/Music.

---

### Post by amunimanghi on 2006-06-26
[QUOTE=aysiu]

1. **Why does it create a folder called ~/Music?** This seems rather intrusive and annoying. I hope it creates it only the first time you launch it, because I've gone ahead and deleted that folder. I keep my music in ~/music (lowercase *m*), and I'm sure every person has her own way of organizing her own music.[/quote]

**Answer:** I don't know. I'll change the folder options in my preferces to test it. 


2. > **Can it be minimized to the notification area?** Both JuK and AmaroK can be minimized to the system tray, and it makes them less intrusive. Sure, I can always move Banshee to another workspace, but that's just annoying--it also doesn't let me see what song is playing unless I hover my mouse over the notification area icon. I'd like to have it so that when I close the Banshee window, it just goes to the notification area and stays there.

**Answer:** There is a plugin that you can select. Edit =>Plugins... (I did not download this plugin.)

3. > **Is there a way to make it stop?** I guess Banshee's a lot like iTunes this way. Maybe I'm just old-fashioned, but I like the idea of sometimes stopping the music, not just pausing. Electronically, is there a difference, apart from pausing just remembering where you left off?

**Answer:** Do you have a stop button on your keyboard? If so, you can add the *Multimedia plugin*. (I didn't download this plugin.) If not, just push the stop button. I may not understan what your asking for though.

4. > **Has anyone gotten the File System Monitor plugin to actually work?**: In Rhythmbox, when I closed it and re-opened it, it would automatically scan my music folder and add new songs. In Banshee, theoretically, the File System Monitor plugin does this... except that it doesn't. Is it just me? I've had to go to Music > Import Music to get the new songs to show up.

**Answer:** It works for me. Do you have the box checked in the plugins? I kinda find this plugin annoying. 

5. > **Is there a way to create dynamic or "smart" playlists?**

**Answer:** Try this link. [http://banshee-project.org/PluginRepository]("http://banshee-project.org/PluginRepository")

---

### Post by aysiu on 2006-06-26
[QUOTE=amunimanghi]
**Answer:** There is a plugin that you can select. Edit =>Plugins... (I did not download this plugin.)[/quote] Actually, it's not in the plugins area. I checked. That's why I posted about it.

Someone earlier in the thread answered this question, though. You just click the notification area icon, and Banshee gets sucked into there.

> 
3. **Answer:** Do you have a stop button on your keyboard? If so, you can add the *Multimedia plugin*. (I didn't download this plugin.) If not, just push the stop button. I may not understan what your asking for though. Yes, I have a stop button, and it does nothing. There is also no stop button in the Banshee interface--only pause and play.

> 
4.  **Answer:** It works for me. Do you have the box checked in the plugins? I kinda find this plugin annoying.  Yes, I have the box checked, and it doesn't work. That's why I asked the question.

> 
5.  **Answer:** Try this link. [http://banshee-project.org/PluginRepository]("http://banshee-project.org/PluginRepository") > It is important to note that this is a completely separate module from Banshee that provides plugins. This module has not yet been released and is only available from Banshee Subversion:

svn co svn://svn.banshee-project.org/trunk/banshee-official-plugins

Additionally, the Podcasting and Smart Playlists plugins requires Banshee from CVS/HEAD (what will be the 0.11.x series). All other plugins in this module will work with Banshee 0.10.10 and higher.  No thanks.

---

### Post by JoWilly on 2006-06-26
[quote=aysiu]

 Yes, I have a stop button, and it does nothing. There is also no stop button in the Banshee interface--only pause and play.
[/quote] 
For the keyboard multimedia keys to work, you need to define them properly in the gnome keyboard shortcuts (menu/system/keyboard shortcuts).

Once properly set up, the keys should work everywhere in gnome apps (rythmbox, banshee...). For banshee you need to enable the multimedia keys plugin, but it does not seem to support the stop function (works on rythmbox).

Come to think about it.... is a stop button even needed, as pause does the same thing ? This is software, and not a physical hihi player that consumes electricity on pause....

---

### Post by aysiu on 2006-06-26
I've already enabled the keyboard shortcut. It works in Rhythmbox.

I've also enabled the multimedia plugin, and it works for play, pause, skip to next track. It does nothing for Banshee.

[quote=JoWilly]Come to think about it.... is a stop button even needed, as pause does the same thing ? This is software, and not a physical hihi player that consumes electricity on pause....[/quote] Yeah, I guess that was the second part of my original question. Am I just an old fogie who needs to "stop," when it's not necessary?

P.S. I mentioned this earlier in the thread, but I switched back to Rhythmbox. If someone can definitively give a solution to these Banshee problems, that's cool. Otherwise, I'm not just going to restate that I've already tried the obvious. I do appreciate people trying to help, though.

---

### Post by sha_man on 2006-06-27
there's no difference between pause and stop button except that with pause, the position of the played song is kept. I think a stop button is unnesserary (and bloat). :)

---

### Post by aysiu on 2006-06-27
[QUOTE=sha_man]there's no difference between pause and stop button except that with pause, the position of the played song is kept. I think a stop button is unnesserary (and bloat). :)[/QUOTE]
Thanks for the clarification. My mind must still be in the tape player days...

---

### Post by sha_man on 2006-06-28
[QUOTE=aysiu]It doesn't matter if I set my own folder in preferences. It still creates its own folder called ~/Music.[/QUOTE]

for me, it does **not**. :D  Maybe try again;)

---

### Post by aysiu on 2006-12-21
Okay, I've been on Rhythmbox for quite a while now, and I'm trying to give Banshee another shot in Edgy to see how it is.

Finally, there's a Smart Playlist plugin. But it's still creating a folder called ~/Music. I find that annoying.

I also have a new issue--is there a way to queue up songs in Banshee? In Rhythmbox and AmaroK, I could right-click on a song and say *Add to Queue*, and the songs would play in the order in which I queued them up. I don't see any kind of option like that in Banshee.

Should I just stick with Rhythmbox?

---

### Post by galv on 2006-12-28
Hi,
I've just tried Banshee I think it's a good player, but I still don't know how to create dynamic playlists (like Listen does). Let me explain, if I add a song from artist B and another from artist C  I want Banshee to use last.fm, for instance, to automatically add songs from artist A and D that are related to B.
Can Banshee do this? How?

Thanks

---

### Post by galv on 2007-01-07
> **galv said:**
> Hi,
I've just tried Banshee I think it's a good player, but I still don't know how to create dynamic playlists (like Listen does). Let me explain, if I add a song from artist B and another from artist C  I want Banshee to use last.fm, for instance, to automatically add songs from artist A and D that are related to B.
Can Banshee do this? How?

Thanks

:)[-( :)

---

