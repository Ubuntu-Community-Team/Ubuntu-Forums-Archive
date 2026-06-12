---
title: "Crash when navigating to /usr/bin/ - broken links"
date: 2011-05-29
forum: General Help
---

### Post by frogotronic on 2011-05-29
Hello,

  Apparently I have some broken links in /usr/bin/ which causes nautilus to crash and restart.  If I navigate to /usr/bin/ using gnome-commander I can see the files, as well as using terminal.  

  How do I figure out which links are broken so that I can delete them?

  Would this work? [http://www.gentoo-wiki.info/HOWTO_Find_broken_links](http://www.gentoo-wiki.info/HOWTO_Find_broken_links)


- CH

---

### Post by WorMzy on 2011-05-29
```
ls -lL /usr/bin 2>/dev/null | grep "\?"
```

Works for me.

```
       -L, --dereference
              when showing file information for a symbolic link, show informa&#8208;
              tion  for  the file the link references rather than for the link
              itself
```

EDIT: If you want to generate a nicely formatted list (pipeable into rm), try this:
```
ls -lL /usr/bin 2>/dev/null | grep "\?" | sed "s/l[\?[:space:]*]*//g" | tr '\n' ' ' > ~/brokenlinks.txt
```

Instead of redirecting the output to a file, you can use backticks with rm:
```
sudo rm `ls -lL /usr/bin 2>/dev/null | grep "\?" | sed "s/l[\?[:space:]*]*//g" | tr '\n' ' '`
```

Make sure that the command works correctly for you before you try this though.

---

### Post by frogotronic on 2011-05-30
Okay, here's what I get:

ls -lL /usr/bin 2>/dev/null | grep "\?"
l????????? ? ?      ?              ?                ? ompi-checkpoint
l????????? ? ?      ?              ?                ? ompi-restart
l????????? ? ?      ?              ?                ? orte-checkpoint
l????????? ? ?      ?              ?                ? orte-restart
l????????? ? ?      ?              ?                ? trash4


And here's the screenshot from gnome-commander, in which I suspected the dead links (attached) with caution triangles.

So...I should just delete these files and I should be okay?

- CH

---

### Post by WorMzy on 2011-05-30
Well, I've never had the problem you're having, so I can't say for certain whether those links would cause it. But those are definitely dead links; so removing them won't do any harm.

---

