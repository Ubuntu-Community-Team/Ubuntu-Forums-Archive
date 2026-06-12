---
title: "Beware of Gnome Brave Patch"
date: 2009-07-21
forum: General Help
---

### Post by dannymichel on 2009-07-21
i followed what he said here. [http://www.gnome-look.org/content/show.php/gnome-brave+custom+extras?content=97196](http://www.gnome-look.org/content/show.php/gnome-brave+custom+extras?content=97196)
i changed the names of the files in the archive for download there to include '.sh' on the end of the file name. i opened the 'gnome-pat' file and changed '/usr/share/icons/gnome' to '/usr/share/icons/gnome-brave' i 'cd'd into the unarchived folder via 'terminal' i ran each new '.sh' file as in this example: 'sudo ./script.sh'' then i copied and pasted what he wrote: ```
cd /usr/share/applications
for f in *; do
original=`cat $f | grep -w "Icon=*" | tr "=" " " | tr "/" " "`
change=`echo ${original##* } > ./temp`
sed -i '/Icon=*/d' $f
echo "Icon=`cat ./temp`" >> $f
rm -f ./temp; done
```
into the terminal. i restarted the computer and all my launcher application icons were gone including firefox and many many more [http://www.imagebam.com/image/5e675242683057/](http://www.imagebam.com/image/5e675242683057/)
how can i reverse this without reinstalling ubuntu?

---

### Post by sisco311 on 2009-07-21
try:
```
dpkg -S /usr/share/applications/* | awk -F ":" '{print $1}' | uniq | grep -v "," > /tmp/pkg.tmp
```
```

sudo apt-get install --reinstall $(cat /tmp/pkg.tmp)
```
```

rm /tmp/pkg.tmp
```

EDIT:

You have to reinstall the applications listed in the menus.

Doing this manually is a PITA.

The first command lists the packages in a file. The second one reinstalls them and the last command removes the temporary file created by the first one.

HTH

---

### Post by dannymichel on 2009-07-21
thanks it seems to have worked 
```
danny@danny-desktop:~$ dpkg -S /usr/share/applications/* | awk -F ":" '{print $1}' | uniq | grep -v "," > /tmp/pkg.tmp
dpkg: /usr/share/applications/mimeinfo.cache not found.
danny@danny-desktop:~$ 

```ur a lifesaver man

---

### Post by sisco311 on 2009-07-21
mimeinfo.cache is not installed by any package, it's created by an application. Therefor the "dpkg ... not found" error. (Just ignore it.)

---

