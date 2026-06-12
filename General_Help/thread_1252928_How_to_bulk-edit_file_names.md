---
title: "How to bulk-edit file names?"
date: 2009-08-29
forum: General Help
---

### Post by jesuisbenjamin on 2009-08-29
Hello,

I'd like to know how to edit file names in bulk, let's say for example that i want to replace all spaces by an underscore?

Thanks! 
:)

---

### Post by geirha on 2009-08-29
The (p)rename command is useful for that. E.g.:
```
rename -n 'y/ /_/' *
```

The -n option means no action; it'll just print what it would've done. Replace -n with -v if it looks right.

See this for more examples of its use [http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal](http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal)

---

### Post by mali2297 on 2009-08-29
If you want to use a GUI tool, the file manager Thunar has a built-in bulk renamer.

---

### Post by kaibob on 2009-08-29
The rename utility is another option. Look at post 2 of the following thread to see what this utility can do.

[http://ubuntuforums.org/showthread.php?p=5210531](http://ubuntuforums.org/showthread.php?p=5210531)

EDIT: After posting, I saw geirha's posting, which I missed earlier. Sorry for the repetition. I'll leave the posting because the above thread supplements the link provided by geirha.

---

### Post by jesuisbenjamin on 2009-08-30
wow this is cool! thanks! But i think i'll go for the GUI :P

---

### Post by ad_267 on 2009-08-30
There's also PyRenamer which is a simple GTK GUI for doing this.

---

### Post by Copernicus1234 on 2009-08-30
Go for Thunar. Its awesome. Much faster than Nautilus and more beautiful. :)

---

