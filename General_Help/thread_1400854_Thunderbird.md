---
title: "Thunderbird"
date: 2010-02-07
forum: General Help
---

### Post by agkq62 on 2010-02-07
How do I transfer my address book, email settings etc from my old computer using Thunderbird on XP.

Thanks.

---

### Post by oldfred on 2010-02-07
Just copy the entire profile. I dual boot xp and ubuntu and put the profile into a shared NTFS partition. When I travel I copy the entire profile to my portable which I just converted from XP only to Ubuntu. You need to start Thunderbird once to create the default profile and then edit the profile.ini to use the one you copied instead of the default.

[http://www.mozilla.org/support/thunderbird/profile#locate](http://www.mozilla.org/support/thunderbird/profile#locate)
[http://kb.mozillazine.org/Profile_Manager#Linux](http://kb.mozillazine.org/Profile_Manager#Linux)

More info:
[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux](http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux)
[http://kb.mozillazine.org/Profile_Manager](http://kb.mozillazine.org/Profile_Manager)

---

### Post by agkq62 on 2010-02-08
Ok I have copied the profile from windows but can't find where to put it in Ubuntu.

I have tried the various commands from the links but none work.

Any ideas, thanks.

max@max-laptop:~$ /usr/lib/thunderbird -ProfileManager
bash: /usr/lib/thunderbird: is a directory
max@max-laptop:~$ path/to/application -profilemanager
bash: path/to/application: No such file or directory
max@max-laptop:~$ : path/to/application -profilemanager
max@max-laptop:~$ cd
max@max-laptop:~$ path/to/application -profilemanager
bash: path/to/application: No such file or directory
max@max-laptop:~$

---

### Post by vttay03 on 2010-02-08
Place the profile in ~/.mozilla-thunderbird...you should see another file in there as well named profile.ini that tells Thunderbird which profile to use.  You can edit that to reflect the profile you copied from Windows.

---

### Post by agkq62 on 2010-02-08
Am I wrong putting this in the terminal?

max@max-laptop:~$ ~/.mozilla-thunderbird
bash: /home/max/.mozilla-thunderbird: is a directory
max@max-laptop:~$

---

### Post by oldfred on 2010-02-08
go to places on the top panel. Home folder, in panel choose view and check box for show hidden files. You will see all the files & folders starting with . dot.

You should be able to scroll down to 
for firefox
/home/fred/.mozilla/firefox

for thunderbird
/home/fred/.mozilla-thunderbird

My profile which shows a path to a shared directory. You should just have to change the xxxxxx.default, do not change IsRelative unless you are not keeping it in the local directory. 

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=/home/fred/shared/mozilla/thunderbird/profiles/[COLOR=DarkRed]lyu25irb.default[/COLOR]

---

### Post by agkq62 on 2010-02-08
Thanks for your patient help, I got there at last :D

---

### Post by oldfred on 2010-02-08
Glad it worked.

---

