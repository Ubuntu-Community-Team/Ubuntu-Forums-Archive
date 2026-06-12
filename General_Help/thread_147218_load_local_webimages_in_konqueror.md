---
title: "load local webimages in konqueror?"
date: 2006-03-19
forum: General Help
---

### Post by harty83 on 2006-03-19
Howdy,

I have am taking an online class.  All the images though are loaded from a CD that I purchased.  They have it where you set up what your CD drive is and then their webpage loads the image from there.  However, konqueror does not seem to load local images.  Is there a way to make this happen?

Thanks!

---

### Post by tuxcantfly on 2006-03-19
Check the <img src=localtion> tags in the html, and they should be there in relation to the directory the html file is in.

For example, if in /media/cdrom/web/site.html there is a <img src=images/logo.png>, you the image should be at /media/cdrom/web/images/logo.png.

Konqueror does support local image files; in fact, I'm using it to redesign my own e-commerce website, [http://www.wordofmice.com](http://www.wordofmice.com), locally on my hard drive before uploading it. Just in case, though, you could try using Firefox (though you'll probably get the same result).

The problem is probably an issue with the html code, not Konqueror.

---

### Post by harty83 on 2006-03-19
here is an example img source from the source file:  file:////home/alan/OnMusicFiles/MetroMotion2.jpg (I copied the CDs contents to my computer for convenience sake.  

Firefox is configured to not be able to load local images, however you can configure it to do so by following directions on their website which I have done.  So Firefox works just fine with loading the images, but konqueror does not.  I would like to get konqueror to work if possible.  If I copy the image source and open it in another window, the image loads right up.  It doesn't though when the  specific webpage calls for it.

---

