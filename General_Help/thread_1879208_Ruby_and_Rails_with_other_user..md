---
title: "Ruby and Rails with other user."
date: 2011-11-11
forum: General Help
---

### Post by kswix on 2011-11-11
Hi!

I have some troubles with my ruby and rails command in ubuntu 11.04.

When I install ruby with a rails gem, it worked with only sudo. Why? If i create a new user, which is not in sudoers list, how I can use ruby and rails commands from him?

I've use rvm and have 'rvm' in my group list. I've added my user to group 'rvm', but for 'ruby -v' command I catch this exception: > The program 'ruby' is currently not installed.  To run 'ruby' please ask your administrator to install the package 'ruby'

Regards

---

### Post by kswix on 2011-11-11
bump!

---

### Post by kswix on 2011-11-16
So, I can easily start the ruby, rvm, cucumber, rails et.c. rvm-specific commands at my first user, but can't understand why other users get this:
```
user@comp:~$ ruby -v
The program 'ruby' is currently not installed.  To run 'ruby' please ask your administrator to install the package 'ruby'
```

---

