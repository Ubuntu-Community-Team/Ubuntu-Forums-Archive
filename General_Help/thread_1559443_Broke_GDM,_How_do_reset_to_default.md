---
title: "Broke GDM, How do reset to default"
date: 2010-08-23
forum: General Help
---

### Post by victor9098 on 2010-08-23
Hi All,

I was trying out a theme from gnome-look (elegant gnome) and it had an option to change my gdm theme. I used it, did not like the look, but when I uninstalled it said there was no back-up. Now my gdm looks like something from windows 95!

How can I reset it back to the original settings? I tried reinstalling GDM in synaptic but no change

Thanks

---

### Post by sisco311 on 2010-08-23
Add gnome-appearance-properties to GDM's autostart directory:
```
sudo ln -s /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow/
```

Log out. The appearance properties window should show up on the GDM screen. 

Configure GDM how you want, then close the window and log back in. 

When you're done and want the window to stop opening with GDM, run:

```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

---

### Post by victor9098 on 2010-08-23
Hi Sisco311,

That seems to have done the job. I think I understand what happened. I upgraded the murrine engine to the daily build which installed the beta versions of the new light themes... so the default ambiance/radiance are gone from my themes.

Thank you for your help!

---

### Post by sisco311 on 2010-08-23
> **victor9098 said:**
> 
Thank you for your help!

My pleasure!

---

