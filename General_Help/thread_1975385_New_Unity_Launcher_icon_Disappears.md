---
title: "New Unity Launcher icon Disappears"
date: 2012-05-07
forum: General Help
---

### Post by Quarkrad on 2012-05-07
Sorry - this is probably basic but I need help.  I can create a launcher on my 12.04 Desktop and can test it by double clicking on it.  As the aim is to have the new Desktop launcher always present in the Unity side launcher I drag it from the Desktop into the Unity launcher.  Great - it now appears as one of my icon set in the Unity launcher.  So I now have the icon sitting on my Desktop and in the Unity launcher.  When I delete the Desktop icon it also disappears from the Unity launcher.  How do I get the icon to be perminately fixed in the Unity launcher?  (note:  I create the new launcher window by typing **gnome-desktop-item-edit ~/Desktop/ --create-new**  in terminal).

---

### Post by hakermania on 2012-05-07
Hello :)
Copy your generated new launcher from your desktop to /usr/share/applications.
Then, search in dash for it, and drag it in your launcher. That's all.
For future reference, please read:[https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)

---

### Post by philinux on 2012-05-07
> **hakermania said:**
> Hello :)
Copy your generated new launcher from your desktop to /usr/share/applications.
Then, search in dash for it, and drag it in your launcher. That's all.
For future reference, please read:[https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)

Or copy it to  ~/.local/share/applications/

---

### Post by Quarkrad on 2012-05-07
Many thanks.

---

