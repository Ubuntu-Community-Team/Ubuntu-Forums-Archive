---
title: "Compress to rar or 7zip"
date: 2010-10-04
forum: General Help
---

### Post by João Oliveira on 2010-10-04
How can i Compress a file in ubuntu 10.04??

Sincerally
João oliveira

---

### Post by gandaran on 2010-10-04
install the rar and p7zip-full packages
to compress, right click the file and chose the format you want to compress

---

### Post by andrewthomas on 2010-10-04
Right-click on the file and select compress.  A menu will pop up with different available compressions

---

### Post by João Oliveira on 2010-10-04
> **andrewthomas said:**
> Right-click on the file and select compress.  A menu will pop up with different available compressions

I don't have that option... and when i go to ubunto software center it doesn't let me install anything it Appears something like this "This action will rquire the installation of unreliable packages"

---

### Post by gandaran on 2010-10-04
> **João Oliveira said:**
> I don't have that option... and when i go to ubunto software center it doesn't let me install anything it Appears something like this "This action will rquire the installation of unreliable packages"
use the command line to install
```
sudo apt-get install rar
```
if any errors post them.
after install you will have the rar and other options when you choose to compress from the right click menu.

---

### Post by lykeion on 2010-10-04
Maybe a sidenote, but if you don't specifically need to compress to rar there are better compression formats in linux.
I tested to compress a couple of files and folders (mostly text files and images)
[FONT=Courier New][SIZE=3]original size........179.9 kB
rar archive size......82.2 kB
tar.bz2 archive size..78.5 kB[/SIZE][/FONT]
Maybe not a huge difference (~2%) but for large archives that could be important.

---

