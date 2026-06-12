---
title: "startup problem!!"
date: 2006-05-30
forum: General Help
---

### Post by mohoso on 2006-05-30
when i startup ubuntu, before its fully loaded, i am met with a !Warning! box that says

"Could not look up internet for ubuntu. This will prevent GNOME from working correctly. It may be possible to correct the problem by adding Ubuntu to the file /etc/hosts."

'Try Again' doesn't work so when i click 'Log in Anyway' an error box appears.

"An error occured while loading or saving configuration information for gnome_segv. Some of your configuration settings may not work properly."

At this stage it all stops working. I cant click 'OK' or 'Deatails'.

This happens even when i am connected to the internet!!
I don't understand.

Does anyone have any ideas what couold be done?

---

### Post by hw-tph on 2006-05-30
You can put your hostname on the localhost  (127.0.0.1) line in /etc/hosts, like I have done on my laptop (which has the hostname "devon"):
```
127.0.0.1               localhost.localdomain   localhost       devon
```

Håkan

---

### Post by jazzgossen on 2006-05-30
It seems like your hostname is "ubuntu" (the default), so you should put that instead of "devon" on the line posted by hw-tph.

And to actually do that, you could run "pico /etc/hosts" when in recovery mode.

---

