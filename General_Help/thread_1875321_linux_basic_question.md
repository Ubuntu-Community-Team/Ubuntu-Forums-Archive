---
title: "linux basic question???"
date: 2011-11-04
forum: General Help
---

### Post by liquidmonkey on 2011-11-04
i have a question on program installation which involves where files end up and what can be and not be deleted afterwards.
please bare with me...


let's say i download a compressed tar program, in this case, PCL (point cloud library).

i download the tar into the 'downloads' directory and then i uncompress it there which gives me a folder called 'PCL-1.3.0-Source'.

i'm doing this all in the terminal BTW.

following on the instructions from the point clouds webpage ([http://www.pointclouds.org/downloads/source.html](http://www.pointclouds.org/downloads/source.html)), i cd into the new directory, run 'cmake ..', 'make', and finally 'make install'.

1) do i need to keep the directory (PCL-1.3.0-Source) or can i delete it or is this where the install files have been put?

2) if i need to keep the 'pcl sources' directory, am i able to move it to a different location?


coming from windows, which keeps things nice and organized for the dumb user, i find linux a bit confusing as to where certain programs are installed and how to reference to them when writing my own code.

thanks for any comments to this basic question, much appreciated.

---

### Post by gordintoronto on 2011-11-04
There's a better way. This web page explains: [http://pointclouds.org/downloads/linux.html](http://pointclouds.org/downloads/linux.html)

In Ubuntu, we try to install from a repository if at all possible. When you do it that way, you don't have to worry about where things are going, everything is looked after for you. The web page has three lines for you to copy and paste (one at a time) into Terminal.

A tar file is just like a zip, it might include anything. Hopefully it has installation instructions.

---

### Post by WorMzy on 2011-11-04
If you installed with "sudo make install", then you should probably keep the folder you ran make install from, just in case you ever need to run "sudo make uninstall".

A better way to install applications compiled from source, is to use "sudo checkinstall" instead of "sudo make install". That should* create a .deb file and then automatically install it. This makes it easier to remove (or update) the application at a later date.


*Never actually used it myself, I don't use Ubuntu.

---

