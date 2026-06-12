---
title: "Picture preview thumbnail not loading"
date: 2009-07-09
forum: General Help
---

### Post by MockY on 2009-07-09
For some reason, picture preview stopped working. Only a few select images is displayed with a preview thumbnail even though my nautilus setting are set to generate preview thumbnails on files smaller than 100mb.

What is going on?

---

### Post by danwood76 on 2009-07-09
There is a cache of thumbnails within your home directory.
If nautilus fails to load a thumbnail it marks the file as 'no thumbnail'.
The way to fix is to delete that directory of thumbnails and make it generate them again.

The directory is .thumbnails (hidden) in your home folder, you can press ctrl + h to show the hidden folders.
To remove the folder from the terminal do:
```

rm -R ~/.thumbnails

```

---

### Post by MockY on 2009-07-11
After restarting Nautilus, your tip sure fixed it. Thanks. Hopefully this won't happen very often....

---

### Post by danwood76 on 2009-07-12
It shouldn't do.
It normally only happens when you dont have the correct codecs installed which shouldn't happen with photos.

---

### Post by MockY on 2009-07-17
Don't know what to tell you, but removing the thumbnails folder fixed the issue. Nautilus is far from stable and have always had random issues that makes no sense. However, as long as there is a fix for the flaw, I'm happy.

---

### Post by buck2825 on 2011-03-06
I have tried 
$rm -R ~/.thumbnails

I even did a 
$killall nautilus

to restart nautilus and restarted my laptop and I still only get one or to of my thumbnails for my jpg images.


......just checked something.

in nautilus under edit-> preferences.  on the preview tab I needed to make my "only for files smaller than"  1 gb.  with my camera I can take images up to 20MB or larger. 

Solved my own problems added this just to help others!!

---

