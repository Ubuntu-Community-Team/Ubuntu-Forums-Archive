---
title: "How to login in tt1, tt2 etx"
date: 2010-05-10
forum: General Help
---

### Post by -_-' on 2010-05-10
Hello,

When I push the buttons Ctrl+Alt+F1 I come into a terminal, tt1.
Before I can use this terminal I've to login. But I can't login with my username and password. The problem is the space in my username, I think. My username is
 'A*** W*****' (I use the * to hide my real name on this forum, but ofcourse, these are normal characters.) 

Who can help me?

---

### Post by Rhubarb on 2010-05-10
While I can't be certain, I'm thinking it should act similar to the way directories or filenames with a space are addressable.

So, to login, try typing in the following for your user name:
```
A***\ W*****
```

Notice the "**\**" just before the space.
Then with any luck it'll prompt you for your password afterwards.

---

### Post by amsterdamharu on 2010-05-10
Are you sure there is a space in the user name? The name displayed in the gui login (graphic login) is not the user name but the full name.

In the gui choose console and type whoami that will give you your user name. The \ is an escape character for spaces, quotes and such so if your user name really has a space you can use that. For example:

my user=my\ user

---

### Post by -_-' on 2010-05-10
Thank you, it worked out!

---

