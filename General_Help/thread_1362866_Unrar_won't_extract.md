---
title: "Unrar won't extract"
date: 2009-12-23
forum: General Help
---

### Post by DJ . on 2009-12-23
Installed unrar through symatic, but it won't extract. It says it was completed successfully but doesn't show up. Help?

---

### Post by jmore9 on 2009-12-23
You could try sudo apt-get install unrar and see what it says.  If installed iti will say so if not it will install or give an error i believe.

---

### Post by DJ . on 2009-12-24
> **jmore9 said:**
> You could try sudo apt-get install unrar and see what it says.  If installed iti will say so if not it will install or give an error i believe.
it is installed

---

### Post by taurus on 2009-12-24
Have you tried to extract it from a terminal and see what happens?  Assuming you have multiple files in ~/Desktop and one of them is filename.rar, open a terminal and run

Applications -> Accessories -> Terminal
```
cd ~/Desktop
unrar x filename.rar
```

---

### Post by 73ckn797 on 2009-12-24
Synaptic has "xarchiver":
```
Xarchiver is a Desktop Environment independent GTK+ 2 frontend for manipulating
7z, arj, bzip2, gzip, rar, tar, zip, and RPM files. It allows you to create
archives and add, extract, and delete files from them. Password protected
archives in the arj, 7z, rar, and zip formats are supported.

Xarchiver uses library package routines, if available. If you need even more
package formats, try xarchive which uses shell scripts.
```

---

