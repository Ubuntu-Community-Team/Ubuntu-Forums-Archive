---
title: "How to share email between Ubuntu and Windows Vista?"
date: 2009-10-03
forum: General Help
---

### Post by rewyllys on 2009-10-03
[FONT=Arial, sans-serif][SIZE=3]I'm currently using Windows Vista 64-bit and dual-booting with Ubuntu, but I'm determinedly working toward the goal of making Ubuntu 9.04 (and its successors) my primary OS.[/SIZE][/FONT]
 

 [FONT=Arial, sans-serif][SIZE=3]A stumbling block has turned out to be my email program:  Thunderbird 2.0.0.23.  I'd like to be able to share accounts, past and future messages, folders under Inbox, address book, etc., between Vista and Ubuntu.  Searching for advice on how to do this, I've found such URLs as the following:[/SIZE][/FONT]
 

 [FONT=Arial, sans-serif][SIZE=3]"Sharing a profile between Windows and Linux[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=3]"[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=3] ([/SIZE][/FONT][[FONT=Arial, sans-serif][SIZE=3]http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux[/SIZE][/FONT]]("http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux")[FONT=Arial, sans-serif][SIZE=3])[/SIZE][/FONT]
 

 [FONT=Arial, sans-serif][SIZE=3]"How To Share Mail Between Windows and Linux[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=3]"[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=3] ([/SIZE][/FONT][[FONT=Arial, sans-serif][SIZE=3]http://web.archive.org/web/20050207141558/http://texturizer.net/thunderbird/share_mail.html[/SIZE][/FONT]]("http://web.archive.org/web/20050207141558/http://texturizer.net/thunderbird/share_mail.html")[FONT=Arial, sans-serif][SIZE=3])[/SIZE][/FONT]
 

 [FONT=Arial, sans-serif][SIZE=3]"[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=3]Dual Boot Sharing: Firefox 3 Bookmarks
Thunderbird 2 Default Directory
Sunbird Calendar 0.9 Default Directory[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=3]"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=3]([/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=3][http://www.ces.clemson.edu/linux/]("http://www.ces.clemson.edu/linux/firefox-thunderbird.shtml")[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=3][firefox-thunderbird.shtml]("http://www.ces.clemson.edu/linux/firefox-thunderbird.shtml"))[/SIZE][/FONT]
 
 

 [FONT=Arial, sans-serif][SIZE=3]The first of these links is quite general; the second dates from February of 2005, and is clearly out-of-date; the third contains a promisingly pertinent section that reads as follows:[/SIZE][/FONT]
 

 [FONT=Arial, sans-serif][SIZE=3]"Thunderbird 2[/SIZE][/FONT]
 

 [FONT=Arial, sans-serif][SIZE=3]"Your Windows XP default directory can be shared with Linux.[/SIZE][/FONT]
   [FONT=Arial, sans-serif][SIZE=3]cd ~/.thunderbird[/SIZE][/FONT]   [FONT=Arial, sans-serif][SIZE=3]mv xexz3f7v.default xexz3f7v.default_orig 
[/SIZE][/FONT]   [FONT=Arial, sans-serif][SIZE=3]ln -s /media/drive-D/profile.cu/Application Data/Thunderbird[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=3]/Profiles/gmbdpxf5.default xexz3f7v.default[/SIZE][/FONT] 


 [FONT=Arial, sans-serif][SIZE=3]"Comments: The directory xexz3f7v.default is created when Thunderbird 2 is installed under Linux, while the directory gmbdpxf5.default is created when Thunderbird 2 is installed under Windows XP.  These directory names are randomly generated."[/SIZE][/FONT]
 


 [FONT=Arial, sans-serif][SIZE=3]Unfortunately, after I tried applying the third link's suggestion (and using the relevant Windows path for my computer), I encountered a serious difficulty.  Attempts to open Thunderbird yield an error message to the effect that a copy of Thunderbird is already running and I need either to close it or to restart my computer.  Naturally, I tried the latter option, but it did not work.[/SIZE][/FONT]
 


 [FONT=Arial, sans-serif][SIZE=3]I tried the only other possibility that has occurred to me.  I set up one of my email accounts in Thunderbird (for Linux), using as the "Local directory" for its 'Local Folders" file the location at which Ubuntu 9.04 sees the "Local Folders" directory of my Vista installation ("/media/HP" is how Ubuntu sees my Windows C: drive):[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=3]/media/HP/Users/Ron/AppData/Roaming/Thunderbird[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=3]/Profiles[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=3]/7othhbcl.default/Mail/Local Folders[/SIZE][/FONT]
 

 [FONT=Arial, sans-serif][SIZE=3]Doing this failed to yield anything useful.[/SIZE][/FONT]
 

 [FONT=Arial, sans-serif][SIZE=3]At this point, I've run out of ideas.  I hope that somebody has succeeded in coping with a similar situation and has found a solution that he or she will share with me.[/SIZE][/FONT]
 

 [FONT=Arial, sans-serif][SIZE=3]Thanks in advance for any help.[/SIZE][/FONT]
 

 [FONT=Arial, sans-serif][SIZE=3]Note:  I've made this plea deliberately verbose in the hope that others may find that it helps them avoid ideas that don't work (at least, not for me). [/SIZE][/FONT]

---

### Post by falconindy on 2009-10-03
Not sure what kind of email volume you get or how often you're switching between OS's, but IMAP might be a feasible solution if your email server supports it. I'd be weary of sharing a profile directory between 2 OS's like this, especially when one is Windoze.

---

### Post by techstop on 2009-10-03
> **falconindy said:**
> Not sure what kind of email volume you get or how often you're switching between OS's, but IMAP might be a feasible solution if your email server supports it. I'd be weary of sharing a profile directory between 2 OS's like this, especially when one is Windoze.

Definitely go IMAP all the way! Then you don't need to "sync" any email, it's all taken care of by the email server.

You will need some other solution for your address book though, although there are plenty of approaches I can see by googling.

---

### Post by rewyllys on 2009-10-04
Thanks, Techstop and Falconindy.  Unfortunately, not all of the servers from which I get email have IMAP capability, so I really need to have a way of dealing with messages on my computer.

---

### Post by rewyllys on 2009-10-08
[FONT=Arial]This is a follow-up report.  [/FONT]
  
  [FONT=Arial]After considerably more searching on the Web for ways of sharing Thunderbird files directly between Windows and Ubuntu, I decided to give up--er, I mean, re-think my objectives:).[/FONT]
  
  [FONT=Arial]My goal being to make Ubuntu my primary OS, I realized that my main interest in the mail currently in my Windows copy of Thunderbird was to save those messages that had potential long-term interest for me.  Since I had already set up sub-folders to my Inbox that hold important messages going back several years (in some cases: e.g., receipts for online purchases), I started searching for ways of storing them in a way that I could access from Ubuntu.[/FONT]
  
  [FONT=Arial]Through Googling I found a Windows program, ABC Amber Thunderbird Converter, that can convert mail messages (".msf" files) into many other formats, including ".hjt" format files, which are  used by Treepad, a quite convenient free-form database manager. I have used Treepad for several  years, and it works just fine in Wine.  So the mail messages that I wanted to archive are now in a Treepad database, and I can read them while using Ubuntu.[/FONT]
  
  **[FONT=Arial]Note:[/FONT]**[FONT=Arial]  After doing what I've described above, I happened across a "mozillaZine" page ([http://kb.mozillazine.org/Thunderbird_:_FAQs_:_Migration](http://kb.mozillazine.org/Thunderbird_:_FAQs_:_Migration)).  It includes the following paragraph, which suggests an easier procedure than that which I used.  The following is probably what Falconindy and Techstop had in mind (I wish I'd found this Webpage earlier!):[/FONT]
  
  **[FONT=Arial]Using IMAP remote folders as an intermediary[/FONT]**
  
  [FONT=Arial]If you have problems migrating your mail, you might consider signing up for a free IMAP account and use it as an intermediary to move your mail. Think of it as a file share that knows about mail folders. You could create a 7GB IMAP account for Gmail using these instructions, or a 2GB IMAP account with AIM using these instructions . When you're done moving your mail, you can delete the IMAP account in both email clients.[/FONT]
  
  [FONT=Arial]IMAP supports remote folders (on the mail server) that you can access just as though they were local folders. You can copy/move messages/folders to/from them, even drag and drop a entire folder hierarchy. This would let you preserve most of the message status information (what messages have been replied to, etc.) and the folder hierarchy. It should cause the least problems, since you're using an Internet standard that both email clients support, rather than trying to convert between two partially documented file formats etc.[/FONT]
  
  [FONT=Arial]Create an IMAP account in both email clients. Copy your messages/folders to a remote inbox folder using one email client, and then copy them from the remote inbox folder to a local folder using the other email client. If you have more messages than can fit in the mailbox, do it in several steps, deleting the messages/folders in the remote inbox and compacting it as needed to free up more space. There are a few email clients whose IMAP support is crippled, and don't support uploading messages. But most popular email clients (Eudora, Outlook, Outlook Express, Pegasus, Thunderbird etc. ) do.[/FONT]
  
  [FONT=Arial]If the performance delay due to sending a lot of messages over the network is an issue, you could temporarily install a local IMAP server and use it to provide the remote folders. hMailServer is an open source IMAP server for Windows that's easy to install. [/FONT]

---

