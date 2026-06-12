---
title: "Is Evolution crashing on anybody else???"
date: 2010-09-09
forum: General Help
---

### Post by held7over on 2010-09-09
Ubuntu 10.04  Evolution 2.30.3  Is this happening to anyone else?

This began when I was running 9.10 and seems to be maybe worse in 10.04. Evolution appears to be unstable, and easily crashes, most often when I attempt to mark something as READ, or sometimes when I SEND, etc., in which case, all CHANGES I have made are lost when I re-execute Evolution.....thus, anything I have deleted or changed the status of, is back or reverted to its original status. This forces me to CLOSE evolution frequently in order to SAVE my changes so that a crash does not bring them back. 

Any suggestions?

Thanks! :D

---

### Post by drewesq on 2010-09-11
Yep, me too! Really annoying as I have spent ages personalising it!

Hopefully an update will sort this out.

---

### Post by DeMus on 2010-09-11
With me it doesn't crash, but it won't keep my view settings in Calendar mode. I use the month view a lot. In the left hand pane there is a month shown. When I pull the line above it almost to the top I see 4 months. Nice, that's how I like it. Next time however I only see one month again.
I hate it when things like this happen. Happily, as with the OP, crashes don't happen.

---

### Post by TNT1 on 2010-09-11
Evolution never crashes on me. Are all your updates up to date?

---

### Post by held7over on 2010-09-11
Yes. I am completely updated.

---

### Post by TNT1 on 2010-09-11
Try starting evolution with no plugins enabled. ```
evolution --disable-eplugin
```

Or roll back to 2.28.3?

---

### Post by zbirdman777 on 2010-09-11
Evolution uses up a lot of memory, what are the specs on your computer or RAM usage when it's running. Mine never crashes, I have 4gb or DDR2.

---

### Post by TNT1 on 2010-09-11
> **zbirdman777 said:**
> Evolution uses up a lot of memory, what are the specs on your computer or RAM usage when it's running. Mine never crashes, I have 4gb or DDR2.

Yeah, but my evo is currently using a whole 19.8 Mb of RAM... It'd have to be a machine like my beloved 12 year old Dell for that to be the cause...

---

### Post by held7over on 2010-09-11
Evolution is using 43.3 MB. I have 2 gig of ram.


**TNT1**  I executed evolution using your command of "evolution --disable-eplugin"  and then deleted a letter and then marked another letter READ, knowing the odds are high that those two actions following one another would cause it to crash. It promptly did. Below is the error report from the commandline which was repeated 6 times:

(evolution:21421): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().
Segmentation fault
lucky@ispy2:~$

---

### Post by TNT1 on 2010-09-11
> **held7over said:**
> 

(evolution:21421): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().
Segmentation fault
lucky@ispy2:~$

That's a gtk or gobject library issue. Did you upgrade to 2.30.3?

---

### Post by held7over on 2010-09-11
Yes. I upgraded to 2.30.3 trying to get away from the crashes.

---

### Post by dcstar on 2010-09-11
> **held7over said:**
> **Ubuntu 10.04  Evolution 2.30.3**  Is this happening to anyone else?

This began when I was running 9.10 and seems to be maybe worse in 10.04. Evolution appears to be unstable, and easily crashes
..........
Any suggestions?

Thanks! :D

So you are complaining about an unsupported version causing problems?

My Evolution 2.28.3 - the official 10.04 version - doesn't crash, and if this version "crashing" was a common problem then this forum would be filled with thousands of posts about it.

Newer Evolution version are notoriously difficult to get working in older Ubuntu releases because of their myriad dependencies on various newer packages not available in that release, so if you have something that somehow has been made to get around these issues then it is no wonder it causes problems.

---

### Post by held7over on 2010-09-11
dcstar   I wasn't complaining. I merely asked if any one else was experiencing crashes of evolution....as it seemed unstable on my system and could use some help figuring out how to solve the problem.

If you missed it, I also added that this was happening to me on the "official" 2.28.3 version of Evolution (Ubuntu 10.04) and even prior to that on Ubuntu 9.10's official version of evolution, and that I had moved a couple of weeks ago to try 2.30.3 to see if I could get away from the crashes. 

Upon realizing the move hadn't helped, I decided to ASK if this was just my system, or if it was a general problem....before I go to all the trouble of reinstalling Ubuntu 10.04 and redoing my customizations again....in order to drop back to evolution 2.28.3, since the option of going to 2.28.3 is no longer showing in my package manager. It's as simple as that.

I really didn't want to have to delete my .evolution file to solve this problem, as I have almost 600 addresses with supplemental info in the file and don't cherish the idea of having to type them all back in by hand again...

---

### Post by held7over on 2010-09-12
A while back, WebUpd8 had the following banner on one of it's mailings:

**"Install Evolution 2.30 In Ubuntu 10.04 Lucid Lynx To Escape The 2.28 Crashes"**

This can be found here: [http://www.webupd8.org/2010/06/install-evolution-230-in-ubuntu-1004.html](http://www.webupd8.org/2010/06/install-evolution-230-in-ubuntu-1004.html)

Having read that banner and their mailing, I thought other people were having crashes of Evolution, and decided to try it to see if it fixed my problem....rather than bugging the community.

It didn't solve it. But, evidently, it fixed the problem for some people.

---

### Post by dcstar on 2010-09-12
> **held7over said:**
> dcstar   I wasn't complaining. I merely asked if any one else was experiencing crashes of evolution....as it seemed unstable on my system and could use some help figuring out how to solve the problem.
...........

Most Evolution problems experienced by some people (because a surprisingly large quantity of people using it seem to have few if any problems) seem to be related to non-standard plugins that they have enabled/installed.

These plugins do not seem to be certified by the Evolution developers and seem to have all sorts of strange interactions with each other, and basically seem to frequently result in systems that just don't work properly.

Disable any strange plugins and see if things improve.

---

### Post by held7over on 2010-09-12
Thanks dcstar. 

Unfortunately, I don't run any additional plugins at all, so there are none to remove.

---

### Post by TNT1 on 2010-09-12
> **held7over said:**
> Thanks dcstar. 

Unfortunately, I don't run any additional plugins at all, so there are none to remove.

Even if you did, you tried starting evo with no plugins and it still crashed. I am working on some other evo issues, will let you know if I find anything for you.

---

### Post by held7over on 2010-09-12
Thanks TNT1! 

If in the meantime I find something that helps, I will publish it here.

---

### Post by wilburg on 2010-10-09
i7-980, fresh install of 10.10, 2.6.35-22, 64 bit, Evolution 2.30.3, nothing added, current updates.

Evolution crashes many times a day. Usually it does not loose anything but it is very unstable indeed. Nothing in the logs that I have found. 

Yes others are experiencing problems.

---

### Post by acreech on 2010-10-18
I have a problem with Evolution 2.30.3 freezing when trying to read an email with an attachement that was sent from a Mac. I have one friend that uses a Mac. If she emails me without attachments then I can read the email. If she puts an attachment on, when I try to open the email, Evolution greys out and I have to "force quit". I can't even delete the email. 

It would be nice to know what to do about this, even to delete the one email.

---

### Post by pauwl on 2010-10-19
Evolution crashes for me when sending mails - but not always.
At least it does save the message in the outbox before crashing, so I need to re-start and then send/receive.

It also has messages "Hang" in the outbox and pops up an error message something like: 
"Error while Sending Message. Timed out trying to get lock file on /home/<name>/.evolution/mail/local/Outbox. Try again later"

Trying again shortly seems to work.

---

### Post by wilburg on 2010-10-22
Evolution 2.30.3, no plugins

Evolution crashes virtually every time on send. I have reinstalled and created new users. 

Does anyone have any ideas about what else to try?

i7-980, 12 gig ram, 10.10 2.6.35-22

---

### Post by Dark7man on 2010-11-17
Got it too - Evolution 2.30.3
Fairly Fresh install Ubuntu 10.10 - 2Days only really updates installed!

Random crashes. can be sending email or opening messages.  Sometimes when I close an open email, instead of closing the window, it seems to close everything.  Its crashed at least 5 times in the past 3 hours! :(

---

### Post by onaridge on 2010-11-17
Evolution works fine for me except for no new mail notification. That has never worked for me.

---

### Post by Dark7man on 2010-11-17
I get the notifications no problem.  The only email account I have running in Evolution is my imap google mail.

It to me is still a random crash.  Sometimes its when I'm reading mail, sometimes when I'm going from preferences etc.  Just getting curious as I started to google it and the posts I'm seeing are like 3 weeks old n more.  I wonder is it something from the update I got earlier?  I'm completely new to the Linux OS, only played around with LiveCD's.  Gonna keep doing some research as its a bit of a pain when You're trying to do something quickly and it decides to play hide n go seek!

Keep me me updated too mate if You come across anything to fix Your problem, like to know how to fix it!

---

### Post by Dark7man on 2010-11-23
Been updates and things installed over the past couple of days - Evolution seems a lot more stable for me... Someone want to mark this as solved, nobodies been back for days? :)

---

### Post by tekkidd on 2010-11-23
Yes, that used to happen to me, evolution and chrome would crash on me all the time. The only thing that really fixed it was a format reinstall. Although you can try running it through the terminal and after it crashes see why it crashed. You can also try ```
dpkg-reconfigure evolution
```

---

### Post by Dark7man on 2010-11-23
thanks for the tip... have noted it down for future :)  Evolution has stopped crashing on me - now just having the problems with sync issues!

Thanks again mate and take care! :)

---

### Post by xfryan on 2011-04-13
It happens to me to the point Im thinking to reinstall Ubuntu, but I resist since I think it has to be a reasonable way to deal with it.

I followed the suggestion and run the dpkg-reconfigure evolution command, and the started evolution from the terminal.

When it crashed I received this:


$ evolution
EI: MAIL PREFS
[U]Created new window in existing browser session.
Segmentation fault[/U]

Anyone another idea on what happens and how to deal with it?

---

### Post by mbck on 2011-07-11
I hope this will help.

I have several boxes running 10.4.  I will try to be more definitive regardfing plugins, but the pattern is as follows:

* If I only use IMAP and local mbox/Maildir, Evolution almost never crashes.
* At work I use the Exchange access mechanism.  

Evolution (when using Exchange) has recently started crashing randomly, at least once a day; this can be immediately after Send, or even at times it's in the background -- It's there, and a few minutes later it is gone.

This is new.  It also displays the usual misbehavior "Lost connection to the Exchange backend", but that's something I got used to.

I could use IMAP to Exchange.  That works fine.  However, I lose some Calendar functionality and a lot of directory functionality if I do so (for some reason, defining an address book based on the same AD/LDAP service as used with the Evo/Exch settings will be more limited if it is an "independent" address book)

I should use MAPI.  I have never been able to have this plugin work reliably.  I actually had to remove it, as it causes crashes even when not actively used.  Tried since 9.04, and through 11.04; it is nastier than others when it crashes.

To summarize: Could you, O fellow posters, inform the blog as to what access mechsnisms you use -  this could help developers narrow their search.



All the best,


Michel.

---

