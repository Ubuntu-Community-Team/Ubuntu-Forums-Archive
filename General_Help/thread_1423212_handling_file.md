---
title: "handling file://"
date: 2010-03-06
forum: General Help
---

### Post by Eraemaajaervi on 2010-03-06
hi,
whenever i use nautilus to get the path of a file I use copy (ctrl+c), paste into the terminal and get a path like
file:///home/user/folder%20one/file%20two.txt
but i can't user any command with this path-format, so i first have to remove the "file:/" and replace all "%20" with "\ " which can get kinda annoying.
any way to fix this?

thanks

btw: copy 'n pasting into this text editor for instance gives me 
/home/user/folder one/file two.txt - just the way it should be

---

### Post by kaibob on 2010-03-06
> **Eraemaajaervi said:**
> hi,
whenever i use nautilus to get the path of a file I use copy (ctrl+c), paste into the terminal and get a path like
file:///home/user/folder%20one/file%20two.txt
but i can't user any command with this path-format, so i first have to remove the "file:/" and replace all "%20" with "\ " which can get kinda annoying.
any way to fix this?

thanks

btw: copy 'n pasting into this text editor for instance gives me 
/home/user/folder one/file two.txt - just the way it should be

I don't know a fix but there are two workarounds. When I copy a file from Nautilus and then right-click in a terminal window, two of the options are "Paste" and Paste Filenames". The first option works as you describe; the second option pastes the filename with path just as it is shown in Nautilus (plus single quotes). You can also get the correct filename with path by dragging the selected file into a terminal window.

---

### Post by Eraemaajaervi on 2010-03-06
wow, i have never accessed the right-click menu in the terminal before....

thanks for that =)
now menu-button + F will be my new friend

---

