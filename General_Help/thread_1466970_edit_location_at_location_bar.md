---
title: "edit location at location bar"
date: 2010-04-30
forum: General Help
---

### Post by creatxr on 2010-04-30
i found that 10.04 hasn't edit location icon at location bar of nautilus. how to get it? thanks

---

### Post by philinux on 2010-04-30
> **creatxr said:**
> i found that 10.04 cannot edit location at location bar of nautilus. how to get it? thanks

Nautilus location bar, bread crumbs vs text based.
Breadcrumbs is now the default. The button to switch between the two has been removed. Users can switch with ctrl+l and then esc to revert to breadcrumbs. To permenantly swith to text users have to use gconf-editor froma terminal. Note: gconf-editor has been removed from the menus.
apps>nautilus> preferences> always_use_location_entry.

Hope this helps.

---

### Post by creatxr on 2010-04-30
i think i didn't well explain what i need. i want to get a edit icon at location bar like 9.10. so i can switch between Breadcrumbs and location entry. in 9.10, when it switch to location entry, it will keep the location of Breadcrumbs

---

