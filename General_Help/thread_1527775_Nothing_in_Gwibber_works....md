---
title: "Nothing in Gwibber works..."
date: 2010-07-09
forum: General Help
---

### Post by bergersen on 2010-07-09
Hi!

Never really used Gwibber before and I'm rather lost here. Whatever I do I can't seem to get anything to actually work. I'm not getting any error messages, but my Gwibber window remains blank no matter how many accounts I'm adding...

**Facebook - **I click add "add", I select Facebook, I enter my details and they successfully authorize my account, but the account is never added to the list. After closing the accounts window it's completely gone.

**Twitter - **Click add just like with Facebook, enter my details and it's added to the list. When I close the accounts window it shows up to the left of my main screen like it's suppose to. I notice Gwibber is refreshing, but nothing appears! Completely blank screen, completely empty inbox. I can type an update, but when I click send it's just cleared. Nothing is updated and nothing appears on my Twitter profile.

I try entering a phony account and it's the same deal. No error messages, Gwibber is refreshing but nothing is appearing.
[B]
Flickr -[/B] All I can do here is to enter my username. I don't know what's suppose to show up in my inbox, but again, nothing. No error, no feedback, not messages... nothing!

I don't get it! I have no idea what I'm doing wrong as Gwibbler gives no feedback what so ever! :(

Anyone?

---

### Post by bergersen on 2010-07-09
When running Gwibber from the terminal I get the following output:
[COLOR=DimGray]
[COLOR=Black][I]** (gwibber:7719): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:7719): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'[/I][I]

** (gwibber:7719): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'[/I][/COLOR][/COLOR]   

Is this even relevant?

---

### Post by elliotn on 2010-07-09
I hate Gwibber, install Pidgin you will never go wrong

---

### Post by bergersen on 2010-07-09
Pidgin aye... I use that for my Windows partition. But last time I check it was only for instant messaging and not social networks like Twitter and Flickr. As far as I can see it doesn't even have Facebook chat...

---

### Post by bergersen on 2010-07-10
Problem solved :D

I had to update Gwibbler to 2.30.1. I did this by opening *System* -> *Administration* -> *Software Sources*, then go to the *Updates* tab and select *Pre-released updates (lucid-proposed)* under *Ubuntu updates*. Then I ran *sudo apt-get update* and *sudo apt-get install gwibber* in the terminal to update it to the new and unreleased version.

This new version had a lot of bug fixes and now everything seems to be working as it should ;)

[https://answers.launchpad.net/ubuntu/+source/gwibber/+question/117199](https://answers.launchpad.net/ubuntu/+source/gwibber/+question/117199)

---

### Post by krishnandu.sarkar on 2010-07-10
Ya the bundled version of Gwibber is buggy, I'd like to wait till I get it from normal updates.

---

