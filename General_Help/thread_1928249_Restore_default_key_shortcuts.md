---
title: "Restore default key shortcuts"
date: 2012-02-19
forum: General Help
---

### Post by Chelidze on 2012-02-19
how do i Restore default key shortcuts ???

 i changed a couple of them and now i have trouble with it

---

### Post by duke.tim on 2012-02-19
Here is a list if you want to manually reset them :/

[https://help.ubuntu.com/community/KeyboardShortcuts](https://help.ubuntu.com/community/KeyboardShortcuts)

This question has been asked before and here are some suggestions

[http://askubuntu.com/questions/17626/how-can-i-restore-default-keyboard-shortcuts](http://askubuntu.com/questions/17626/how-can-i-restore-default-keyboard-shortcuts)

I'm really not sure if there is an easy way to reset the shortcuts

---

### Post by bibble235 on 2012-02-19
From [http://askubuntu.com/questions/17626/how-can-i-restore-default-keyboard-shortcuts](http://askubuntu.com/questions/17626/how-can-i-restore-default-keyboard-shortcuts)

cd /usr/share/gnome-control-center/keybindings
for entry in $(grep KeyListEntry * |cut -d'/' -f2- |cut -d'"' -f1); do
    echo $entry
    gconftool -u "/$entry"
done

---

