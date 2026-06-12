---
title: "Changing emacs color scheme."
date: 2010-06-21
forum: General Help
---

### Post by artursm on 2010-06-21
This question refers to emacs and the standard gnome-terminal in Ubuntu. When you start emacs in terminal mode "-nw", it uses the same color scheme as the terminal you're running it on. In my case, the terminal is "White on Black" and I find it's a great color scheme for programming. 

The thing is, I sometimes need to run emacs in a window because of a couple of features not available in terminal mode, but I don't really care for the standard white background you get. 

My questions is: How can I get emacs to use the white-text-on-black-background color scheme? 

It can be a command-line argument, a couple of lines in the .emacs file, or whatever else works.

[SIZE="1"]I'm running ubuntu 10.04, and emacs 2.3, in case it matters.[/SIZE]

---

### Post by artursm on 2010-06-21
Found it. I installed
```
sudo apt-get install emacs-goodies-el
```
then I added 
```
    (require 'color-theme)
    (color-theme-initialize)
    (color-theme-robin-hood)
```
to .emacs file.

---

