---
title: "Alt+Menus in programs vs Unity"
date: 2012-05-25
forum: General Help
---

### Post by ScottTParker on 2012-05-25
So I'm a big fan of using keyboard shortcuts and many years ago got used to doing quick keyboard shortcuts using the Alt sequences to access menu options (e.g Alt+f+o to open the File menu and then Open [yes I know that ctl+o also works but it's an easy example]).

While Unity has done away with many menus, many programs have not (like Libreoffice) but now, as soon as I tap 'Alt', it brings up the HUD instead of going to the program menus.  Is there any way to get around this so I can still navigate through program menus?  Ideally I would like to find a solution that doesn't kill the HUD either.

FYI, I'm currently using Precise.

---

### Post by raja.genupula on 2012-05-25
we have one solution that , if you choose Ubuntu-2D at the login screen as your session , then it will be as you desired . 

try that ,:)

---

### Post by ScottTParker on 2012-05-25
I tried using Unity 2D from the login screen (actually the option for me is Ubuntu 2D) and it didn't make any difference.  Tapping Alt still gives me the HUD.

Also, it seems as though even if I log in using the 3D environment (the option just says Ubuntu), running ```
echo $DESKTOP_SESSION
``` from gives me "2D" so it looks like it's falling back anyway.

---

### Post by philinux on 2012-05-25
> **ScottTParker said:**
> So I'm a big fan of using keyboard shortcuts and many years ago got used to doing quick keyboard shortcuts using the Alt sequences to access menu options (e.g Alt+f+o to open the File menu and then Open [yes I know that ctl+o also works but it's an easy example]).

While Unity has done away with many menus, many programs have not (like Libreoffice) but now, as soon as I tap 'Alt', it brings up the HUD instead of going to the program menus.  Is there any way to get around this so I can still navigate through program menus?  Ideally I would like to find a solution that doesn't kill the HUD either.

FYI, I'm currently using Precise.

You could change the huds alt shortcut to suit you using compizconfig settings manager.

---

### Post by ScottTParker on 2012-05-25
Ha, what a simple solution.  Thanks to philinux and raja.genupula for the help but I finally figured out that just holding the Alt button down while pressing the hot-key opens the appropriate menu (at least in Libreoffice) and then I can then let go of both and use the standard hot-key navigation.  

Not the way I'm used to operating, but it seems pretty easy to relearn.

---

