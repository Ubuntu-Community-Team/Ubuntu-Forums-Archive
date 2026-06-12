---
title: "Good Burner program"
date: 2006-04-22
forum: General Help
---

### Post by morbid_bean on 2006-04-22
Dose anybody know of a good burner program for ubuntu?  And is there a burner program that came with the ubuntu cd that didnt install by defult? If so whats it called.

---

### Post by Ramses de Norre on 2006-04-22
I like k3b very much, it's in the repos.

---

### Post by morbid_bean on 2006-04-22
Explain to me what repos is exactly?....Resporites? if so how do i install it

---

### Post by Ramses de Norre on 2006-04-22
Packages in the repos are made and tested for ubuntu and easily to install through synaptic or apt.
You can open synaptic, search for the package and install it (search for k3b).
Or execute this in terminal: sudo apt-get install k3b
Do in terminal killall gnome-panel (or wait a minute or ten untill the panels refresh themself) and k3b will be in the applications > sound & video menu.

---

### Post by morbid_bean on 2006-04-22
i found it but it looks like its for KDE is it alright to use in GNOME???

---

### Post by xXx 0wn3d xXx on 2006-04-22
[QUOTE=morbid_bean]Explain to me what repos is exactly?....Resporites? if so how do i install it[/QUOTE]
Yes, he means the repositories. You should be able to install it from synaptic or by typing "sudo apt-get install k3b" in terminal. Don't use quote symbols.

---

### Post by Ramses de Norre on 2006-04-22
It's a kde app yes, but kde apps work fine in gnome and vice versa ;)

---

### Post by morbid_bean on 2006-04-22
now i have a problem....i try installing it using terminal   "sudo apt-get install k3b"
and i get a bunch of BS

"The following packages have unmet dependencies:
  k3d: Depends: atlas3-base but it is not going to be installed or
                refblas3 but it is not installable or
                libblas.so.3
       Depends: libglib1.2 (>= 1.2.0) but it is not installable
       Depends: libgtk1.2 (>= 1.2.10-4) but it is not installable
       Depends: libmagick++6c2 but it is not installable
       Depends: libsigc++-2.0-0c2 (>= 2.0.2) but it is not installable
       Depends: libsuperlu3 (>= 3.0) but it is not going to be installed
E: Broken packages"

---

### Post by Ramses de Norre on 2006-04-22
sudo gedit /etc/apt/sources.list
Delete all the # in front of lines starting with deb.
Then run ```
sudo apt-get update && sudo apt-get install -f && sudo apt-get install k3b
```

---

### Post by morbid_bean on 2006-04-22
well i got it downloading/installing it now...will take awhile due to my slow internet.   Thanks for the help:)

---

### Post by qpieus on 2006-04-22
Yep, I have to agree that k3b is very nice. From my windows days, I really like Nero. k3b is just as good as Nero. Yet another reason NOT to keep windows :cool:

---

