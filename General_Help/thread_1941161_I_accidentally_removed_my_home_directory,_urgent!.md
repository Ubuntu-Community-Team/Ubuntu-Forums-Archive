---
title: "I accidentally removed my home directory, urgent!"
date: 2012-03-15
forum: General Help
---

### Post by NaturistGirl on 2012-03-15
I had two accounts on this computer. I created a new one and somehow merged to home folder in with my new one. I also had the login names the same, wasn't sure what I was doing. I can log on, but the desktop is empty and nothing will load. I am able to access the terminal and deleted the 2nd account, now still have my old account with the same name. Which is Lexi. There is only one folder in the home folder named Lexi, but there is nothing in it.

I don't have a CD to reinstall it.

---

### Post by decrepit on 2012-03-15
have you looked in trash? You may just be lucky.

---

### Post by dragonfly41 on 2012-03-15
I'm not sure if [COLOR=DarkSlateBlue]**extundelete**[/COLOR] might help you ..

[http://samiux.blogspot.com/2011/04/howto-undelete-files-and-directories-on.html](http://samiux.blogspot.com/2011/04/howto-undelete-files-and-directories-on.html)

perhaps others will advise on this.

---

### Post by winh8r on 2012-03-15
> **NaturistGirl said:**
> I had two accounts on this computer. I created a new one and somehow merged to home folder in with my new one. I also had the login names the same, wasn't sure what I was doing. I can log on, but the desktop is empty and nothing will load. I am able to access the terminal and deleted the 2nd account, now still have my old account with the same name. Which is Lexi. There is only one folder in the home folder named Lexi, but there is nothing in it.

I don't have a CD to reinstall it.

You posted a couple of days ago about a hard drive issue, and I recall the advice given was to back up all your data to an external source. If you have done this then you can just transfer your backed up data into the new home partition.

If on the other hand you never backed up your data as advised then you will need to download a Ubuntu live cd and burn it to a CD and use that to run testdisk/photorec on the partition to try and recover your data to an external medium.

For the time being it would be advisable to stop using that hard drive as using it will cause data to be written to it and could lessen the chances of any successful recovery.


If you are unsure about anything, do some research and ask some questions BEFORE you do anything. it is much easier to help people to make choices than to recover from disasters.

---

### Post by NaturistGirl on 2012-03-15
> **winh8r said:**
> You posted a couple of days ago about a hard drive issue, and I recall the advice given was to back up all your data to an external source. If you have done this then you can just transfer your backed up data into the new home partition.

If on the other hand you never backed up your data as advised then you will need to download a Ubuntu live cd and burn it to a CD and use that to run testdisk/photorec on the partition to try and recover your data to an external medium.

For the time being it would be advisable to stop using that hard drive as using it will cause data to be written to it and could lessen the chances of any successful recovery.


If you are unsure about anything, do some research and ask some questions BEFORE you do anything. it is much easier to help people to make choices than to recover from disasters.

I did back up my data, this is on another hard drive. When I got it a user account was already set up for me, but I wanted to change the username and password, so I created a new account, and wanted to remove the old one, but it said that was the only administrative account, even though I put my new one as administrator. 

So, I tried to merge the two, by making the first account, directory it the one I created, which was /home/lexi/ It asked me if I wanted to move the files, and I said sure, becuase I had already got some things set up on the first account. But then it deleted both directories. So I just have /home/lexi with nothing in it. When I log in, the password from the first account works. So Basically I didn't accomplish aything except delete my home directory. When I log in, it said there was a problem becuase it had two identical user accounts (Even though one is deleted now). I just get a blank desktop, only thing that will work is the terminal if I press the ctrl+alt+t.

---

### Post by winh8r on 2012-03-15
try this:

press control + ALT + F1

you will see a command prompt on a black screen.

enter lex (not lexi)

and the password you created for the new account.

and let me know what the result is please.

You will need to press control + ALT + F7 to get back to a desktop after doing this.

---

### Post by NaturistGirl on 2012-03-15
A new system was installed on my hard drive, so I'm unable to try ty it now, but thanks.

Next time I will search before doing anything I'm not sure of.

---

### Post by winh8r on 2012-03-15
Don't be afraid to ask about anything you are unsure of. There will always be someone able to help you in some way.

Remember the rule though, always keep backups of your data!! 


Good Luck.

---

