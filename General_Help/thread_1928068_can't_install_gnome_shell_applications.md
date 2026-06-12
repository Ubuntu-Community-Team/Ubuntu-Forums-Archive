---
title: "can't install gnome shell applications"
date: 2012-02-19
forum: General Help
---

### Post by princeofnam on 2012-02-19
I don't see an install or download button? Has anyone else encountered this issue? 

[https://extensions.gnome.org/extension/70/window-icon-list/](https://extensions.gnome.org/extension/70/window-icon-list/)

---

### Post by kazztan0325 on 2012-02-19
Hi princeofnam,

I saw an message like below on the page which you mentioned.
*"You do not appear to have an up to date version of GNOME3. You won't be able to install extensions from here. See the about page for more information"*

This is because I am running XFCE session, though I may run GNOME3 session on my machine too.

Have you logged in GNOME3 session when you visited the site?

---

### Post by bluexrider on 2012-02-19
Extensions are installed using a plugin, included with GNOME, that  currently only works with Firefox. When it’s working, an extension’s  page has a large switch to enable and disable the extension. Flip the  switch, select *Install* in the confirmation dialog, and the extension almost immediately activates.

** How do I uninstall my extensions? **

  Unfortunately, there are some bugs in GNOME 3.2 that prevented uninstallation from working properly for some extensions. GNOME Shell 3.2.2.1 has fixed these problems. Make sure your system is fully updated if you are having issues uninstalling extensions. 
  If you do not have GNOME Shell 3.2.2.1 and may be unable to get it, or are unsure, you can uninstall the extension manually. Remove the extension's directory, and then restart the Shell. The extension should be stored under ~/.local/share/gnome-shell/extensions. Removing the directory won't be enough: you will need to restart the Shell to make sure the extension is completely uninstalled: open the run dialog with Alt+F2, and enter restart. 
** How do I update my extensions? **

  To update your extension to the latest version, unfortunately you have to uninstall and reinstall the extension. Due to bugs in GNOME 3.2, you may need to uninstall extensions manually. See [How do I uninstall extensions?]("https://extensions.gnome.org/about/#uninstall") for more information. GNOME 3.4 will include features that will make sure your extensions can be updated automatically for you.

---

