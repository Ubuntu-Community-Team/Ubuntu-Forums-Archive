---
title: "Open files with other applications sometimes not possible"
date: 2012-07-24
forum: General Help
---

### Post by Redsandro on 2012-07-24
Since **Ubuntu 12.04** you cannot manually specify a program anymore in the *Open With* context-item.

According to the documentation at:
[https://help.ubuntu.com/12.04/ubuntu-help/files-open.html](https://help.ubuntu.com/12.04/ubuntu-help/files-open.html)

you'll have to click on *"Other Applications"* to find all available applications, which isn't always true.

For example, I installed [XnViewMP]("http://newsgroup.xnview.com/viewtopic.php?f=60&t=26033"), the image viewer that is a ridiculous amount better than anything available in the repositories.

Here is the application installed. It works perfectly when I start it from here.

[img]http://ubuntuforums.org/attachment.php?attachmentid=221723&stc=1&d=1343141370[/img]

Here is the list of other applications, and the application I installed is not there.

[img]http://ubuntuforums.org/attachment.php?attachmentid=221724&stc=1&d=1343141370[/img]

Some time ago I did have an association with an older installation of XnViewMP, which was installed at a different path and doesn't exist anymore. For PNG files, this association is still visible but broken:

[img]http://ubuntuforums.org/attachment.php?attachmentid=221725&stc=1&d=1343141370[/img]

There is no way to remove or edit (repair) it.

[LIST]
[*]How do I add applications that are not listed?
[*]How do I remove obsolete apps that cannot be removed?
[*]Is there a mimes cache somewhere? Note that ~/.local/share/mime does not help.
[/LIST]

When I google, I'm getting results from the good old days, where you had an add and a remove button:
[http://www.watchingthenet.com/ubuntu-guide-for-windows-users-how-to-change-file-typs.html](http://www.watchingthenet.com/ubuntu-guide-for-windows-users-how-to-change-file-typs.html)
Unfortunately, that's not possible anymore.

---

### Post by dino99 on 2012-07-24
i suppose your 12.04 installation is a 64 bits one, because xnview is.

---

### Post by Vaphell on 2012-07-24
check /usr/share/applications/xnviewmp.desktop (or whatever it's called)
is there a placeholder for opened file in Exec= line? something like *Exec=xnviewmp **%U***
afaik 'other applications' dialog shows only those programs which have that explicit %U

---

### Post by Redsandro on 2012-07-24
> **Vaphell said:**
> check /usr/share/applications/xnviewmp.desktop (or whatever it's called)
is there a placeholder for opened file in Exec= line? something like *Exec=xnviewmp **%U***

Yes, and the file does exist. It is a batch file referencing a binary file which also exists. When I run either of those, the application starts normally.

```
$ cat /usr/share/applications/XnView.desktop 

[Desktop Entry]
Type=Application
Name=XnView Multi Platform
GenericName=XnViewMP
Comment=Graphic viewer, browser, converter
Exec=xnview %U
TryExec=xnview
Terminal=false
Icon=/opt/XnView/xnview.png
Categories=Graphics;
StartupNotify=true

$ which xnview 
/usr/sbin/xnview
$ 

```

> **dino99 said:**
> i suppose your 12.04 installation is a 64 bits one, because xnview is.

True. I think I couldn't even install the 32 bit .deb if I wanted to. Please note that the app works fine if I launch it from the menu or command line. The problem lies with associating files.

---

### Post by spacemig on 2012-07-24
Any luck with this problem?

I get the same problem when I try to associate Matlab files. It won't show in the 'Other Applications' list.

Any idea how to associate Matlab (*.m) files with Matlab in Ubuntu 12.04?

---

### Post by HiImTye on 2012-07-25
search for the extension in /usr/share/applications/mimeinfo.cache and then copy that extension type into $HOME/.local/share/applications/mimeapps.list below 'added associations'

make sure you are using the .desktop file for that program. for instance, if I want to add GIMP to .png I would do something like:


```

tye@T:~$ cat /usr/share/applications/mimeinfo.cache | grep -iE 'png|gimp'
application/pdf=evince.desktop;gimp.desktop;
application/postscript=evince.desktop;gimp.desktop;
image/bmp=gimp.desktop;eog.desktop;
image/g3fax=gimp.desktop;
image/gif=gimp.desktop;firefox.desktop;eog.desktop;
image/jpeg=gimp.desktop;firefox.desktop;eog.desktop;shotwell-viewer.desktop;
image/pcx=gimp.desktop;
image/png=gimp.desktop;firefox.desktop;eog.desktop;shotwell-viewer.desktop;
image/svg+xml=inkscape.desktop;gimp.desktop;eog.desktop;
image/tiff=evince.desktop;gimp.desktop;eog.desktop;shotwell-viewer.desktop;
image/x-compressed-xcf=gimp.desktop;
image/x-fits=gimp.desktop;
image/x-icon=gimp.desktop;
image/x-png=eog.desktop;
image/x-portable-anymap=gimp.desktop;eog.desktop;
image/x-portable-bitmap=gimp.desktop;eog.desktop;
image/x-portable-graymap=gimp.desktop;eog.desktop;
image/x-portable-pixmap=gimp.desktop;eog.desktop;
image/x-psd=gimp.desktop;
image/x-psp=gimp.desktop;
image/x-sgi=gimp.desktop;
image/x-tga=gimp.desktop;
image/x-wmf=gimp.desktop;
image/x-xbitmap=gimp.desktop;eog.desktop;
image/x-xcf=gimp.desktop;
image/x-xpixmap=gimp.desktop;eog.desktop;
image/x-xwindowdump=gimp.desktop;
tye@T:~$ cat $HOME/.local/share/applications/mimeapps.list | sed 's|\(\[Added Associations\]\)|\1\nimage/png=gimp.desktop;|' > mimeapps.list
tye@T:~$ mv -f mimeapps.list $HOME/.local/share/applications/mimeapps.list

```

---

