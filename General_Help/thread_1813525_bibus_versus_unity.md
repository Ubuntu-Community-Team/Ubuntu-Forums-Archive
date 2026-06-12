---
title: "bibus versus unity"
date: 2011-07-27
forum: General Help
---

### Post by vahaboglu on 2011-07-27
I recently installed Ubuntu 11.04 and trying to learn the new Unity environment. 
Bibus is a reference manager which I used with  great pleasure for sometime. It was perfect in terms of inserting and  formating references to openoffice-writer.
Now, with 11.04 Unity environment Bibus  can insert references to Libreoffice-writer but can not change reference  styles. Once I log out and re-enter with ubuntu-classic environment I  see that Bibus is working perfectly in Gnome desktop of 11.04.
In the Unity desktop I have to run Bibus as root to change styles and change reference formats.
Can anybody solve this problem? Why Bibus can not change styles and format references in Unity environment unless having root privileges?

---

### Post by 3Miro on 2011-07-27
You shouldn't use software as root unless you absolutely have to.

Open nautilus (file manager, you can just go to home) and check the files that you are trying to edit with Bibus. Right-click on them and check the preferences. Those files are probably owned by root and your default user doesn't have the "permission" to edit those files.

To fix this, you can open nautilus as root by opening a terminal (search for Terminal in the Unity menu) and then type:
```
gksudo nautilus
```
BE CAREFUL, in root mode you can damage your system. Find your files and you should be able to change their ownership to your default user and make sure they have the read/write permission for the user.

---

### Post by vahaboglu on 2011-07-28
Thank you 3M for this reply. Unfortunately, I do not think that this is simply an issue of privileges. In some way I am able to use Bibus as before (open as root, select the style, close and open again..). My question is not with Bibus but my question is about Unity. Why I can manage styles in Bibus on Gnome desktop (by logging with ubuntu classic) but can not manage styles in Unity desktop. If it was simply an issue of privileges the problem should have to continue in Gnome desktop as well.
 On the other hand, Bibus uses ~/.bibus/bibus.conf to select the current style. I am the owner of this file (no permission problem) but Bibus when loaded by Unity Launcher cannot modify this file. If I load Bibus by dbl click to /usr/share/bibus/bibus.py in nautilus the style editor is working just as in Gnome desktop.
 This problem might help me (if solved) to understand the Unity desktop.

---

