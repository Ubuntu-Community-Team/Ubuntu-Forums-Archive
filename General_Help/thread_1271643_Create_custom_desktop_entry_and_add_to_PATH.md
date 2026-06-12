---
title: "Create custom desktop entry and add to PATH"
date: 2009-09-21
forum: General Help
---

### Post by fanis on 2009-09-21
Hello everyone.

I downloaded eclipse for php developers for ubuntu 9.04 64.
I extracted it to ~/eclipse and it works fine. To run it I need to go to the folder and run ./eclipse 

What I want to do is to add it to the path so i can run it from anywhere by typing eclipse and also to create a custom entry for the menu. I know those are simple questions, but I don't wanna mess it up, so any help would be appreciated. Thanks in advance :)

---

### Post by nikhilk on 2009-09-21
> **fanis said:**
> What I want to do is to add it to the path so i can run it from anywhere by typing eclipse and also to create a custom entry for the menu. I know those are simple questions, but I don't wanna mess it up, so any help would be appreciated. Thanks in advance :)

Add the following line in your ~/.bashrc file
```
export PATH="~/eclipse:$PATH"
```
and then after saving the file run
```
source ~/.bashrc
```

Eclipse should now be in your PATH and you should be able to run it from any directory.

---

### Post by geirha on 2009-09-21
Add the following line to the end of ~/.bashrc (gedit ~/.bashrc)
```
export PATH=$HOME/eclipse:$PATH
```

Log out and back in, and you should now be able to type just "eclipse" to start it. Confirm that the following prints the right path: ```
type eclipse
```

---

### Post by fanis on 2009-09-21
Thanks! It's good to know how to add something to $PATH after all this time! What about the menu entry? When I installed eclipse from the repositories it created an entry eclipse under the category programming. That's what I am trying to do. But I can't quite figure what to write on the e.g. eclipse.desktop file

---

### Post by fanis on 2009-09-21
Bump for edit. Day was crazy at work and I accindentaly posted half the sentence,, :lolflag:

---

### Post by geirha on 2009-09-22
> **fanis said:**
> Thanks! It's good to know how to add something to $PATH after all this time! What about the menu entry? When I installed eclipse from the repositories it created an entry eclipse under the category programming. That's what I am trying to do. But I can't quite figure what to write on the e.g. eclipse.desktop file

What does the Command for that menu-entry say? To find out, either edit it from alacarte, or «grep "Exec=" /usr/share/applications/eclipse.desktop»

If it has the full path (/usr/bin/eclipse), you'll need to change it, if it has just «eclipse», it should use the first eclipse it finds in $PATH (whichever is reported by the type command).

Actually, in either case, the following should ensure that that menu-entry executes your custom install of eclipse:

```
sed "s#Exec=.*#Exec=$HOME/eclipse/eclipse#" /usr/share/applications/eclipse.desktop > ~/.local/share/applications/eclipse.desktop
```

If a .desktop file with the same name is found in both ~/.local/share/applications/ and /usr/share/applications/, the one under your home directory will be the one that actually gets used.

---

### Post by andrew.46 on 2009-09-23
Hi fanis,

If you are not happy to move your files to /usr/local/bin perhaps you could create your own bin directory in $HOME/bin, add this to your path and put your eclipse files there. This would be a little tidier and a little more traditional as well...

Andrew

---

