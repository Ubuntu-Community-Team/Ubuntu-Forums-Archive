---
title: "Error whiletrying to 'make' ideviceinstaller"
date: 2011-07-23
forum: General Help
---

### Post by greendaygal540 on 2011-07-23
After the config. stage and when i try to 'make' ideviceinstaller', I get the following error:
```


april@ubuntu:~/Desktop/ideviceinstaller-1.0.0$ make
make  all-recursive
make[1]: Entering directory `/home/april/Desktop/ideviceinstaller-1.0.0'
Making all in src
make[2]: Entering directory `/home/april/Desktop/ideviceinstaller-1.0.0/src'
  CCLD   ideviceinstaller
libtool: link: cannot find the library `/lib/x86_64-linux-gnu/libgcrypt.la' or unhandled argument `/lib/x86_64-linux-gnu/libgcrypt.la'
make[2]: *** [ideviceinstaller] Error 1
make[2]: Leaving directory `/home/april/Desktop/ideviceinstaller-1.0.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/april/Desktop/ideviceinstaller-1.0.0'
make: *** [all] Error 2
april@ubuntu:~/Desktop/ideviceinstaller-1.0.0$ 

```any thoughts? is there a package available for download containing the file that seems to be missing? Any and all help will be appreciated.
...this is my 3rd post in the forums in less than 48hrs, but we're a community, right? (=

---

### Post by greendaygal540 on 2011-07-24
/bump

---

