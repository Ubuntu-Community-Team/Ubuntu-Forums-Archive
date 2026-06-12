---
title: "Change the umask on a per user/group basis?"
date: 2011-03-25
forum: General Help
---

### Post by spirit.986 on 2011-03-25
*I've decided to move this question into a new thread since i haven't received an answer for 3 days.* :(

This question was originaly posted here:
[URL="http://ubuntuforums.org/showthread.php?p=10585086#post10585086"]http://ubuntuforums.org/showthread.php?p=10585086#post10585086
[/URL]
----------------------------------------------------------------

I've already searched in google, however i wasn't able to find an answer that solves my problem... 

**How can i change the umask on a per user basis so that each user can have its own umask to fit his needs?**

For example:
I have four accounts on my system ex. 
[LIST]
[*]admin1 : admin, 
[*]admin2 : admin, 
[*]manager : stuff,
[*]user : user,
[/LIST]

-So now I want everything from the admin group to be by default set to 002 (so that every user that is in the admins group can have a full share (-rwx rwx r--) of everything that is created by the admins).

-Then the similar to the above managers shoud have 022 umask.

-And each of the regular users should have 002 or 022 or 077 it is up to the users choice.

I hope that i have provided enough info thorough the example.

Thanks in advance..

---

### Post by Ghost_Mazal on 2011-03-25
I don't know how to set a group umask. But for each user you need to edit his/her ~/.bashrc file and add

```
umask <nr>
```

at the bottom of the file.

The user will then have that umask everytime he/she logs in.

That's the only way I know. Maybe someone knows of a better way.

---

### Post by spirit.986 on 2011-03-25
Thank you Ghost_Mazal :)

this works for me! :D I will mark this thread as solved

[SIZE="3"]**TIP:**[/SIZE]
If anyone has this problem i just want you to know that for some reason the file **~/.bashrc** will not be shown in the terminal if you try to display it instantly by pressing the TAB key. For a moment i was thinking that the file does not exist on my pc untill i tried:
```
$sudo gedit ~/.bashrc
```

---

### Post by blind2314 on 2011-03-25
It won't show by using Bash auto-complete (tab) because it's a hidden file.
 
Just as an FYI.

---

### Post by Ghost_Mazal on 2011-03-25
> **spirit.986 said:**
> Thank you Ghost_Mazal :)

this works for me! :D I will mark this thread as solved

[SIZE="3"]**TIP:**[/SIZE]
If anyone has this problem i just want you to know that for some reason the file **~/.bashrc** will not be shown in the terminal if you try to display it instantly by pressing the TAB key. For a moment i was thinking that the file does not exist on my pc untill i tried:
```
$sudo gedit ~/.bashrc
```

That's because it's a hidden file. All files that start with a . means it's hidden. To see them in Nautilus for example you have to press ctrl-h. This shows hidden files.

---

