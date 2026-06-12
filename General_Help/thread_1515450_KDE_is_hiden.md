---
title: "KDE is hiden"
date: 2010-06-22
forum: General Help
---

### Post by adeee on 2010-06-22
guys i have upgrade ubunto 9 to 10.04 so that in log in section there is a KDE session appears. when i log on in KDE then it will came a new KDE screen with drive icon and setting icon also desktop icon.. unfortunately i click on there and these desktop screen disappear.. so how to do for come back KDE in right position.?

Now when i login in KDE it will show total dark screen. so help me...

---

### Post by dabl on 2010-06-22
Here are two things to try.

1. Boot Recovery Mode, choose "Drop to root prompt", then at the "#" prompt, issue ```
service kdm start
```

2. At the KDE greeter (the GUI login screen), click the menu and choose "console login".  Log in with your user name and password, then issue ```
startx
```

Post back with any errors that you see on screen.

---

### Post by adeee on 2010-06-26
> **dabl said:**
> Here are two things to try.

1. Boot Recovery Mode, choose "Drop to root prompt", then at the "#" prompt, issue ```
service kdm start
```2. At the KDE greeter (the GUI login screen), click the menu and choose "console login".  Log in with your user name and password, then issue ```
startx
```Post back with any errors that you see on screen.


Oh budy i tried to do the process you say..

first put command service kdm start
it replied unrecognized srevice..

then i wrote only kdm
it say kdm service not install.
i wrote apt-get install kdm
then it replied.
E: kdm service cannot be installed. 


so now what you say?

can you tell me about kubuntu cd installation?
i have kubuntu cd.
it will effect on ububntu?
and a question my window vista is demmaged and i install ubuntu with wubi.
so if i install windows then what effect come on ubuntu..

thanks for your response. ;)[-(

---

