---
title: "No folders in Thunderbird"
date: 2011-07-06
forum: General Help
---

### Post by sbarmeier on 2011-07-06
Upon opening Thunderbird today, no single folder (inbox, trash, local folders, etc.) is showing.

The mail accounts are all still correctly registered, the search function finds the messages. Yet, the folders (in oder to browse the mail accounts, check for new messages, etc.) are not showing up.

The folder pane is showing, but empty. I can toggle between 'Unified Folders', 'All Folders', 'Unread Folders', etc., but they are all empty. 

This seems to have happened before on a Mac after an upgrade to version 3.1.2. [http://forums.mozillazine.org/viewtopic.php?f=39&t=1970759&start=30](http://forums.mozillazine.org/viewtopic.php?f=39&t=1970759&start=30)

I am using the latest version (3.1.10) on Natty (64-bit).

Any help would be much appreciated!
Sev

---

### Post by sbarmeier on 2011-07-06
I just got a new email and clicked on the little pop-up notice. This took me to the unified inbox, and now I can see the inbox, the folder pane, and the message in split view.

However, the folder pane is still empty, and I can't browse the other folders...

Also, the split view looks now like

| pane | folder        |
| selected message |

Before it had always been

| pane | folder                  |
|         pane | selected message | 

Any ideas?

---

### Post by sbarmeier on 2011-07-06
[BUMP] Still no change. I've tried safe mode (thunderbird -safe-mode) without any change.

Also, the search function finds the messages (and displays the first few lines in the search). But trying to open any message doesn't work. You get taken to a new tab in split view, but none of the split windows has any content...

Am I the only one with this problem? (I've even had a dream about Thunderbird last night. Clearly I am very desperate... Please help me.)

---

### Post by sbarmeier on 2011-07-09
[BUMP] Nobody? You could just tell me, you have no idea either, or you've never heard of this problem...

---

### Post by amanchesterman on 2011-07-09
I've used Thunderbird for several years now, initially on a Windows machine and now on a Ubuntu one, and I have never had a problem like this, nor ever heard of it.

But that's no help to you!

If I was in your situation I would be tempted to remove and re-install Thunderbird. I suggest
1) Find the (hidden) .thunderbird folder inside your /home folder. Within it is a folder called 'xxxxxxx.default', where the x's are a random string of characters. That is your Thunderbird 'profile' folder which contains all your saved emails and mail settings. Copy that whole profile folder somewhere safe.
2) Remove Thunderbird from your system including the backup and configuration files.
3) Re-install Thunderbird using the package manager.
4) Find the (empty) profile folder for the newly installed version of Thunderbird: this will be in the same location as above.
5) Delete the empty profile and then copy your profile folder back into that location, renaming it so that it has the 'xxxxxxx' string of the empty profile you have just removed.

You should then have a fresh installation of Thunderbird with all your emails and settings restored. With luck, it will show your mail folders as it is supposed to!

(That's what I did when I migrated from my old Windows laptop to my present one, and it worked fine. A fuller version of those instructions is on the Thunderbird website.)

Good wishes
John

---

### Post by sbarmeier on 2011-07-09
Thank you for your reply! I created a new profile (thunderbird -profilemanager) and copied over my settings into the new profile. Easier than expected, and the bug has been left behind in the old profile.

[http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Thunderbird](http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Thunderbird)

has all the info I needed.

---

### Post by shaneonabike on 2011-12-09
I also had this issue (Ubuntu 11.10 and TBird 8.0)  and read on another forum to check (or in my case uncheck) the 'Keep messages for this account on this computer'.

I think that somehow the files became slightly corrupted and making this change causes them to be fixed. Hope that helps other people.

---

### Post by sports supplement on 2012-01-05
I have had the same problem with Folders missing.  I worked through your instructions but decided to do a full reinstall (entering my e-mail account details etc) - I wishes I had followed your instructions.  However, the folders have now reappeared.  

I am using Ubuntu 10:04 and Thunderbird 9.0 - 64bit.  

I really appreciated this thread!

---

### Post by xadder on 2012-04-03
Hi folks,

I am having similar problems on a couple of PCs, one Ubuntu+xfce, the other linux mint 12, but I think the basic problem was some recent upgrade of Thunderbird.

I am using IMAP (nothing stored locally), and if I use webmail to access my account I see that all is well, all folders still exist. If I use thunderbird, I see Inbox, one of my "normal" subfolders, then Drafts, sent, etc,

Yesterday In uninstalled thunderbord completely, deleted the .thunderbird, and re-installed. No difference :-(

Help appreciated.

---

### Post by xadder on 2012-04-03
Found the solution to my problem here:

[https://amahanty.wordpress.com/2010/07/03/mozilla-thunderbird-nested-folders-subfolders/#comment-175]("https://amahanty.wordpress.com/2010/07/03/mozilla-thunderbird-nested-folders-subfolders/#comment-175")

Very simple once you know how.

---

