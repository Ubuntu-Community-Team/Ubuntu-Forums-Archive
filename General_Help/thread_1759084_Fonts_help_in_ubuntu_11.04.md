---
title: "Fonts help in ubuntu 11.04"
date: 2011-05-15
forum: General Help
---

### Post by ahsan08 on 2011-05-15
I tried to read 'The daily noyadiganta' but because of font problems I couldn't read the newspaper. NOW  what should I do?? In windows, there was an option that: download the font and paste it in- C/windows/fonts. BUT what about ubuntu 11.04???

Is there any 'Terminal Command' to see the current version of Ubuntu that I  am using??

---

### Post by Toz on 2011-05-15
> **ahsan08 said:**
> I tried to read 'The daily noyadiganta' but because of font problems I couldn't read the newspaper. NOW  what should I do?? In windows, there was an option that: download the font and paste it in- C/windows/fonts. BUT what about ubuntu 11.04???

If it doesn't already exist, create a .fonts folder in your home directory```
mkdir ~/.fonts
``` and put your fonts in that folder then regenerate the font cache```
fc-cache -v -f
```

> Is there any 'Terminal Command' to see the current version of Ubuntu that I  am using??
```
cat /etc/lsb-release
```

---

### Post by kostkon on 2011-05-15
Open your language support preferences (search for "language" in your dash) and add the bengali language; then restart your browser.

---

