---
title: "Can't apt-get install limewire"
date: 2009-10-09
forum: General Help
---

### Post by c0mput3r_n3rD on 2009-10-09
Hello,
I'm trying to install limewire on my machine, and when I type "sudo apt-get install limewire" I get a "Package not found" message.  When I googled apt-get install limewire it said that it was the correct command.  I know I could just go to the LimeWire website and download it from there, but just prefer the console so if any body knows why this is that would be great.

Thanks

---

### Post by mikewhatever on 2009-10-09
I don't think limewire is in the repositories. Perhaps a third party repository exists, that makes the command work, I don't know.

---

### Post by nick_nik on 2009-10-09
there is a deb package available

[http://www.limewire.com/download/](http://www.limewire.com/download/)

---

### Post by Anarci on 2009-10-09
Package not found means the package isn't in your current repos, you can check this using
```
apt-cache search limewire
```

---

### Post by ArcaVex on 2009-10-09
Could search for it in a package manager like synaptics. Or just go to the website and download the .deb file

---

### Post by steeleyuk on 2009-10-09
Frostwire is an alternative in the repo's.

---

### Post by c0mput3r_n3rD on 2009-10-09
Awesome guys thank you very much for all the help :)

---

