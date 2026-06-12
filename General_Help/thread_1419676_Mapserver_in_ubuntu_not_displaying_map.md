---
title: "Mapserver in ubuntu: not displaying map"
date: 2010-03-02
forum: General Help
---

### Post by ashka_a on 2010-03-02
I am trying to run Mapserver in Ubuntu Karmic Koala. I have successfully used Mapserver in windows and now want to migrate to ubuntu . But  I'm very much new to ubuntu and struggle to get the work done smoothly.
 
The  Mapserver and Apache both are running. I use only the localhost
I can get a map in map mode ( based on map server tutorial examples) but failed to get the map display in  the browse mode.

There is no error massage and the web templete is displaying with all components except the map image. The map images are  created inside the tmp folder however they are not displayed in the template interface.

I think its due to permission issues but failed to solve it, even after going through forums.

The locations of the templete and map files are /var/www/tutorial
The location of the image path /var/www/tutorial/tmp

For /var/www/tutorial/tmp permissions are as follows 

```
drwxrwsr-x 2 gisuser www-data  4096 2010-03-02 16:14 tmp
```

when the new map images are created by the mapserver , the image files have permissions like this

```
-rwxrwxr-- 1 www-data www-data 11686 2010-03-02 16:14 EX2.1_12675266704111.png
```
Why doesn't these map images are not displying in the web templete file?

Can anyone suggest a way to solve this issue?
appreciate any help .

---

