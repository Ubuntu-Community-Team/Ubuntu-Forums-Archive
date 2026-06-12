---
title: "[server] Screen"
date: 2009-12-17
forum: General Help
---

### Post by Canha on 2009-12-17
Ubuntu Server 9.10:
So I heard there is an app called screen, that allows you put processes running behind and being able to watch those processes whenever you want.
For example, my source engine server, runs by typing ./steam commands, etc

How can I use "screen" to help me run it and still being able to do other stuff meanwhile?
Oh and also how can I make my steam server run when the OS starts?

Thanks in advance.

---

### Post by Canha on 2009-12-17
No bump feature.
Bump.

---

### Post by i.r.id10t on 2009-12-17
There are some good screen tutorials in google land, but briefly -

Login, start screen with the

screen

command.

Do something - start your steam server, etc. Then open a new screen session by pressing ctrl+a and then the c key.  You'll be back at a prompt.  Start something else.  Then start another session (3 now total) - ctrl+a and then c again.  Back to prompt.  Then cycle thru all your running sessions - ctrl+a and then the n key.  Rinse, repeat.  End up at your prompt session, type 

screen -d

And screen will go to the background - your stuff is still running.  Log out, fly to Detroit or wherever, log back in, start screen and reconnect to your existing sessions with 

screen -r

Then cycle thru them and be amazed as your processes continue to run!

---

### Post by Canha on 2009-12-17
> **i.r.id10t said:**
> There are some good screen tutorials in google land, but briefly -

Login, start screen with the

screen

command.

Do something - start your steam server, etc. Then open a new screen session by pressing ctrl+a and then the c key.  You'll be back at a prompt.  Start something else.  Then start another session (3 now total) - ctrl+a and then c again.  Back to prompt.  Then cycle thru all your running sessions - ctrl+a and then the n key.  Rinse, repeat.  End up at your prompt session, type 

screen -d

And screen will go to the background - your stuff is still running.  Log out, fly to Detroit or wherever, log back in, start screen and reconnect to your existing sessions with 

screen -r

Then cycle thru them and be amazed as your processes continue to run!

I love you sir.

---

