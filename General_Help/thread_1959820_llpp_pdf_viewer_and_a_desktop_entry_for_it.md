---
title: "llpp pdf viewer and a desktop entry for it"
date: 2012-04-16
forum: General Help
---

### Post by oiyyyob on 2012-04-16
hey there,

i compiled this great pdf viewer: [http://repo.or.cz/w/llpp.git](http://repo.or.cz/w/llpp.git) successfully and now I wanted to create an .desktop file in /usr/share/applications for the application. 

I put llpp to my PATH-variable and it works when I do: llpp <some path to pdf> but I want to use it as my primary pdf tool to open pdfs on double click. For that I created the llpp.desktop file with the following content:
```

[Desktop Entry]
Name=llpp pdf viewer
Comment=View multi-page documents
Exec=llpp %u
StartupNotify=true
Terminal=false
Type=Application
Icon=
X-GNOME-DocPath=
MimeType=application/pdf;application/x-pdf;
Categories=Viewer;Graphics;

```But the application is not opening the pdf file. I also tried %f as mupdf does as parameter, but it's not working. I know I had it running on my last arch linux machine, so I wonder what I'm doing wrong. Thanks for any help or ideas.

I'm running on 12.04 beta 64bit.

---

### Post by LewisTM on 2012-04-16
Quick question: Is the application not opening the PDF file or not opening period?

EDIT: Nevermind, I guess llpp cannot be opened without a file. My uneducated guess would be that your PATH is only set for the shell and not for your DE. Use the full path to the llpp executable in your .desktop file and see if that helps.

---

### Post by oiyyyob on 2012-04-17
I also tried it with the full path in the .desktop file earlier, but no success, but thanks anyway.

---

### Post by oiyyyob on 2012-04-18
Problem solved, I had a typo in my path.... now it works with 
```
[Desktop Entry]
Name=llpp pdf viewer
Comment=View multi-page documents
Exec=/home/<user>/apps/llpp/llpp %f
StartupNotify=true
Terminal=false
Type=Application
Icon=
X-GNOME-DocPath=
MimeType=application/pdf;application/x-pdf;
Categories=Viewer;Graphics;

```

how to mark this thread solved?

---

