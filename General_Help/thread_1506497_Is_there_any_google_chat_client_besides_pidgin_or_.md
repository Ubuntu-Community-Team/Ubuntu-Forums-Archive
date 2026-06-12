---
title: "Is there any google chat client besides pidgin or empathy?"
date: 2010-06-10
forum: General Help
---

### Post by rifter on 2010-06-10
I need to use a chat client that at least talks to google talk.  Others would be appreciated of course.

My problem is that Empathy does not allow logging of conversations, which is a deal breaker for me.  It also lacks sound.  

I have been using pidgin for many years since it was called gaim, and I have been loyal and patient with it.  However it is no longer usable at all for me.  I have had some sporadic cpu issues in the past, but usually  they were cleared up or an update fixed them.  But it never went beyond pranging one core, and restarting always fixed it.

Now (as in after 2.7.1 got pushed through the updates) I have regular cpu spikes that use up all four cores of my cpu at 100%.  :evil:  I disabled all plugins, that didn't work.  I wasn't using custom smilies but I saw they were checked, so I unchecked them.  No joy.  I reluctantly moved my ~/.purple directory so a new profile was created, with no buddy pounces, and everything turned off.  Within minutes the cpu spiked out of control.

What seems to happen is that pidgin takes up all of one core, and spawns a bunch of other processes that take up the other cores as well.  There are a lot of them, as in way more than four; I would say six to ten at least just looking at the ones that are high enough in cpu usage to jump to the top of htop. :mad: I have no clue why pidgin needs all those processes, much less why it needs to hog the cpu so much. :confused: This is on top of the recent problem that it no longer makes a sound when I chat, or on certain other events, which was horking me off but at least wasn't lethal.  When I quit pidgin, all those processes stay until I do a kill -9 on them (regular kill does not work, and if it did they probably would have died when I quit pidgin).  Very often pidgin will immediately take up all the cores again if I restart it.  Sometimes I get lucky and it is mostly okay for awhile.  Still high cpu usage, but not 100% on every core.   It soon disabuses me of any notion that it is finished messing with me because it takes up all the cpus again, sometimes when I least expect it.

I have to have something for IM, this is a critical function.  But so far google searches lead back to empathy or pidgin, and since the former does not do what I need and the latter is now irredeemably broken, I need to figure something else out pronto.  Any ideas? [-o<

---

### Post by rifter on 2010-06-10
Ok, so far I have found the following chat clients:

amsn and emesene only do msn messenger
kopete which does a lot of things
galaxium which only does msn in the version in the repositories but which seems to do google talk, msn, and irc in the svn version.

Galaxium seems to work well, but I had the following hoops to jump through:
The version in the regular repositories is 0.7.4.1 and only supports msn

There is a ppa that is supposed to be regularly updated, but it is for Jaunty or older only, with apparently only Jaunty being updated regularly:

[color=blue]_[http://code.google.com/p/galaxium/wiki/Repositories](http://code.google.com/p/galaxium/wiki/Repositories)_[/color]
[color=blue]_[http://code.google.com/p/galaxium/wiki/InstallUbuntuJaunty](http://code.google.com/p/galaxium/wiki/InstallUbuntuJaunty)_[/color]

This is what you would add to your repositories:
```

deb http://ppa.launchpad.net/galaxium/ubuntu jaunty main
deb-src http://ppa.launchpad.net/galaxium/ubuntu jaunty main

```

Then you would do

```

sudo apt-get update
sudo apt-get install galaxium-svn

```

Otherwise you can [color=blue]_[compile](http://code.google.com/p/galaxium/wiki/Instructions)_[/color] the package.

The code tarballs are not for anything later than 0.7.4.1, but you can get the svn here:

[http://code.google.com/p/galaxium/wiki/Instructions](http://code.google.com/p/galaxium/wiki/Instructions)

[http://code.google.com/p/galaxium/source/checkout](http://code.google.com/p/galaxium/source/checkout)
# Non-members may check out a read-only working copy anonymously over HTTP.
```

svn checkout http://galaxium.googlecode.com/svn/trunk/ galaxium-read-only

```

They list a bunch of libraries you need


and there are more listed [color=blue]_[here](http://code.google.com/p/galaxium/issues/detail?id=408&q=karmic&colspec=ID%20Type%20Status%20Priority%20Milestone%20Owner%20Component%20Summary%20Stars)_[/color]:

```

*gtk-sharp2
*libnotify0.4-cil
*libgstreamer-dev
*libhal-dev
*libwebkit1.0-cil
*libwebkit1.0-1
*libgcong2.0-cil

```

Now I did not install anything that was not in the repositories, as far as the libraries they are talking about are concerned.  I also installed a lot of probably unrelated stuff just to cover my bases.  Even so, I will attach the part of the apt log showing what I installed.

After I did that, I navigated to the directory I had brought down the svn checkout and did the following:

```

cd /home/rifter/downloads/galaxium/svn-06-10-2010/galaxium-read-only
sh autogen.sh --enable-msn --enable-irc  --enable-xmpp  --enable-adium  --enable-webkit  --enable-gnome
make
sudo make install

```

BTW enabling gecko did not work.  It said that I was missing gecko-sharp-2.0 and I did not feel like looking for that by then.

At any rate then galaxium was in my menu and worked.  It has kind of a funny interface.  Each login is a "Session" and you start new sessions to log in to other accounts.  But once you do that and check save password and automatically log in the next time it logs in all the accounts.  It also groups your contacts and allows you to look at contacts from individual "sessions" or all sessions (default).  It does support logging and unlike empathy has working sounds and logging.

There are people who like galaxium because they try to support everything a given protocol does.  

Nevertheless, I was on to kopete.  My apt log includes the plugins and such I installed for kopete, so I won't go into it too much here.  You do need the kde libraries installed, but it will run in gnome just fine (like all Qt apps do) if you have them installed.  Installing kopete using apt should also install any and all dependencies, as expected.

It turned out that kopete works very well and supports the most protocols.  It also supports encryption, logging, and has a lot of interesting plugins.  I couldn't get the facebook login to work, but I don't care much since I never used a facebook chat program anyway.

---

### Post by LowSky on 2010-06-10
I have never seen pidgin use 100 of the computer's resources, something tells me something is very wrong with your install, or one of the plugins.

And I belive empathy can save history now

As a standby you could use gtalk from iGoogle or Gmail inisde a web browser.

You can try Gajim, or any other XMPP (jabber) client and then enter the gtalk info by hand.

---

### Post by hugmenot on 2010-06-18
Gajim is a very good client for Google Talk chats. No video/audio though.

---

### Post by rifter on 2010-07-20
> **LowSky said:**
> I have never seen pidgin use 100 of the computer's resources, something tells me something is very wrong with your install, or one of the plugins.

And I belive empathy can save history now

As a standby you could use gtalk from iGoogle or Gmail inisde a web browser.

You can try Gajim, or any other XMPP (jabber) client and then enter the gtalk info by hand.

Thank you for your suggestions.

As it turned out the solutions I tried were inadequate in the end.  Kopete turned out to be the only thing that really worked and covered all the protocols, but for some reason it stopped making sounds when people chat, which is a show stopper because it basically means I would not know that people were even trying to talk to me.  Pidgin at least would make bubbles when people talked, and Kopete does have notify bubbles, but it seems only to use those for logons and logoffs.  For historical reasons, one of my aim logins has an insane number of contacts that I actually don't need anymore, but never could convince aim to delete.  So most of these logons are irrelevant to me, and the ones that are I don't tend to see.  It does not help that most of the people I generally talk to are online all the time and only come in or out of idle.

I checked Empathy again and it still has no option for logging.  Even if it had the option to save history (which it apparently does not have) that would still not be logging.  Logging is not saving.  Logging is LOGGING, as in everything get logged whether you remember to save or not; as in if you were to have a crash or a reboot the conversation would still be saved.  The lack of logging and notification sounds are probably the two biggest gripes I have read of with Empathy, and two major reasons that although Ubuntu may have decided it is the new default im client, most people are still immediately installing something more useful.

As for the pidgin cpu spikes, it seems according to the internet these are pretty common.  I didn't have anything weird installed, just the basic patches from the Ubuntu repository.  I never used any plugins, but I did make sure they were all disabled before concluding I was at a loss to regain my cpu.  As noted before I also tried with a clean config.  Something in like the update before last to pidgin caused this to happen.  Maybe I should try to regress to the previous version and see if it works better.  Even though there were cpu spikes before, at least there were periods of usability in between the spikes.

I have not tried Gajim, so I will try that at least for google talk applications.  In my frustration I had tried using the regular google talk client under wine, but it did not work.  There was probably some font problem, but basically none of the text was visible.

I miss being able to use google talk in a browser.  That used to always work.  But I had consistent problems with the "new" interface to gmail ever since they came up with it.   Basically, it just seems way too slow to me.  So I use settings and a bookmark to force the "old" interface.  And that interface used to allow you to google talk from the browser, but this feature has been removed. I guess they want you to use the "new" interface if you want that feature.

As for pidgin, I took one more stab at it.  This time, in addition to moving my ~/.purple directory, I did an apt-get purge on all the pidgin packages I had installed (well, basically; I actually used synaptic for this to make sure I didn't miss any packages, and made sure all the marked changes were set to purge).  Then I installed just the main pidgin package.  I'm going to give it a whirl again and see how it goes.  I'm even going to give pidgin the chance of only logging into one of my many accounts.

I think that one thing that might be affecting me that may not affect most people is that I have quite a few IM accounts on different services that I login to, and have a lot of contacts on there.  I am sure that things like the notification are working way harder on my setup than on others.  But then, I have used pidgin basically forever, and almost always like that with basically the same accounts.  It was only recently that it got too nasty to allow.

---

### Post by rifter on 2010-07-21
Well, after moving ~/.purple and purging every pidgin package, just as I said above I installed just the main pidgin package and gave it a go.  For awhile it seemed okay.  At least for several hours.  So I went ahead and added all my im accounts to it and let it go for awhile longer.

One thing I noticed was that if I watched htop pidgin would cause a very short spike to 100% on one core every time it had to make an alert sound of some kind.  But they were brief spikes.

I let it go awhile longer and when I came back pidgin was going strong on all four cores of my cpu at 100%, *and* hogging all sound so nothing else made noise.  Now I might not hesitate to lay blame for this on pulseaudio, but clearly this is just the behaviour I was talking about before, once again demonstrated on a fresh install with a new config.

---

### Post by rifter on 2011-03-05
For anyone else having this problem, it turned out to be what I had gstreamer set to.  Basically any sounds that happened were causing cpu spikes and it was building.  Going into gstreamer-properties and switching to pulseaudio fixed it.  Using anything else under Ubuntu still goes through pulseaudio.  It has been awhile but I think I had it set to sdl or alsa and whatever it was pidgin didn't like it as well as using the direct pulseaudio interface.

In the end nothing else was as good as pidgin so I ended up back with that.

---

