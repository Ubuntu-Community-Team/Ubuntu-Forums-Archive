---
title: "Sync Thunderbird between two computers"
date: 2009-10-01
forum: General Help
---

### Post by ninjapirate89 on 2009-10-01
I have thunderbird set up on my desktop and my laptop and I'm wondering if there is a way to sync the two of them because I use it to check news feeds in addition to my email and end up checking the same feeds twice.

---

### Post by oldfred on 2009-10-02
I do not know if my method will work if you want to do this all the time.

When ever I travel I just copy the entire profile & directory over to my portable. I currently share one profile for both Firebird & thunderbird dual boot. Shared is in a FAT32 directory. In your home directory is a hidden file .mozilla-thunderbird that holds the profile and xxxxx.default that is all the data. Firebird is in .mozilla.

---

### Post by ninjapirate89 on 2009-10-02
> **oldfred said:**
> I do not know if my method will work if you want to do this all the time.

When ever I travel I just copy the entire profile & directory over to my portable. I currently share one profile for both Firebird & thunderbird dual boot. Shared is in a FAT32 directory. In your home directory is a hidden file .mozilla-thunderbird that holds the profile and xxxxx.default that is all the data. Firebird is in .mozilla.

Yeah, I was hoping for a way to maybe have both thunderbird accounts use one configuration folder. The only possible way I can think of is putting my config folder in DropBox and maybe configure Thunderbird to use it instead of the one in my home folder.

---

### Post by gogolink on 2011-01-02
> **ninjapirate89 said:**
> Yeah, I was hoping for a way to maybe have both thunderbird accounts use one configuration folder. The only possible way I can think of is putting my config folder in DropBox and maybe configure Thunderbird to use it instead of the one in my home folder.

That's what I do: I moved my Thunderbird profiles folder into Dropbox folder, and it works rather nicely.  The only problem: every once in a while Thunderbird creates "conflicted copies" of some of the files; I think that happens when I start working with Thunderbird before my computer is done downloading the latest changes to my Dropbox folder.  And these "conflicted copies" eat away at my Dropbox storage space.

I described this problem -- and what I did to move my profiles folder -- in [this post]("http://ubuntuforums.org/showthread.php?t=1651563").

---

### Post by JimS on 2011-11-05
...
Perhaps I misunderstand the issue, but I simple adjust
my account/servers settings to leave mail on server for
20 days.  That way all my TB clients will be able to
sync up provided none wait longer than 20 days.

This only works for Inbox's mail.  Sent mail will
only show on the computer which sent it.
...

---

