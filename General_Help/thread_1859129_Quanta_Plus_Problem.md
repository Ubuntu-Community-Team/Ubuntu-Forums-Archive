---
title: "Quanta Plus Problem"
date: 2011-10-13
forum: General Help
---

### Post by Njlarson88 on 2011-10-13
Just installed ubuntu 11.10.  I love Quanta Plus (I do all the coding in the code not through the WYSIWYG but I do like to pop over and take a look at changes that I have made in the code to get a good idea of what it looks like before I save it)

Why did this disappear from the Ubuntu Software Center?  I would love to get this installed again.  Any idea on how to get installed again would be greatly appreciated!

---

### Post by tofuconfetti on 2011-10-14
Wondering the same thing.  This is a critical program for me.

---

### Post by Giana on 2011-10-14
Just upgraded my PC to 11.10 and I've discovered the same thing.
Frankly I didn't like it so much.
Anyway, is it still compatible with the new release?

G.

---

### Post by james@finnall.net on 2011-10-15
I upgraded my machine at the office yesterday to 11.10 and Quanta ran just fine afterward.  All my kde apps, except kmail, were OK.  The kmail is another story all together, really messed me over good on that one.  But today I upgrade my machine at home, following day, and no quanta anymore.   Listed in the database but no information to use for the installation.  No other information regarding status or anything.  So is it a work in progress or being dropped or what?

I have been using quanta for years, it works good for project and file management.  I code all html by hand, so the auto GUI stuff makes no difference to me.  I find that more trouble than it is worth.

---

### Post by james@finnall.net on 2011-10-15
Well it looks like the problem is with porting Quanta Plus to KDE4.  Lack of developers for really a long time.  So maybe no short term resolution.  That could explain why it has been removed from 11.10.  :(

I did find a dirty hack as it was called in the KDE forums.  It seems to work for me.  I had to add the natty (11.04) software repository to the software selections and reload the new databases.  Quanta was available.  When I installed it, it removed several newer packages and downloaded about 8 others.   So it could have major effects on other KDE applications.  Your mileage may vary.  I also use k3b and that appears to be OK for me.:P

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main universe

The line above is what I added to the software resources under the Other Software for United States.  The KDE forum also mentioned it should be removed after Quanta is installed to prevent other programs from being damaged using the older repositories.  Since this process is new to me, I am not able to evaluate the risks but I thought it wise to pass the warning along.  I did remove it from my system after installation and reload the databases.  Quanta was still listed as installed and it was operational.   Future upgrades will probably result with the same original problem again.

On my machine at the office I must have something different in my software resource settings that allowed Quanta to remain installed and not removed during the upgrade to 11.10.

Perhaps some others will find this helpful.
James

---

### Post by choclatboy on 2011-10-17
Hi

it seems there is hope in porting Quanta+ to KDE4 soon
[URL="http://alien.slackbook.org/blog/quanta-plus-for-kde4/"]
_Quanta Plus for KDE4_[/URL]

> the developers have been working on a Qt4 port for a while now, re-creating it as a plugin to kdevelop4.
[_http://quickgit.kde.org/?p=quanta.git&a=summary_]("http://quickgit.kde.org/?p=quanta.git&a=summary")

---

### Post by warsev on 2011-10-21
On the off-chance that anyone on the Quanta development team reads here, I want to add a great big [SIZE=4]+1[/SIZE] to the count of people who are waiting with high hopes that Quanta will be brought back SOON.

Having used a lot of web development tools, I've found that I can get more done faster with fewer mistakes using Quanta than with any other tool. It's all about productivity.

---

### Post by de Bacon on 2011-11-20
Unless I can find a workaround, understandable to my pea brain, I shall wait also, though it may prove inconvenient.  Quanta is a great program for web-development.

---

### Post by hal8000 on 2011-11-20
There was talk of Quanta returning in Kde5, when that will be I don't know.
I also used Quanta but now got used to working in Bluefish.

To get round the templates in quanta, just save a couple of html files as templates from your website.

To get around the changed pages and integral ftp program in Quanta I use
sitecopy  (available via synaptic).

If you worked in the code pages of Quanta, changes are not too different,
only if you worked in the WYSIWYG editor then Bluefish may be more difficult to use.

---

### Post by CodigoVision on 2012-01-28
Also a big fan of Quanta, use it exclusively for html / css, so another huge +1 from me too. Tried Bluefish, but it's not worth the switch, sticking with Ubuntu 10.10 for now.

---

