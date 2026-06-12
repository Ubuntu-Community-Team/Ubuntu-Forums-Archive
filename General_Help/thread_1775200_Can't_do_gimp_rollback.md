---
title: "Can't do gimp rollback"
date: 2011-06-04
forum: General Help
---

### Post by savaan on 2011-06-04
My wife and I installed the gimp 2.7 version that recently came out. NOT happy with it at all so I'm trying to roll us back. Problem is, I'm getting this error when trying to install 2.6 through Ubuntu Software Center:
> The following packages have unmet dependencies:

gimp: Depends: libc6 (>= 2.11) but 2.13-0ubuntu13 is to be installed
      Depends: libfontconfig1 (>= 2.8.0) but 2.8.0-2.1ubuntu3 is to be installed
      Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but 2.23.3-0ubuntu1 is to be installed
      Depends: libglib2.0-0 (>= 2.24.0) but 2.28.6-0ubuntu1 is to be installed
      Depends: libgtk2.0-0 (>= 2.20.0) but 2.24.4-0ubuntu2 is to be installed
      Depends: libjpeg62 (>= 6b1) but 6b1-1ubuntu1 is to be installed
      Depends: librsvg2-2 (>= 2.26.0) but 2.32.1-0ubuntu3 is to be installed
      Depends: libxfixes3 (>= 1:4.0.1) but 1:4.0.5-1ubuntu1 is to be installed
      Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu3 is to be installed
      Depends: python (>= 2.7) but 2.7.1-0ubuntu5 is to be installed
      Depends: python-gtk2 (>= 2.8.0) but 2.22.0-0ubuntu1.1 is to be installed
**EDIT**
Well I restarted, went into the package manager and completely removed gimp and its data files. Restarted again and it allowed me to install gimp 2.6. I installed, went to my icon to open it up and nothing. My cursor timer just sits there, and then it disappears and GIMP never opens :(

**EDIT** OK after working at this for about 2hrs I found this page:
[http://bentwithlove.blogspot.com/2011/05/gimperror-while-loading-shared.html](http://bentwithlove.blogspot.com/2011/05/gimperror-while-loading-shared.html)

following the terminal commands there did the trick and I've rolled back to version 2.6. I don't know how to mark this SOLVED :/

---

