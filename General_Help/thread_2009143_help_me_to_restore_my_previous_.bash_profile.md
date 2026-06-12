---
title: "help me to restore my previous .bash_profile"
date: 2012-06-24
forum: General Help
---

### Post by sorabh.v6 on 2012-06-24
I was editing the bash_profile with vi and suddenly i quit the vi due to which i lost my previous bash_profile and new bash_profile is a blank file .Please help me..

---

### Post by Cheesemill on 2012-06-24
Do you have a file called .bash_profile~

vi will often save a  previous version of the file you are editing with a ~ on the end.

If not then I think you are out of luck.

Also Ubuntu doesn't have a .bash_profile file in a normal installation, what are you trying to achieve by creating one?

---

### Post by zombifier25 on 2012-06-24
Ubuntu uses .profile, not .bash_profile (however, Ubuntu will ignore .profile if .bash_profile is present).

If vi does not backup the old file (like Cheesemill stated), then remove both .profile and .bash_profile (if any) in your home directory and copy the stock .profile file from /etc/skel to your home folder.

---

