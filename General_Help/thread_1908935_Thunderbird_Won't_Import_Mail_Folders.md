---
title: "Thunderbird Won't Import Mail Folders"
date: 2012-01-14
forum: General Help
---

### Post by SillySod on 2012-01-14
I want to use Thunderbird to read my e-mail and I have tried to configure it several times but I can never get it to work properly.

Whenever I add a new account, the only folders which show up are "Inbox", "Deleted" and "Drafts".

I have several e-mail accounts that I want to import into Thunderbird.  They all have a "Sent" folder and several of them have other custom folders such as "Read" or folders relating to specific topics where I move messages to keep track of them.

I can't get any folders other than Inbox, Deleted and Drafts to show up.  How can I do this?

I have read many postings about the trouble people have had trying to get the "Sent" items folder showing up.  The solution seems to be to send a message and then the folder will show up.

That's no use to me.  I have tried it before and all that happens is that the message you just sent appears.  I need Thunderbird to import all messages currently in the Sent folder (and every other folder), and keep it up-to-date when I send messages from Thunderbird or from a webmail client.

Surely Thunderbird can do this?

---

### Post by SeijiSensei on 2012-01-14
We need a bit more information.

First, are the accounts you're adding using IMAP?  That's the only mailbox protocol which will give you an identical view of your mail from any client, e.g., Thunderbird and a webmail app.

Next, if you are using IMAP, it's likely that you haven't "subscribed" to your mail folders.  Right-click on the email address at the top of the folder tree and choose "Subscribe".  If you try subscribing and still don't see your folders, you probably need to specify a different mail directory in Thunderbird's IMAP settings (Account Settings > Server Settings > Advanced).

---

### Post by ajgreeny on 2012-01-14
Are you using pop or imap for your mail protocol, and how are you attempting to import your mail folders?

If you use pop you will see many **name.msf** files and similar number of empty (probably) folders with the same names, in the hidden folder in your  **/home/user/.thunderbird/*#x#x#x#x*.default/Mail/Local Folders**.  These files contain all your downloaded emails, and can be copied from machine to machine if you wish.

If you use imap you will need to setup the mail account in thunderbird, to do what you want regarding the local archiving of messages.  Often nothing is archived locally, or it may be just the headers.

---

### Post by SillySod on 2012-01-15
That's it, "Subscribe" was just what I needed, all my mailbox folders show up now if I tick everything using "Subscribe"!

It appears my mail uses IMAP, and I was using the "Add account" option in Thunderbird, which asks you for your e-mail login details and then works out the rest for itself.

I don't know much about anything, even less about the innards of e-mail, so I wouldn't have a clue to try to set up my mail accounts manually.

I'm not sure how well-known this straightforward "fix" is: I must have read 20 or 30 different topics all over the internet about how to get the "Sent items" folder showing up and importing all the previously sent messages.  They all seemed to involve fiddling about with files in the home folder or using the terminal instead of just ticking Subscribe to Sent items, so I hope anyone with a similar problem will find this!

A couple more things if I may - to try to help me understand things a bit more:

I selected "Subscribe" on my main PC yesterday, today I am setting up Thunderbird from scratch on another PC, but as soon as I add an account, all the folders are already subscribed: does this mean the subscribe setting is part of the mail server rather than Thunderbird?

Is there a way to change the order of mail accounts in the left-hand pane of Thunderbird? At the moment they are appearing in the order I remember to add them, which is a bit random, but I can't find a way of shuffling them about.

Thanks for the help on this, I'm so pleased to be moving onto Thunderbird, it makes me feel one step more Ubuntuy than I did before!

---

### Post by SeijiSensei on 2012-01-15
> **SillySod said:**
> does this mean the subscribe setting is part of the mail server rather than Thunderbird?

Yes, I believe the subscription list is maintained by the IMAP server.

> Is there a way to change the order of mail accounts in the left-hand pane of Thunderbird?

In my experience the accounts appear in the order in which they were added.  I don't know of any way to change this from the GUI client, but you might be able to change the order by manually editing $HOME/.thunderbird/randomchars.default/prefs.js, or perhaps .../localstore.rdf.  I'd search the forums at [mozillazine]("http://forums.mozillazine.org/viewforum.php?f=39") for help with this.

---

### Post by SillySod on 2012-01-17
I have installed various add-ons to Thunderbird to get it to do what it doesn't do on its own: the account listing order in the left-hand pane can be controlled with an add-on called "Manual sort folders".  I also have add-ons to password-protect Thunderbird when it is started up, and for controlling how messages are quoted in replies and forwards - add-ons for all these kinds of things can be loaded from the Mozilla site.

I still have a problem with Thunderbird which needs fixing, but it's different to the one in this topic so I will set this as solved and start a new one.

---

### Post by barmax on 2012-01-18
Hi All,

My problem is a bit deeper then described above.  I installed Xubuntu (clean) after haveing used Ubuntu with the Gnome desktop.  Prior to the install, I backed up my data in the home directory that I wanted to keep which included my settings for skype, firefox, thunderbird etc.  All went well....  except with thunderbird.  

I copeid my default folder into the .thunderbird directory and then modified the profile.ini file to point to the new default.  I have done this before with success.  

It didn't work.  No account details show up in TB and consequently there are no mail folders.  My default email account uses POP and not IMAP.  

Any suggestions?

Thanks

---

