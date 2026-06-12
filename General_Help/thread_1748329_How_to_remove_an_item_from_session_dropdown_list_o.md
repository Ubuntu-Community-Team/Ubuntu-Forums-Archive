---
title: "How to remove an item from session dropdown list on the login screen?"
date: 2011-05-03
forum: General Help
---

### Post by etdsbastar on 2011-05-03
Dear Friends,

I want to remove a item in the login screen session list shown in the bottom.

I am using Natty and I want to use 'Ubuntu Classic' (though I am using it), but I want to remove the default 'Ubuntu' option including its files.

Please help. Thanks.

---

### Post by etdsbastar on 2011-05-03
is there anyone who can help me...

---

### Post by etdsbastar on 2011-05-04
please help...

---

### Post by etdsbastar on 2011-05-07
bump... pls help

---

### Post by grahammechanical on 2011-05-07
As I understand it, the login screen remembers the last used user interface. So, if you select Ubuntu classic, then the next time you login Ubuntu classic will be the default user interface.

Do you want to prevent other users from changing the default user interface? Is this the reason why you want to remove user interface options from the login screen?

Regards.

---

### Post by etdsbastar on 2011-05-07
I want to remove the item 'Ubuntu' completely with the files associated with it. My machine is a single user machine.

---

### Post by etdsbastar on 2011-05-15
bump...

---

### Post by serengeor on 2011-05-15
I can't believe that they even added this kind of crap into ubuntu.. Its even more buggy then the gnome3 installed on 11.04..

I guess for me the only solution is to switch to Kubuntu, even though I prefer gnome, because ubuntu can't work with gnome3, or older gnome correctly anymore..

---

### Post by marquinos on 2011-05-16
Remove files in /usr/share/xsessions ;)
Remember do as root, as:
sudo rm /usr/share/xsessions/file....
Best regards.

---

