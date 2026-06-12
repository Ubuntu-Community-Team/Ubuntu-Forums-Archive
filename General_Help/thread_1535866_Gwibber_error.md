---
title: "Gwibber error"
date: 2010-07-21
forum: General Help
---

### Post by borth92 on 2010-07-21
Trying to set up Gwibber to see status updates from my desktop. When I try to authorize gwibber for facebook, it goes to the login screen like normal. But when I hit login, it says "gwibber encountered an error, please try again later." I tried rebooting and reinstalling gwibber and cannot seem to find a cause for the error.

---

### Post by deathadder on 2010-07-21
Can you run gwibber from a terminal and post any errors?

---

### Post by Amoura_usa on 2010-07-21
I was having that, the fix for me was simply waiting till late at night when facebook isn't so busy to add my account.

---

### Post by borth92 on 2010-07-21
> **deathadder said:**
> Can you run gwibber from a terminal and post any errors?

Running the program is not where the error comes. It's when I authenticate facebook. Maybe When it's less busy it will work...

---

### Post by deathadder on 2010-07-21
I would imagine that gwibber would post any runtime errors to the terminal, or debug output (like timeout messages)...

---

### Post by borth92 on 2010-07-21
> **deathadder said:**
> I would imagine that gwibber would post any runtime errors to the terminal, or debug output (like timeout messages)...

me@mylaptop:~$ gwibber

** (gwibber:2338): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:2338): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:2338): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Updating...
Updating...

** (gwibber-accounts:2374): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber-accounts:2374): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber-accounts:2374): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Updating...
Updating...


Thats what the terminal said the whole way through the process

---

### Post by pvossen on 2010-07-27
Basically same issue. I can use Twitter and other social
nets in Gwibber. Facebook I authorize and authorize, and
it never is considered and added item or installs.

Bummer

Patrick

---

### Post by Sarii on 2010-07-29
As far as I know, the "gwibber encountered an error, please try again later" error message is a current issue with how Facebook and Gwibber are communicating. My current understanding (I know there are bug alerts out atm)of this is that it's related to how many queries are being done against how much Facebook is throttling. 

I personally don't have the capability to verify it, so I'm just going by word and memory. Some people have issues and others don't have any (known) problems.

Here's an excerpt from gwibber.log when it gives me that error as well.
 
2010-07-29 22:50:41,523 - Gwibber Dispatcher - ERROR - Failed to raise client (DBusException(dbus.String(u'Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.'),),)

---

### Post by borth92 on 2010-07-31
Sorry for the late reply, but thank you for the information. Are you aware of another program that works with facebook?

---

### Post by owainb on 2010-08-02
The experience I've just had is sometimes it works sometimes it doesn't. I just kept trying. The time it worked I ran it from the command line but I don't think that should make a difference.

---

