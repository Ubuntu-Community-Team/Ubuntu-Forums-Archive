---
title: "Ugly fonts in Java GTK Theme"
date: 2009-08-26
forum: General Help
---

### Post by 5n4K3 on 2009-08-26
Hi there! i have a little problem with java apps...see the screenshots

**FrostWire with Metal Theme**
[http://www.ubuntu-pics.de/bild/22927/screenshot_15_Od9n1H.png](http://www.ubuntu-pics.de/bild/22927/screenshot_15_Od9n1H.png)

**FrostWire with GTK Theme**
[http://www.ubuntu-pics.de/bild/22925/screenshot_16_eHgomo.png](http://www.ubuntu-pics.de/bild/22925/screenshot_16_eHgomo.png)

same issue in JDownloader...any help is appreciated :)

---

### Post by kpkeerthi on 2009-08-26
What version of Java are you using? Check with **java -version** command.

I use Sun's JDK 6 and the font rendering on Java GUI applications is as good as GNOME's native.

---

### Post by 5n4K3 on 2009-08-26
> **kpkeerthi said:**
> What version of Java are you using? Check with **java -version** command.

I use Sun's JDK 6 and the font rendering on Java GUI applications is as good as GNOME's native.

```
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.4.1) (6b14-1.4.1-0ubuntu11)
OpenJDK 64-Bit Server VM (build 14.0-b08, mixed mode)
``` i use ubuntu jaunty :(

---

### Post by Cypher1101 on 2010-01-31
I just upgraded to karmic and reinstalled jdownloader. The first time I used OpenJDK, and the fonts were completely unreadable. I then googled for an solution and found this thread. After seeing kpkeerthi's post, I tried reinstalling with Sun's JDK. Now the fonts are perfect.  Oddly enough, I never had a problem with OpenJDK under jaunty. I had been using jdownloader for months.

---

### Post by 5n4K3 on 2010-02-02
> **Cypher1101 said:**
> I just upgraded to karmic and reinstalled jdownloader. The first time I used OpenJDK, and the fonts were completely unreadable. I then googled for an solution and found this thread. After seeing kpkeerthi's post, I tried reinstalling with Sun's JDK. Now the fonts are perfect.  Oddly enough, I never had a problem with OpenJDK under jaunty. I had been using jdownloader for months.

```
sudo update-java-alternatives -s java-6-sun
``` this fix my problem with the fonts :D

---

### Post by mastery82 on 2010-05-18
Worked for me.
Thanks man.

---

### Post by eb sol on 2010-08-30
Try :

java -Dswing.defaultlaf=com.sun.java.swing.plaf.gtk.GTKLookAndFeel -jar [Your App]

---

