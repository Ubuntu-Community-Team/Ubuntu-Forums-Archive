---
title: "Remove Docky Anchor Icon"
date: 2010-07-05
forum: General Help
---

### Post by darthpenguin on 2010-07-05
Let me start off by saying how much I love opensource software. I especially like using Linux on my desktop. Not just because it is different and sexy, but also because it is just about as problematic as any other OS (ie. Windows, Mac) but it doesn't cost me a dime. If I am going to pay for software I expect the damn thing to work. If I get software for free I don't expect much at all. Linux (specifically Ubuntu) has exceeded all my expectations. I do have some minor problems I'd like to get sorted out however.

First, Thunderbird is an amazing email client and the only one that works well with IMAP and gmail. I mean the ONLY one. Seriously, not even Apple's Mail.app is up to the task (not last time I checked). That would be fine but Thunderbird is missing one key component, new mail notification. Now I feel I must clarify that a bit. An email client should be always open/active in the background. Not minimized in the task bar but in a system tray or notification area. Thankfully there is an addon that will offer this functionality on Windows and it works on Linux as well (though it is buggy). 

However one thing is still missing, unread email count. A brief onscreen notification of new mail might be handy if you happen to be sitting at your PC but when I return to my desk I want to see (without clicking anything) exactly how many unread email messages I have. Again, this is an integral feature that I think every body wants and every email client should have but Mozilla refuses to put it in their program. WTF. When I installed Thunderbird on my MacBook it automatically showed an unread email count with the icon on the dock. No need to install any addon or anything. I don't know if I get a notification (like through growl or anything) for new mail but that doesn't really matter. If I see a number in a green circle over Thunderbird's icon I know I need to check my email. That is how email programs are suppose to work. Thank you Apple (or Mozilla or whoever made this work).

All of this lead me to a neat app for Ubuntu called Docky. I have tried so many ways to get Thunderbird to stay open in a sys tray or something with a new message count and this is the only one that works. I just installed Docky, and added the "Docky Unread Count" addon to Thunderbird. I'm not about to let Docky go because it is the only thing that working for me. But I would like to iron out some issues with it.

First, I can't launch a file browser from it and second, I don't like the anchor icon. Hey if you guys are trying to rip off Apple's Dock why not go all the way? Instead of an anchor icon that launches preferences there should be a file browser link (like Apple's "Finder"). How can I do this? I tried to remove the anchor icon using the instructions here ([http://www.omgubuntu.co.uk/2010/04/remove-anchor-icon-from-docky.html](http://www.omgubuntu.co.uk/2010/04/remove-anchor-icon-from-docky.html)) but it doesn't work. Any suggestions? Thank You.

---

### Post by darthpenguin on 2010-07-05
ok, I can launch a file browser. I'd like the option to change the icon the the "Home Folder" icon. though I suppose the folder-with-the-cursor make more sense anyway.

I still really want to get rid of that damn anchor icon though.

---

### Post by darthpenguin on 2010-07-08
Ok, a resent system update allowed the workaround here [http://www.omgubuntu.co.uk/2010/04/remove-anchor-icon-from-docky.html](http://www.omgubuntu.co.uk/2010/04/remove-anchor-icon-from-docky.html) to work and the anchor icon is effectively removed. I can still access settings for the dock by right clicking on the divider between the launchers and the docklets. That works for me. I had to make some changes to the "Home Folder" launcher in /usr/share/applications to get it to properly launch when dragged to the dock. Now I have a dock that works well and looks decent.

I didn't really want a dock but it was the ONLY way I could get a mail program to behave properly on Linux. I even added Thunderbird to the indicator-applet -- which was quite a chore -- only to find that this was just another way to launch the app. If you want to be notified of new messages you need to keep Thunderbird open in taskbar. And even then I don't think there was an in-your-face unread message count to let you know -- when you sit at your computer -- that YOU'VE GOT MAIL! Evolution was already integrated with the indicator applet (which -- as we have seen -- is useless) but that is moot as evolution simply does not integrate with gmail/imap at all well. And of course if you use multiple machines you simply have to use imap. Who wants to sit down at a machine only to seen some "new" mail that you already read somewhere else? Or worse, you have some emails on one machine and the rest on another. Or what about when you setup a new client and you need to wait to download a year's worth of email. Or when you have to backup emails and contacts whenever you get a new machine or reinstall your OS?

Basically, POP sucks, most email services suck, most email clients suck, and Microsoft sucks. IMAP is the right way to handle email, gmail is the best service, Thunderbird is the only email client that works (even if it requires a **** load of addons to work properly), and Linux simply rocks. Getting all these to work together is a pain in the face (and it really shouldn't be). But I finally got a setup that works.

And hey, if I have to use a dock at least it blends well with my macbook. Side-by-side my friends can't tell the difference. lol.

I'd like Thunderbird to minimize to the dock when I hit the X in the window frame. You know, just like it works on the Mac. I just like to keep things consistent I guess. But this is a small thing. I just need to remember to minimize Thunderbird instead of exit.

I'll mark this as solved in any case.

---

### Post by bobcollard on 2010-07-08
Try cairo-dock, you can change the icons to your heart's desire.  It also runs desklets and many other things like weather and notifications.

---

### Post by darthpenguin on 2010-07-08
cairo-dock is a great application. I played with it once (just for shits and giggles). It seems to take a lot of configuring to get it right tho and even then it was never quite what I wanted. I ended up going with AWN for a time. Mostly because it was not as complicated as cairo-dock. When I installed my second monitor AWN completely goofed up (It's worth noting that cairo-dock does support dual screens). I was fine with that. I wasn't married to the idea of a dock. And nothing was handling my email program the right way anyway. I only tried Docky because Thunderbird had an addon for it that showed an unread message count. Now that the ugly anchor icon is gone I actually like Docky. It's just very simple -- does everything a dock should do (almost) with little configuring.

I'll just take this opportunity to make some small suggestions. The 'Helpers' are a neat feature of Docky. The Rhythumbox helper is cool -- kinda useless for me and everyone else with a multimedia keyboard tho. The Thunderbird addon works for unread email count but this function in the form of a 'Helper' might be nice (for consistency). And a Transmission helper would be amazing. maybe something that shows transfer rates like on the mac. Or (and this is where Apple got it wrong) something that shows download progress (by progress bar or percentage). That's what the user cares about -- "When is my torrent going to be done?" not "How fast is it downloading?". Though I see where something like this could be a problem if, say, 3+ torrents are downloading at a time.

---

### Post by darthpenguin on 2010-07-10
Right. Sometimes you just can't win. My system updated and a new version of Docky came through. Cool right? Wrong. My joyful bliss of the past few days has come to an abrupt halt. The "Docky Unread Count" addon no longer works. I updated to the latest Thunderbird (3.1) just to see if that would fix it (the addon says it supports 3.1) but I still have nothing. All other icon badges still work such as Transmission (yes, I got that one working) and the rhythmbox count down. If anyone has any blinding incites into how to fix this I would appreciate it. But I'll leave it be for now. I'll prob just wait until an official email helper is released. It's gotta happen soon anyway. I mean, an email notification is far more important than knowing how fast a torrent is downloading or how much time is left in a song. The only notification that may be slightly more important is unread IM's in pidgin (which works great by the way) and even that is debatable. I'm not saying that the other functions are useless - they're not. It just seems like someone's priorities are all messed up. I'm not even saying that there has to be a Thunderbird helper (though that would be nice). I don't even see a helper for Evolution, Gnome's default mail client, as one would expect from a *gnome* dock (it is an extension of *gnome*-do, is it not?). Oh, there is a gmail docklet that shows me an unread count - good form - but it just links to gmail's web interface when clicked. If I wanted gmail's web interface I wouldn't be using a mail client would I?

I chose to use docky just because of the unread message count addon. Although that feature is no longer working I will keep running the dock and gnome-do. partly because I expect it to improve with time (I know it is still a young app) and partly because I really do love it. It looks great (aesthetics are important), it's simple, and it works (not buggy). It's just missing a pretty damn important feature. Thats all.

I love Docky, I love Gnome-Do, I love Linux, And I love you.

Thanks Guys.

---

### Post by CMXILies on 2012-02-28
I use Cairo and Docky both for numerous reasons, but I really would like to get rid of the anchor icon as well.

---

### Post by nothingspecial on 2012-02-28
Old thread.

Closed.

---

