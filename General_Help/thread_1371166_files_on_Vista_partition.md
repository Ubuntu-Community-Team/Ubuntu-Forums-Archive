---
title: "files on Vista partition?"
date: 2010-01-03
forum: General Help
---

### Post by sprunkie on 2010-01-03
So, can I boot up ubuntu with all the files in my vista side?  Like with all the "Places" being linkes or short-cuts to my vista partition? :confused:

Because I saved Ubuntu on about 30 gb and the  rest of them about 470gb is vista.  So, if I need windows for something dumb.  I also swipe it clean about every 6 to 12 months.  So,  I don't have to relaod my media.  

Oh, But I would like to have a password still.  So, if someone has to use my computer.  It will be like a guest be not. Just easier.  And they can't erase my music.  

Can you make it so that you go to the login screen when you click on the media files or links?

Thanks

---

### Post by rnerwein on 2010-01-03
hi 
1. open a terminal and execute a root shell: sudo /bin/bash (be carefull if you not confirm to unix)
2. cd /
3. mkdir vista_root (you can name it like you want)
4. edit /etc/fstab (i use vi - use your preffered editor )
5. insert following line(s) at the end of fstab
   /dev/sda2 /vista_root ntfs ro,nosuid,allow_other,default_permissions,   0   0
   /dev/sda3 /vista_data ntfs ro,nosuid,allow_other,default_permissions,   0   0
# /dev/sda2 and /dev/sda3 are my configuration - i ain't no where your vista resides in your configuration
 6. save the file and exit your editor
 7. reboot
now your partition(s) should be mounted (read only - comes from "ro" in the mount options)
my configuration works - yours must work too (oh - i think your vista filesystem is ntfs too)
ciao

---

