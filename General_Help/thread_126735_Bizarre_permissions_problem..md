---
title: "Bizarre permissions problem."
date: 2006-02-07
forum: General Help
---

### Post by Snoopy2052 on 2006-02-07
Recently, I moved /home onto a different partition from the rest of Ubuntu. Since then, until last night, straight after login, Gnome berated me, saying that it had problems saving my settings, and that the $/home/.dmrc file ought to be owned by me and have 644 permissions. This confused me, as Gnome seemed to be saving my settings absolutely fine, and all .dmrc contained was 

[Desktop]
Session=default

which was the same as other directories I had made for users added after the great partition shift. More strangely, while the contents of .dmrc were the same, their copies had 600 permissions. Eventually I found a way to get the error message to go away -- change my home directory from 770 permissions to 700. 

Why should this make such a difference?

Yours confusedly,
Snoopy

---

### Post by earobinson on 2006-02-07
from the man page > 0400    Allow read by owner.
           0200    Allow write by owner.
           0100    For files, allow execution by owner.  For directories,
                   allow the owner to search in the directory.
           0040    Allow read by group members.
           0020    Allow write by group members.
           0010    For files, allow execution by group members.  For directo-
                   ries, allow group members to search in the directory.
           0004    Allow read by others.
           0002    Allow write by others.
           0001    For files, allow execution by others.  For direc

I guess the problem gnome had is it dident like the fact that people in your group could alter your home!

**Disclamer:** Only a guess!

---

### Post by Snoopy2052 on 2006-02-07
Oh, I know what the permission numbers mean, but it was weird that Gnome was shouting at me that it couldn't save my settings, but restricting access to home stopped it shouting that.

---

### Post by earobinson on 2006-02-07
Again my guess is that gnome thinks its risky to save your settings if the group can edit them.

Numbers up there to make it more easy for other people to read the post.

---

### Post by Snoopy2052 on 2006-02-07
I hadn't thought about it quite that way. It seemed to me to be complaining that it **couldn't** save my settings, (when it clearly was) rather than it didn't want to.

Interesting.

Thanks!

---

