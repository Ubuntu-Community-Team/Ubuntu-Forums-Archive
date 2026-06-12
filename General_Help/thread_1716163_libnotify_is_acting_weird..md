---
title: "libnotify is acting weird."
date: 2011-03-28
forum: General Help
---

### Post by Mr. ViC on 2011-03-28
Hi guys.

So, I'm using Emesene here and trying to use a libnotify plugin.

But then, this annoying thing happens:

[img]http://uppix.net/5/e/2/8285b429789d01b1a9e82292770b2.png[/img]

But I'm pretty sure I have libnotify installed, saw that on Synaptic.

What am I doing wrong here?

Thanks in advance guys. :)

---

### Post by Mr. ViC on 2011-03-28
Bumping...

---

### Post by Mr. ViC on 2011-04-02
Bumping..

---

### Post by Mr. ViC on 2011-04-03
Last bump...

C'mon people, a little help here pleaseeeee. :)

---

### Post by Krytarik on 2011-04-03
You need to have both packages installed, "libnotify-bin" and "libnotify1".

Is that the case?

---

### Post by Mr. ViC on 2011-04-03
Hi, thanks for replying!

Yes it is, they both are installed.

---

### Post by Krytarik on 2011-04-03
What plugins have you enabled in Emesene?

---

### Post by Mr. ViC on 2011-04-03
Thanks for replying.

The list of the installed plugins (all of them) are:

```
 - Plugin Downloader
 - AbsoluteNotify
 - Ninja Mode (Anti-Boss plugin)
 - Audo Idle v0.1
 - Awn Unread Plugin
 - Censore
 - Commands
 - Compiz Integration
 - Autocomplete
 - Countdown
 - CurrentSong
 - Custom Gtk Style
 - Custom Status
 - D-Bus
 - Emotion Stopper
 - Encode Plugin
 - Eval
 - Facebook
 - gmailNotify
 - Html Commands
 - Idle Status
 - Imitate
 - Inline Notifications
 - Knotify
 - Last Said
 - Conversation Logger
 - Logger
 - mailChecker
 - MSNPLusSound
 - Multiple Send
 - Mute Sounds
 - OldNotifications
 - NotifyOsdImproved
 - OSD
 - Personal Message
 - Picture Preview
 - PlusPlus
 - Plus Color Panel
 - Psycho Mode
 - RotatePM
 - Screenshots
 - Spell
 - StatusHistory
 - Tiny URL
 - Toolbar
 - Google Translate
 - Web Sender
 - Wikipedia
 - Window Trembling Nudge
 - Wink Receiving
 - Wordpress
 - Xkcd
```

The current ones in use are:

```
 - CurrentSong
 - Custom Gtk Style
 - Custom Status
 - MSNPLusSound
 - PlusPlus
 - Plus Color Panel
 - Screenshots
 - Tiny URL
 - Toolbar
```

Now, this is what happens when the AbsoluteNotify is enabled (it returns an error now because I removed a Clist plugin that was always giving errors when starting emesene):

[img]http://uppix.net/3/f/2/c2b0e458277573b8fafc0b29d1310.png[/img]

---

### Post by Krytarik on 2011-04-03
You have some more plugins installed than I, and the both last mentioned are also not installed at my system. What if you disable both of them?

---

### Post by Mr. ViC on 2011-04-03
Which plugins do you want me to disable?

By the way, is there like a test I can perform to see if libnotify is indeed working? With another app or something?

---

### Post by Krytarik on 2011-04-03
> **Mr. ViC said:**
> Which plugins do you want me to disable?

AbsoluteNotify
Clist (already removed)
> **Mr. ViC said:**
> 
By the way, is there like a test I can perform to see if libnotify is indeed working? With another app or something?
Simply enter in a terminal:
```
notify-send foo bar
```

---

### Post by Mr. ViC on 2011-04-03
Thank you for replying.

Well that's it, nothing happened with the command. It's a libnotify problem really. :(

---

### Post by Krytarik on 2011-04-03
Then try reinstalling the mentioned packages.

---

### Post by Mr. ViC on 2011-04-03
Reinstalled and rebooted, still nothing. :(

---

### Post by Mr. ViC on 2011-04-03
Ok now, I have a big trouble here.

Tried to completely remove libnotify-dev and libnotify1, and then install them again.

Rebooted.

Can't login. I write my password, hit enter, and returns to the login screen.

Tried to CTRL+ALT+F1, works.

Logged in from there.

Tried to startx, this happens:

```
Fatal server error:
Server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock and start again.

Please consult the X.org Foundation support at http://wiki.x.org for help

ddxSigGiveUp: Closing log
Invalid MIT-MAGIC-COOKIE-1 keygiving up.

xinit: Resource temporarily unavailable (errno 11): unable to connect to X server

xinit: No such process (errno3): Server error.
```

What now? I'm screwed. :(

---

### Post by Krytarik on 2011-04-03
Do you get any other usual notifications (through notifiy-osd)?

If not, try reinstalling "notify-osd"?

Also, what version of it are you using, the official/default version, or a patched version provided by any PPA?

Did you modify its settings in any way?

---

### Post by Mr. ViC on 2011-04-03
Should I install notify-osd from the terminal at CTRL+ALT+F1?

And no, didn't do any modifications and installed everything from Synaptic.

Edit: Just tried to install it, doesn't do anything, it's already installed. As well as libnotify1 and libnotify-dev.

I still can't get on to my Desktop. :(

---

### Post by Krytarik on 2011-04-03
Sorry, we were posting at the same time before.

By removing "libnotify1", you obviously confirmed the removal of all packages that depend on it! They are quite a lot!

So to fix it, take a look into the log of apt: "/var/log/apt/history.log".

Then reinstall all packages that have been removed along with it.

---

### Post by Mr. ViC on 2011-04-03
Understood.

Just one question. As I don't have the acess to my Desktop, can I get acess to that list via the terminal? Because you mentioned apt and I don't know if that is any special command to open it, or if I should just "cd" until that folder.

Edit: Ok I saw your edit, trying to go there again.

---

### Post by Krytarik on 2011-04-03
Run this command to print the log, the most recent operations are listed at the bottom:
```
cat /var/log/apt/history.log
```To install any package, run a command like this:
```
sudo apt-get install PACKAGE1 [PACKAGE2] ...
```You should start with "ubuntu-desktop", it's a metapackage, some of the removed packages will get installed along with it. So, while proceeding, you will encounter some error messages about that the specified packages are already installed, simply proceed then.

You can specify multiple packages at a time, but definitely install "ubuntu-desktop" separately at first.

---

### Post by Mr. ViC on 2011-04-03
Hi.

God bless you, I'm on my desktop again! I'm glad I can learn with my errors, thank you so much for your patience with me and all this.

Now, I think this is good news:

[img]http://uppix.net/7/4/1/97b746dea51e60dc952ca1f4fd9d6.png[/img]

This is libnotify working properly, right?

But it is still giving me that error exception on Emesene...

---

### Post by Krytarik on 2011-04-03
Glad that you're back on the desktop again!

Also, that the notifications apparently work now, looks great!
I wonder what was actually the clue to this. Did you reinstall "notify-osd"?

As for the error messages of those plugin, are you sure that it is actually needed to display the notifications? I don't know, since I don't use Emesene regularily, usually I use Pidgin, and all my MSN contacts do have also an ICQ account, and use them at the same time.

If it's indeed needed, is there any way to upgrade it, or reinstall it?

---

### Post by Mr. ViC on 2011-04-04
Yeah I understand you.

But I would really like to get this working as it is a great utility plugin for me.

I'll try to get my problem solved with the coders of the plugin, or try to contact them. :)

As for you, thank you very much again for your patience and help! :P

---

