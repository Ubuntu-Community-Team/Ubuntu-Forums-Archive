---
title: "Didn't finish installing Java, now has error...."
date: 2009-08-26
forum: General Help
---

### Post by hatecrewdeathroll on 2009-08-26
I was downloading and installing java (sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts) but when it got to the Agreement page, I couldn't go any further so I exited the terminal. Now if I try to run the same command or try to install using the package manager I get errors.

---

### Post by michy99 on 2009-08-26
When you get to the agreement page, use the tab key to select and then press enter.

What errors are you getting currently? One of these will probably fix it:```
sudo dpkg --configure -a
sudo apt-get install -f
```

---

### Post by hatecrewdeathroll on 2009-08-26
It worked! Thanks so much

---

