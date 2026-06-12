---
title: "ive become root!"
date: 2009-08-18
forum: General Help
---

### Post by u_kapaley256 on 2009-08-18
hi,
I was messing around with the ubuntu gnome-panels and deleted the gnome-panel file and then killed the process
it made situations bad for me with the window borders disappearing and alt+f2 launcher not available
so i restored it and restarted the system
now i login as root and have to change as 'su wolverine'
what should i do?
Thanks in advance

---

### Post by michy99 on 2009-08-18
Can you not log in as wolverine? What happens if you try?

---

### Post by HiImTye on 2009-08-18
for future reference, to remove gnome-panel do the following:

system tools > configuration editor
navigate on the left to /desktop/gnome/session/required_components_list
remove 'panel'
(note: do not remove 'gnome-panel' from /desktop/gnome/session/required_components/panel)
to reverse it, simply add 'panel' back to the list

---

