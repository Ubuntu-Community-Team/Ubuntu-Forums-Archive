---
title: "non-empty directory appears as empty in nautilus"
date: 2009-11-18
forum: General Help
---

### Post by Suiname on 2009-11-18
Hello all,
  I had a user who was reporting strange behavior on his 64-bit 9.04 ubuntu box using gnome.  There is a directory named /research/mike on his computer, which is also the home directory of another user.  This directory always appears as empty when viewing it through nautilus, though it is actually filled with sub directories and files.  

Here's what I've done so far:
I checked to make sure nautilus is set to show hidden files, it is.
I checked to make sure he had the proper permissions to see files in that directory, he does.
I've tried running nautilus as root, directory still shows as empty.
I tried logging in as myself (we both are admins on the box, so same permissions), I could also not see the files while logged in as myself.
I tried viewing the contents of the directory in the terminal, the terminal shows all files and folders.
I had the user mike log in (this folder is his home directory) and open the directory through nautilus, he sees all the files and folders.

Has anyone else had this problem?  So far this is the only directory which exhibits this behavior, there are 4 other users with home directories which are all visible.  I've tried looking on this forum and all over google, but I couldn't find anything.  Any help would be much appreciated.

---

### Post by Suiname on 2009-12-03
Just wondering if anyone has any ideas on this one.  I'm having the user use thunar now without incident, it would be nice if he could also use gnome though.

---

### Post by HappyHenry on 2009-12-28
I just did a fresh install of Jaunty (9.04) from a disk in the publication Linux Format. I am "mister paranoid," so I was looking around the files, after the install and found the sam e file you wrote about. I is in Home/mike. It doesn't show in the user groups but the file is there. I tried to creat a new user "mike" and system reports "user already..." This has me scratching my head.
Please anyone know what this user file is doing in the home directory of a fresh install? As of now I wont use any distros off the magazine rack. I checked there web sight for an explination - nothing there. I, like you, have looked here and around the net but, nothing about user mike in the home directory. I'm guessing from your info this is a research folder placed to report someting to someone??? Even as admin I cant deleate this user. I am too 'noid to use a system with a user account I can not admin over.
Please inlighten this ignorant, paranoid newbie...anyone???

---

