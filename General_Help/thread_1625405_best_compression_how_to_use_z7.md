---
title: "best compression how to use z7"
date: 2010-11-19
forum: General Help
---

### Post by ahso4271 on 2010-11-19
Hi
nullsoft installer brings down size to 130 MB, zip ~230MB the best i found so far .xz to 170mb.
Now how can i get it down to 130mb or even more? z7? How can i use that on 10.04? I need it working on MacOSX/Windows as well.
Thanks

---

### Post by patryk77 on 2010-11-29
Hey!

To add 7zip support, just install the p7zip package.

```
sudo apt-get install p7zip
```

You will have an option to use it with file-roller when you right-click on a file/folder and choose compress by selecting the .7z extension, or from the terminal, just read the man page:

```
man p7zip
```

Generally, I find .tar.bz2 to offer a decent compression rate (though .7z is slightly better) while being faster, but 7z is still useful for very large files.

Both formats should be compatible with OSX, and I know WinRAR supports .tar.bz2 on Windows.

---

