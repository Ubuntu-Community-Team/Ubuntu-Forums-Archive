---
title: "Installing packages in home directory"
date: 2006-06-28
forum: General Help
---

### Post by buttari on 2006-06-28
Hi all,
is it possible to install a .deb package in my home directory (or wherever I don't need root privileges)? To be more precise I need to do something that is equivalent to "make" but without doing "make install".
Thanks

alfredo

---

### Post by schilcha on 2006-06-28
[QUOTE=buttari] To be more precise I need to do something that is equivalent to "make" but without doing "make install".[/QUOTE]
If you aim at configure->make->make install, then try:
```

./configure --prefix=$HOME/local
make
make install

```
This will install the program in the subdirectory local of your home-dir instead of e.g. /usr/local, which is frequently the default install path. Instead of $HOME/local, choose any path you like and you're allowed to write to.

Good luck!

---

### Post by buttari on 2006-06-28
Yes I know how to do that with a source code but I wanted to do that with a .deb package. If I install a .deb package with 
```
dpkg -i package.deb
```
what usually happens is that binaries are installed in /usr/bin. I just want to avoid that  because I don't want to overwrite previous versions of my package. That's it.
Thanks anyway.

alfredo

---

### Post by schilcha on 2006-06-29
[QUOTE=buttari]... I wanted to do that with a .deb package. [/QUOTE]

ok, I think I got it now. You migth try:
```

dpkg -x package.deb $HOME/package

```
I guess installation-related scripts will not be executed. 

I've never tried that, but as far as I can tell from dpkg-deb's man-page, this should work
```

       --extract, -x, --vextract, -X
              Extracts the filesystem tree from a  package  archive  into  the
              specified directory.

              --vextract  (-X)  prints  a listing of the files extracted as it
              goes, while --extract (-x) is silent unless an error occurs.

              Note that extracting a package to the root  directory  will  not
              result  in  a  correct installation !  Use dpkg to install pack&#8208;
              ages.

              directory (but not its parents) will be created if necessary.

```

Good Luck!

---

