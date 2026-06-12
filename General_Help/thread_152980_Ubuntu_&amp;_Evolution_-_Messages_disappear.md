---
title: "Ubuntu &amp; Evolution - Messages disappear?"
date: 2006-03-31
forum: General Help
---

### Post by Robor on 2006-03-31
I've been using Evolution as my Email program.  I have it setup with several sub folders under my Inbox for organization.  One folder was 'Shopping' where I dumped all of my online purchases and such.  Well, I took a look in there yesterday and found that there were only 4 messages displayed.  There should be a few hundred!

Now tonight I got a audible sound saying I got a new message and when I looked in the Inbox folder there were no messages there.  Inbox showed like 'Inbox(1)' to indicate a new message but my Inbox was empty.  If I right-click on it and select properties it shows that there's 91 messages yet none display.  Now, I know that there were not 91 messages before tonight - there were probably 20 or so.

I've searched all through Evolution's settings to try and find something to reindex my messages but can't find anything.  Please help.

---

### Post by dcstar on 2006-03-31
[QUOTE=Robor]I've been using Evolution as my Email program.  I have it setup with several sub folders under my Inbox for organization.  One folder was 'Shopping' where I dumped all of my online purchases and such.  Well, I took a look in there yesterday and found that there were only 4 messages displayed.  There should be a few hundred!

Now tonight I got a audible sound saying I got a new message and when I looked in the Inbox folder there were no messages there.  Inbox showed like 'Inbox(1)' to indicate a new message but my Inbox was empty.  If I right-click on it and select properties it shows that there's 91 messages yet none display.  Now, I know that there were not 91 messages before tonight - there were probably 20 or so.

I've searched all through Evolution's settings to try and find something to reindex my messages but can't find anything.  Please help.[/QUOTE]

See that search bar near the top to the RHS of folder list?, make sure you select "Clear" to ensure that it doesn't filter anything.

---

### Post by Robor on 2006-03-31
That was the problem - sort of.  I did have search info in my Inbox and Shopping folders.  When I cleared that search bar it looks like (I didn't count them) all of the messages in the shopping folder are there.  However, when I cleared the Inbox search bar nothing happened.  I did get 3 new Emails and they displayed but there's now 94 messages with only 3 of them showing up.  Any ideas? 

Thanks very much for the help!  :)

---

### Post by Robor on 2006-03-31
Followup...  Apparently during some trial-and-error I had some Inbox messages marked as hidden because when I did a Ctrl-A to select all and hid the entire Inbox it worked - nothing displayed.  Then I did a Ctrl-A to unhide all and the messages appeard.  There are about 25 messages displayed.

The problem is, when I right-click my Inbox and select properties it shows there are 95 messages.  Now there's none hidden and no search filter.  Any idea where these additional 70 messages or so are?  :-k

---

### Post by dcstar on 2006-03-31
[QUOTE=Robor]Followup...  Apparently during some trial-and-error I had some Inbox messages marked as hidden because when I did a Ctrl-A to select all and hid the entire Inbox it worked - nothing displayed.  Then I did a Ctrl-A to unhide all and the messages appeard.  There are about 25 messages displayed.

The problem is, when I right-click my Inbox and select properties it shows there are 95 messages.  Now there's none hidden and no search filter.  Any idea where these additional 70 messages or so are?  :-k[/QUOTE]
There will be Inbox index files in your hidden .evolution/mail/local directory somewhere, you may want to try moving them and then restarting Evolution (I believe that they will be recreated automatically).

---

### Post by Robor on 2006-04-10
Ah, so that's how to do a re-index?  Thanks!  :)

---

