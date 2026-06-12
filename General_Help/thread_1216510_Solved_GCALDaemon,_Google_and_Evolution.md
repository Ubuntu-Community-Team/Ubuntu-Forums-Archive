---
title: "Solved: GCALDaemon, Google and Evolution"
date: 2009-07-18
forum: General Help
---

### Post by thelaw on 2009-07-18
To start off, I've searched and searched and tried and tried and have found a solution to a problem (actually, two problems).  This post serves to assist anyone else that encounters what I encountered.

Here's my scenario:
I am using Linux (Kubuntu) and my client is Novell's Evolution.  My Calendars are setup in Evolution and I am using GCALDaemon to sync the Calendars.

My first problem was with GCALDaemon spewing out bunches of errors and config-editor.sh failed.  After googling around for those errors, I had a couple of people say to run the following:

java -version.

This spewed out version 1.5, which should've been good.  However, when using Firefox at Sun's site, my version info was 1.6.11.  Hmmmm..about:plugins 1.6.11.

So, first, I grabbed 1.6.14 for Firefox - why not, eh.

Then I ran the following:

sudo apt-get install sun-java6-jre 
sudo apt-get sun-java6-plugin

java -version from the cmd prompt, spit out 1.6.014.

I have no idea why I have two separate Java installs - perhaps someone can help me on this one.  Anyhoo, GCALDaemon now works.

Next, I had a problem with the correct Google Calendar Share Permissions

Let's say I have 4 Calendars - Cal1, Cal2, Cal3 and Cal4.
Let's say I have a User - User1 - and I have Shared Cal1, 2, 3 and 4 to that User from my Google Calendar.
I would like User1 to see Full Details for Cal1 and only Free/Busy for Cal2, 3 and 4.

When setting Evolution Appointment Classification to "Public" (and re-syncing) with the above permissions, User1 can see All Details for all Calendars
When setting Evolution Appointment Classification to "Private" (and re-syncing) with the above permissions, User1 can only see Free/Buys for all Calendars
When setting Evolution Appointment Classification to "Confidential" (and re-syncing) with the above permsissions, User1 can see Cal1 (Free/Busy) and Cal2, 3 and 4 Full Details as required.

I hope this helps someone else!

---

