---
title: "delete Gmail msg using IMAP by configuring Evolution client"
date: 2010-04-29
forum: General Help
---

### Post by aliqon on 2010-04-29
I'd like to configure Evolution (or Thunderbird) to delete Gmail messages.

When I select messages and hit "Delete", the messages go to my local trash and they loose their Inbox label in Gmail.

I would like that in Gmail, they loose their Inbox label and go to [Gmail]/Trash so that they'll be deleted after a month.

[LIST]
[*]Could I configure the "delete" key of my keyboard to move msg to [Gmail]/Trash ?
[*]Could I configure another key to move msg to [Gmail]/Trash ?
[/LIST]

What other solution ? Because moving to the trash is not convenient, it takes a lot of time without a key shortcut.

Thank you.

_**See also:**_

[LIST]
[*]Google support: "Deleting IMAP messages" 
[http://mail.google.com/support/bin/answer.py?answer=78755&topic=12815](http://mail.google.com/support/bin/answer.py?answer=78755&topic=12815)

[*]Ubuntu forum: "Can't delete Gmail msgs in Evolution, using IMAP"
[http://ubuntuforums.org/showthread.php?t=742198&highlight=gmail+delete](http://ubuntuforums.org/showthread.php?t=742198&highlight=gmail+delete)
[/LIST]

---

### Post by aliqon on 2010-04-29
A **better solution** would be that when I empty my local trash, the messages are moved to [Gmail]/Trash to be trashed.

[INDENT]**How to configure Evolution so that the messages in local trash are moved to [Gmail]/Trash when I empty the local trash ?**[/INDENT]

Thanks !


PS: Notice that in Evolution you can configure the folders for draft and sent messages, but you cannot configure the trash folder :(...

---

### Post by kismeras on 2010-05-02
*BUMP*

I'd like to know too. I hate having to manually move msgs to trash.

---

### Post by nLinked on 2010-09-03
Bump. Works with Thunderbird, but want to get it working in Evolution.

I want messages I delete in my Evolution Gmail account to go to Gmail's Bin folder so it will sync with Gmail webmail too. I use Gmail IMAP in Evolution by the way.

---

### Post by earlra on 2010-12-16
I've been looking for a solution to this for two years and haven't found one yet.  I use Thunderbird because I can delete there.  However, I miss the other PIM functions in Evolution that don't function properly in Tbird/Ubuntu... :-(

Please update if you find a solution.

---

### Post by sgosnell on 2010-12-16
If you have the Google imap configured properly, whatever you delete in Evolution is deleted on GMail, and vice versa.  That's what imap does.  You do need to click the Send and Receive button to make it happen immediately, or else it only happens at the normal update time.  I've never had a problem with this, and I'm surprised that people are unable to get it to work.

---

### Post by nLinked on 2010-12-17
> **sgosnell said:**
> If you have the Google imap configured properly, whatever you delete in Evolution is deleted on GMail, and vice versa.  That's what imap does.  You do need to click the Send and Receive button to make it happen immediately, or else it only happens at the normal update time.  I've never had a problem with this, and I'm surprised that people are unable to get it to work.

It is deleted on Gmail yes, but doesn't appear in Gmail's bin. It doesn't get the Bin label through Evo. It goes into Evo's local trash.

---

### Post by sgosnell on 2010-12-17
From the GMail documentation: > If you're not using one of the above listed clients, as a general rule, we suggest the following settings:

Sending:

    * Do NOT save sent messages on the server. If your client is sending mail through Gmail's SMTP server, your sent messages will be automatically copied to the [Gmail]/Sent Mail folder.
    * DO save draft messages on the server. If you want your drafts in your mail client to sync correctly with Gmail's web interface, set your client to save drafts to the [Gmail]/Drafts folder.

Deleting:

    * Do NOT save deleted messages on the server. Messages that are deleted from an IMAP folder (except for those in [Gmail]/Spam or [Gmail]/Trash) only have that label removed and still exist in All Mail. Hence, your client doesn't need to store an extra copy of a deleted message.
    * Do NOT save deleted messages to your [Gmail]/Trash folder because this will delete a message in all folders.
    * Do NOT save deleted messages to your [Gmail]/All Mail folder as some clients will try to empty this folder and ultimately fail. This can lead to delayed mail access or excessive battery consumption on a mobile device.



---

### Post by nLinked on 2010-12-17
Thunderbird lets me choose to have any message I delete, to go into the Gmail Bin folder - fully synced with Gmail's Bin. I want this option in Evolution. Evo only delete's to the local client.

---

### Post by sgosnell on 2010-12-17
If you want to delete it, why don't you want to delete it?  I don't quite understand your position, but you're certainly free to use whatever email client you want.

---

### Post by Yettie on 2010-12-18
Messages moved into Gmail's Bin folder are automatically deleted after 30 days. Deleting in Evolution removes them from the Inbox, but leaves them in the Gmail 'All mail' folder, where they stay archived and clog up the storage. To permanently delete them from Gmail they need to be moved to the Bin folder.

---

### Post by jingaling on 2010-12-18
Here are my thoughts:

Why not create a rule in Evolution to move all items in the local trash folder to [Gmail] > Bin. This way once the rule has run in evolution it will be replicated online at gmail soi when you log on using webmail all your deleted items will be in the gmail bin.

I have to ask this...If you are deleting the emails then why does it matter where they go as they are being deleted anyway? I am assuming they are no longer required (hence the deletion). So why does it matter if they are in the gmail bin or the evolution trash folder? Anyway, the above system should work.

If you don't know how to create rules (known as filters by some email clients) then see the link below:
[http://library.gnome.org/users/evolution/stable/usage-mail-organize-filters.html.en]("http://library.gnome.org/users/evolution/stable/usage-mail-organize-filters.html.en")

---

### Post by Yettie on 2010-12-18
> **jingaling said:**
> I have to ask this...If you are deleting the emails then why does it matter where they go as they are being deleted anyway? I am assuming they are no longer required (hence the deletion). So why does it matter if they are in the gmail bin or the evolution trash folder?

Because, as I understand it, emails are only deleted from Gmail if they are in the Bin folder. Otherwise they stay in the All Mail folder (even if they are deleted in Evolution). Eventually there will be a huge number of unwanted emails in the All Mail folder, which could make Gmail slow.

---

### Post by jingaling on 2010-12-18
Well just empty the trash in evolution then ?! This way the mail will be deleted for ever.

Anyway, the work around I gave you will definitely work...don't worry about it by the way, your welcome :)

Jing

---

### Post by Yettie on 2010-12-18
> **jingaling said:**
> Well just empty the trash in evolution then ?! This way the mail will be deleted for ever.

Anyway, the work around I gave you will definitely work...

Jing

Well I'm not sure about that, unless I'm missing something. If I delete in Evolution, the message is removed from the Gmail Inbox and appears in Evolution Trash. I've tried emptying Trash and clicking Send/Receive, but the message is still in the Gmail All Mail folder.

Thanks for the work around, it sounds promising and I'll give it a try.

---

### Post by sgosnell on 2010-12-18
No, having emails on GMail won't make it slow.  You have > 7.5GB of storage there, and they serve up lots of messages every day.  Having a few thousand in your All Mail folder won't take any more time than having a few dozen.  GMail has lots of very fast servers.  It might take a couple of microseconds longer, worst case a few milliseconds longer, to load your page, but you certainly won't notice it.  It only loads a page at a time anyway.

---

### Post by Yettie on 2010-12-18
Oh, OK. Maybe this isn't a problem at all then. I can just leave the deleted messages archived and forget about them.

Thanks for the information. :)

---

