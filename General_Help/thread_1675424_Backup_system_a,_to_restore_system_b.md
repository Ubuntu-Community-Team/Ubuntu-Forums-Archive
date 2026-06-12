---
title: "Backup system a, to restore system b"
date: 2011-01-25
forum: General Help
---

### Post by simolokid4 on 2011-01-25
Hi Ubuntuforums,

Recently I've backupped my entire /home folder on my laptop with grsynch trough ssh.

Since I already had a simply text file containing all installed programs, I figured 'then, when i go from the backup trough my desktop, all my program settings will be restored if i run the txt file to install all those programs first.

So i installed al programs, then i went from backup to /home on desktop, logged out and back in. Started up a random program (tried thunderbird and filezilla) and no settings were to be found. In retrospect, docky did start, but didnt have all the launchers i had on my laptop. so that could have been a clue.

Why isnt this method working? ;x

Kind regards

---

### Post by simolokid4 on 2011-01-26
Bump.

---

### Post by tgalati4 on 2011-01-26
Did you back up /etc?  Configuration files are stored there.

---

### Post by oldfred on 2011-01-26
Only system settings are in /etc. If you manually configured something that file should also be saved, otherwise everything is default.

How did you backup /home? If you copied to NTFS you may have lost permissions and ownership.

You should be able to view the hidden files & folders and see if your Thunderbird & Firefox folders are there.

This has the correct settings for /home:

Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)
#Replace all instances of username with your login name.
sudo chown username:username /home/username/.dmrc
chmod 644 /home/username/.dmrc
sudo chown username:username /home/username     
chmod 755 /home/username

---

### Post by simolokid4 on 2011-01-26
I Backupped my /home folder (so .encryptfs and <myusername> folders are the 'root' ) with grsynch, to my nas. Which has a stripped down linux version. and is running the ext3 filesystem. (Found out with mount command)

Then I simply switched source and destination since I have the same username and password on my desktop, also with home dir encryption... same pass = same encryption.

Or doesnt grysnch automaticly backup hidden folders aswell ;x (I'm going to hit google for that but in the meantime, thansk for the replys so far )

The .filezilla and .thunderbird folders are there, in my home. I just checked that :)

Should I maybe try running grsync as root? Doesnt make much sense since it's my homedir... i should have sufficient rights.

---

