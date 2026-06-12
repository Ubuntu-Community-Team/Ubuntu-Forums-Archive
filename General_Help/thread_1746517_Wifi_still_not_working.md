---
title: "Wifi still not working"
date: 2011-05-01
forum: General Help
---

### Post by Total Noob on 2011-05-01
I have lost regular wifi access with the upgrade to 11.4 on my Celeron M laptop. It may be Network Manager, I don't know. I need some assistance or I am screwed.

This problem has persisted off and on and in various random ways all day, indicating to me that the programming of 11.4 is extremely buggy if not unstable.

Previously, the receiver (or network manager) icon showed after a left click a pulldown menu of available networks, and on right click, a pulldown menu of available network by network settings with the opportunity to edit the connection.

But with the upgrade, the same menu appears on left click or right click, and though both sides included checkoffs to enable wireless connection and wired connection, and though I have both enabled, they both show a greyed out "wireless disconnected" tab, so you can't do anything with it.

There's also no place else to go to find available networks and no place to lock into one. There also does not seem to be a place to find wired networks either.

I would have been pleased to show a picture of this, but for unknown reasons, PrintScreen is also disabled whenever a pulldown menu appears, which is absurd.

Since I was offered a chance to edit "hidden networks" and since mine was registered and worked well with 10.10, I was able to access the previously saved settings with a pulldown menu from there, and I checked the settings of wifi network in it, and put in the correct password and and security type, set it to come on automatically.

But 3x restarts did not yield any changes, only a continuous search icon and futility. Moreover, subsequent efforts to get it going through "hidden networks" revealed that the edited settings did not take. The security type kept going back to the wrong original setting despite repeated OK's and saves.

Apparently network finding is disabled in this version or at least my copy.

It isn't the computer: I'm on line with it now on the Windows XP side.

And twice, but only twice, with no specific actions on my part, the computer did find my network. Yesterday afternoon, I rebooted after lunch to find the computer could see my network and the neighbors' networks, including some hundreds of feet away, no problem.

But it didn't last. Later in the evening, it was dead again.

Today, I attached the laptop to my network by wire hoping for an upgrade that would make it work consistently, and it wasn't a problem getting on line that way. But at that point I also got an up arrow/down arrow icon -- which has not reappeared no matter what I did -- and the computer found my wifi network and neighbors' wifi. I disconnected the wire and got on line by wifi then, and then I rebooted, and was on line just fine.

Then I turned it off, had lunch, and it was dead again.

Then, after dinner, another different result. I got as far on Network Manager as a list that included my wifi network an dmy neighbors' wifi's, but I was inexplicably unable to get on to any of them, including the non-secured ones. 

But that only lasted a few minutes. After that, no networks showed up.

Even more bizarrely, I tried to launch network manager, which was listed as installed. But when I did, it didn't launch, I was redirected to Ubuntu software, which also indicated it was installed. What it would not do for me was turn on. 
There does not seem to be an icon or other easy way to launch the network manager to make sure that the wifi receiver is launching.

So the result is that whatever allows me to see networks and get on line only works occasionally and inconsistently. If wifi doesn't work for my laptop, it is a paperweight unless I use the Windows side of it.

Does anybody know for certain what is wrong and how I can fix it?

Thanks.

---

### Post by perspectoff on 2011-05-01
I don't.

I have never been able to get network manager to work and thought it worked with natty, but then got the same old problems.

I always install Wicd and then uninstall Network Manager (and all related modules). I have never had a problem with Wicd. YMMV.

---

### Post by Total Noob on 2011-05-02
> **perspectoff said:**
> I don't.

I have never been able to get network manager to work and thought it worked with natty, but then got the same old problems.

I always install Wicd and then uninstall Network Manager (and all related modules). I have never had a problem with Wicd. YMMV.

Maybe I am the first to have Wicd fail. After removing network manager, inexplicably, Wicd did not permit entry to my network, saying there was a password problem; this has never happened before and I know my own password.

Then again, it could not enter a neighboring unsecured network either, failing to find an IP address even though it saw the network and it had a strong signal.

I also installed something called network radar, and that didn't work either.

I also tried something called Network Selector, and that wouldn't even launch, so less than useless.

Any other thoughts before I revert to 10.10? It is very frustrating to have hardware regression on a key component like Internet connection. The remaining part of the upgrade isn't too satisfying either, and in some ways makes Ubuntu less friendly especially to a Noob, because finding apps and launching apps are more of a chore that that used to be, to be compounded by hardware regression certainly makes it much more difficult to choose Ubuntu as a useful alternate to commercial products.

---

### Post by xtremesupremacy3 on 2011-05-02
Well I have to admit, what the hell did they do to anything internet related.

I used to have to put OpenDNS on my laptop to get decent speed.

But even with that on Natty the speed 1) is never reaching its potential, and 2) seems to be inconsistent...first fast enough, then almost non existent.

I know that isn't really your problem, just thought I'd join your rally lol

---

### Post by garvinrick4 on 2011-05-02
```
sudo lshw -C network
```
will show your network cards and drivers: Lets see what they are:

---

### Post by garvinrick4 on 2011-05-02
Someone keep an eye on this thread if OP gives us his cards and drivers going out for a while
and will not be able to answer in a acceptable amount of time. Thanks.

---

### Post by Total Noob on 2011-05-04
> **garvinrick4 said:**
> Someone keep an eye on this thread if OP gives us his cards and drivers going out for a while
and will not be able to answer in a acceptable amount of time. Thanks.

Thanks but not necessary. I have gone back to 10.10.

Additional tinkering continued to produce results that were intermittant at best. Sometimes the computer would find the networks, sometimes not, no rhyme or reason to when and when not.

I have long suspected that Linux and Celeron M don't mix too well, especially since other Linux flavors would not take at all in that computer. 

I also have my suspicions about the capabilities of Ubunutu's wifi drivers; at times, when I was using a dongle with a desktop, reception would be poor on the Linux side even when very strong on the Windows side without moving the dongle an inch.

As a Noob end user, I'm trying to avoid hassle, so the line seems to end for me at 10.10. Please let me know if 11.10 has a consistent network managing system that faithfully provides a connection.

---

