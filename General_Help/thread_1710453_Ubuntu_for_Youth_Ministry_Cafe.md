---
title: "Ubuntu for Youth Ministry Cafe"
date: 2011-03-19
forum: General Help
---

### Post by SuperTeece on 2011-03-19
All,

I'm looking for a way to fullfill the following requirements for a group of public computers that will be used by students in a youth ministy chapel cafe:

1. User is limited to the browser only
2. User is required to establish a user account for tracking usage

So I want the monitor to display a login gui that gives the student the option to make an account. Then I want the ability to run reports showing URLs visited and which users visited them.

This can be local to each machine or server based.  The plan is to start with three computers but I'm sure I can get a fourth for a server if needed. I've been playing around with OpenKiosk today to see if it would meet my needs but I can't make it through the install. All documentation seems to be for earlier versions.

Thanks,
TC

---

### Post by upptown on 2011-03-19
I assume that you want to make sure that the systems are being used in a manner consistent with the value system of your ministry. 

Make sure that your users have signed a "user agreement" that clearly states that their use of the systems is being monitored otherwise there could be issues.

---

### Post by SuperTeece on 2011-03-19
> **upptown said:**
> I assume that you want to make sure that the systems are being used in a manner consistent with the value system of your ministry. 

Make sure that your users have signed a "user agreement" that clearly states that their use of the systems is being monitored otherwise there could be issues.

So yeah, an "I Agree" button with the user registration that is logged would be awesome.

---

### Post by flipper T on 2011-03-19
why would you want to "monitor" the urls visited by the users (you made no mention of age concerns, so i will assume that's not it)

do you want to know if they are visiting the sites of dawkins or hitchens ? what will you do with this information ?

well, whatever, im not comfortable with providing you with any assistance whatsoever.

god bless.

---

### Post by abyrne on 2011-03-19
> **flipper T said:**
> why would you want to "monitor" the urls visited by the users (you made no mention of age concerns, so i will assume that's not it)


He did note that he is implementing this system in a *youth* ministry cafe. If he is only using this for content blocking purposes (which is understandable in a youth cafe), I recommend just blocking the offending sites with either your router or iptables.

---

### Post by flipper T on 2011-03-19
there is no mention of blocking in the post, only monitoring and reporting.

i have no problem with blocking (its his dime)...anything else stinks.

---

### Post by decktrio on 2011-03-19
> **abyrne said:**
> He did note that he is implementing this system in a *youth* ministry cafe. If he is only using this for content blocking purposes (which is understandable in a youth cafe), I recommend just blocking the offending sites with either your router or iptables.

Going along these lines, would it be good idea to try out a DNS service, like OpenDNS Deluxe (for small businesses). [https://www.opendns.com/start/](https://www.opendns.com/start/)
[CENTER][LEFT]Then you could blacklist/whitelist domains, and the logs would be archived for up to a year. But then again, I'm sure you've thought of that... I'll keep thinking.
[/LEFT]
[/CENTER]

---

### Post by abyrne on 2011-03-19
Alright. If the OP just wants to log the accessed websites, then I believe that the web browser Epiphany had some options to lock the browser in full screen (or it had some compatibility with a parental controls software; it's been a while since I've used it), preventing users from erasing the history.

---

### Post by flipper T on 2011-03-19
wow

just me with moral concerns about this then ?

---

### Post by abyrne on 2011-03-19
> **flipper T said:**
> wow

just me with moral concerns about this then ?

I understand your concern. However, these are the OP's machines, and he is allowed to configure them to his liking.
 
I don't want to start a flame war. Let's focus on the technical aspect of this problem, not the religious or moral aspects.

---

### Post by flipper T on 2011-03-19
> However, these are the OP's machines, and he is allowed to configure them to his liking

yes they are.

for whatever reason it is done, i would still urge no member of this forum to offer assistance to anyone attempting to spy on others.

ps no idea what a flame war is, hope this isn't one.

---

### Post by howefield on 2011-03-20
Please keep to the topic at hand. :)

No-one is obliged to offer assistance, but neither should anyone who does be discouraged from doing so.

---

### Post by hunterkasy on 2011-03-20
Ubuntu Forums Code of Conduct

[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Section I - General Policy:

# Trolling, Attacks and Flaming: These are always forbidden.

    * Trolling is posting in a way that provokes emotional responses.
    * Attacks and derogatory terms of any kind are not welcome. This includes references to other operating systems and the companies that produce them.
    * Flames are messages that personally attack or call any people names or otherwise harass. These, along with any generally condescending posts will be edited or removed at the moderators discretion.
    * If a thread is flame-bait (appears to be intended to start an argument or is likely to cause an argument rather than enhance discussion, as in trolling), it will be locked or removed without notice. Individual flame-bait comments in a post may be deleted or edited at the moderators' discretion.
    * If the thread turns into an argument, it can be closed to further comment or removed without notice. Sometimes a moderator may split the thread or delete certain portions in order to keep the discussion going, but that is not always possible since we are a staff of volunteers with limited time and numbers.

# Politics and Religion: These two topics have caused serious problems in the past and are now forbidden topics in the forums. Please find another venue to exercise your freedom of speech on these topics.
# Thread Drifting/Steering: Please keep discussions on topic. Topics that do not belong in the technical or 3rd party project sections belong in the Cafe, if they fit the posted rules in the Cafe.

---

### Post by flipper T on 2011-03-20
ok guys, if the posting of the terms is aimed at me, i dont believe that i have broken or intended to break any of them.

spying is wrong.

dont encourage it.

---

### Post by hunterkasy on 2011-03-20
> **flipper T said:**
> ok guys, if the posting of the terms is aimed at me, i dont believe that i have broken or intended to break any of them.

spying is wrong.

dont encourage it.

I didn't post directly at you, I posted to everyone.

spying is legal, as long as the user knows about, that's all that matters


now to the origanal problem, I don't know how to help you like the way you want to, but in my case I have a firewall server running smoothwall 3 and I have dansgaurdian installed to filter the web for inappropriate sites

---

### Post by abyrne on 2011-03-20
I don't know if the self-creating users plan that you laid out is possible. A low-tech solution would be just a little sign-in pad of paper for users to sign during their time online. So you can match an entry in the browser history to a person, if needed.

---

### Post by SuperTeece on 2011-03-20
So wow, what a range of responses :)

I didn't specify any content filtering requirement because the plan is to use opendns. The monitoring aspect is simply for accountability. When you average 55-60 students and only 5 adults it is challenging to be everywhere at once.

We don't *want* to spy on anyone, but we do need to ensure that the service provided isn't being abused. No key loggers or anything like that.

I'll check out the mentioned programs and see how they fit.

Thanks,
TC

---

### Post by decktrio on 2011-03-20
I know it's not exactly what you need, but have you tried out the OpenKiosk firefox add-on?

---

### Post by SuperTeece on 2011-03-20
> **decktrio said:**
> I know it's not exactly what you need, but have you tried out the OpenKiosk firefox add-on?

I'll check it, I've been fiddling with openkiosk for KDE with no compiling luck.

---

### Post by SuperTeece on 2011-03-20
> **decktrio said:**
> I know it's not exactly what you need, but have you tried out the OpenKiosk firefox add-on?

I looked at the openkiosk add-on and it's last update was in 2007. Though this did lead me to r-kiosk which I think is going to get me going in the right direction.

Thanks,

TC

---

### Post by Script Warlock on 2011-03-20
> **SuperTeece said:**
> All,

I'm looking for a way to fullfill the following requirements for a group of public computers that will be used by students in a youth ministy chapel cafe:

1. User is limited to the browser only
2. User is required to establish a user account for tracking usage

So I want the monitor to display a login gui that gives the student the option to make an account. Then I want the ability to run reports showing URLs visited and which users visited them.

This can be local to each machine or server based.  The plan is to start with three computers but I'm sure I can get a fourth for a server if needed. I've been playing around with OpenKiosk today to see if it would meet my needs but I can't make it through the install. All documentation seems to be for earlier versions.

Thanks,
TC

there are several approaches

> User is limited to the browser only

you can install pessulus and hide every menu content in your ubuntu. wew, they are also not permitted to use office suite?.

> User is required to establish a user account for tracking usage
you can install mkahawa cyber manager and create a member account and add some credits. although reporting is not that yet detailed, hope we can add this feature on the next release, but yes it will log there usage time and date. and its free to use.

and for webfilter you may use opendns or this one
[http://www.liberiangeek.net/2010/03/how-to-filter-web-contents-with-danguardian-in-ubuntu/](http://www.liberiangeek.net/2010/03/how-to-filter-web-contents-with-danguardian-in-ubuntu/)

---

