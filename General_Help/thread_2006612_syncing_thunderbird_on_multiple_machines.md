---
title: "syncing thunderbird on multiple machines"
date: 2012-06-19
forum: General Help
---

### Post by hwttdz on 2012-06-19
I use thunderbird as my email client and there are many things that I like about it.  My issue at the moment is that it is somewhat difficult to keep settings/messages in sync between different machines.  I use imap mail, so they will pull in all the same messages eventually, but I find that I usually have to restart thunderbird when I get to work to get it to pull all the overnight messages/read statuses correctly.  So I was wondering if people had an idea to keep the profiles synced. 

What I've tried already:
1) no solution, just let it redownload the messages at every location, and setup all the preferences myself.  This requires restarting thunderbird fairly often and making multiple changes to the preferences every time I want to change something.
2) put my thunderbird profile directory on dropbox.  This was an interesting solution, but I found that if the same file was in use in two places dropbox would fork it, then to resync I had to delete the "conflicted copy" files and close and reopen thunderbird.  
3) put my thunderbird profile directory on an sshfs drive.  I think this would actually work well, and I guess my issue is that my connections aren't fast/stable enough to make it work consistently.  The downside here is that if your connection is out you don't have any of your mail, because of the way dropbox works, you'd have mail up until when the connection cut (which is sort of all you can hope for anyways). 
4) what I'm thinking of trying now is rsyncing the directory a few times a day? 

Any other thoughts? has anyone else tried this?

---

