---
title: "sharing information between users on the same system"
date: 2011-11-03
forum: General Help
---

### Post by enimeizoo on 2011-11-03
Hello, 

My goal is to share a file with another user on the same system. 
I could give him read access, but I can't create groups, and there is not group with that user and me only. 

We can communicate via the system with write : is there a way to log what I receive with write? Before going into syslog, I'd like to know if it actually can do the job (it confuses me, I don't know anything about the syntax, so I wouldn't know what selector to use for these messages, I don't even have a syslog.conf file at all, so I don't know if it is actually there...). 

Besides, I don't have root access, so I'd need something doable as a normal user. (syslog.conf seems to be on /etc normally, so I'm not even sure I could use it...)

Well, what we do for the time being is emailing, but I hope there is a better solution.

Thanks in advance.

---

### Post by alco75 on 2011-11-03
What about Google Docs or Dropbox (Shared Folders)?

---

### Post by gsmanners on 2011-11-03
> **enimeizoo said:**
> My goal is to share a file with another user on the same system. 
I could give him read access, but I can't create groups, and there is not group with that user and me only.

You can't create a folder in /tmp?

If you're worried about other users on the machine, you can encrypt the file (there are a lot of archivers that can do that) and you simply share the password with the other user via some trusted means.

---

### Post by enimeizoo on 2011-11-03
Thanks for the answers. I'll look more into the encryption idea and the dropbox thing. 

I knew about dropbox, but if you want to sync a folder, you have to install something, right? If you don't, I guess you have to use a web browser or something to access it... Thing I would like it to be synchronized with a command, not sure dropbox can achieve that.

Also, I wondered if it was possible to install a svn or git server locally, if it was easy without root privileges, and if it took a lot of disk space (crappy 500MB limit... ). But even if I install it on my userspace (say from source), will another user be able to commit to or update from the server (which will be running under my user account)?

---

### Post by alco75 on 2011-11-03
> **enimeizoo said:**
> I knew about dropbox, but if you want to sync a folder, you have to install something, right? If you don't, I guess you have to use a web browser or something to access it... 

You'd need to install the Dropbox client on both machines, yes.

But once the Shared Folder is set up, you don't even need a command to synchronize. As soon as you write to the Shared Folder, the other party will get the updated file.

---

