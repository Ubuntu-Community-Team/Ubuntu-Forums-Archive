---
title: "Restoring orginal firefox path"
date: 2006-06-20
forum: General Help
---

### Post by Owdy on 2006-06-20
After some manual installation, Firefox starts from /opt/firefox. How do i restore orginal path /usr/lib/firefox?

---

### Post by xXx 0wn3d xXx on 2006-06-20
[QUOTE=Owdy]After some manual installation, Firefox starts from /opt/firefox. How do i restore orginal path /usr/lib/firefox?[/QUOTE]
Why would you want to change it's location ? If you can't launch it modify/create a launcher pointing to:
> /opt/firefox/firefox

---

### Post by Owdy on 2006-06-20
[quote=xXx 0wn3d xXx]Why would you want to change it's location ? If you can't launch it modify/create a launcher pointing to:[/quote]

Because i want to use that version what comes via package manager. That other is installed via mozilla site and got troubles with certain plugins etc.

---

### Post by Ramses de Norre on 2006-06-20
This will do the job: ```
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
sudo rm /usr/bin/mozilla-firefox
sudo dpkg-divert --rename --remove /usr/bin/mozilla-firefox
```

---

### Post by Owdy on 2006-06-20
Thanks Ramses de Norre! :D

---

