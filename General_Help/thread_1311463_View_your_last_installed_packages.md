---
title: "View your last installed packages?"
date: 2009-11-02
forum: General Help
---

### Post by viking_maniac on 2009-11-02
I've installed some development packages from the repos that I don't remember the exact name of. And I didn't install it in the terminal, I used the graphical package manager, in my case KPackageKit.

Are there any commands or logs that can show you the latest installs from the repository?

---

### Post by liquidbee on 2009-11-02
Not sure if it's still possible in Karmic but [COLOR=DimGray]Synaptic - File / History[/COLOR] should reveal the secret.

---

### Post by ajgreeny on 2009-11-02
You can also find all details in /var/log/apt, though there are usually a number of archives with huge text files, and it can take a long time to read through them.  There will probably be a small recent log file as well which you will need to open as root ```
gksudo gedit /var/log/apt/filename
```or ```
kdesu kate /var/log------
```in your case with kubuntu.

---

