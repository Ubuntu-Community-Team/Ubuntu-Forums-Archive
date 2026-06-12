---
title: "Please I really need help! :("
date: 2011-12-08
forum: General Help
---

### Post by Silentkiller101197 on 2011-12-08
Hey guys I need help. I don't know where thread should I post this comment. I am new to Ubuntu and to the Forums. Sorry for my bad English. I am spanish.

Heres my problem:

I mistaken removed a startup item on the "Startup Applications", something like "Update User folder...". Now I want it back... but there is no revert option.

Could anyone be kindly enough to post the original content of that item? That is, the Name, the Command, and the Comment of it. Thanks you very much for your time and effort.

BTW I am using Ubuntu 11.04. I provided a screenshot below Incase you need. As you can see there's no "User Folder Update" entry.

---

### Post by An Sanct on 2011-12-08
The command for that is:

Name
```
User folders update
```
Command
```
xdg-user-dirs-gtk-update
```
comment
```
Update common folders names to match current locale
```

Add the command and you will have it back.

---

