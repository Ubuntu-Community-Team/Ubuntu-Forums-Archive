---
title: "Can't launch Firefox"
date: 2009-08-11
forum: General Help
---

### Post by Tribulation on 2009-08-11
A few days ago I decided to try Minefield 3.5. It was nice but some colors were wrong. I got tired of seeing purple people and pink and blue giraffes so I went back to using Firefox. Now I can't use that. When I click on my Firefox icon, it keeps bringing up Minefield. I've removed Minefield and when I try to launch Firefox I get the message "Failed to execute child process "firefox" (No such file or directory)". I've even un-installed and re-installed Firefox but no dice. I had to re-install Minefield just to get on here. Any ideas what the problem could be?

---

### Post by wojox on 2009-08-11
Open a terminal and type:
```
whereis firefox
```

See if it's still there. Where did you get Minefield from? Repo's Mozilla? What version Ubuntu are you using?

---

### Post by Tribulation on 2009-08-11
I got

```
/usr/bin/firefox /usr/lib/firefox /usr/lib64/firefox /usr/share/firefox
```

when I typed in whereis firefox. I just typed in apt-get install firefox-3.5 to get Minefield, I didn't even know it was going to be Minefield. I'm assuming it's from Ubunutu's repos as I haven't added mozilla's (they might already be in there by default, forgive my ignorance, I haven't done too much with repos at this point in time). I'm currently using Ubuntu 9.04.

EDIT: I solved the problem. I had been using apt-get remove firefox. I tried apt-get remove firefox-3.0 and then I re-installed firefox-3.0 and it's working fine now.

---

