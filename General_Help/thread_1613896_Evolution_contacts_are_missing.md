---
title: "Evolution contacts are missing"
date: 2010-11-05
forum: General Help
---

### Post by kiwited on 2010-11-05
After a major computer malfunction, I had to replace my machine. I was able to get the contents of two partitions off, fortunately including my current active one, and used Nautilus to dump my entire user onto an external drive.

After reinstalling Ubuntu on my new machine yesterday, I copied my .evolution folder across. My emails were there, but all other data seemed to be gone, including most annoyingly all my contacts. Email addresses I can laboriously recover from the emails, but the phone numbers, street addresses etc are gone. There are a lot of folders in the .evolution/addressbook/local folder. Are they the ones?

The only thread I have seen that claimed to have a solution had a link to a foreign language page so was not much help.

I am certain there must be a way to get at this stuff, but do not have a clue how.

To the developers - how about making auto backup a feature. From what I can see, backing up is already possible with a simple command. Why not make it automatic?

Theo

---

### Post by dcstar on 2010-11-05
> **kiwited said:**
> 
........
After reinstalling Ubuntu on my new machine yesterday, I copied my .evolution folder across. My emails were there, but all other data seemed to be gone, including most annoyingly all my contacts. Email addresses I can laboriously recover from the emails, but the phone numbers, street addresses etc are gone. There are a lot of folders in the .evolution/addressbook/local folder. Are they the ones?
........

Try replacing the new addressbook.db & addressbook.db.summary files from your old system.

---

### Post by kiwited on 2010-11-05
Thanks for that.

I had installed Evolution, then copied the entire .evolution folder from my backup to replace the new .evolution folder, which obviously included the addressbook folder.

My emails were there, but I had to set up my server settings again. I also had a very old contacts list, not the contacts I had previously had.

In the addressbook/local folder are 13 folders which I assume are various contact lists and have lengthy numerical names, but the contents are unreadable. There is a 14th folder which is called "system".

I'm guessing that Evolution is finding the wrong list. I cannot see any way of finding what list to use or how to tell Evolution to use another list.

Theo

---

### Post by rabbits on 2010-11-07
I also lost my "contacts" within Evolution yesterday and then got it back by removing Empathy and restoring "evolution-backup.tar.gz".

Background: I upgraded from 10.04 to 10.10 about 3 days ago, all successful and Evolution was working.  Yesterday I tried to setup Empathy and encountered "connection problems", with Yahoo IM.

Immediately after, I found my contacts were lost within Evolution. At this point I tried to restore a recent evolution-backup.tar.gz ; and still had no contacts.  Then I ran Synaptic to remove "Empathy",  and another restore of "evolution-backup" and I could see the contacts again.

Thankfully I had a recent evolution-backup file.  I have been using Pidgin before this arose and will go back to Pidgin again.  

Hope this is relevant and helps you.

---

