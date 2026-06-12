---
title: "Want Something Better Than Gwibber For Twitter"
date: 2010-09-06
forum: General Help
---

### Post by jakj on 2010-09-06
I am getting frustrated with trying to find a good Twitter client for Ubuntu. (And I would prefer to spare myself the hassle of AIR, but I will if that's the best option.)

My main complaint is that I cannot find a single client anywhere with a working tray icon for unread messages. I have tried Gwibber with and without the Messaging Menu installed, and I have scoured the websites of everything from Twitux to Mixero, and not a single one admits to any sort of mechanism for showing unread messages. Gwibber specifically says they -do- include this feature, except it works not for all messages, but only for messages specifically directed at me, at which point I reject a piece of software that is trying to tell ME what I should be doing with my computer.

(There are even closed bug reports against Gwibber on this issue, and the response to users saying "I want this" is the developers saying "You shouldn't want that", which is...silly beyond belief. There is a very big difference between saying "Not enough people want a feature to justify the development time" (which I would accept) and saying "People are wrong to want this feature" (which I do not accept).)

All I want is 1) a tray icon to change colour, or shape, or something, to indicate there are unread messages, and 2) some way, with the client open, to see which messages are unread and to mark them as read explicitly. (Basically, it should work like most email clients do, where you read a message and it marks it as read.)

---

### Post by rapidDazz on 2010-09-09
Howdy,

I agree to a point.  I don't understand what the developer is saying he won't fix or implement, but I'm frustrated that gwibber ignores certain replies to my comments I make in facebook.  Which is annoying enough in itself.

Having said that, on your comment of setting up AIR - I'm not sure the troubles you're having.  About 3 minutes ago I downloaded from adobe the .bin installer file, added execution rights and ran the file.  Said yes to install, (nothing installed with sudo I might add, if that's causing you grief perhaps), and restarted firefox.

Then proceeded to install TweetDeck which I keep hearing good things about.  While I think AIR is slower than something that's not written for a development platform, installing tweetdeck seemed okay.

Instead of saving tweetdeck I just said "open" which installed it enough to be in my applications menu, I have the little icon on the notifcation toolbar and when you mention @darrennolancom in twitter, I'll let you know if the icon changes XD

Anyway - Here's hoping for something better than gwibber.

Cheers,

---

### Post by rapidDazz on 2010-09-09
So far I'm not a fan of TweetDeck but now I have AIR installed there should be a billion other tweetdeck alternatives to try out.

PS: Really not a fan of TweetDeck at this stage.  If you discover something else (even driven by AIR) please let me know :D

---

### Post by jakj on 2010-09-09
I did get AIR working, since it actually does use the package manager in Ubuntu and doesn't just throw crap everywhere like I was worried it would. It is indeed slow, but so is Java, and...well, so few people nowadays have the time, energy, or ability to develop cross-platform, which is unfortunate, but understandable, so stuff like Java and AIR do allow us to get applications we otherwise wouldn't get.

I'm using Mixero at the moment, and as it turns out, it actually does do what I want...mostly. The functionality is all there: All I have to do is add everyone in my entire list to the active list, and use the Avatar mode, and it shows me with a little bubble how many unread messages there are for each contact.

Problems with Mixero:

*) The tray icon updates in a very buggy manner, so Avatar mode is the only reliable way, which then consumes desktop space at all times.

*) One of the contacts is always shown as "the current selected item" in Avatar mode, leading to two issues: 1) When updates occur, the current selected item remains in its position instead of sinking to below other items that get updates, and 2) If the current selected item gets updates, any time you click on any Avatar (even the currently selected one), it marks everything in it as "read" before it even shows it (because, even if you click the one currently selected, the code de-selects it and selects it again).

*) It may as well be a read-only application, because any time it opens a window for any purpose whatsoever, like to make a post, it flips out like a squirrel on cocaine and you desperately have to spam-click just to close that window.

*) Transparency doesn't work at all on Ubuntu, so you can't use Avatar mode as the author intends, which is to have it unobtrusively on top of whatever you are doing.

*) If you're not careful, you can open ghost side panels that prevent opening real side panels until you kill the application entirely.

*) Slower than a native application would be.

Buuuuut...it does function, more or less. I am starting to get -very- tempted to poke into the Gwibber source and see if fixing this issue would be as simple as commenting out a check somewhere to unrestrict the new-message notification. I have no idea where to even find the source code, however, other than deb-src, because the Gwibber website is old and half-broken. Bleh. I'm surprised Ubuntu chose gwibber for its "Social From The Start"...or maybe not, since it seems to be the best of a lot of mediocre choices.

---

### Post by rapidDazz on 2010-09-09
Well, after everything I myself am having issues with running Firefox (and flash) at the same time as an AIR application.  Which really does my head in a bit.  And I can't be assed working out what's going on.

You're right, about not being as fast as a native application, but I'm actually thinking AIR at this stage is far backwards compared to Java.  If cross platform was a concern there's always much faster methods like the QT framework

Regardless, no Air application I tried tonight made me want to spend more than 30 seconds on solving the "flash why do you keep crashing" bug.  Going back to Bitlbee (which is more than fine for my twitter needs) and facebook via the website.

---

### Post by jakj on 2010-09-09
Well, I'm trying out Choqok right now.

Pro: Linux-native (KDE) - meaning fast
Con: Just a tad buggy here and there
Pro: Handles read/unread in the main window and the tray the way Gwibber -would- if they had any sense.
Con?: I can't actually confirm the tray works the way their site says it does because the icon is functional, yet blank. Heh.

If you want to try it, use [https://launchpad.net/~neversfelde/+archive/experimental](https://launchpad.net/~neversfelde/+archive/experimental) and also add the package "libqca2-plugin-ossl" or it will crash when adding a Twitter account. If you're not using KDE, copy the slew of packages it installs into a file so you can see what you need to remove if you don't end up liking it.

I don't know how much of me liking this product after only a couple minutes is due to just a calm sense of relief of something that 1) works and 2) isn't AIR. We shall see how it goes.

---

### Post by rapidDazz on 2010-09-10
Doesn't seem to support facebook at this stage, which is what I'm really after.  Hrmm.

---

### Post by Balthazar_Droid on 2010-09-19
Tweetdeck seems to be the most polished Twitter/Facebook client I've used. Having said that, I still wish there was a native Linux app that had that much polish and features.

If anyone is looking for a strictly Twitter client, Turpial is an awesome native Linux client that I would use exclusively if it worked with Facebook too.

---

### Post by nutznboltz on 2010-09-19
I reported what was going wrong with tweetdeck installation via firefox and I was told that "nothing has broken" even though it used to work in the past and I was told that it was "my system" even though it happens on multiple computers (not that Chris Coulson bothered to ask if it happened on multiple computers before he insinuated that it was only on one system.)

That being said comment #15 in the bug report is how to install tweetdeck:

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/641294](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/641294)

Hope that helps (more than Chris Coulson helped)

---

### Post by Vrroom on 2010-09-20
Have you tried 'Turpial'....its really nice and similar to tweetdeck with multi account support. It also have gtk native interface. The tray icon won't show number of unread tweets but it will turn green if there is a new tweet. Desktop Notifications are also supported. I am using it and its really nice.

Turpial Stable ppa: [https://launchpad.net/~effie-jayx/+archive/turpial](https://launchpad.net/~effie-jayx/+archive/turpial)
Turpial Development ppa: [https://launchpad.net/~effie-jayx/+archive/turpial-devel](https://launchpad.net/~effie-jayx/+archive/turpial-devel)

---

### Post by Jitse on 2010-09-25
In my opinion the best Twitter-only client for Ubuntu is **twhirl** (by Seesmic). Unfortunately it is another AIR app, but it runs without any trouble whatsoever. To see for yourself check out [http://twhirl.org]("http://twhirl.org"). The website states that it runs on Microsoft Windows and Mac OSX but it also works on Ubuntu (and probably on every other distro which supports AIR).

---

