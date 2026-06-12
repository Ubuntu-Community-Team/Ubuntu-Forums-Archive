---
title: "Thunderbird Win2k to Kubuntu"
date: 2006-03-30
forum: General Help
---

### Post by dawhoo on 2006-03-30
One of the things that's really giving me some trouble: migrating email apps.

I've been using thunderbird for a long time and I would like to migrate my accounts, inbox and contacts from my Win2K to Kubuntu.

I have my NTFS drive mounted, so I can access the correct files in windows, and the files seem to be located at /usr/lib/mozilla-thunderbird/ in Kubu.  

Can I jsut copy the win2k profile over to Kubu?  I have multiple accounts, lots of emails and several contact lists that I don't want to lose.  The files have different extensions and don't seem to follow the same naming scheme.

I don't know if it makes a difference, but I installed Thunderbird via 'Adept' package manager.  Any advice is appreciated :D

---

### Post by nanotube on 2006-03-31
hey
to copy your profile properly, see instructions on my howto page, here:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Thunderbird](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Thunderbird)
in there you will also find links to more detailed help, if you end up needing it.

---

### Post by DeadEyes on 2006-03-31
I have a dual boot XP Kubuntu that share data. Thunderbird is on both OSs and they both look for profiles and mail in the same place (a fat32 partition).
This means I can download mail in XP reboot into Kubuntu and see the mail (and vice versa).
If your interested try [http://www.plaintivemewling.com/?p=20](http://www.plaintivemewling.com/?p=20)

---

### Post by dawhoo on 2006-03-31
Thanks guys!  

I now have all my old mail and addresses from my Windows installation of Thunderbird.  

I can't share the data between the two installations.  Windows is NTFS, which is on it's own HD and Kubuntu is on its own HD that's formated with whatever file system it uses.  I don't have a 3rd HD and the other two are full disk partitions.  But that's OK, all I plan on using Windows for now is Paint Shop Pro and Dreamweaver.

If you're attempting this yourself, you'll need to change folder permissions in Kubuntu after copying the folders to your Linux folder before the application can write new emails to the folder.

---

### Post by CameronCalver on 2006-03-31
hey i want to set up my gmail or hotmail with evolution or thunderbird with thunderbird i did what this guide told me to do and it looks for email then it does pik any up

---

### Post by dawhoo on 2006-03-31
CameronCalver,

I may not know all the information, but what you're trying to do shouldn't work.

Thunderbird is for POP mail and Hotmail, Gmail and the like are not accessible via POP.  Some of the web based emails allow you to get your email via POP for a fee, but they're not likely to give it to you.  They give you email services so the can sell advertising.

Now I may be wrong, but last time I checked, this was the way it is.

---

### Post by nanotube on 2006-04-02
sorry dawhoo, you may be right about hotmail, but gmail DOES provide free POP service, so it is entirely possible to set thunderbird to pick up gmail. they even have a very nice link on how to set it up with various email clients, including thunderbird, here:
[http://mail.google.com/support/bin/answer.py?answer=13285&topic=1555](http://mail.google.com/support/bin/answer.py?answer=13285&topic=1555)
have fun, cameroncalver. :)

---

### Post by dawhoo on 2006-04-02
no need to be sorry, I'm the one who's sorry for providing bad information!

That's awesome that gmail will allow POP access.  I might start using my gmail account again :D

P.S. Thank goodness the forum colors have changed back

---

