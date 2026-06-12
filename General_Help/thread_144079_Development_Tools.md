---
title: "Development Tools"
date: 2006-03-13
forum: General Help
---

### Post by karmon on 2006-03-13
i noticed that ubuntu 5.10 didnt have any development tools pre-installed. is there an efficient way for me to download all the development tools in one? or do i have to download each package individually?

---

### Post by 4dz0 on 2006-03-13
Check out the build-essential package

---

### Post by Bandit on 2006-03-13
sudo apt-get install build-essential

---

### Post by karmon on 2006-03-13
ok thanks, that worked, but still i feel like i am missing a bunch of packages. for example (non development tools related), i get an error when trying to open files with the .rpm or .deb extension, should this happen?

---

### Post by taurus on 2006-03-13
If you want to install .rpm, you first need to convert it to .deb with alien and then install it with dpkg...
```

sudo apt-get install alien
sudo alien <filename>.rpm
sudo dpkg -i <filename>.deb

```

---

### Post by karmon on 2006-03-13
one more question, well for now...

i was able to install SDL, but how would i install SDL_image?

---

