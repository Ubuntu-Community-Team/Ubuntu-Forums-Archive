---
title: "qt4 designer link"
date: 2006-04-10
forum: General Help
---

### Post by bcroesch on 2006-04-10
I recently install qt4 from Trolltech. When I try to start designer by simply typing designer in a terminal, it starts qt3-designer. However, if I navigate to the Qt4 bin directory, which is /usr/local/Trolltech/Qt-4.1.1/bin, and type ./designer, the qt4 designer will start. 

If I am headed in the right direction, I think I need to change the link in /usr/bin to point to /usr/local/Trolltech/Qt-4.1.1/bin/designer, instead of the qt3 version, but I haven't been able to figure out how to do this. Can anyone point me in the right direction? Thanks.

---

### Post by trent dillman on 2006-04-10
```
sudo ls -l `which designer`
``` That will tell you where it is, and if it's a link. If it is a link, just remove it and link to the new version:
```
export myDesigner=`which designer`
sudo rm $myDesigner
sudo ln -s /usr/local/Trolltech/Qt-4.1.1/bin/designer $myDesigner
```

---

