---
title: "Everything is missing in Evolution"
date: 2011-11-05
forum: General Help
---

### Post by jakeypie on 2011-11-05
Hi, I turned on my netbook this morning and everything was fine, Left it for an hour or so came back to check my emails and all folders and mail in Evolution have disappeared. Inbox has gone, sent items gone the only thing that is there is a folder called unmatched. I have checked preferences and my account are still there. I am using 11.04 and the evolution mail that came with it. 
I am a very very very beginner at ubuntu (and everything to do with computers)
I have tried to attach a screenshot of evolution  (not sure if I was successful)
Any help would be great.

---

### Post by BillyBoa on 2011-11-05
Try to reinstall evolution. Just go to the Ubuntu software center and unistall-reinstall the program.
Do you have an IMAP account? Maybe from there starts the problem.

---

### Post by jakeypie on 2011-11-05
Thanks I will try that. I have POP account.

---

### Post by jakeypie on 2011-11-05
Uninstalled it and reinstalled but that didnt work.

---

### Post by raja.genupula on 2011-11-05
Hi man in your home folder look for this in hidden files 

~/.evolution/mail/local/ 

it will have all your mails take backup all of your mails and then while doing uninstallation do with purging

```
sudo apt-get remove --purge <app_name>
```
sudo apt-get clean

and then re install.

all the best.

---

### Post by BillyBoa on 2011-11-05
Then from Home directory copy the .evolution folder, just to make a backup. If you don't find any better solution and the messages are important, you could reinstall ubuntu and restore the folder to it's place, to recover your mail.

---

### Post by jakeypie on 2011-11-05
Thanks guys, i have found the back up file but cant get it working, the emails werent important or that many of them.  I just find it weird that everything disappeared - is there a different email program that is better than evolution.

---

### Post by BillyBoa on 2011-11-05
For professional email use Thunderbird from Mozilla. It's the better.

---

### Post by raja.genupula on 2011-11-05
> **jakeypie said:**
> Thanks guys, i have found the back up file but cant get it working, the emails werent important or that many of them.  I just find it weird that everything disappeared - is there a different email program that is better than evolution.

I love Thunderbird and upto now its never gave me any problem to me.You can get that from software center.

all the best.

---

### Post by jakeypie on 2011-11-05
Thanks, am having a really bad day. Got thunderbird and got it set up with one of my email accounts but it wont set up my other one it keeps saying incoming server already exists can you have more than one email account on thunderbird?

---

### Post by jakeypie on 2011-11-05
thanks so much for your help guys, have sorted out the problem with thunderbird it was trying to set up on port 143 or 145 when it should have been 110.

---

### Post by BillyBoa on 2011-11-05
With Thunderbird you can have as many email accounts you like. But it's only integrated to ubuntu 11.10. If you are using a previous version, you are going to be disturbed by Evolution integration problems.

---

