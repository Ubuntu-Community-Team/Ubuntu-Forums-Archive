---
title: "Is there a shell command to close a program with dump?"
date: 2011-02-03
forum: General Help
---

### Post by ninjaaron on 2011-02-03
I'm running into some problems using pkill in my scripts. I'm using a program that needs to dump.

---

### Post by Brandon Williams on 2011-02-03
If you issue a signal that causes a dump (e.g. SIGABRT or SIGSEGV), then the program will dump, provided that the ulimit settings for the process allow the dump. You should make sure that you run "ulimit -c unlimited" before starting the program in order to ensure that it will dump core when it receives SIGABRT, rather than just exiting.

---

### Post by ninjaaron on 2011-02-03
Hmm...  it's not giving the result I want.

The program updates it's configuration file when it closes from the GUI, or with the ctrl+c command in the Terminal. When you terminate it, it doesn't do that. It also doesn't do that with the SEGV signal. I just tried using INT and QUIT, but they didn't close it at all (which is weird because INT is supposed to be the same as ctrl+c, right?)

Any other signals worth trying, or another way?

---

### Post by Brandon Williams on 2011-02-03
Yes, SIGINT is the same as Ctrl+c, so there should be no difference in how the program handles it.

Are you trying to get a core dump or a clean shutdown? According to your explanation, your program updates the configuration on a clean shutdown, but a clean shutdown will not general a core file. If you want both, you would have to somehow manage to issue the right signal just after the config gets updated during a clean shutdown, which seems like difficult timing.

Both SIGSEGV and SIGABRT should generate core files.

---

### Post by ninjaaron on 2011-02-03
No, I don't need a core dump. I believe I misunderstood what a core dump was. What I needed was a clean shutdown.

I've discovered that this is only a problem when the program is run with a user-defined configuration file, so it's probably a problem with the program and not with my commands. I've contacted the developer.

so "SOLVED", I guess. Thanks guys.

---

