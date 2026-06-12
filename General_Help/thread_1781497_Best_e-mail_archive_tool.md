---
title: "Best e-mail archive tool"
date: 2011-06-13
forum: General Help
---

### Post by tomreid on 2011-06-13
Hi

I'd like to download all the mail from an old web mail account I have into either Evolution or Thunderbird.

As I like to do clean installs (not upgrades) when a new version of Ubuntu is released, I'd like some way of archiving all these old mails, and then being able to  re-import them into Evolution or Thunderbird. 

What's the best way to do that?

cheers

---

### Post by dragonfly41 on 2011-06-13
Here is one approach I'm looking at myself .. not necessarily the "best" way ..

[http://www.enkive.org/](http://www.enkive.org/)

---

### Post by psusi on 2011-06-13
Just transfer the mail to a local folder, compact it, then back up the file.

---

### Post by ajgreeny on 2011-06-13
Having downloaded the one time, all the mail messages will be in the hidden folders **.evolution** and/or **.thunderbird** in your home.  Simply backing up those two folders should do everything, along with all your contacts/address book etc etc.

When you do a clean install of the next version of ubuntu, just copy those folders back into your home folder and everything will be there.  Alternatively use a separate home partition and updating will suddenly become very much simpler.

Do you need more?

---

### Post by tomreid on 2011-06-13
Hi, 

I'm not sure how I transfer to a local folder? Ah it's OK I see the answer above now. Thanks all.

cheers

---

### Post by psusi on 2011-06-13
Backing up all of .thunderbird will get the caches of the remote folders as well.  Under .thunderbird there is a XXXX.profile directory that contains Mail/Local Folders.  In there you will find foo and foo.msf files for each local folder ( foo ) in thunderbird.  You only need to back up the main foo file for each folder you want to keep.  The msf files are indexes to speed up access and will be regenerated when not found.

When you reinstall, simply drop the mailbox files into your new .thunderbird/XXX.default/Mail/Local Folders/ directory, and they will show up when you open thunderbird.

---

### Post by ajgreeny on 2011-06-14
> **psusi said:**
> Backing up all of .thunderbird will get the caches of the remote folders as well.  Under .thunderbird there is a XXXX.profile directory that contains Mail/Local Folders.  In there you will find foo and foo.msf files for each local folder ( foo ) in thunderbird.  You only need to back up the main foo file for each folder you want to keep.  The msf files are indexes to speed up access and will be regenerated when not found.

When you reinstall, simply drop the mailbox files into your new .thunderbird/XXX.default/Mail/Local Folders/ directory, and they will show up when you open thunderbird.
Agreed!

But if you want to make sure you have all the email account(s)  info as well, you may as well backup and restore the whole .thunderbird folder

---

### Post by Jan Greeff on 2011-06-24
All my msf files are in the home folder, but when I try to import everything into Thunderbird, the only option I get is to import from Communicatorx. 

If I try to import mail only, the "import preferences" option does not activate, i.e. there is no way that I can select any preferences. The window says to import from:   then there is just a "dead" window.

---

### Post by psusi on 2011-06-24
> **Jan Greeff said:**
> All my msf files are in the home folder, but when I try to import everything into Thunderbird, the only option I get is to import from Communicatorx. 

If I try to import mail only, the "import preferences" option does not activate, i.e. there is no way that I can select any preferences. The window says to import from:   then there is just a "dead" window.

You don't import them; you just drop the files back in the right place in the .thunderbird directory.

---

### Post by KeyserSoze93 on 2011-06-24
On your old system, run:

```

tar czvf thunderbird_backup.tar.gz ~/.thunderbird

```

Then copy thunderbird_backup.tar.gz to a USB stick or whatever you're using to store your files during your reinstall.

On your new system, drop it into your home folder and run:

```

mv .thunderbird thunderbird_old

tar xvf thunderbird_backup.tar.gz

```

The mv command is only necessary if you've opened thunderbird already on the new machine, since we don't want any new settings to interfere with the old profile.

When you next start thunderbird you should get all your old stuff just like nothing's changed.

---

### Post by Jan Greeff on 2011-06-29
> **KeyserSoze93 said:**
> On your old system, run:

```

tar czvf thunderbird_backup.tar.gz ~/.thunderbird

```

Then copy thunderbird_backup.tar.gz to a USB stick or whatever you're using to store your files during your reinstall.

On your new system, drop it into your home folder and run:

```

mv .thunderbird thunderbird_old

tar xvf thunderbird_backup.tar.gz

```

The mv command is only necessary if you've opened thunderbird already on the new machine, since we don't want any new settings to interfere with the old profile.

When you next start thunderbird you should get all your old stuff just like nothing's changed.
Many thanks. Is there a similar way to transfer bookmarks and stored passwords from Mozilla Firefox?

---

### Post by Habitual on 2011-06-29
```
tar -pczf myfirefox.tar.gz ~/.mozilla
```

or 

Ctrl+Shift+O in Firefox > Import and Backup > Export HTML > /path/to/backup/bookmarks.html

I suggest both. :)

Ya know none of this would be an issue if you had a separate /home partition?
Something to ponder during the "next" install or reformat.

---

### Post by Jan Greeff on 2011-06-30
Many thanks. How do I go about creating a separate /home partition?

---

### Post by dFlyer on 2011-06-30
To create a separate /home partition during install select manual configure for partitions. You will need to create at least a 10 - 20 gig / (root) partition. than create a separate partition for /home, you should make this as large as possible.

---

### Post by Jan Greeff on 2011-06-30
> **Habitual said:**
> ```
tar -pczf myfirefox.tar.gz ~/.mozilla
```or 

Ctrl+Shift+O in Firefox > Import and Backup > Export HTML > /path/to/backup/bookmarks.html

I suggest both. :)

Ya know none of this would be an issue if you had a separate /home partition?
Something to ponder during the "next" install or reformat.


My outcome from the code:
jan@jan-desktop:~$ tar -pczf myfirefox.tar.gz ~/.mozilla
tar: Removing leading `/' from member names
jan@jan-desktop:~$

---

### Post by Jan Greeff on 2011-06-30
Originally Posted by **KeyserSoze93**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10976212#post10976212")                 
                 [I]On your old system, run:

     Code:
     tar czvf thunderbird_backup.tar.gz ~/.thunderbird 
Then copy thunderbird_backup.tar.gz to a USB stick or whatever you're using to store your files during your reinstall.

On your new system, drop it into your home folder and run:

     Code:
     mv .thunderbird thunderbird_old

tar xvf thunderbird_backup.tar.gz 
The mv command is only necessary if you've opened thunderbird  already on the new machine, since we don't want any new settings to  interfere with the old profile.

When you next start thunderbird you should get all your old stuff just like nothing's changed.


[/I]**[COLOR=black]Tried this, everything seemed to work fine, all the files showed up in the terminal on the new system, but when I started Thunderbird there was a fresh new version with nothing in it at all.   [/COLOR]**

---

### Post by Jan Greeff on 2011-06-30
Tried this, everything seemed to work fine, I could even see all the folders in the terminal on the new system, but when I opened Thunderbird it was a new, clean version with not even mailbox configs.

---

### Post by Habitual on 2011-06-30
```
mv .thunderbird_old .thunderbird
```
to restore your previous Tbird settings.

---

### Post by Jan Greeff on 2011-07-01
Tried this, here is the outcome: 

jan@jan-System-Product-Name:~$ mv .thunderbird_old .thunderbird
mv: cannot stat `.thunderbird_old': No such file or directory
jan@jan-System-Product-Name:~$

---

