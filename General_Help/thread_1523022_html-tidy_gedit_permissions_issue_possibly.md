---
title: "html-tidy gedit: permissions issue possibly"
date: 2010-07-03
forum: General Help
---

### Post by yakcamydna on 2010-07-03
hi

fairly long while linux fan but only just getting down to the nitty gritty. have been trying to install the html-tidy plugin for gedit and seem to be hitting a wall.

i have followed the instructions for download on the following page:

[http://www.eng.tau.ac.il/~atavory/gedit-plugins/html-tidy/#download_inst]("http://www.eng.tau.ac.il/%7Eatavory/gedit-plugins/html-tidy/#download_inst")

i.e.

 sudo apt-get install tidy

and then downloading and extracting the package.

i then succesfully moved the extracted html-tidy folder to /usr/share/gedit-2/plugins

(this took some fiddling and getting my head around the file system and terminal- i really never imagined that simply moving a file would make me smile that much :D
)

after this i then restarted gedit and looked in the edit-preferences-plugins tab but there is no option for html-tidy showing (i also noticed that there is no tab for semantic highlighting either and wondered if this could be related?)

next i did some searching and found this thread:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1028847](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1028847)

and following the instructions performed a :/usr/share/gedit-2/plugins$ sudo chmod 777 ./html-tidy

even so an: ls -al

revealed this;

drwxr-xr-x  2 root root 4096 2009-10-28 20:59 filebrowser
drwxrwxrwx  4 andy andy 4096 2007-07-02 22:43 html-tidy
drwxr-xr-x  2 root root 4096 2009-10-20 05:05 indent

which to my uninitiated brain looks as if the permissions where not correctly changed.

I'm using Karmic Koala.

any ideas??

thanks,

 Andy

---

### Post by ionospheric on 2011-01-02
Just as you did, I first placed the plugin in 
/usr/share/gedit-2/plugins

and tried all the permission modifications as recommended-no change.

Once I placed the plugin in

~/.gnome2/gedit/plugins/

as the author suggests, it worked.

Some plugins work out of the first location (which makes it accessible to all users), this one doesn't.

---

### Post by stevenvu on 2011-01-31
I've just installed html tidy. The instructions arn't the clearest.

When you extract the file, it'll create a folder. You need to go into the folder, copy all of those files and place them into the plugins folder.

Placing the folder that is originally extracted won't work.

---

### Post by pascie on 2011-08-18
I'm looking for this plug-in but the files everyone point to are no longer online. :(

Can someone provide me with the plug-in? Thanks!

---

