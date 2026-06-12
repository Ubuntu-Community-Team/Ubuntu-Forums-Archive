---
title: "How do you recreate a fresh home directory?"
date: 2011-11-19
forum: General Help
---

### Post by quickk on 2011-11-19
I would like to recreate a fresh home directory.   How do you do this?

I've been using the same home directory since ubuntu/kubuntu 9.04 and have now been experiencing some strange things.   For example, the size of windows are not remembered.   Also, I have problems with some settings in kde programs.   

I created a new user, and from this user, renamed my home to old_home.   Now I need a way to recreate "home" with the standard bare-bones files.   I thought this would be simple enough, but can't find anything on google that works!

---

### Post by dcstar on 2011-11-19
> **quickk said:**
> I would like to recreate a fresh home directory.   How do you do this?

I've been using the same home directory since ubuntu/kubuntu 9.04 and have now been experiencing some strange things.   For example, the size of windows are not remembered.   Also, I have problems with some settings in kde programs.   

I created a new user, and from this user, renamed my home to old_home.   Now I need a way to recreate "home" with the standard bare-bones files.   I thought this would be simple enough, but can't find anything on google that works!

Copy the new user home folder to the original name and then change the ownership to the old user:
```
sudo chown -r olduser /home/freshfolder
```
You can compare the credentials with the renamed folder you saved previously.

---

### Post by quickk on 2011-11-19
Thanks for the advice.  I finally figured out how to manually recreate the basic home folder structure.   All that was needed is to manually make my home directory and copy the contents of /etc/skel to it:

```
mkdir /home/newhome
cp -R /etc/skel/* /home/newhome
```

where "newhome" is actually the name of my original home directory (which I renamed to old_home).   It turns out that there are only three files in /etc/skel: .profile, .bashrc, and .bash_logout.

---

