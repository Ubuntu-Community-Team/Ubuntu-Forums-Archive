---
title: "Removing Programs"
date: 2006-04-01
forum: General Help
---

### Post by Mau on 2006-04-01
Hi guys,
What is the best way to remove a program not created by apt-get?

For example, I've installed Apache, but I realize that I now need to get rid of it (I've installed it twice).  Do I just delete the folder?

Also, while we're at it, where do people normally install/build applications to?  I'm use to Windows/Mac with a Applications or Programs directory, so it's odd to install to /usr/bin or /user/local or /opt.

---

### Post by Barrakketh on 2006-04-01
[QUOTE=Mau]Hi guys,
What is the best way to remove a program not created by apt-get?

For example, I've installed Apache, but I realize that I now need to get rid of it (I've installed it twice).  Do I just delete the folder?[/quote]
Use apt-get remove <packagename>

> Also, while we're at it, where do people normally install/build applications to?  I'm use to Windows/Mac with a Applications or Programs directory, so it's odd to install to /usr/bin or /user/local or /opt.

It's best to only use packages, but it's probably a good idea to install them to /opt so you don't cause any potential conflicts with other installed packages.

---

### Post by Mau on 2006-04-01
I didn't install Apache via apt-get though, I built it using the make sequence.

---

### Post by Barrakketh on 2006-04-01
[QUOTE=Mau]I didn't install Apache via apt-get though, I built it using the make sequence.[/QUOTE]
You shouldn't have done it that way.  The package manager exists for a reason.  If you have the source around you can try "make uninstall".  Otherwise I'm inclined to say that you're SOL and would have to remove it manually.

---

### Post by Rog131 on 2006-04-02
When building from sources use checkinstall. Checkinstall — generate packages by tracking installation scripts. Homepage: [http://asic-linux.com.mx/~izto/checkinstall/](http://asic-linux.com.mx/~izto/checkinstall/)

Checkinstall 1.5.3 is in the repositories.

---

