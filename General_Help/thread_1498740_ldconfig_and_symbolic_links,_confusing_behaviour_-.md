---
title: "ldconfig and symbolic links, confusing behaviour - libtiff.so.3"
date: 2010-06-01
forum: General Help
---

### Post by mr_guy99493 on 2010-06-01
Original problem started with this error message: 
```
./Scene3D: error while loading shared libraries: libtiff.so.3: cannot open shared object file: No such file or directory

```but i have libtiff.so.4 installed so i symbolic linked to it.
```
sudo ln -s /usr/lib/libtiff.so.4 /usr/local/lib/libtiff.so.3
```running ldconfig gives:```

ldconfig -v |grep libtiff

    libtiff.so.4 -> libtiff.so.3 (changed)
    libtiff.so.4 -> libtiff.so.4.3.2
    libtiffxx.so.0 -> libtiffxx.so.0.0.6
    libtiff.so.4 -> libtiff.so.4.3.2
```i dont know why it says libtiff.so.4->libtiff.so.3?? shouldnt the arrow point the other way?

checked /usr/local/lib, and there is a libtiff.so.4 file there now.. it wasnt before
```
 cd /usr/local/lib
ls -l libt*
lrwxrwxrwx 1 root root 21 2010-06-01 19:24 libtiff.so.3 -> /usr/lib/libtiff.so.4
lrwxrwxrwx 1 root root 12 2010-06-01 19:28 libtiff.so.4 -> libtiff.so.3

```version 4 is pointing back at version 3?

ldd Scene3D still shows libtiff.so.3 => not found. (it has multiple rows saying this {if that matters})

im very confused. any help will be appreciated

mr_guy99493

---

### Post by mr_guy99493 on 2010-06-01
using 64 bit karmic, and i think this is a 32 bit exec, but i have ia32-libs installed so im running out of ideas.

---

### Post by BoneKracker on 2010-06-01
Yes, I think your link should point the other way (but don't do anything yet, before you read all this).

When you link, it goes like this:
```
ln -s <from> <to>
```
Or you could think of it this way> "create a link <foo> to file <bar>"
Maybe you did that backward.  Lord knows I've done it many times.[B]
[Edit: No, the above is backward. Don't do it that way.][/B]

Now, on the actual problem.  When see something like that, where a binary executable is asking for a library that you only have a newer version of, it's a sign that the binary was compiled against the old version.  For it to work, it needs to be recompiled to link against the new version.

Unless you manually installed the package (outside of the apt package management system), then this should have been handled for you automatically.

If you installed the program normally, through the ubuntu package management system, then running an update and upgrade might fix this.  If it doesn't, then should search the forums to see if anybody else is having a similar problem, and you should probably submit a bug.  It's possible that there is a mismatch between the library version the source is linked to and the version specified by the package as a dependency.

In fact, that is a likely problem, since I think libtiff 4 was released recently, and it's linked to by butt-loads of applications.  Pretty good chance one or more of them screwed up the update.

Less likely: If you manually installed the program (outside of the ubuntu package management system) then you are responsible for installing its dependencies.  In this case, that means installing libtiff.so.3.  You should be able to search the ubuntu repository for the library (as a package) and install it.  I dont' use Ubuntu, but most package managers like to only have the latest version of a program, and it's necessary to use a special command to install more than one version of a library.  Again, you should only have to worry about that if you manually installed the program (i.e., you didn't use apt to install it).  If it's not possible to make it install both versions, then you may be able to configure the package manager to block libtiff.so.4 for now, which ought to cause it to fall back to installing libtiff.so.3 instead.
[B]
It would be helpful if somebody familiar with apt and Ubuntu's handling of libraries could chime in here.[/B]

---

### Post by mr_guy99493 on 2010-06-01
> **BoneKracker said:**
> Yes, the link should point the other way.  When you link, it goes like this:
```
ln -s <from> <to>
```or you could think of it this way
"create a link <foo> to file <bar>"
Maybe you did that backward.  Lord knows I've done it many times.

No, man says ln is ln <target> <linkname>, only ldconfig was pointing the other way. ls -l showed the correct link.

>  installing libtiff.so.3.  You should be able to search the ubuntu repository for the library (as a package) and install it.  I dont' use Ubuntu, but most package managers like to only have the latest version of a program, and it's necessary to use a special command to install more than one version of a library.  Again, you should only have to worry about that if you manually installed the program (i.e., you didn't use apt to install it). i didnt use apt to install it, its commercial software. so i searched and found the old package and installed the libraries manually. the program needed the i386 libs. it works now.

im still confused why ldconfig ignored what i told it, and made its own links, and why every other dependency issue i have had with this program could be solved with symlinking, but not this one.

---

### Post by mr_guy99493 on 2010-06-01
thanks for your help

mr_guy99493

---

### Post by BoneKracker on 2010-06-01
> **mr_guy99493 said:**
> No, man says ln is ln <target> <linkname>, only ldconfig was pointing the other way. ls -l showed the correct link.
Oh, man.... :oops:

Sorry, I am forever screwing that up.  I can't even remember my own mnemonics.  Just what you needed. :lol:

> **mr_guy99493 said:**
> i didnt use apt to install it, its commercial software. so i searched and found the old package and installed the libraries manually. the program needed the i386 libs. it works now.

im still confused why ldconfig ignored what i told it, and made its own links, I'm not familiar with Ubuntu's toolchain setup; the only thing that comes to mind is that you may have configuration files on your system (e.g. for binutils or ld) that influence its behavior by setting environment variables (e.g. LIBPATH), although I would expect any paths you provided explicitly to be honored.
> and why every other dependency issue i have had with this program could be solved with symlinking, but not this one.
If you're referring to creating a symlink to the version that's present and naming it the version that's required, I think that may be a matter of backward compatibility or ABI compability.  The only way you can really be sure is reading the release notes or examining the header files.

I do know that on my (non-Ubuntu source-based) systems, when I hastily upgraded libtiff a few weeks ago, my desktop system basically purged its bowels in my lap and I had to recompile dozens of packages.  But now that I look, it's a later version:
```
# ldconfig -v |grep libtiff
	libtiffxx.so.5 -> libtiffxx.so.5.0.2
	libtiff.so.5 -> libtiff.so.5.0.2

# ls -l /lib/libtiff*
-rw-r--r-- 1 root root 508910 May 21 19:08 libtiff.a
-rw-r--r-- 1 root root    942 May 23 10:21 libtiff.la
lrwxrwxrwx 1 root root     16 May 21 19:08 libtiff.so -> libtiff.so.5.0.2
lrwxrwxrwx 1 root root     16 May 21 19:08 libtiff.so.5 -> libtiff.so.5.0.2
-rwxr-xr-x 1 root root 418956 May 21 19:08 libtiff.so.5.0.2
-rw-r--r-- 1 root root   6122 May 21 19:08 libtiffxx.a
-rw-r--r-- 1 root root    955 May 23 10:21 libtiffxx.la
lrwxrwxrwx 1 root root     18 May 21 19:08 libtiffxx.so -> libtiffxx.so.5.0.2
lrwxrwxrwx 1 root root     18 May 21 19:08 libtiffxx.so.5 -> libtiffxx.so.5.0.2
-rwxr-xr-x 1 root root   9424 May 21 19:08 libtiffxx.so.5.0.2
```

I'm glad you got it working and I apologize for adding to the confusion and that I wasn't of more help.


[COLOR="White"].[/COLOR]

---

