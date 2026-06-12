---
title: "Shell sending commands to background and stopping them when not told to"
date: 2011-06-08
forum: General Help
---

### Post by ultraata on 2011-06-08
Has anyone found a solution?
This is very annoying - any process started in bash gets stopped after some time. For example:
test@sandbox:~$ firefox -no-remote
[1]+  Stopped                 firefox -no-remote
test@sandbox:~$ 

It gets stopped after some time by itself. And I can't use fg:

test@sandbox:~$ fg
firefox -no-remote

[1]+  Stopped                 firefox -no-remote
test@sandbox:~$ 

How do I make bash behave as usual? I mean it should move process to background only if i explicitly specify that (Ctrl+z, Ctrl+y or &).

---

### Post by ultraata on 2012-04-27
up

---

### Post by CharlesA on 2012-04-27
Moved to it's own thread.

The original thread can be found [here]("http://ubuntuforums.org/showthread.php?t=1705063").

---

### Post by efflandt on 2012-04-27
From what I can tell from a quick web search, you would not use -no-remote for the first firefox instance, just for subsequent instances using a different profile (since profiles in use are locked).  So I imagine you also need to use the -P switch to specify a different profile.

[http://kb.mozillazine.org/Opening_a_new_instance_of_your_Mozilla_application_with_another_profile](http://kb.mozillazine.org/Opening_a_new_instance_of_your_Mozilla_application_with_another_profile)

---

