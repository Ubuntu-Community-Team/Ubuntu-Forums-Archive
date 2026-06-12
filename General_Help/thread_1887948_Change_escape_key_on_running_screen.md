---
title: "Change escape key on running screen"
date: 2011-11-28
forum: General Help
---

### Post by Tovam on 2011-11-28
Hello.
I use screen all the time, and often have the need to have different escape characters for different screens.
I know how to set the escape character while starting a new screen process, as an argument or in screenrc.
But is there a way to change the escape key in an *already running* screen? In other words, to change the escape key without having to interrupt the processes running in that screen?
Thanks.

---

### Post by Tovam on 2011-11-28
In retrospect, this was a stupid question.
Just detach and reattack with a different escape key.

---

### Post by peter4512 on 2012-01-19
This was actually helpful. I didn't know you could reattach to an existing screen and change the escape character.

For anyone else who might want to do this, you'd do something like the following:

Control-A d             # to detach the existing session
$ screen -x -e^Bb   # where Control-B is your new desired escape key

---

