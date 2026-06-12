---
title: "Keep losing title bars"
date: 2011-08-10
forum: General Help
---

### Post by yossarianlives78 on 2011-08-10
Hey everyone,

(first time posting) :)

I am curious if anyone has more information on the issue in unity where you will from time to time lose title bars, and have to restart the window decorator.

This thread is related to the issue at hand:
[http://ubuntuforums.org/showthread.php?t=1598884]("http://ubuntuforums.org/showthread.php?t=1598884")

I know about the workaround, which is to execute the following command:
gtk-window-decorator --replace

You can also execute it like so, making it so you don't need to keep the terminal window open:
nohup gtk-window-decorator --replace &

But I am curious if there has been any new information on this.  The issue happens often enough that it becomes a real annoyance.  In addition (on my system anyway), after a few bouts of having to run this, I start getting SIGSEV messages from the new window decorator process, and eventually I have to reboot.

Has anyone gotten closer to the actual cause, perhaps something that will stop it from happening in the first place?

Thanks guys,
Mike

---

