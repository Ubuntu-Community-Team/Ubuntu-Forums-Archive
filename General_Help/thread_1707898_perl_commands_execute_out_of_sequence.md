---
title: "perl commands execute out of sequence"
date: 2011-03-15
forum: General Help
---

### Post by motoperpetuo on 2011-03-15
firstly, sorry if this was supposed to go somewhere else, but i don't see how to start a thread under "development and programming."

i'm writing a perl script that extracts user account info from a large text file. some of the processing takes a while, so i want to include print statements to let the user know what's going on. i'm using this sort of pattern:
```

print "The script is doing X...";
(for loop A, which finishes in less than a second, here)
print "done.\n";

print "Now the script is doing Y...";
(for loop B, which takes 30 seconds or so to finish, here)
print "done.\n";

```
the crazy thing is that the message "Now the script is doing Y..." only appears after loop B finishes, along with the "done" part. the first part, with the loop that finishes quickly, works as expected.

this isn't preventing my script from working, it's just annoying. does anyone know why the print command executes after the loop in this case, even though it precedes the loop sequentially in the script? is there any way to force perl to print the message before the loop starts, so that the user knows what's going on while the loop executes?

---

