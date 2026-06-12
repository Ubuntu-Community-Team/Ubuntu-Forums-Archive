---
title: "thunderbird and sharing profiles ... specific"
date: 2010-04-02
forum: General Help
---

### Post by zero7404 on 2010-04-02
i have done this once before, but recently suffered corrupted profile ...

i have a dual-boot system, windows vista and ubuntu on one physical disc (hdo, seperate partitions). i have another physical disc (hd1) that has an ntfs partition, and on it are stored my firefox and thunderbird profiles.

when i use firefox and thunderbird in windows, both profiles are on the hd1 drive (email, bookmarks, etc.)

in ubuntu, i have the ntfs partition on hd1 automount, so that i can use it.

in ubuntu:
i have made thunderbird share the thunderbird profile on this partition (hd1), but recently, trying to set up the profilemanager to access this has caused me problems and while starting thunderbird, i see all my emails for a brief second (in the inbox), and then they disappear.

i am using the latest thunderbird from the unmaintained repositories (3.0.5), but i don't have a problem reverting back to an older version...

i use it for gmail, so the folder i point profilemanager to is:

/media/sdb1/Mozilla Profiles/Thunderbird/Mail/pop.gmail.com/Mail/pop.gmail.com

this is where my inbox, sent items are stored.

can anyone give advice on how to get this profile to work well with thunderbird in ubuntu ? i have read the mozillazine help pages, but it's not specific to my situation because i am trying to share a profile i have moved to a seperate location ...

thanks in advance

---

### Post by nem75 on 2010-04-02
I completely realize that this is not an answer to your question and apologize for my curiosity but - if you want to access your e-mails from two (or more) different OS's and are using GMail ... why not use IMAP instead of POP3?

---

### Post by oldfred on 2010-04-02
I have not converted to the new version of thunderbird but have not had any problem sharing firefox and thunderbird for 3 years. Orginally it was a FAT partition but with Karmic I converted to NTFS.

I avoid spaces on anything related to linux and now even in windows to avoid issues.



Start Thunderbird & shut down. In place, homefolder, (change view setting check to show hidden files), scroll down to .mozilla-thunder
on my system:

/home/fred/.mozilla-thunderbird

It should contain a profile file and a directory xxxxxx.default
You can copy the entire default directory from one computer to another. If the name or path is different you can edit the profile with the correct entry. I also copy my shared to my portable and back when I travel without any problem.

More info:
[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux](http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux)
[http://kb.mozillazine.org/Profile_Manager](http://kb.mozillazine.org/Profile_Manager)

my fstab:
# Entry for /dev/sdc2 :
UUID=44332FD360AA9657                      /home/fred/shared  ntfs-3g      defaults                             0  0  

my profile:
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=/home/fred/shared/mozilla/thunderbird/profiles/lyu25irb.default
Default=1

---

### Post by zero7404 on 2010-04-02
> **nem75 said:**
> I completely realize that this is not an answer to your question and apologize for my curiosity but - if you want to access your e-mails from two (or more) different OS's and are using GMail ... why not use IMAP instead of POP3?

i don't understand the question ... thunderbird sets up my gmail as imap, but the path where my mail is shows it as pop ...

not sure why that is, maybe it's from some time before thunderbird adopted imap for gmail ?

---

### Post by zero7404 on 2010-04-02
oops, there's my problem right there, i forgot about editing the profile.ini file ...

it's been a long time since i last did that, so i forgot. simply pointing the profilemanager to the correct directory doesn't work.

edit:
attempted again, no dice. it seems no matter what i do, i cannot get it to play nice, find and display my email properly.
i even tried copying the main files (Inbox, Inbox.msf, Sent, Sent.msf) and pasting them into a newly created profile (in the same location as the newly created files would be), thunderbird doesn't want to display my email.

this was the initial cause for my post, no matter which sub-folder i point it to, no matter what i seem to do, it does not want to display my email.

i use mozbackup in windows, so i keep it as a safeguard in cases i lose some data. regardless, when i create a brand new profile in a new directory, then try to paste my mail files in it, they don't show in thunderbird.

---

### Post by lidex on 2010-04-02
I would not be comfortable using one profile for two separate installs. My suggestion would be to follow oldfred's directions. If you want to have your email data in one location you may be better served by using gmail (or equiv). I have three ubuntu and one winxp versions of thunderbird that I've copied the profiles to and just leave the email on the server. Easy enough to download the email to the version I'm currently in without the problem of conflicts/corruption affecting all plus you have backups inherently.

---

### Post by zero7404 on 2010-04-02
i don't really care to share the entire profile, i just want my inbox, sent items, and contacts to be in one location and live within both OS's. so that when i am in ubuntu i can check and send mail, and see those in thunderbird when in windows ....

since it's the same program and uses the same files, i figure it would be easy to do, but i have had a hard time trying different things over and over, so i don't care to try anymore.

---

