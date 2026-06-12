---
title: "Upgrading to Firefox 3.6 on Hardy 8.04"
date: 2010-01-26
forum: General Help
---

### Post by michael37 on 2010-01-26
I just upgraded Firefox from updated yet ancient version 3.0.17 to modern 3.6 using [Firefox-stable repository]("https://launchpad.net/~mozillateam/+archive/firefox-stable")

March 15, 2010 update: **[SIZE="4"]Firefox 3.6 works perfectly on Hardy 8.04 using firefox-stable repository[/SIZE]**

[quote="OUTDATED INFORMATION SINCE THE BUG WAS FIXED"]
I ran into two problems.

1. Firefox packages conflicted.  I had to manually force-remove firefox-3.0 to install firefox-3.6.

2. Firefox 3.6 was not able to start.  It was giving some kind of an error message.  I worked around the problem by creating a new profile.  but my old 3.0 profile with all my stored passwords, bookmarks, etc is unusable in 3.6.
[/quote]
Any solutions?

P.S. Thank you, Mozilla team and esp. asac, for making new Firefox available for Hardy LTS users.  It's been a drag not having 3.5 as an option in repositories.

UPDATE.

Filed bug which was assigned high importance. [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/513074](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/513074) - [COLOR="Red"]**[SIZE="3"]BUG IS NOW FIXED[/SIZE]**[/COLOR]

Also, found a workaround for a profile change.

start firefox as
firefox -ProfileManager
create new profile (let's call it new)
firefox will start and display a blank look (without any of your extensions)
close firefox
go to directory .mozilla/firefox
copy "important data and their files" EXCEPT User styles (see [http://support.mozilla.com/en-U/kb/Recovering+important+data+from+an+old+profile#Your_important_data_and_their_files](http://support.mozilla.com/en-U/kb/Recovering+important+data+from+an+old+profile#Your_important_data_and_their_files)) from broken profile XXXXXX.default to YYYYYY.new
do not copy anything else, esp User styles and extensions.

you will lose all your extensions, so you will need to manually download them.

---

### Post by byStanderone on 2010-01-26
...i think the latest version of firefox is not supported in 8.04

---

### Post by michael37 on 2010-01-26
> **byStanderone said:**
> ...i think the latest version of firefox is not supported in 8.04

It wasn't until January 24, 2010, when Mozilla Team released Firefox 3.6 for Hardy in Firefox-Stable PPA.  See link in the OP.

---

### Post by JayMan8081 on 2010-01-28
> **michael37 said:**
> I just upgraded Firefox from updated yet ancient version 3.0.17 to modern 3.6 using [Firefox-stable repository]("https://launchpad.net/~mozillateam/+archive/firefox-stable")

I ran into two problems.

1. Firefox packages conflicted.  I had to manually force-remove firefox-3.0 to install firefox-3.6.

2. Firefox 3.6 was not able to start.  It was giving some kind of an error message.  I worked around the problem by creating a new profile.  but my old 3.0 profile with all my stored passwords, bookmarks, etc is unusable in 3.6.

Any solutions?

P.S. Thank you, Mozilla team and esp. asac, for making new Firefox available for Hardy LTS users.  It's been a drag not having 3.5 as an option in repositories.

Agreed! Thanks for helping those of us that are taking advantage of the LTS idea in a work environment!

Also thanks to Michael for the tip to move your old profile. It didn't even occur to me until I read this post. I'm okay with resetting all of my prefs and add-ons for a newer version of Firefox.

---

### Post by fbrauer on 2010-03-16
I just upgraded to Firefox-3.6 by following the instructions at the Stable Repository, then
sudo apt-get remove firefox
sudo apt-get install firefox-3.6

and my profile, passwords etc. were already preserved!

---

### Post by michael37 on 2010-03-16
> **fbrauer said:**
> I just upgraded to Firefox-3.6 by following the instructions at the Stable Repository, then
sudo apt-get remove firefox
sudo apt-get install firefox-3.6

and my profile, passwords etc. were already preserved!

Good catch, the bug is now fixed and the problem no longer occurs.

---

