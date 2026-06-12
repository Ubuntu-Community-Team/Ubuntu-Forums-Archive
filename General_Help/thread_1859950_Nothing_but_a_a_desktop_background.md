---
title: "Nothing but a a desktop background"
date: 2011-10-14
forum: General Help
---

### Post by sg_singh on 2011-10-14
Just upgraded to 11.10.  At first everything was fine.  This morning I have nothing but a desktop background.  No launcher, no way to get to terminal, and no way to log out but turning off the machine.  Strangely enough, if I log on from my wife's account, everything is fine.  

Any ideas how to restore functionality?

Thanks!

---

### Post by 23dornot23d on 2011-10-14
Possibly Xauthority ..... check in my link below ... others had similar problems and I added
a link to the solution in there

---

### Post by hwttdz on 2011-10-14
I'd alt+ctrl+f2 and login as you at the prompt, and 

mkdir dot_files_and_folders
ls -A1|grep -E '^\.'|xargs mv -t dot_files_and_folders

Then logout and log back in, it will reset _all_ your settings, and if you want to get something back just copy it back from that folder (for instance your .bashrc).

---

### Post by sg_singh on 2011-10-14
> **hwttdz said:**
> I'd alt+ctrl+f2 and login as you at the prompt, and 

mkdir dot_files_and_folders
ls -A1|grep -E '^\.'|xargs mv -t dot_files_and_folders

Then logout and log back in, it will reset _all_ your settings, and if you want to get something back just copy it back from that folder (for instance your .bashrc).

Thanks, that worked.

Now, could you give me info on getting back my email & browser bookmarks?  Nothing is as I remember it & I'm still new to Ubuntu in the first place...

---

### Post by hwttdz on 2011-10-14
Depends on which programs you were using.  

I'd suspect a

cd
cp --force -r dot_files_and_folders/.mozilla .
cp --force -r dot_files_and_folders/.thunderbird .

would do it for firefox and thunderbird.

---

### Post by sg_singh on 2011-10-14
That, too, worked.  However, after 30 minutes the computer froze & we are right back to the original problem.  Beginning to regret the 'upgrade'...

---

