---
title: "Tweetdeck has stopped working under XFCE."
date: 2009-08-13
forum: General Help
---

### Post by jstrevino on 2009-08-13
To give you a bit of background, I just switched from Gnome to XFCE, per the generous advice given in this thread:

[http://ubuntuforums.org/showthread.php?t=1239001](http://ubuntuforums.org/showthread.php?t=1239001)

To recapitulate a bit, my system setup is as follows:

-- Dell Mini 10v
-- Ubuntu Netbook Remix 9.04
-- XFCE environment

Everything in XFCE is thus far a great whopping deal faster, but there is one saddening development: Tweetdeck no longer works. It sits there, mute, with a blank screen and inoperable buttons. Two de-installs and re-installs have failed to change this.

Poking about the archives, I came across this thread, which has some advice:

[http://ubuntuforums.org/showthread.php?t=1095493](http://ubuntuforums.org/showthread.php?t=1095493)

Unfortunately, none of the suggested fixes there seem to work. (And my terminal doesn't recognize getlibs as a valid command in any case.)

Given that this particular Tweetdeck malfunction appears to be a known issue, does anyone have any ideas on the fix? And why would switching to XFCE break it like this?

---

### Post by jstrevino on 2009-08-13
Poking about the interweb for a bit, it seems that the problem is in Tweetdeck's reliance upon Gnome and KDE keyrings -- which are not readily available in XFCE. With that in mind, turns out that if I enter the following in the Terminal, Tweetdeck works just fine:

GNOME_DESKTOP_SESSION_ID="4" /opt/TweetDeck/bin/TweetDeck

That session ID, of course, is just a number chosen at random.

Problem: a bit tedious to type this in every time I want to run TweetDeck, no? Any pointers on creating an executable script that will accomplish this via my launcher?

---

### Post by meeples on 2009-08-13
i highly recommend using [twitterfox]("https://addons.mozilla.org/en-US/firefox/addon/5081") instead :)

---

### Post by jstrevino on 2009-08-13
I guess this thread is just a monologue now, but I'll post here in the interest of getting this fix in the archives, so the next guy who needs this answer has it.

Basically, what I did was open up gedit and create a shell script thus:

--------------------
#!/bin/bash
GNOME_DESKTOP_SESSION_ID="4" /opt/TweetDeck/bin/TweetDeck
--------------------

I saved it as "tweethack" inside of /opt/TweetDeck/bin -- and then went to the command line and navigated to that same directory, where I entered the following:

chmod 755 tweethack

This apparently makes it executable. Then, from the terminal, and still within that same directory, I enter:

./tweethack

Tweetdeck launches, and all is well. This is pretty freaking imperfect, as I apparently have to launch from the command line, but it's better than no TweetDeck at all. QED.

---

### Post by jstrevino on 2009-08-13
Thanks, meeples, but I'm not a Firefox user -- and nothing beats TweetDeck for functionality.

---

