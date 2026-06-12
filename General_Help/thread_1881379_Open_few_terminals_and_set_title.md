---
title: "Open few terminals and set title"
date: 2011-11-15
forum: General Help
---

### Post by abratt on 2011-11-15
Hello,

I'm trying to create a script which should open few gnome-terminal windows with the few tabs.

My gnome-terminal does have 2 profiles (Default and My profile),
I've configured to load My profile automatically when  gnome-terminal is opened. My profile connects to remote server.

So my goal is to open gnome-terminal window with few tabs with different names (e.g. s1,s2,s3 ...). Below is the script which opens the terminal with windows and it also renames all title correctly, but at the same time terminal connects to the remote server (as configured in My profile) and after success connecting the titles rename tot he default name.

```

gnome-terminal --tab -t "s1" --tab -t "s2" --tab -t "s3" --tab -t "s4"

```

Could anyone advice me in this matter?

---

