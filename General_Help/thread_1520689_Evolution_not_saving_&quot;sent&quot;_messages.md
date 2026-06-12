---
title: "Evolution not saving &quot;sent&quot; messages"
date: 2010-06-29
forum: General Help
---

### Post by DerRosaElefant on 2010-06-29
Hello again everyone!

I've been using Ubuntu off and on for a long time, and now that 10.04 is out, I just had to come back to it, and leave Windows completely behind. They ***finally*** did Ubuntu right. However, I am having one problem with the Evolution email program, that I never had in the past. 

I send some very important messages several times a day, that I really absolutely MUST keep a copy of. I looked in my "sent" folder earlier, needing to find one. I noticed that it has not saved a single message I have sent for days. Just to see, I sent a test message, and as soon as it sent, the outbox was emptied and the message was not in the "sent" folder. I have looked around here and so far, have not come up with anything like what I am having happen. I've checked all the settings, I can't find anything that seems it would affect saving sent messages.

Anyone have any ideas of anything I can check? I even got desperate and did a fresh install of Ubuntu, same problem :confused:

---

### Post by DerRosaElefant on 2010-06-30
Just giving it a bump :)

---

### Post by dcstar on 2010-07-01
> **DerRosaElefant said:**
> 
.......
I've checked all the settings, I can't find anything that seems it would affect saving sent messages.
......

Apart from the specific Sent items folder setting in every Account?

---

### Post by DerRosaElefant on 2010-07-01
Yes, I have checked every setting I can find... There's only one account. But by this point I might be looking so hard I am missing something. I saw nothing specific in preferences or by right clicking the sent folder that would seem to set anything related to that :confused:

Really a confusing issue. That or I've just completely missed something *most likely*, or something is no longer enabled by default that was on older versions of Evolution :/

---

### Post by plucky on 2010-07-01
> **DerRosaElefant said:**
> Yes, I have checked every setting I can find... There's only one account. But by this point I might be looking so hard I am missing something. I saw nothing specific in preferences or by right clicking the sent folder that would seem to set anything related to that :confused:

Really a confusing issue. That or I've just completely missed something *most likely*, or something is no longer enabled by default that was on older versions of Evolution :/

Open in Evolution **Edit > Preferences > Select Account > Edit > Defaults** and make sure the "Sent Messages Folder" is actually set to "Sent" and not something else.

Good Luck

---

### Post by DerRosaElefant on 2010-07-01
Yep, I've checked that, and it's set correctly :) 

But thanks anyway! :)

---

### Post by sgosnell on 2010-07-01
It's possible to have more than one Sent folder.  Are you sure they're going to the one you're checking?

---

### Post by DerRosaElefant on 2010-07-01
I've only got one account/sent folder, and I checked to see if it had been sending them to any of the other folders (drafts, etc.) and it hasn't... Weird!!

---

### Post by jackeryf on 2010-07-02
I have the same problem.
Sent emails are not saving to any folder that I can find.
And the Sent email folder in the Account Editor->Defaults tab is set to "Sent"

I have also noticed a problem with expanding folders in the tree view, namely they won't expand.  They seem to expand some of the time but it is very random.

My version is  2.28.3
I have two accounts setup, both IMAP
I'm on Lucid 10.04 and I've done all the latest updates.

---

### Post by MechaMechanism on 2010-07-02
Create a folder called archive to do a test.  Now when you get an email, right click the email in the subject line in the top pane and select move to folder.  Move to archive folder and see if your email shows up there.  I think Evolution has a bug concerning this matter.  There is also the possibility that the IMAP provider has configured their settings a certain way.

---

### Post by philinux on 2010-07-02
> **DerRosaElefant said:**
> I've only got one account/sent folder, and I checked to see if it had been sending them to any of the other folders (drafts, etc.) and it hasn't... Weird!!

Does your outbox get flushed or does it still show messages in there?

[https://bugs.launchpad.net/evolution-mapi/+bug/361991](https://bugs.launchpad.net/evolution-mapi/+bug/361991)

---

### Post by sgosnell on 2010-07-02
What server are you using?  The imap server might be doing something weird, and the settings for the imap server can affect what happens to the sent messages.  If the server moves or deletes them, then they will naturally be deleted from the sent folder on the local machine.

---

### Post by sgosnell on 2010-07-02
Dup, somehow.

---

### Post by DerRosaElefant on 2010-07-02
I use pop, so I'm not sure what the difference/similarity might be with imap. My outbox does get flushed. At the bottom, it shows the message being sent, the out box is flushed and it shows "storing message" (or something along those lines, it flashes very quickly) 

I can check on gmail's site physically, and if i set gmail to download all pop messages even if they've already been downloaded, it fetches all the sent messages. Trouble with that is, as it says, it downloads every other message, too #-o

Since it's flushing my outbox however, I guess it's something different than that bug :/

---

### Post by sgosnell on 2010-07-02
OK, now we're getting somewhere.  You're using gmail.  So do I.  There are **two** Sent folders in Evolution for that.  One is the local Sent folder, near the top, and the GMail Sent folder.  My GMail sent folder is empty, but the local Sent folder has everything I've sent from Evolution.  I don't know exactly how you've set up your account in Evolution, but look one more time, please, and make sure there isn't another local Sent folder somewhere, with your sent items.

On closer inspection, I actually have 3 Sent folders.  One is under "On this computer", and it only has items I've sent through Evolution.  The second is under "User@gmail.com", where User is actually my gmail username.  That one is empty.  Then, under GMail under that heading, when expanded, there is another Sent folder, which does hold what is in my Sent folder on GMail.  It can be a little confusing, but you have to look in several places to find everything.

---

### Post by DerRosaElefant on 2010-07-02
Thanks for the reply :) I checked, and there is only one sent folder :/

But thanks for all the suggestions, and trying to help! I really appreciate it :)

---

### Post by forestcomber on 2010-11-09
This is probably not your case but ...

I had the same problem; for weeks, after sending messages, no sent mail in the Sent folder.

Then I realised that some time earlier I had searched the Sent folder for a word that had 0 hits, this results in an empty looking Sent folder.

If the search bar is not cleared out then the search and results remain.  Every time I went to the Sent folder it was empty because the search term was still there and the Sent folder was still displaying the 0 search results.

I cleared the search bar and my sent items returned.

---

