---
title: "gnome-terminal with clickable links"
date: 2009-08-12
forum: General Help
---

### Post by earthmeLon on 2009-08-12
I was trying to find out how to make gnome-terminal's links load in FF when they are left clicked.  I know that I can right click, or control click the links, but this isn't what I want to do.

I found a post: [here]("http://ubuntuforums.org/showthread.php?t=476723") but it didnt seem to work for me.  I installed urxvt/urxvt-unicode and created a new file ~/.Xdefaults with the suggested info:

```

URxvt*urlLauncher: firefox
URxvt*matcher.button: 1
URxvt*perl-ext-common: matcher

```


Any help with this or any other method to make links in gnome-terminal left-clickable would be greatly appreciated :D

---

### Post by quintopia on 2011-01-26
hello.  good choice switch to urxvt!  The correct content of .Xdefaults is:

```
URxvt.perl-ext-common: default,matcher
 URxvt.urlLauncher: firefox
 URxvt.matcher.button: 1
 URxvt.matcher.pattern.1: \\bwww\\.[\\w-]\\.[\\w./?&@#-\[\]]*[\\w/-]
```

just don't forget to "xrdb .Xdefaults" any time you change it!

(I apologize for no one answering this for months, but maybe this will help those in the future.)

---

