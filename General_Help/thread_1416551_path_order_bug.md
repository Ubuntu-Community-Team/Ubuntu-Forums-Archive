---
title: "path order bug?"
date: 2010-02-26
forum: General Help
---

### Post by silencej on 2010-02-26
issue:
User-specified path could work only when added before the default path, i.e. PATH=UserPath:$PATH, but not when added in the end, i.e. PATH=$PATH:UserPath.

In my opinion, they should both work, with only the difference in searching order. Right?

operation:

I installed matlab, gmlive etc in ~/Software, and made symbolic links of their bin to ~/Software/bin, adding ~/Software/bin in PATH in ~/.bashrc file.
After i reboot, typing 'matlab' in terminal produces 'command not found'.
```
echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/opt/real/RealPlayer:/home/myusername/Software/bin
```

However, if i do the following:
```
export PATH=~/Softwares/bin/:$PATH;
$ echo $PATH
/home/myusername/Softwares/bin/:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/opt/real/RealPlayer:/home/myusername/Software/bin
$ gmlive
```
gmlive will start.

I am using bash.
$ bash --version
GNU bash, version 4.0.33(1)-release (i486-pc-linux-gnu)

and
$ uname -rs
Linux 2.6.31-19-generic

I don't know whether it is ubuntu specific. But ubuntu is the only linux distro i've used so i come here for help.

---

### Post by silencej on 2010-02-26
Sorry, Turns out to be that i mistyped 'Softwares' to 'Software'. Stupid me 8.|
But i can't find how to close or delete this thread.

---

