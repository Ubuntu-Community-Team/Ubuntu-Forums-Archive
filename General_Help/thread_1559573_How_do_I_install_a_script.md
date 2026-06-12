---
title: "How do I install a script?"
date: 2010-08-23
forum: General Help
---

### Post by TheNerdAL on 2010-08-23
I want to install this: [http://www.omgubuntu.co.uk/2010/08/upload-images-to-imgur-via-nautilus.html](http://www.omgubuntu.co.uk/2010/08/upload-images-to-imgur-via-nautilus.html) 

But I am sort of a newb at installing tar.gz files. D: How do I do it?

---

### Post by Vaphell on 2010-08-23
tar.gz is a compression format widely used in linux, simply decompress it - and there is README file which says 'run install script' which is there too

when you see tar.gz you can always look inside and see if there are instructions included.

---

### Post by Jesus_Valdez on 2010-08-23
If its a Nautilus script you just need to decompress it and move it to the relevant folder on Home.

---

### Post by ankspo71 on 2010-08-23
Hi,
Extract the tar.gz file then double click on the file named "install". The "install" file was already marked as executable so you won't have to change the permissions. This should work on the Ubuntu desktop, but if it doesn't you can use these commands:

If you downloaded the file to your desktop:
Extract the tar.gz on the desktop.
Next, open the terminal and do the following:
```
cd Desktop
ls
```
That changes your working directory to the Desktop,
then terminal will show the contents of the Desktop.
Next, change directories into the "ImgurUploader-r13" folder:
```
cd ImgurUploader-r13  
```
(or cd Img[tab key] for auto completion)
Next you can run the script using bash:
```
bash ./install
```
That should do it. PS. I don't use the Gnome desktop, so let us know if these instructions don't work.
Hope this helps.

---

### Post by TheNerdAL on 2010-08-23
I think I got it.

---

