---
title: "share folder between user sessions"
date: 2012-01-23
forum: General Help
---

### Post by andres-bracho on 2012-01-23
After searching I coudn't find an answer...

In an Ubuntu 11.10 system I want to share one folder with three different user sessions, basically I want to save files in my session and make it available to my daugther session and another one to an xbmc session. How do I do that? Remember that I want to share a folder between sessions in the same PC/system, not in a different PC/system.

Thanks in advance for your help.

Regards.-

---

### Post by cortman on 2012-01-23
Easy enough.
First figure out what your user group is called. You can do this by opening a terminal and typing your username and "groups"-

```
groups cortman
```

The first one listed is probably the group for all users.
Next type

```
cd /
sudo mkdir shared_dir
sudo chown user_group_name shared_dir
```

In other words, if my group is called cortman, and the folder I create is called stuff, it would be 

```
cd /
sudo mkdir stuff
sudo chown cortman stuff
```

chown changes the ownership of the new folder from root to your user group.

---

### Post by andres-bracho on 2012-01-24
Thank you very much but when I type my username followed by the word "groups" it return my username with the phrase "order not found"... I'll try to use it using the GIU (changing a folder properties) and if it not work I coma back here again, if it works I'll change the prefix to [solved].

Thank you again.

---

### Post by andres-bracho on 2012-01-24
Ok, done, but the problem now is that the other two users are in different user groups and the new ubuntu 11.10 interfase for users don't let me change groups. Which command should I use to add them to the same group?

---

### Post by cortman on 2012-01-24
> **andres-bracho said:**
> Thank you very much but when I type my username followed by the word "groups" it return my username with the phrase "order not found"... I'll try to use it using the GIU (changing a folder properties) and if it not work I coma back here again, if it works I'll change the prefix to [solved].

Thank you again.

TYPO- Sorry! To find groups you're supposed to do

```
groups username
```

*facepalm.

> **andres-bracho said:**
> Ok, done, but the problem now is that the other two users are in different user groups and the new ubuntu 11.10 interfase for users don't let me change groups. Which command should I use to add them to the same group?

[Here's a link]("http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/") that outlines that procedure.

---

### Post by andres-bracho on 2012-01-24
Wow! thank you very much.

---

### Post by cortman on 2012-01-24
> **andres-bracho said:**
> Wow! thank you very much.

Glad it worked. Thanks for marking [SOLVED], and feel free to come with any more questions!

---

