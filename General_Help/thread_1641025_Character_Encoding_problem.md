---
title: "Character Encoding problem?"
date: 2010-12-08
forum: General Help
---

### Post by zigtor on 2010-12-08
[SIZE=3]When I try to open  /usr/bin/conky with "Text Editor"I receive this message?[/SIZE]

[I][SIZE=4][COLOR=Red]gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again.[/COLOR][/SIZE][/I]

[COLOR=Black][SIZE=3]*Anyone have a clue as to what I'm missing?*[/SIZE][/COLOR]

---

### Post by tredegar on 2010-12-08
I don't have conky installed, but as the file you are looking at is in **/usr/bin/** it is likely to be a **bin**ary file. This will not make any sense at all if you open it with a text editor.

If you want to see how the program was written, you need to look at the source code from which the binary was compiled. Your preferred search engine will help you here.

---

