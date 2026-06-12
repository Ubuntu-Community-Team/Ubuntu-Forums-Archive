---
title: "Ubuntu 9.04 doesnt check for updates automatically"
date: 2009-06-26
forum: General Help
---

### Post by ulli.winter on 2009-06-26
Hi guys,

my problem is that i'm not notified when there are updates for my system.
As far as i can tell its not a problem of the new update notification system (i've set gconftool -s --type bool /apps/update-notifier/auto_launch false).
I recently didn't do any manual "check for updates available" for 7 days, and after that a notification icon appeared, telling me that my interent connection might be broken because ubuntu couldn't check for updates the last 7 days. :confused:

So it seems like that there is some "thing" that might trigger the update check automatically thats not working.

I don't know much about how that stuff, the only thing i've discovered is that "update-notifier --startup-delay=60" is in my startup applications list and seems to start on every boot.



Would be great if someone could help me...

---

### Post by t0p on 2009-06-26
Have you got the 'Update Notifier' in your list of apps to be run on start up?  I'm afraid that I'm using Xubuntu at the moment - on this machine the relevant list is at **Settings> Settings Manager > Autostarted Apps**.  On a computer running Gnome-based Ubuntu, it is under something like **System > Administration > Sessions**... well, it was like that on Hardy, it's very likely a bit different on Jaunty, but I expect it isn't hugely different, you should be able to find the list in question without too much trouble... When you have found the list, see if 'Update Notifier' is on it.  If not, add it yourself.  I think it's 'Update Notifier' you want, anyway...

This post hasn't been as helpful as I planned, has it?  Sorry about that...

---

### Post by billgoldberg on 2009-06-26
> **ulli.winter said:**
> Hi guys,

my problem is that i'm not notified when there are updates for my system.
As far as i can tell its not a problem of the new update notification system (i've set gconftool -s --type bool /apps/update-notifier/auto_launch false).
I recently didn't do any manual "check for updates available" for 7 days, and after that a notification icon appeared, telling me that my interent connection might be broken because ubuntu couldn't check for updates the last 7 days. :confused:

So it seems like that there is some "thing" that might trigger the update check automatically thats not working.

I don't know much about how that stuff, the only thing i've discovered is that "update-notifier --startup-delay=60" is in my startup applications list and seems to start on every boot.



Would be great if someone could help me...

I don't know if it's broken.

Ubuntu 9.04 has a new thing in that it only reports updates every week. Unless there are important security updates.

You make it notify you whenever any update is available in gconf-editor. I believe it's under apps->nofity-... -> autolaunch. Disable autolaunch.

---

### Post by themusicalduck on 2009-06-26
I've been having this same problem since I upgraded to Jaunty.. It doesn't even notify me of security updates anymore.

I tried changing my gconf to make Ubuntu check for updates daily but it doesn't seem to be working. Update notifier is enabled in startup applications too.

---

### Post by ulli.winter on 2009-06-26
Thanks for your quick replies!

T0p: "update-notifier --startup-delay=60" is in my startup list, and is activated

billgoldberg: as mentionend i think that theres something wrong.
i've already applied this "bugfix" : "gconftool -s --type bool /apps/update-notifier/auto_launch false", i think that is what you mean?

to sum it up: i dont get any notification of any updates at any time! additionaly update manager shows that the package-information isnt updated unless i do it manually... (like musicalduck is reporting)

what i didn't mention yet: i've installed ubuntu 9.04 RC / beta something like that, and upgraded afterwards to 9.04 final
i'm not sure if updates were working with the beta version though.....

---

### Post by jmfal on 2009-06-26
re: ULLI.WINTER
G`morning, yes you do need a good internet connection. Sometimes I dont get a notification so I just check up date manager.What you should do is system>administration>software sources, enter password, there are 5sections at the top of window, #1:ubuntu software put a check on all except source,uncheck cd  down towards bottum. in the middle of window >download from< if your in US CHECK SERVER FOR US.
#2: third party,there should be some http:// headings in this window with a box in front of them >put a ckeck in box.
#3:Updates: ubuntu updates, put a check by security and reccomemded,its up to you for the other ones.>automatic updates<>check box< and choose how you want to set the rest,i set mine for daily, and download in background.
I`M new to ubuntu, but thisdid the trick. you`ll find out that if you cruise through the forums, your question has been asked many times.
ALSO: wheh you exit software sources if there are updates it will let you know ckick refresh it will do its thing then exit,THEN  go to update manager install security updates,it up to you for the other updates.I know I probably missed some info, but this should get you going

---

### Post by billgoldberg on 2009-06-26
> **ulli.winter said:**
> Thanks for your quick replies!

T0p: "update-notifier --startup-delay=60" is in my startup list, and is activated

billgoldberg: as mentionend i think that theres something wrong.
i've already applied this "bugfix" : "gconftool -s --type bool /apps/update-notifier/auto_launch false", **i think that is what you mean?**

to sum it up: i dont get any notification of any updates at any time! additionaly update manager shows that the package-information isnt updated unless i do it manually... (like musicalduck is reporting)

what i didn't mention yet: i've installed ubuntu 9.04 RC / beta something like that, and upgraded afterwards to 9.04 final
i'm not sure if updates were working with the beta version though.....

Yes.

Have you checked launchpad.net to see if a bug has been reported?

Sometimes work-arounds are posted in the comments of those bugs.

---

### Post by ulli.winter on 2009-06-26
jmfall: Thanks for summing up the reasonabe settings, i've checked them and they are as you said

billgoldberg: [https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/332945](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/332945) i've read most some of them, but it seems to deal with how you should be informed about about updates, and not that i'm not informed at all

one big question to those who're informed about updates: if you start system->administration->update manager
what does the information say how old your package information is?

---

### Post by themusicalduck on 2009-06-29
Bumping this cause still looking for a fix.

---

### Post by ulli.winter on 2009-06-29
indeed,

maybe executing "apt-get update" on every boot (automatically) would be working?

(if that IS the problem, which i tried to discover with my question "what does the information say how old your package information is?")

---

### Post by themusicalduck on 2009-06-29
If my memory serves me right, the last time I looked at update manager without doing apt-get update first, it always said my updates were out of date by however long ago I last updated manually. (I can't check now since I've updated today)

So it does seem like Ubuntu is just not checking.. I'm not sure if it's in anyway related, but I did have a problem recently with a missing pgp key, which I fixed using a command to download and load the key automatically from the keyserver. While I was having this problem, my updates would not come up automatically, but I would get an error notification in my toolbar, suggesting that Ubuntu had at least tried to get latest update info. I could only update manually after that, much like now.

Perhaps the update notifications were turned off because of the error notifications and they have not been re-enabled since fixing the key problem? Update manager settings definitely say to check and notify me daily.

---

### Post by zmiq2 on 2009-07-15
Take a look at [http://spareinfo.blogspot.com/2009/07/ubuntu-automatic-updates.html](http://spareinfo.blogspot.com/2009/07/ubuntu-automatic-updates.html).

The solution I found to solve this problem was to type in the console, as root,

chmod ugo+x /etc/cron.daily/apt

See the above link for more details.

HTH

---

### Post by ulli.winter on 2009-07-16
thanks zimq2, i'm up to date again! :)

---

### Post by ma7hatter on 2009-07-16
I was having the same problem and the previously linked blog post fixed my issue.  Thanks for the help.

---

### Post by parsim on 2009-08-11
Thank you! Same problem: /etc/cron.daily/apt did not have execute permissions (unlike every other entry in that directory).

---

