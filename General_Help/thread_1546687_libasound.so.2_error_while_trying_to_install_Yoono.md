---
title: "libasound.so.2 error while trying to install Yoono Desktop"
date: 2010-08-05
forum: General Help
---

### Post by kripplinger.home on 2010-08-05
Hi all, I've downloaded an application called Yoono Desktop directly from their site: [http://yoono.com/desktop_features.html](http://yoono.com/desktop_features.html). I saved the file to my home directory and extracted it there. It extracted 5 folders, 2 plain text documents (no readme) and an executable file called yoono-desktop.

When I try to install it, I double-click the executable file, nothing happens. So I opened a terminal and tried:
./yoono-desktop

Then I got this error message:

./yoono-desktop: error while loading shared libraries: libasound.so.2: cannot open shared object file: No such file or directory

This happens with other executable files as well except the file it can't open is not libasound.so.2. For example, I tried installing another app similar to Yoono, called Instantbird. When I try running that executable in the terminal I get this:

./instantbird-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

I'm relatively new to linux so any help would be appreciated.
Thanks!

---

