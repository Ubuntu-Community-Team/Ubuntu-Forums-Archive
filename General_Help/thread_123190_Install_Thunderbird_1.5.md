---
title: "Install Thunderbird 1.5"
date: 2006-01-29
forum: General Help
---

### Post by hove99 on 2006-01-29
How do I install Thunderbird 1.5 in Ubuntu Breezy easily?

Thanks :-)

---

### Post by kaamos on 2006-01-29
[https://wiki.ubuntu.com/ThunderbirdNewVersion](https://wiki.ubuntu.com/ThunderbirdNewVersion)

---

### Post by hove99 on 2006-01-29
Thanks! :-)

---

### Post by chadbst on 2006-01-29
Thanks for the link kaamos.  I ,too, was unable to install Thunderbird using Mozilla's directions on their site.  I have not yet tried the instructions for the link you have posted because I am at work.  However, those instructions make sense and I am sure that they will work.

---

### Post by Klingstedt on 2006-01-29
well i just installed Automatix and I could choose it from a list.. ^^ easy as hell.. ;)

---

### Post by darknightuk on 2006-01-30
[QUOTE=Klingstedt]well i just installed Automatix and I could choose it from a list.. ^^ easy as hell.. ;)[/QUOTE]think u might be a bit confused there tween firefox n thunderbird

---

### Post by chadbst on 2006-01-30
I have followed the directions to install Mozilla Thunderbird 1.5 from [https://wiki.ubuntu.com/ThunderbirdNewVersion?highlight=%28thunderbird%29](https://wiki.ubuntu.com/ThunderbirdNewVersion?highlight=%28thunderbird%29)

and I get the following error message when I type thunderbird at the terminal:
"error while loading shared libraries libstdc++.so.5 cannot open shared object file: no such file or directory"

Can someone please help me with this?

---

### Post by aysiu on 2006-01-30
Have you tried this? ```
sudo apt-get update
sudo apt-get install libstdc++5
```

---

### Post by chadbst on 2006-01-30
I have now that you mentioned it, and it works like a charm!

I am now able to type "thunderbird" from the terminal window and thunder 1.5 comes up.  Thank you so very much for your help

---

