---
title: "home page in firefox shows private files; can't change it"
date: 2010-07-01
forum: General Help
---

### Post by rolypolycat on 2010-07-01
Hello!
I have xfce on my machine, running lucid lynx. For some weird reason, I can't change my firefox home page. I've changed it to the same one time and again in preferences, but every time I open firefox, it shows all the files in my home directory, including hidden ones. I uncheck the "show hidden files box", change it again in "preferences", but it still does this. And the home page in "preferences" is set to the right page I want; firefox just won't go there when I start it up. 
I really don't want my home directory in plain view like that; how do I make firefox recognize my settings?

---

### Post by sisco311 on 2010-07-02
Hi!

Sounds like a permission issue. Did you run firefox with sudo? If so, then try to chown the config files:
```
sudo chown -R $USER ~/.mozilla
```

---

### Post by rolypolycat on 2010-07-04
Sorry, but that didn't change anything. When I click on the hidden folder, it says I have both read and write permissions, as does my group. Is this some sort of wonky bug, maybe?

---

