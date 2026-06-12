---
title: "How to change the directory into which a program opens"
date: 2010-02-11
forum: General Help
---

### Post by Diminished on 2010-02-11
Hi all,

I'm working in R and would like to change where the program opens. Currently my default working directory is home/dave and I would like it to open into home/dave/R by default. I'm running mint with xfce.

Any thoughts?

Thank you.

---

### Post by patchwork on 2010-02-11
I'm sure there is an easier way, but you could always jam out a quick script like this (substitute your terminal program for xterm if you like):


```
#!/bin/bash

xterm |cd R
```Slap it on your Desktop, then make it executable using

```
sudo chmod +x ~dave/Desktop/script
```and click on it when you want to run the script.

As I said, there is probably a much simpler method, but this should work (though it's kind of kludgy)



EDIT:  OK, maybe I totally misread your question...
I take it you are asking for R to open into the specified folder?   If so, what I wrote above will not work.  Sorry about that.

---

### Post by HotForLinux on 2010-02-11
You can try the following:

1. Find out what is the command to launch the program.
Right-click the Application menu item on the panel and select the 'Edit Menus' option. In the Main Menu editor locate and right-click the item that launches R and select 'properties' to open its properties window. Copy the command to launch the program.

Let's say the command is /bin/program-r.

Now choose one of the following:

a) In the properties window, change the command for:
cd ~/R;/bin/program-r

b) Make a new launcher that executes:
cd ~/R;/bin/program-r
and place it in your desktop or panel.
The easiest way to do this will be to drag R's launcher from the menu and place it on your desktop (it will be a copy); right-click it to edit its properties and change the command to the same in (a).

c) Do the same in the panel instead of the desktop.

---

