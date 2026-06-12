---
title: "Creating an .sh file to copy lots of files in directories"
date: 2009-07-09
forum: General Help
---

### Post by themattbeballin on 2009-07-09
Hello, I am new to the forums but I am just learning how to make .sh files. and I am trying to get a bunch of files to copy through a .sh file.

Here is the code if any of you can help. ```
#!/bin/bash

echo "Are sure you want to copy these files? (y/n)"

read answer

if [ "$answer" = "y" ]; then
    mkdir ~/foldername
    cp -r *.* ~/foldername

if [ "$answer" = "n" ]; then
    exit
```

This is also for an install type thing so any help would be great.

---

### Post by themattbeballin on 2009-07-09
I got it! 

I ended up creating the following .sh file.

```
echo "Do you want to install these files? (y/n)"
read i;

case $i in
   y)     echo "Now copying files..."
    mkdir ~/Desktop/test
    cp -pr themes/* ~/Desktop/test
    echo "Congratulations! You copy is now complete!"
    echo "Thank you for installing these files!!" ;;
   n) exit ;;
esac
```

---

