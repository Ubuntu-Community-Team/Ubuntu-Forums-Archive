---
title: "Gui Root text editor/gedit"
date: 2009-11-09
forum: General Help
---

### Post by Tony Ricena on 2009-11-09
If your a newbie to Ubuntu and can't break away from a gui especially when it comes to editing files in ubuntu, here is a little trick for you.. hope it helps.

Your gedit can easily be used as a root text editor.  All you have to do is open your edit menu by right clicking on your menu.  Navigate to Accessories > gedit.  Highlight gedit and click properties.  In the command entry just add gksu in front of gedit.  Thats it.  Now when you need to edit a file that root has ownership of, you just enter your su password and can edit and save the file.  

This is for us newbies.  I find the text editor to be confusing and clunky, so I use it this way and love it.  Thats all, enjoy :P

---

### Post by michy99 on 2009-11-09
Even better: Install the nautilus-gksu package and you can right click on a file and "Open as Administrator."

---

### Post by sisco311 on 2009-11-09
How about [nautilus-gksu]("apt://nautilus-gksu") (<- click to install, apturl link, see my signature). Log out and log back in. 

Open the file manager, navigate to the file you want to edit as root, right click and select *Open as administrator*.

Directories are files too. ;)

---

### Post by Giblet5 on 2009-11-09
> **sisco311 said:**
> Directories are files too. ;)

Can we come over and gedit your / directory? :D

```
Backspacebackspacebackspacebackspacebackspace

This is Giblet5's directory. Isn't it nice?AltFSAltFX
```

---

### Post by sisco311 on 2009-11-09
> **Giblet5 said:**
> Can we come over and gedit your / directory? :D

```
Backspacebackspacebackspacebackspacebackspace

This is Giblet5's directory. Isn't it nice?AltFSAltFX
```

you're always welcome.

i will send you the user name & public key to my ssh server in a PM.

just give me a moment to edit my sudoers file to allow you to edit directories with gedit. 

/offtopic

---

### Post by Giblet5 on 2009-11-09
> **sisco311 said:**
> you're always welcome.

That's real neighborly! ):P

---

