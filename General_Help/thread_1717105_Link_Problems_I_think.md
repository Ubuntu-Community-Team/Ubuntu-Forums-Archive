---
title: "Link Problems I think?"
date: 2011-03-29
forum: General Help
---

### Post by joelkhayad on 2011-03-29
ok so here is my problem: everytime i click on "downloads" or "documents" or "pictures" under places menu i end up opening vlc.

my version of ubuntu is 10.10 maverick, my laptop is sony vpcs111fm

need some help please

---

### Post by 3Miro on 2011-03-29
- Open Place -> Home
- Right-click on any folder and select "Open with other application"
- Scroll to "Open Folder" and check the "custom command", it should be nautilus
- You should check "remember" for those settings
- You may have to logout-login for the changes to take place

Let us know if this works.

---

### Post by joelkhayad on 2011-03-29
I've tried but its not working. even when i right click on a folder the vlc player still appears

---

### Post by ~Plue on 2011-03-29
> **joelkhayad said:**
> I've tried but its not working. even when i right click on a folder the vlc player still appears
right click a folder on the desktop, not from the places menu 
(if you dont have one, right click the desktop > create new folder)


/or another way to accomplish the same thing;
press alt+F2 to bring up the run dialog,
enter, *```
gedit .local/share/applications/mimeapps.list
```*then delete the line *'inode/directory=........' *and save the file

---

### Post by joelkhayad on 2011-03-29
your code works ~plue, thanks a lot you saved me a lot of time.

one last thing if you don't mind, i am having problems with my built-in microphone, i can't use it with my skype. any ideas on how to solve this?

---

### Post by ~Plue on 2011-03-29
> **joelkhayad said:**
> 
one last thing if you don't mind, i am having problems with my built-in microphone, i can't use it with my skype. any ideas on how to solve this?
tbh, nope. but it might help others to help you if you give more info about the device (type lspci in a terminal)

/i see that you have a separate thread for that issue. maybe it would be better to continue there

---

### Post by joelkhayad on 2011-03-30
hello

ok big problem again, the link probelm is back again, after watching movies using vlc, all the links under places link to vlc already.

what to do please?

---

### Post by newbuntuxx on 2011-03-30
Re-install VLC.

---

### Post by ~Plue on 2011-03-30
> **joelkhayad said:**
> hello

ok big problem again, the link probelm is back again, after watching movies using vlc, all the links under places link to vlc already.

what to do please?
just redo the procedure in post #2 or #4,

the issue usually arises when you open a directory with vlc (or any other application for that matter). gnome remembers the last application that was used for the file type ('folder' in this situation) and sets it as default.. its been a problem for quite some time now..

---

