---
title: "2nd user email troubles"
date: 2009-09-21
forum: General Help
---

### Post by Piznaz on 2009-09-21
Setting up my main email account with Rogers was a snap.  Secondary user's email pop account bouncing back with RETR command failure.  I've setup both accounts the same way but the secondary fails every time.  I can't figure out what the problem is.  I'm open for suggestions.

---

### Post by Piznaz on 2009-09-25
> **Piznaz said:**
> Setting up my main email account with Rogers was a snap.  Secondary user's email pop account bouncing back with RETR command failure.  I've setup both accounts the same way but the secondary fails every time.  I can't figure out what the problem is.  I'm open for suggestions.

I figured this one out on my own.  Not a Linux issue like I thought.  That's what I get for being a newbie.  Everything MUST be a Linux issue, because I don't understand it.  Lesson learned, assume something else is the issue before blaming my new OS.

The RETR error message was being generated for my wife's email account when trying to retrieve her emails.  One of the messages was corrupted and couldn't be processed by Thunderbird, stopping the download of messages and generating the error message.  
Fix: I had to log on to her email account using the Rogers web-based email client and delete the oldest email on the server.  It happened to be a photo sent on a Blackberry.  Once the corrupted file was deleted everything else downloaded into TBird just fine.

Hope this helps someone else who might experience the same thing.

Cheers

---

### Post by akakingess on 2009-09-25
Glad to hear it wasn't a Linux/Ubuntu issue, but of course, those of us here knew there was no way that the OS could be the problem :)

---

