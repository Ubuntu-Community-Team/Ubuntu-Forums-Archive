---
title: "Titlebars missing in all GTK applications"
date: 2010-03-02
forum: General Help
---

### Post by AnthIste on 2010-03-02
I actually have no idea what the cause of this problem could be, but all my GTK programs don't display a menubar O.o

For example, the main menu of gedit with File, Edit, Help etc is just not there. I usually keep the menu hidden in the terminal, but checking the 'Show Menubar' option doesnt bring it back. Rhythmbox as well. Theres just nothing.

Any takers?

---

### Post by jose_Afonso on 2010-03-02
try search an option for resolve this problem in gconf... i'm searching this...

---

### Post by AnthIste on 2010-03-02
> **jose_Afonso said:**
> try search an option for resolve this problem in gconf... i'm searching this...

By "I'm searching this", do you mean that you're experiencing the same problem or that you're simply searching for a solution? That would be nice of you :)

I think it might have been an update that broke it but I cant be sure. This is really retarded and doesnt seem to be a common problem so any help would be great :S

---

### Post by AnthIste on 2010-03-02
shameless bump

---

### Post by AnthIste on 2010-03-03
anyone?

---

### Post by drewsus on 2010-03-03
fyi i couldnt find a global option in gconfig-editor...

---

### Post by AnthIste on 2010-03-14
For anyone who might ever have this issue, the problem seems to be with gnome-globalmenu

> 
sudo apt-get remove --purge gnome-globalmenu*

did the trick

---

