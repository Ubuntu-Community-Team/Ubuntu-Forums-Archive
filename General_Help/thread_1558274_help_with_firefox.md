---
title: "help with firefox"
date: 2010-08-22
forum: General Help
---

### Post by tal32123 on 2010-08-22
I recently installed some bad extensions on firefox and it doesnt work. So I tried Removing it and then Re-installing. But that didn't work. Any help would be appreciated.

---

### Post by earthpigg on 2010-08-22
> mv ~/.mozilla ~/.mozilla-backup

see if that fixes it for ya.

if you have firefox import bookmarks and point it to one of the files in ~/.mozilla-backup/firefox/random-letters-and-numbers.default/bookmarkbackups, you can get your old bookmarks back.

---

### Post by tal32123 on 2010-08-22
> **earthpigg said:**
> see if that fixes it for ya.

if you have firefox import bookmarks and point it to one of the files in ~/.mozilla-backup/firefox/random-letters-and-numbers.default/bookmarkbackups, you can get your old bookmarks back.

i dont know what im supposed to do with the quote and firefox doesnt work :(

---

### Post by ubun_two on 2010-08-22
Open terminal and type in the command that was quoted.  Then try opening Firefox.

---

### Post by tal32123 on 2010-08-22
> **ubun_two said:**
> Open terminal and type in the command that was quoted.  Then try opening Firefox.

tal@tal-desktop:~$ mv ~/.mozilla ~/.mozilla-backup
mv: cannot stat `/home/tal/.mozilla': No such file or directory
tal@tal-desktop:~$ 


thats what i get

---

### Post by J V on 2010-08-22
sudo chown tal:tal /home/tal
chmod 700 /home/tal

---

