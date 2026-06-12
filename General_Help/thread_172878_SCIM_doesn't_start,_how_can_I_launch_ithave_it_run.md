---
title: "SCIM doesn't start, how can I launch it/have it running on startup?"
date: 2006-05-09
forum: General Help
---

### Post by tsb on 2006-05-09
I can launch it from terminal, but it doesn't do anything.  The keyboard icon shows up but I can't change languages.  As soon as I close terminal it stops.  If I log in using English instead of my default Trad. Chinese it works fine.  How can I get it to work in Trad. Chinese?

---

### Post by tsb on 2006-05-09
bump

---

### Post by tsb on 2006-05-09
got it figured out

add a new file called ".xsession" in the home directory

paste: 

export XMODIFIERS=@im=scim
export GTK_IM_MODULE=scim
gnome-session

in the file and save it

Go to "System" -> "Perferences", and select "Sessions". In "Startup Programs", add the command "scim -d".

After a reboot/new login everything should be golden

;)

---

