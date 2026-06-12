---
title: "autoclean doesnt work in bash script"
date: 2009-09-21
forum: General Help
---

### Post by J V on 2009-09-21
I wrote a small script to automatically clean up the pc (Involves deleting the FF cache, and running apt-get autoclean/autoremove, but I decided against autoremove after a thread involving the inadvertant removal of KDE teehee...)

The problem is, if I run "sudo ./script.sh" I get an "E: Invalid operation autoclean" error, if I run "sudo apt-get autoclean"  from the terminal rather than the script, it works fine... What's happening?

```
#!/bin/sh
apt-get autoclean 
rm -rf /home/*/.mozilla/firefox/*/Cache
```

On a side note, is there a simple way to call up a message box in bash? (Something like msgbox "title" "text" would be ideal...)

---

### Post by J V on 2009-09-21
bump

---

### Post by J V on 2009-09-21
resentfull bump

---

### Post by J V on 2009-09-21
wtb bump button so I don't have to spam my own threads :)

---

### Post by NoaHall on 2009-09-21
```
#! /bin/bash
sudo apt-get autoclean
rm -rf /home/*/.mozilla/firefox/*/Cache 
```

Works for me.
And the acceptable time to bump your thread is 24 hours.

---

### Post by J V on 2009-09-22
hmm, weird...

And sorry about the bumps...

---

### Post by NoaHall on 2009-09-22
You need sudo in your script.

---

### Post by J V on 2009-09-22
I thought if I ran the script as "gksudo ./script.sh" it would work...

oh well, either way its fine :)

---

