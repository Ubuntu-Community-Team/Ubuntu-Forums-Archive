---
title: "I think I broke XFCE?"
date: 2010-01-19
forum: General Help
---

### Post by Tidbit on 2010-01-19
So I fell asleep with my computer running, and when I woke up I had 2 crash error messages.

The first one said that EnvyNG had closed unexpectedly, and the second one said there had been a major kernel error, and advised that my system may be unstable and that I should restart...

So I restarted....

Now I can only log into xterm... When I try to log into an XFCE session I get the loading screen, then my screen goes white, then it goes back to the loading screen, then it takes me back to the login screen...

Just before I fell asleep I had been trying to find any graphics drivers for my GeForce2 Ti... I had installed EnvyNG hoping it might find something, but it didn't, and I didn't make any installations or changes to anything. Then I left the Envy program open while I went to check some reference books, and instead ended up taking an unexpected nap...

Any ideas on how to fix this? I can still log into an xterminal session so at least I can still use my browser and access my files, I guess...

---

### Post by pmlxuser on 2010-01-19
try removing the last installed application with purge of course or reconfiguring X

if everything else fails why not try reinstalling xface

```

$sudo apt-get purge xubuntu-desktop && apt-get install xubuntu-desktop

```

---

### Post by Tidbit on 2010-01-19
Thanks for the help. Your advice didn't seem to work though.

I eventually just reformatted and installed plain old Ubuntu instead.

---

