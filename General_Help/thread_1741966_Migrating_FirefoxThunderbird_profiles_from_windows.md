---
title: "Migrating Firefox/Thunderbird profiles from windows problems"
date: 2011-04-28
forum: General Help
---

### Post by TheWSD on 2011-04-28
I am trying to do as the title states, I am however having problems.  I have tried deleting the profile and profile.ini in kubuntu and copying over the windows profile to home/user/.mozilla/firefox for example with firefox, this didn't work.  I tried copying it there with the existing profile and changing the path of the ini file, to the windows profile name, this didn't work either.  The only thing that I can think is that I am using 64 bit windows and 32 bit kubuntu.  If this is the problem does any one have any other ideas?  I have tried using firefox sync, this didn't work either.  Any help would be greatly appreciated :D

---

### Post by TheWSD on 2011-04-29
Sorry to bump already but after only 12 hours it's on teh 15th page, lol!

---

### Post by decrepit on 2011-04-29
I've never tried the profiles.ini file, I copy the whole ------.default folder.
That has all the bookmarks and stuff in it, and has worked every time.
Haven't tried with 64 bit

---

### Post by chrisccoulson on 2011-04-29
If you're using Firefox 4, then why not just set up a sync account? That can sync all of your bookmarks, history, preferences, passwords and open tabs.

---

### Post by TheWSD on 2011-04-29
Despite firefox sync not working for me last night, have tried again and it has thanks.  

That is half of the problem solved, does anyone have any idea about Thunderbird?  For me move away nearly completely from windows as you all understand I need to be able to transfer my emails over.

---

### Post by decrepit on 2011-04-29
In XP for me it's similar to firefox.
Documents & Settings-user-Application Data-Thunderbird-Profiles-########.default

If you copy the whole "########.default" folder you'll get all your old mail, server settings, passwords etc.
I paste it into. ".mozilla-Thunderbird"

Should work.

---

### Post by TheWSD on 2011-04-29
[decrepit]("http://ubuntuforums.org/member.php?u=240230"), I have already tried to copy teh profile over but it isn't working :(

---

### Post by decrepit on 2011-04-30
I vaguely remember having trouble a while ago, I think thunderbird was still using the old profile, I had to rename/delete the old one. 
But you say you've deleted the old profile, so perhaps you're right it's the 64bit thing.
Sorry I can't think of anything else.

---

### Post by decrepit on 2011-04-30
Something just occurred to me, when I was using windows and linux to look at mail, I created a mail swap folder in both versions. I used to transfer new mail to the swap folder in one OS so I could copy it into the other OS.

It would be interesting if you could do something similar, create a new mail folder in ubuntu thunderbird, then go into the windows profile and copy a mail folder from there into the one you created in ubuntu.
If that works you may be able to copy the whole profile a bit at a time?

---

### Post by TheWSD on 2011-04-30
decrepit, your last post gave me an idea, that I can't believe that I didn't try before, I have deleted the contents of the kubunu profile folder, and copied the contents of the windows profile into it and now it works! Thanks decrepit, sorted now

---

### Post by decrepit on 2011-05-01
Well glad that's solved, but it would be nice to know what the problem was.
I have got into the habit, of copying the whole .thunderbird folder over, before I install/start up Thunderbird in a new OS, that may be because I had trouble with old-new profile folders. (It's a real pain having a sieve for a memory)

---

### Post by SeijiSensei on 2011-05-01
Look at the file ~/.thunderbird/profiles.ini.  It contains a reference to the current profile directory.  If you copy a different profile over to .thunderbird, you need to change the entry in profiles.ini to point to the new directory.

---

### Post by decrepit on 2011-05-02
Great, that explains it, thanks.

---

### Post by venik212 on 2011-05-02
It is somewhere between outrageous and pathetic that after being out for so long people still have these kinds of problems, especially with an OS that is revised every 6 months.  Why isn't there an icon to click to migrate mail from a previous installation to a new one?  Why are there both .mozilla-thunderbind AND a .thunderbird folder in /home/user?  Which one should be used?  Where is the mail actually stored?  Both folders are very large, suggesting that the mail is somehow in both?  
I am confused (again...)

---

### Post by decrepit on 2011-05-03
> **venik212 said:**
> It is somewhere between outrageous and pathetic that after being out for so long people still have these kinds of problems, especially with an OS that is revised every 6 months.  Why isn't there an icon to click to migrate mail from a previous installation to a new one?  Why are there both .mozilla-thunderbind AND a .thunderbird folder in /home/user?  Which one should be used?  Where is the mail actually stored?  Both folders are very large, suggesting that the mail is somehow in both?  
I am confused (again...)

In my computer, .mozilla-thunderbird is only a link to .thunderbird, this is where everything is.
Probably done for compatibility reasons with different versions.

I guess this is why some people have a separate partition for "home", that way every thing can be kept when installing new OS. Haven't done that yet, but I'll be tempted next time.

---

