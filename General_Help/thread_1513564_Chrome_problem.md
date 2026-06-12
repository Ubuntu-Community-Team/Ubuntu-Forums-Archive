---
title: "Chrome problem"
date: 2010-06-19
forum: General Help
---

### Post by Odaym on 2010-06-19
I installed Chrome last night and it was working, today i cannot find the icon under Internet. I download again and try to install and i see that it already is installed, what's the problem? any help is appreciated, thank you!

---

### Post by waynemeat on 2010-06-19
This happened to me too. 

Try re-adding a launcher to the menu.

Right click the **Applications **menu (usually top left beside **Places** and **System**)
Select [B]Edit Menus
[/B]Select **Internet** from the Menus list
Click **New Item**

Enter the following:

Name: **Google Chrome**
Description: **Web Browser**
Command: **/opt/google/chrome/google-chrome %U**
Icon:** /usr/share/icons/hicolor/256x256/apps/google-chrome.png** (You need to click on the launcher picture and browse to where the icon is located).

Click **OK**
Click **Close**

It should now be back in your menu.

Hope this helps.

---

### Post by Odaym on 2010-06-19
thank you very much, it did :)

---

