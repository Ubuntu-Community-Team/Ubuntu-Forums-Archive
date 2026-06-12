---
title: "Links not working"
date: 2010-02-13
forum: General Help
---

### Post by thameera on 2010-02-13
I'm using Ubuntu 9.10 in a gnome environment.

The links from external programs don't work anymore. For example, when I click on a link in Choqok or Akregator, it does nothing. Thought it's only for KDE apps, but seems it's same for any application. (eg: Links in About boxes in apps) 

Clicking on links does not give any error message, either.

I'm using Chrome as the default browser. Tried changing that to Firefox, but it wouldn't help.

Any suggestions?

---

### Post by ibuclaw on 2010-02-13
Try:
```
sudo update-alternatives --set x-www-browser /usr/bin/google-chrome
```

At least, that is what I *think* I did.

(edit):
To add google-chrome to the alternatives system:
```
sudo update-alternatives --install /usr/bin/x-www-browser x-www-browser /usr/bin/google-chrome 10
```
Then try the first command again.

Regards
Iain

---

### Post by thameera on 2010-02-14
@ibuclaw
Thanks for the reply! I followed your procedure exactly. But the problem remains same.
Can anybody help me?

---

