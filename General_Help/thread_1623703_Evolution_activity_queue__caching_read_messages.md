---
title: "Evolution activity queue / caching read messages"
date: 2010-11-16
forum: General Help
---

### Post by dewdrop_world on 2010-11-16
It seems that Evolution queues its server-access activities, such that downloading the content of a message with a large attachment will hijack the whole app until the download completes.  I also saw it when moving quickly through a number of messages in the  inbox while the message pane was open. Evolution displayed each message  in turn (several seconds for each download), instead of recognizing that  I was no longer interested in messages 1, 2, 3... 10.

A sane way to handle it would be to allow the user to switch to a different message, and push other downloads to a lower priority. Does Evolution not do this? Instead it seems to say: "Oh no, you asked for message *n*, and I'm going to show it to you whether you want it or not."

The (X) buttons in the activity bar do not do anything.

Why am I not using tbird or something else? Tbird seems to be really dumb about folder sync - you MUST download EVERYTHING, or download headers only (and previously-read messages are not cached).

Maybe I'll look at kmail but I've already wasted almost 2 hours this morning trying to figure out what these clients can and cannot do. The thought of downloading another client is raising my blood pressure.

This is what I want: load only message headers when initially synchronizing the inbox. When I  read a message, I want it to cache the message contents on disk so that  it does not have to go back to the server for a message I already read. <-- Two hours wasted trying to get this (and I still don't have it, except for Evolution whose thread handling is really poor). Sorry if I sound cranky, but seriously... it's not that hard, is it? Two hours??? (My internet connection has suddenly gone really slow, and tbird's help system is ALL online. So every query takes, like, 5 minutes. That didn't help matters any.)

PS Ubuntu maintainers: If Evolution really is as much crap as people here seem to say, please fix it or stop installing it by default :)

---

### Post by dcstar on 2010-11-17
> **dewdrop_world said:**
> 
..........
PS Ubuntu maintainers: If Evolution really is as much crap as people here seem to say, please fix it or stop installing it by default :)

This is a forum where Ubuntu users help other Ubuntu users, such comments are a total waste of time as "maintainers" do not read every single message posted in a support forum - they do not read **any** messages in a support forum because they are busy dealing with the people who bother to actually lodge useful bug reports.

---

