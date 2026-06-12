---
title: "a user which files owner permission can overwrite by anyone"
date: 2010-06-25
forum: General Help
---

### Post by InfernalAngel on 2010-06-25
I'm working on developing a web application ... you all know that under apache the user should be www-data so I've create a shell wrapper to let the server side script (php) can execute some root user function such as "chown". but then I need to change back all the files owner to it proper owner which should be took from "/home/[username]/public_html"
web folder.

but incase can't find the user name i need to give it a default username which can be removed later by that user ... which username that should be (nobody or www-data)

---

