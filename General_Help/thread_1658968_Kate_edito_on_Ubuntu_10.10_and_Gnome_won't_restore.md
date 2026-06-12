---
title: "Kate edito on Ubuntu 10.10 and Gnome won't restore session"
date: 2011-01-03
forum: General Help
---

### Post by metalball on 2011-01-03
hey all,

i've just moved to Ubuntu from Win7, and i'm new to Ubuntu forums, so if this is not the place for my post, i'd love if someone moved it to the right place.

so i'm trying to find good editor to replace Notepad++,
and after playing around little bit it came down to Kate as the best replacement, but it has this annoying bug that driving me crazy.

Kate won't store my sessions, though in Settings->Configure Kate->Applications->Sessions
i've set Behavior on Application Starup to Load last-used session.

any ideas why is that? maybe Kate is not fully integrated into Gnome?
anyway, ideas are welcome!

thanx.

---

### Post by matt_symes on 2011-01-03
Hi

Have a look at this with gedit. Lists alot of the plugins for it (including session saver).

[http://grigio.org/pimp_my_gedit_was_textmate_linux](http://grigio.org/pimp_my_gedit_was_textmate_linux)

EDIT: There is also this link

[https://help.ubuntu.com/community/gedit](https://help.ubuntu.com/community/gedit)

Kind regards

---

### Post by Kirboosy on 2011-01-03
I think you are correct to say that it might be a Gnome/KDE issue.

You didn't like gEdit? I find gEdit very useful and its fully compatible with Gnome.

A command line editor is Vim. Just run from a Terminal (Applications -->Accessories --> Terminal)
```
sudo apt-get install vim
```Then to use the program run
```
vim /your/file/location
```A good example is lets say you have a file named MyScript.txt and it was stored in your Documents folder. 
```
vim /home/metaball/Documents/MyScript.txt
```IF you don't understand the file structure on your computer just open Places-->Computer-->File System and that will allow you to look through your computer the GUI way. 

It will take a little bit to get used to vim but I like it a lot. 

[Homepage for Vim]("http://www.vim.org/")

Hope that helps :)

---

### Post by metalball on 2011-01-03
yea, tried the Vim, it looks verry impressive, but its very complicated and not similar at all to NPP, and i'm looking for a "quick" replacement. Kate just felt right.

gedit seems powerfull too even without extensions, but looking for extensions that will complete the NPP functionality also takes time, but if i won't figure out the session saving issue soon, i think i'll give it another shot.

tried also jedit, heavy heavy heavy...
eclipse as editor, heavy heavy heavy
geany was very nice, maybe i'll try that again.

still, if anyone has solution for kate... i'd LOVE to hear it!

---

### Post by matt_symes on 2011-01-03
Hi

Have a look at this for saving Kate sessions. It's an old post so i don't know if it will work but...

[http://ubuntuforums.org/showthread.php?t=678404](http://ubuntuforums.org/showthread.php?t=678404)

Kind regards

---

### Post by metalball on 2011-01-03
nope, no luck. anyway,  i've found this page: [http://live.gnome.org/Gedit/Plugins]("http://live.gnome.org/Gedit/LineToolsPlugin")
and it concetrates pretty much every plugin i need, so i guess gedit it is!

---

