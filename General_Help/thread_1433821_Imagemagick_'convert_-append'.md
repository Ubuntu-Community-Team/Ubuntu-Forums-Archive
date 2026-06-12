---
title: "Imagemagick 'convert -append'"
date: 2010-03-19
forum: General Help
---

### Post by Penguin Guy on 2010-03-19
I've made some custom icon mashups in inkscape and want to display the entire collection [here]("http://ubuntuforums.org/album.php?albumid=1109&pictureid=4756") on the forums. I'm trying to use imagemagick to put the icons into a square formation. However by default it does it in a long line - how do I force imagemagick to try to make a square image as the end result? 

Solution: [SIZE="3"][FONT="Courier New"]montage * Mime-Icons.png[/FONT][/SIZE]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=150744&stc=1&d=1269095566[/IMG]

Thanks.

---

### Post by kaibob on 2010-03-19
I think you have to use Imagemagick Montage:

[http://www.imagemagick.org/Usage/montage/](http://www.imagemagick.org/Usage/montage/)

---

### Post by Penguin Guy on 2010-03-20
> **kaibob said:**
> I think you have to use Imagemagick Montage:

[http://www.imagemagick.org/Usage/montage/](http://www.imagemagick.org/Usage/montage/)
That worked great - thanks!

---

