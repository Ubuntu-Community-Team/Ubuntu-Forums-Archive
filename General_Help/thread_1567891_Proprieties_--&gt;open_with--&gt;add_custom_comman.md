---
title: "Proprieties --&gt;open with--&gt;add custom command"
date: 2010-09-04
forum: General Help
---

### Post by frs89 on 2010-09-04
A time ago I add a custom command to open .C files with gvim trough 'Proprieties -->open with-->add custom command '. There's any way to see those commands? because I've forgotten what options I used.
Thanks.

---

### Post by akoskm on 2010-09-04
> **frs89 said:**
> A time ago I add a custom command to open .C files with gvim trough 'Proprieties -->open with-->add custom command '. There's any way to see those commands? because I've forgotten what options I used.
Thanks.

In the* Open With* tab click to *Add* and expand the *Use a custom command*.
You can type there any command what you can use in the Terminal without specifying the complete path - how to see these commands, just hit 2x<TAB> and it will list you the possible commands, 2252 on my laptop.
Anyway, If you now the correct path to it, navigate to there with *Browse*.

---

### Post by frs89 on 2010-09-04
> **akoskm said:**
> In the* Open With* tab click to *Add* and expand the *Use a custom command*.
You can type there any command what you can use in the Terminal without specifying the complete path - how to see these commands, just hit 2x<TAB> and it will list you the possible commands, 2252 on my laptop.
Anyway, If you now the correct path to it, navigate to there with *Browse*.

That wasn't my question, sorry. I've added a custom command a time a ago. I can still choose this command from the menu, it's the selected in the image below.

[IMG]http://img36.imageshack.us/img36/7802/screenshot1ot.png[/IMG]

And I want to unfold the command that I've written because I don't remember it.

---

### Post by sam_scott89 on 2010-09-04
I think there's two options here:

1.) Install ubuntu-tweak  (very useful little program for this kind of task)

Then go to the section "File Type Manager" and you can change it there.

OR

2.) Go to ~/.local/share/applications/
This has a list of launchers, one of which should be the one you are looking for. I'm not sure if this will have a sensible name, but possibly something like userapp-gvim-___.desktop

If you can't find it, try looking in the file mimeapps.list
There should be an entry telling you what association has been made.

Hope that helps,

Sam

---

### Post by frs89 on 2010-09-04
> **sam_scott89 said:**
> I think there's two options here:

1.) Install ubuntu-tweak  (very useful little program for this kind of task)

Then go to the section "File Type Manager" and you can change it there.

OR

2.) Go to ~/.local/share/applications/
This has a list of launchers, one of which should be the one you are looking for. I'm not sure if this will have a sensible name, but possibly something like userapp-gvim-___.desktop

If you can't find it, try looking in the file mimeapps.list
There should be an entry telling you what association has been made.

Hope that helps,

Sam

That really help. Thank you!

---

