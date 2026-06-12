---
title: "how to move Thunderbird email program?"
date: 2011-09-21
forum: General Help
---

### Post by goodbye-windows(tm) on 2011-09-21
Hi All,

I have been using Xubuntu on my old Dell laptop for the last couple of months. I've worked out all the bugs, and have the laptop nicely customized, including a full blown multi account thunderbird email program. The laptop is my daughters primary computer and my back up system. She loves xubuntu, especailly because it's faster than windows.

Last week, I installed xubuntu on my primary computer, after dumping XP completely. My primary computer is a homebuilt desktop unit, 3.2 Ghz P4, with 1.5 GB of ram, running on an MSI motherboard. Everything works works on it, Xubuntu runs great!!!

But, now I want to move the Thunderbird from the laptop to the primary desktop computer. I searched this forum, but found the posts all involve moving t'bird from Linux to windows, or visa versa. When using google, the vast majority of the web resources are for those  running windows.

How to move t'bird from one xubuntu system to another xubuntu system? Both systems are running xubuntu 11.04.

Can I simply take the entire home folder from one machine and use it to overwrite the home folder on the desktop? 

TIA

Art

---

### Post by drs305 on 2011-09-21
I'm working from memory, but I think the only folder you need is ~/.thunderbird  (/home/username/.thunderbird).

In your new computer, rename the existing .thunderbird folder (for instance, .thunderbird.new), then copy the original .thunderbird folder to the /home/username folder. I think the profile will be automatically called up when Thunderbird is started from the profile file in the transferred .thunderbird folder.

I think that's all that's required (assuming the same username for permission purposes). As long as you rename or move the original .thunderbird folder rather than delete it you won't hurt anything and can restore it if necessary.

Note: This will not save any new mail/settings you have made on the new computer.

---

### Post by oldfred on 2011-09-22
I have my Thunderbird and Firefox profiles in NTFS partition so I can share in every install including XP. But when I travel I just copy the entire profile to my portable and copy it back.

If you have not started Thunderbird start it once to create a default profile. Then edit profile.ini with the XXXXX.default profile you copy from your old computer.

# Tbirdshare.txt
Update to tb3
[http://ubuntuforums.org/showthread.php?t=1349889](http://ubuntuforums.org/showthread.php?t=1349889)
new 
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

I think drs305's way works but you may have to start it manually with the --profileManager option to be able to choose an existing profile.

---

### Post by goodbye-windows(tm) on 2011-09-22
Tnx to you both!!!

I had no idea it would be so easy, but it actually was! 

I had opened thunderbird once, although I had not entered any data into it.

I copied the .thunderbird folder from the old system to the new one. I did not move or rename the .thunderbird folder on the new system, I just dragged and dropped. I had to overwrite some files. 

Since the new system's thunderbird folder was unused, there was very little risk.

It worked like a champ, although one of the passwords needs to be entered again. 

Again, many tnx to you both! I'll mark this one as 'solved'.

Art

---

### Post by goodbye-windows(tm) on 2011-09-23
It looks like my proclamation regarding the success of the move was premature. There is still a problem.

When I downloaded mail from the moved folder, the new messages download ok. But, as I click on the various mailboxes to read the new mail, thunderbird deletes all the old messages. So, I have the new email, but for some reason, the program deletes the old messages.

I've tried various fixes and experimenting.

If I use the profile manager to point to the new profile, the program launches without any filters and everything else is gone-as though I was a new user with no previous accounts.

If I copy the new profile and run it, the old mail is deleted as the new mail is added to the old mailboxes.

Some things that might be significant...

The original source file was a wubi install, the new data is loaded as the sole partition (no windows partitions, only Xubuntu).

Additionally, the original source file was taken from a computer without any encryption....but the machine it was copied to has the home folder encrypted.

Any suggestions? 

TY.

Art

---

### Post by oldfred on 2011-09-23
I know nothing about encryption.

Did you look at your profile.ini. It is in .thunderbird hidden folder.

---

### Post by ClientAlive on 2011-09-25
For what it's worth I found this link that might help.

[http://support.mozillamessaging.com/en-US/kb/moving-thunderbird-data-to-a-new-computer?redirectlocale=en-US&redirectslug=how-do-i-move-my-thunderbird-data-to-a-new-computer](http://support.mozillamessaging.com/en-US/kb/moving-thunderbird-data-to-a-new-computer?redirectlocale=en-US&redirectslug=how-do-i-move-my-thunderbird-data-to-a-new-computer)

HIH

;)

---

