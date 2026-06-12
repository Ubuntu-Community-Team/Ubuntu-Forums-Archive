---
title: "panel/dock help in Xubuntu"
date: 2011-05-16
forum: General Help
---

### Post by danbuter on 2011-05-16
I am using the bottom panel as a dock. It's actually working pretty well, with one exception. I added the file opener, but when I click it, it gives me a dragdown leading to docs, pics, etc., and then I have to click on open file. 

Is there a way to just click the file icon on the panel so that it will open thunar up to my home directory, the way it would if I used the desktop icon?

---

### Post by Toz on 2011-05-16
Just create a new launcher for Thunar and it will open in your home directory automatically when you click on it.

---

### Post by danbuter on 2011-05-16
The panel options do not allow for that. They only offer the Directory Menu, which gives me the directory tree I currently have and don't want.

---

### Post by gsmanners on 2011-05-16
You can drag application icons straight from Application Finder to your panel in Xfce 4.8. Just go to Accessories / Application Finder. Look in Accessories (or type Thunar into the search field). Then drag the Thunar icon to your panel.

---

### Post by danbuter on 2011-05-16
Got it! The program is labeled as File Manager and not Thunar, but that worked. Thanks a lot!

---

### Post by Toz on 2011-05-16
> **danbuter said:**
> The panel options do not allow for that. They only offer the Directory Menu, which gives me the directory tree I currently have and don't want.

Right-click the panel, select Panel->Add New Items. In the dialog that pops up, select Launcher then click the Add button (this will put a new launcher (button) on the panel. Close the Add New Items Dialog.

Right-click the new launcher button and choose Properties. Click on the Add a New Empty Item button. In the Name field, type Thunar and it will offer up two choices, select either one then click on Create.

Or drag and drop like in post #4.

---

