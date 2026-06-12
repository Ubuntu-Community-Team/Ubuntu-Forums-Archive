---
title: "How can I archive some photos after the time they were created?"
date: 2011-11-19
forum: General Help
---

### Post by radu992 on 2011-11-19
I have to archive some photos from my holiday this year and I need to archive them after the date they were created because I have the photos in many folders, the photos aren't only from the holiday this year and it would be very hard for me to archive them manually. Also I would like to archive them after the size in MB because I shoot them with two different cameras, a normal one and a mobile camera, and also I would like to select only the ones with .jpg extension because in those folders i have .avi  and .mp4 files. Please help me.:)

---

### Post by WasMeHere on 2011-11-19
Welcome to the Ubuntu Forums, radu992,

I suggest that you use a photo organizer like Shotwell or Digikam. Browse the internet to find out about these tools!

Shotwell is included in new versions of Ubuntu and can be installed from the repositories with ```
sudo apt-get install shotwell
``` in older Ubuntus.

Digikam belongs to KDE (Kubuntu), but it can also be downloaded to the other Ubuntu flavours from the repositories
```
sudo apt-get install digikam
``` It will bring some of the KDE infrastucture (libraries etc) but I like it and I use it in Ubuntu 10.04.

Have fun finding out about Ubuntu :-)
Olle

---

### Post by radu992 on 2011-11-19
It seems complicated the way you told me earlier. Isn't it a much easier method like some commands in the bash terminal? I was thinking about using the find command but I don't know how to use it very well.

---

### Post by WasMeHere on 2011-11-19
Those tools are developed to make it easy. It makes it easier than to use find. At one time I tried using find and a system with symbolic links, but today 'no way'.

Digikam is a mature tool with so many ways to organize and search for thousands of pictures. Try it, if you don't like it you can delete it and recover the disk space.

If you like to work with command line tools, install ImageMagick, which can do everything and a little more with your pictures, including reading the exif information from the camera!

---

### Post by WasMeHere on 2011-11-19
Read also the following thread! You may have ideas in common with rocksockdoc
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showthread.php?t=1839153_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1839153")

---

