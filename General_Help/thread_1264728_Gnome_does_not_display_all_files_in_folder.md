---
title: "Gnome does not display all files in folder"
date: 2009-09-12
forum: General Help
---

### Post by jcobban on 2009-09-12
I have a folder that contains 2 large JPEGs, among other files.  I have my Nautilus options set so that it will only display thumbnails for images that are less than 100KB in size.  However if an image has been viewed in the Gnome image viewer the image is cached somewhere so that the file size option is ignored and Nautilus builds a thumbnail anyway. That is Nautilus displayed all of the files in the folder, including these 2 JPEGs (without thumbnails) until I used the Gnome viewer to view the two images.  Now Nautilus goes into a very long loop, presumably preparing to display the thumbnails of the two files it is not showing.  I waited for many minutes but Nautilus never displayed the two files.  As a consequence I cannot even delete them using the GUI.  I don't know what it is about these 2 JPEGs, GIMP also seemed to struggle to load them, although ls says they are only 1.6MB and 1.7MB.

Does anyone know how to purge Gnome's image cache or some other way to make Nautilus obey my instruction to not display thumbnails for images more than 100KB in size?

Running Nautilus 2.26.2 on Gnome 2.26.1 on Ubuntu 9.04.

---

### Post by StuartN on 2009-09-12
The thumbnail files are in ~/.thumbnails in folders normal, large and fail. I have found that emptying the fail folder can clear this kind of problem.

I guess Nautilus is not building thumnails, but Eye of Gnome has no option to disable thumbnailing, so it thumbnails any image you view and any collection you view. You can disable all thumbnailing by setting the size or age to 0 in desktop/gnome/thumbnail_cache in the configuration editor (gconf_editor).

---

### Post by jcobban on 2009-09-12
> **StuartN said:**
> The thumbnail files are in ~/.thumbnails in folders normal, large and fail. I have found that emptying the fail folder can clear this kind of problem.

On the topic of cleaning up Gnome thumbnails I found a web page that indicated to issue the command:

find /home/username/.thumbnails -type f -mtime +30 -exec rm {} \ 

Issuing this command gives me the error "Missing argument to -exec".  I have read through man find, and cannot figure out how the author of the web page came up with that syntax, but none of the other syntaxes suggested by the man page can get me past that error.  The man page says:

 -exec command ;
     Execute  command;  true  if 0 status is returned.  All following arguments to find are taken to be arguments to the command until an  argument  consisting of ‘;’ is encountered.

But replacing the backslash with a semi-colon still gives me the "Missing argument to -exec" error message.

---

### Post by Vaphell on 2009-09-12
it's not replacing / with ;, it's adding ;

look at examples
[http://www.wagoneers.com/UNIX/FIND/find-usage.html](http://www.wagoneers.com/UNIX/FIND/find-usage.html)

---

### Post by jcobban on 2009-09-13
> **Vaphell said:**
> it's not replacing / with ;, it's adding ;

look at examples
[http://www.wagoneers.com/UNIX/FIND/find-usage.html](http://www.wagoneers.com/UNIX/FIND/find-usage.html)

Thank you.

---

