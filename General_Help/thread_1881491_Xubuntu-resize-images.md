---
title: "Xubuntu-resize-images"
date: 2011-11-15
forum: General Help
---

### Post by mike555 on 2011-11-15
If you want to be able to resize images to an email size (640) in Thunar ,open leafpad and paste this;

#!/bin/sh                                                                                                                     

mkdir -p ./Resized/$1

for file
    do
    if [ ! -e $file ]
        then
        continue
    fi
    toname="./Resized/"$1"/"$( echo $file | cut -f1 -d.)"_"$1".jpg"
    convert -geometry $1x$1 -quality 100 "${file}" "${toname}"
done

save it in your /home as " .resize " without the quotes , allow it to run as program in properties ...... then make a thunar custom action called "resize 640"  and the command "  /home/mike/.resize 640 %N " (changing mike for your user name) then set the appearance settings to "  *.jpg;*.JPG;*.jpeg;*.JPEG;*.png;*.PNG  "  and image files............

---

### Post by jnhollow on 2012-05-02
The script generates the 2 directories, but doesn't provide a resized image for me. The directory is empty.  I am on Xubuntu 12.04.

---

### Post by mike555 on 2012-05-02
make sure you have "imagemagick" installed, sorry I forgot to say that before.

---

### Post by jnhollow on 2012-05-02
That did it.  Thanks for the quick response.
Nautilus-image-converter works but it has way too many dependencies.

---

