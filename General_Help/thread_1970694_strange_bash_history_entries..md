---
title: "strange bash_history entries."
date: 2012-05-01
forum: General Help
---

### Post by alxkls on 2012-05-01
Hi guys. I noticed today some strange things in my bash history. after some work over ssh i logged out yesterday and when i logged in today i had to replicate a command. and when i scrolled up i noticed some lines which obviously werent mine. most of them were echo's of "ls somedir/someotrherdir" most of which were directories that i had browsed to via mc. and all of those were after i had exited the ssh. so any idea what this might be? thanks!

---

### Post by alxkls on 2012-05-02
anyone????

---

### Post by codemaniac on 2012-05-02
Are you sure you have not run any application or something that remotely ssh your box and executes the echo or ls commands .
That might also be traced into your bash history .

Like i have a Java application that checks status of some files on remote unix box through ssh .

---

