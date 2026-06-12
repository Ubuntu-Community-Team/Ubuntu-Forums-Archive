---
title: "Downloading GoogleEarth using 8.04"
date: 2010-03-16
forum: General Help
---

### Post by atravnic on 2010-03-16
Hi all -- Downloaded GoogleEarth and now don't know how to proceed. It's on my desktop, and when I click on it (it's a Linux binary file) it says it can't open a .bin file and wants to know what other application I'd like to use, and so would I. Can anyone give me detailed instructions on how to make it work. Thank you!  ...Fred

---

### Post by wojox on 2010-03-16
You need to open your terminal and:

```
cd Desktop
```

```
chmod +x Google_Earth_CZXD.bin
```

```
 ./Google_Earth_CZXD.bin
```

Substitute Google_Earth_CZXD.bin for what ever the file is called.

---

### Post by dcstar on 2010-03-16
> **atravnic said:**
> Hi all -- Downloaded GoogleEarth and now don't know how to proceed. It's on my desktop, and when I click on it (it's a Linux binary file) it says it can't open a .bin file and wants to know what other application I'd like to use, and so would I. Can anyone give me detailed instructions on how to make it work. Thank you!  ...Fred

Use the **googleearth-package** package to allow you to make your own .deb from the latest version:

```
make-googleearth-package
```

---

### Post by atravnic on 2010-03-17
Thanks, but not sure how to do that. So I tried 'terminal' and here's what I got:
atravnic@atravnic-laptop:~$ make googleearth package
make: *** No rule to make target `googleearth'.  Stop.
Obviously that ain't workin'.


> **dcstar said:**
> Use the **googleearth-package** package to allow you to make your own .deb from the latest version:

```
make-googleearth-package
```

---

### Post by atravnic on 2010-03-17
Not sure what went wrong, but here is what I got:
atravnic@atravnic-laptop:~$ cd desktop
bash: cd: desktop: No such file or directory
atravnic@atravnic-laptop:~$ chmod +x googleearth.bin
chmod: cannot access `googleearth.bin': No such file or directory
atravnic@atravnic-laptop:~$ ./googleearth.bin
bash: ./googleearth.bin: No such file or directory
atravnic@atravnic-laptop:~$
By now you've probably guessed I'm not a super techie. Please help.
Thanks    ...Fred



> **wojox said:**
> You need to open your terminal and:

```
cd Desktop
```

```
chmod +x Google_Earth_CZXD.bin
```

```
 ./Google_Earth_CZXD.bin
```

Substitute Google_Earth_CZXD.bin for what ever the file is called.

---

### Post by scouser73 on 2010-03-17
Follow the instructions on this link to install Google Earth: [[COLOR="Red"]**Tombuntu: How To Install Google Earth**[/COLOR]]("http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/")

---

### Post by dcstar on 2010-03-17
> **atravnic said:**
> Thanks, but not sure how to do that. So I tried 'terminal' and here's what I got:
atravnic@atravnic-laptop:~$ make googleearth package
make: *** No rule to make target `googleearth'.  Stop.
Obviously that ain't workin'.

Why did your use spaces instead of the correct command which was provided?

---

### Post by cranecreek on 2010-03-17
Reread what wojox said. Its:
```
cd Desktop
```
not
```
cd desktop
```

---

### Post by atravnic on 2010-03-17
> **scouser73 said:**
> Follow the instructions on this link to install Google Earth: [[COLOR="Red"]**Tombuntu: How To Install Google Earth**[/COLOR]]("http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/")

[SIZE="5"][SIZE="6"]

Thank you Scouser73 -- worked like a charm.  ...Fred[/SIZE][/SIZE]

---

