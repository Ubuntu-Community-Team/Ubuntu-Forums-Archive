---
title: "Installing Inkscape"
date: 2010-06-18
forum: General Help
---

### Post by LeoVanRomunde on 2010-06-18
Today I installed Inkscape.
It is a program with the Ubuntu image in the synaptic package manager.

The Alt key did not function as described in the tutorial.
It took me some hours to find the solution:

1: edit ~/.config/inkscape/preferences.xml 
2: find **mapalt**
3: change the number from **1** to **4**.

Now the "Window"key can be used as Alt key.

When no Window key is available, you can use the number **2** to use the NumLock key instead of the Alt key.

It would be nice if the Ubuntu version installed already number **4** instead of **1**, since **1** does not work.

Success, Leo van Romunde

---

