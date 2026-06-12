---
title: "possible to restart Xorg without logging out?"
date: 2010-03-20
forum: General Help
---

### Post by evencoil on 2010-03-20
Question is just the title...On my system Xorg seems to have some sort of memory leak and often times I have command-line programs running in the background that I don't want to stop.

---

### Post by roccivic on 2010-03-20
no

---

### Post by slakkie on 2010-03-20
Have a look at screen for those commands, or...

./start-my-script &
disown

and you can kill the term and the application will continue to run.

---

### Post by evencoil on 2010-03-22
oh...great, thanks!

I actually already use screen so that programs don't quit when I start them from an SSH login...should have realized there isn't a distinction on whether the login is SSH or physical...

---

