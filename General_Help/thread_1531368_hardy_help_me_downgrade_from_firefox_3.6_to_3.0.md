---
title: "hardy: help me downgrade from firefox 3.6 to 3.0"
date: 2010-07-14
forum: General Help
---

### Post by ChrisC on 2010-07-14
Short version:  I'm running Ubuntu 8.04 (Hardy Heron) and need downgrade ASAP from Firefox 3.6 back down to Firefox 3.0.  In Synaptic, the firefox-3.0 package cleverly now shows up as version 3.6.  How can I downgrade?  I'm open to anything.

Long version:

I just did a security update on my Ubuntu 8.04 (Hardy Heron) installation.  It upgraded Firefox from 3.0.x (x=19, I think) to 3.6.x.  This broke an absolutely critical plugin for me, pretty much the one and only plugin I care about, and one that doesn't support Firefox beyond 3.0.  More on the plugin below if you care.

But for now I MUST downgrade immediately to Firefox 3.0.x.  I realize that The Powers That Be probably forced us to upgrade to 3.6 for a reason (i.e. 3.0 isn't supported anymore, or something like that) but I really can't deal with a 3.0-3.6 sea change right now.  I need to get the FF install back down to 3.0 pronto.  My work is piling up fast.

If there's no way to do it within the carefully security-controlled world of officially-supported 8.04 LTS, I'm open to steps that will force it.  I just need my FF 3.0 to work for a couple more months.

Related question:  If I downgrade, what are the chances that FF 3.0 will be able to parse my (carefully crafted) profile, now that the newer 3.6 has gone in there and presumably mucked it up with 3.6-specific things?  I can extract the 3.0 profile file(s) from a backup if needed (a snapshot was taken just before the security upgrade!) 

Sidebar 1:

I'm not going to say what the plugin is, but it's critical to me.  I literally can do virtually nothing without it.  I will find a replacement for it (one that supports 3.6+) when I tackle the OS upgrade, but NOT NOW :)

Sidebar 2:

I know 8.04 is a little old, but I don't have the time right now to deal with upgrading.  It's a massive undertaking for me to do that, and I plan on doing it in the fall (read: not now!)  As part of that OS upgrade (wipe and reinstall, actually), THAT is when I would tackle migrating to a newer version of Firefox, including figuring out all the preference adjustments to get it to my liking and, most importantly, get my critical plugin to work.  And that's also when I would upgrade to FF 3.6 (or whatever) on ALL of my machines.  I have several computers (Linux and Windows), and I keep them all at the same identical level of Firefox, with the same prefs, and that same critical plugin, so I have the same browsing experience and feature set no matter which computer I'm at.

Sidebar 3:

While I'd love to sanctimoniously wag my finger at Ubuntu for doing this Terrible Thing to us users, I imagine there were good reasons for it and perhaps was even some debate about forcing a 3.0 -> 3.6 update.  I'd love to see that debate, if someone can point me to it (e.g. a bug discussion thread on launchpad).

This has really screwed up my life.  Hopefully someone can help me out.

---

### Post by jmszr on 2010-07-14
ChrisC,

Here is a ppa for 3.0.00: [https://launchpad.net/ubuntu/+source/firefox-3.0/3.0~b5+nobinonly-0ubuntu3](https://launchpad.net/ubuntu/+source/firefox-3.0/3.0~b5+nobinonly-0ubuntu3) .

If that doesn't work you could try using the Firefox addon "Nightly Tester Tools": [https://addons.mozilla.org/en-US/firefox/addon/6543/](https://addons.mozilla.org/en-US/firefox/addon/6543/) . It has a "force compatibility" function that might get your addon working. Once you install Nightly Tester Tools you will need to re-download your addon and when you attempt to install it there will be a "force compatibility" button in the install window. Might work.

---

### Post by ChrisC on 2010-07-15
Thanks jmszr for the excellent info.  Let me parse it.

PPA ... OK, it took some Googling, but I understand now that a PPA is a custom packaging system [1], and I can use that URL you gave me to ultimately install that package without too much fuss [2].

Now, what you actually directed me to was the 3.0beta5 release, which is what was originally packaged in 8.04 upon its release in April 2008.  OK, that's a start :)  I don't need to go that far back, just to the latest 3.0.x .  I think 8.04 LTS was at 3.0.19 before I got the surprise upgrade to 3.6.x.  Can I get a 3.0.19 PPA, or something close to it?

I searched the PPA system and I see that it only lists two "firefox-3.0" packages:  the 3.0beta5 that you directed me to, and the 3.6.6 that's current.  I do see a 3.0.19 package [3] but it's listed as available only for 9.04 Jaunty.

Thanks for the "force compatibility" tip; I'll consider that if I have no luck finding an up-to-date plugin WHEN I get around to tackling FF 3.6.  For now, though, I'm trying to avoid 3.6 altogether and just eke out life with 3.0 a little longer.

Any further help will be greatly appreciated!

[1] [https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)
[2] [https://help.launchpad.net/Packaging/PPA/InstallingSoftware](https://help.launchpad.net/Packaging/PPA/InstallingSoftware)
[3] [https://launchpad.net/ubuntu/+source/firefox-3.0/3.0.19+nobinonly-0ubuntu0.9.04.1](https://launchpad.net/ubuntu/+source/firefox-3.0/3.0.19+nobinonly-0ubuntu0.9.04.1)

---

### Post by jmszr on 2010-07-15
ChrisC,

I just found these: 32-bit:[http://packages.ubuntu.com/intrepid/i386/firefox-3.0/download](http://packages.ubuntu.com/intrepid/i386/firefox-3.0/download) and: 64-bit: [http://packages.ubuntu.com/intrepid/amd64/firefox-3.0/download](http://packages.ubuntu.com/intrepid/amd64/firefox-3.0/download) . That's the 3.0.19 version. Downloads as .deb. It is Intrepid 8.10 so it remains to be seen if that causes any problems, but Hardy only has the Beta5 available.

---

### Post by lovinglinux on 2010-07-15
The simplest solution is to download [Firefox 3.0.19](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/3.0.19-real-real/) from Mozilla, extract it and execute the firefox file inside it. This way you don't need to mess with the package manager or PPA repositories. There are some additional steps to make sure everything work. See method #1 details in my [tutorial on how to install other versions](http://firefox-tutorials.blogspot.com/2010/05/installing-other-versions.html). 

That being said, I also would recommend forcing the compatibility, if that works. I prefer the [Add-on Compatibility Reporter](https://addons.mozilla.org/en-US/firefox/addon/15003/).

The third option would be to send me the link for the add-on via private message, if you don't want to share it publicly. I could try to apply the necessary updates and send back to you. Depending on the add-on complexity, that could be easily done in a couple of minutes and I could also make sure the add-on doesn't behave badly. (I'm an extension developer btw).

---

### Post by ChrisC on 2010-07-25
Thank you both for your help.  Less than a day after I posted this, another one of my machines (Windows this time) spontaneously upgraded itself from 3.0 to 3.6 as well.

So I decided to hold off on the downgrade for a couple days and see how it went.  I found a replacement plugin (more on that below) and it seems to be working.

So I may not do the downgrade after all.  Except for breaking my plugin, the 3.0->3.6 upgrade went very well and I only had to tweak a few more thing in 3.6 and now it seems to be OK.  Normally I'm enormously irritated at the UI of new browsers, but FF 3.6 seems to be OK, or at least it imported my 3.0 prefs very well.

The mystery plugin:  cookie management.  I've been carefully managing my cookies for a decade now, from the Netscape days, continuing though the early days of the Mozilla milestone releases, and up through Firefox today.  First it was with Cookie Pal (on Win95!), then I migrated to Cookie Safe Lite (aka CS Lite), and now I'm trying out Cookie Monster.  I was happy to see that generally it already knew about my cookie rules (e.g. allow domainx.com for session only) so that made the whole migration nearly painless.  I just had to learn a new UI.

In fact, migrating myself to FF 3.6 was a task for the fall, and this seems to show that it'll be painless.  That means that I may tackle a computer upgrade after all.  I had been starting to think about pushing it back beyond Christmas, because of competing demands on my time, but this just got a lot easier since the FF 3.6 issue may now be mooted.

Again, thanks!

---

