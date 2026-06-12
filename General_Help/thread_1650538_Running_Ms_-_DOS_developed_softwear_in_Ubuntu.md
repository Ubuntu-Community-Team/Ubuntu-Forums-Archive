---
title: "Running Ms - DOS developed softwear in Ubuntu"
date: 2010-12-21
forum: General Help
---

### Post by carolina on 2010-12-21
I am interested in running a softwear program originally developed for Windows - MS - DOS called Time Wave Zero and was wondering if anyone had ever installed it within Ubuntu as well as their results . I am assuming one might have to use Wine but i haven't seen any actual references to the use of this program within a Linux application . 

Thanks

---

### Post by JC Cheloven on 2010-12-21
Just try, you haven't anything to loose except some of your time and some disk space (& this one is recoverable).

- Install wine ```
sudo apt-get install wine 
```

- Copy the installing .exe of your windows application somewhere (your home diectory is fine).

- Right-click on it and choose "open with wine" (...blah blah)

- Follow the installation process as if you were on windows

- Launch your newly installed program from Applications-Wine-Programs (... you'll find it over there)

If everything was fine, the program may work completely, or "to some degree". In the "configure wine" entry at the wine menu you can tell wine which windows version is to be emulated. Perhaps that can be of help.

Please let us know how was it :)

---

### Post by cwwilson721 on 2010-12-21
If wine doesn't work, and the application is actually DOS based, you might want to try DOSBox (install thru Software Center).

DOSBox lets me play some OLD games I had

---

### Post by carolina on 2010-12-21
> **cwwilson721 said:**
> If wine doesn't work, and the application is actually DOS based, you might want to try DOSBox (install thru Software Center).

DOSBox lets me play some OLD games I had



Ok , thanks to both you guys . I will see what i can do later ..

---

