---
title: "This is how to transfer Evolution to Sylpheed"
date: 2010-06-23
forum: General Help
---

### Post by CurtM on 2010-06-23
I was using Evolution 2.28.3, and I am now using Sylpheed 3.0.2.  This is how I copied my email (inbox and sent messages) from Evolution to Sylpheed:

1. In Evolution, in the left pane, click on the Inbox folder (right below “On this computer”)
    2. In the command bar, click “Folder” “Select All Messages”
    3. In the command bar, click “File” “Save Message”
    4. Type the folder name (“inbox”), browse for the proper place where you want to save it, and hit the “Save” button
    5. Repeat steps 1-4 for the Sent folder
    6. In Sylpheed, in the left pane, select the folder where you want the messages to go (Inbox)
    7. In the command bar, click “File” “Import mail data”
    8. For source, click “Select” and find the inbox file you created with Evolution
    9. For Destination folder, click “Select” and select the folder where you want the emails to go
    10. Click Ok, Ok, then repeat steps 6-10 for the Sent folder.

I am a bit disappointed that Evolution did not present an easy way to export messages.  Maybe there is an "official" way to do it, but I didn't find it.  And since others will probably be in the same boat as me, I thought I'd present my procedure.

The primary reason I switched from Evolution to Sylpheed is because I switched from Ubuntu to Lubuntu.  Both programs are available to both operating systems, but Ubuntu comes with Evolution as standard, and Lubuntu uses Sylpheed by default.  Some research tells me that Sylpheed runs faster, but I didn't notice it -- they are both plenty fast on my fast computer.  On a slower computer it might make a difference.

I may switch back to Evolution someday, since I like the way I used to synchronize Microsoft Outlook with my Windows Mobile phone PDA.  That was back in the "old days" when I used Windows.  Now that I am a Linux guy, I still need to figure out how to set up Evolution to synchronize my emails, contacts, calendar, tasks, spreadsheets, word documents, notes, and favorite downloaded websites for offline browsing.  That sounds like a lot of work to me, which is why I haven't done it yet.

For now, I am happy to be running Lubuntu with Sylpheed.  A big thank-you to everyone who has contributed to making Ubuntu and its variants, and all open source software.

---

### Post by Lucky. on 2010-06-23
A great writeup.  Thanks for the info!

---

### Post by dcstar on 2010-06-24
> **CurtM said:**
> 
........
I am a bit disappointed that Evolution did not present an easy way to export messages.


Evolution uses standard mbox format for storing e-mails, you should have been able to simply point to the relevant files in the .evolution tree to import them.

---

