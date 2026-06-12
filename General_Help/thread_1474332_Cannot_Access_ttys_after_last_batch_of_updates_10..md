---
title: "Cannot Access ttys after last batch of updates 10.04"
date: 2010-05-05
forum: General Help
---

### Post by beastrace91 on 2010-05-05
Howdy All,

So I just did the last batch of updates to my Kubuntu system and these included a kernel update - I manually install my nVidia drivers from the .run package and for some reason I can no longer access my tty logins from which I would reinstall the drivers from...

I press ctrl+alt+f1-4 and all I get is a frozen image of my X server - not a tty login. Any suggestions? I *really* want to play my games again

/sigh I guess I should know better after three years of using Ubuntu than to run kernel updates.

Help!
~Jeff

---

### Post by beastrace91 on 2010-05-06
Lesson learned - kernel updates are the anti christ on Ubuntu if you are using the non-repository nVidia drivers.

I ended up mangling my xorg.conf so the system booted into "low graphics mode" from there it let me use a tty for some reason.

God I can't wait for Mint 9 to come out so I don't have to deal with goofy things like this >.<

~Jeff

---

