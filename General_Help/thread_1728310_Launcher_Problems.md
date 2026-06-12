---
title: "Launcher Problems"
date: 2011-04-13
forum: General Help
---

### Post by Rishav Thakker on 2011-04-13
Hi

I am creating a launcher (a menu item named nfuploader.desktop) in /usr/share/applications for my application nfuploader ([http://apps.facebook/nfuploader](http://apps.facebook/nfuploader)).

the contents of nfuploader.desktop are:

```
[Desktop Entry]
Version=602.5
Name=Nautilus Facebook Uploader
Comment=Desktop application to upload pictures to Facebook
Categories=Network;
Exec=/usr/bin/nfuploader %f
Terminal=false
Type=Application
Name[en_US]=Nautilus Facebook Uploader
GenericName[en_US]=Nautilus Facebook Uploader
Icon=nfuploader
Comment[en_US]=Desktop application to upload single or multiple pictures to Facebook with ease
MimeType=image/bmp;image/gif;image/jpeg;image/jpg;image/png;image/tiff;image/x-bmp;image/x-pcx;image/x-tga;image/x-portable-pixmap;image/x-portable-bitmap;image/x-targa;image/x-portable-greymap
```

Now, after doing that and installing my program:
1. I drag the icon of nfuploader from the Main Menu to gnome-panel. It gets pinned there.
2. I click on the icon on the panel. My app opens up.
3. I drag a picture to the icon on the panel: My app opens up with that picture as a command-line-argument.
4. I drag multiple pictures to that icon on the gnome-panel, and MULTIPLE instances of nfuploader open up, with one picture as argument each. There lies the problem.

I want only one instance of nfuploader to open up, with all the pictures as arguments (space-separated).

Any help would be really appreciated.
Thanks :)

---

### Post by Krytarik on 2011-04-13
What if you set the command this way? I just took it out of "gedit.desktop".
```
[Desktop Entry]
Version=602.5
Name=Nautilus Facebook Uploader
Comment=Desktop application to upload pictures to Facebook
Categories=Network;[COLOR=Red][B]
Exec=/usr/bin/nfuploader %U[/B][/COLOR]
Terminal=false
Type=Application
Name[en_US]=Nautilus Facebook Uploader
GenericName[en_US]=Nautilus Facebook Uploader
Icon=nfuploader
Comment[en_US]=Desktop application to upload single or multiple pictures to Facebook with ease
MimeType=image/bmp;image/gif;image/jpeg;image/jpg;image/png;image/tiff;image/x-bmp;image/x-pcx;image/x-tga;image/x-portable-pixmap;image/x-portable-bitmap;image/x-targa;image/x-portable-greymap
```Greetings.

---

### Post by Rishav Thakker on 2011-04-14
> **Krytarik said:**
> What if you set the command this way? I just took it out of "gedit.desktop".
```
[Desktop Entry]
Version=602.5
Name=Nautilus Facebook Uploader
Comment=Desktop application to upload pictures to Facebook
Categories=Network;[COLOR=Red][B]
Exec=/usr/bin/nfuploader %U[/B][/COLOR]
Terminal=false
Type=Application
Name[en_US]=Nautilus Facebook Uploader
GenericName[en_US]=Nautilus Facebook Uploader
Icon=nfuploader
Comment[en_US]=Desktop application to upload single or multiple pictures to Facebook with ease
MimeType=image/bmp;image/gif;image/jpeg;image/jpg;image/png;image/tiff;image/x-bmp;image/x-pcx;image/x-tga;image/x-portable-pixmap;image/x-portable-bitmap;image/x-targa;image/x-portable-greymap
```Greetings.

Thanks a lot :D It worked.
I'll mark this as solved then.

---

