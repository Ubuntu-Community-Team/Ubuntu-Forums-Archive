---
title: "ROXterm Misbehavin'"
date: 2009-09-27
forum: General Help
---

### Post by uberg on 2009-09-27
Greetings Ubuntu fans,
    Today, my favorite terminal program, ROXterm, has started to misbehave in a very strange way.  Everytime I hit the 'a' character ROXterm launches a new window.  From the command line or even in Vim, my finger touches the 'a' key and here comes a new instance ROXterm.  And no 'a' gets to the screen or file that I am currently working on.  Very Strange.  I have plenty of other terminal programs to choose from.  ROXterm is the current end of a long string of default terminal programs for me.  I won't suffer unduly but I really liked ROXterm but it is rendered pretty much useless.  Any help would be greatly appreciated.

---

### Post by uberg on 2009-09-29
Hello,
    Thank you to anybody that might have pondered this question but were unable to come up with advice.  I have found out what was wrong if not how it went wrong.  I eventually found the file .config/roxterm.sourceforge.net/Shortcuts/Default in my home directory.  I further found that somehow the first line of the file was changed to:

```
File/New Window=a
```

    Further investigation lead me to the correct code for that line:

```
File/New Window = <Shift><Control>n
```

    I have no idea how that changed.  I certainly wasn't editing that file at the time (didn't know it existed) and don't know of anyway to change a shortcut on the fly like that in ROXterm.  Maybe I inadvertently hit some key combination that I am aware of (I was editing a html file in Vim in a Screen instance???)

    However I got there and the important thing is that I am able to use ROXterm again.

    Thanks again to anybody that might have scratched their head over this.

---

