---
title: "Copying Thunderbird Files from One Machine to Another"
date: 2010-07-27
forum: General Help
---

### Post by 4String_Gal on 2010-07-27
Hi All,

I have a tarball of my old .thunderbird directory that I untarred onto my new machine. When I open Thunderbird, it wants me to go through the setup process. I've copied these files before and was able to get into my email. But not this time.

Any suggestions? I've spent hours searching online and haven't found anything to solve the problem.

Thanks!

-Susan

---

### Post by oldfred on 2010-07-28
I thought you had to go thru the set up once to get it to create a profile.ini and xxxxxxx.default directory. I regularly copy from my desktop to my portable but have same directory structure and have edited profile.ini to use the xxxxxxx.default that I copy not the one the install creates. The new t-bird also uses a different directory.

Update to tb3
[http://ubuntuforums.org/showthread.php?t=1349889](http://ubuntuforums.org/showthread.php?t=1349889)
new 
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux](http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux)
[http://kb.mozillazine.org/Category:Profiles](http://kb.mozillazine.org/Category:Profiles)

---

### Post by lidex on 2010-07-28
Once you setup a new profile you should be able to copy the 'Mail' data from old profile directly into it. You should first recreate your email accounts. Close t-bird and navigate to '~/.thunderbird/xxxxxxxx.default/Mail'. You'll find a folder for each account in that directory. Copy data from backup to corresponding account  folder there then delete all '.msf' files. Start t-bird and see if your folders/emails appear. If not go into account settings, select 'Server Settings' in the left pane (do this for each account) and at the bottom-right browse to the correct folder.
Ex:
```
/home/lidex/.thunderbird/td83om2x.default/Mail/pop.fuse.net 
```
Once done you may need to restart t-bird.

---

