---
title: "Removing KDE programs"
date: 2011-02-22
forum: General Help
---

### Post by skytreader on 2011-02-22
I installed KDE alongside GNOME. However, this resulted in my system having multiple programs for practically the same purpose (e.g., Kate vs Gedit). Is it safe for KDE to remove these programs?

---

### Post by skytreader on 2011-02-22
*bump*

---

### Post by Old *ix Geek on 2011-02-22
> **skytreader said:**
> I installed KDE alongside GNOME. However, this resulted in my system having multiple programs for practically the same purpose (e.g., Kate vs Gedit). Is it safe for KDE to remove these programs?It should be safe as long as you're just removing apps (like Kate) as opposed to system files.

If you do it via Synaptic you should be okay because it will tell you what it's going to remove before it does it. Check that list and if you see anything that you don't think is safe to remove, cancel the action.

---

### Post by skytreader on 2011-02-26
> **Old *ix Geek said:**
> It should be safe as long as you're just removing apps (like Kate) as opposed to system files.

If you do it via Synaptic you should be okay because it will tell you what it's going to remove before it does it. Check that list and if you see anything that you don't think is safe to remove, cancel the action.

Thanks for the advise. I've done it. Problem is, the menu items for the programs I removed (like Kate) remained at my Applications menu. How do I clean that up? They now display question mark icons and do nothing when clicked.

---

### Post by SeijiSensei on 2011-02-26
Run **kmenuedit** by typing its name in the Search box at the top of the main KDE menu.  If it's not there, you don't have the kdebase-workspace-* packages installed.

---

### Post by Old *ix Geek on 2011-02-26
> **skytreader said:**
> Thanks for the advise. I've done it.You're welcome. :)
> Problem is, the menu items for the programs I removed (like Kate) remained at my Applications menu. How do I clean that up? They now display question mark icons and do nothing when clicked.Right-click on your main menu button, then select **Menu Editor**. From there, just navigate through your menus to find the now-deleted applications, highlight each one, and either select **Delete** from the top menu or right-click and choose **Delete** from the menu that pops up.

---

