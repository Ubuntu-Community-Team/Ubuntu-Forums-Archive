---
title: "Startup error- can't log in"
date: 2006-05-01
forum: General Help
---

### Post by DDaland on 2006-05-01
Due to the fact that my main HD bit the dust over the weekend, have to use my backup solutions- I keep a couple of spare 20 gigs handy- 1 with Ubuntu (5.10) for AMD64, 1 with Ubuntu (5.10) 32 bit.  Of the 2- prefer the 32 bit version- easier to get all the multimedia, Java, etc,etc to work
 After running updates today, (including a new kernal update) upon booting up, and logging on- get the message "Your $Home/.dmrc file has incorrect permissions and is being ignored. This prevents the default session and language from being saved. File sould be owned by user and have 644 permissions"
  After brief moment with just a brown screen, it returns to the log in page. I've tried the assorted options in the sessions area- no luck

 Any suggestions, or do I just say to heck with it, and re-install?

---

### Post by Ramses de Norre on 2006-05-01
Press alt-ctrl-F1, log in and execute this: ```
sudo chown -R username ~ && chmod 644 ~/.dmrc
```

---

### Post by DDaland on 2006-05-01
Worked Like a charm!, A thousand thanks!

---

