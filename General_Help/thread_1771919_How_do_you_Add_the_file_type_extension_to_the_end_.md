---
title: "How do you Add the file type extension to the end of multiple files"
date: 2011-05-30
forum: General Help
---

### Post by firefish5000 on 2011-05-30
I have made the simple mistake of using dolphin to rename several picture files of types jpg and png. I have no problem viewing them and Ubuntu still knows which is which (if i view their properties it will state File Type: JPEG or PNG) but unfortunately Ubuntu Tweak does not allow you to chose them without the extension (I am trying to change my login background using this)
 So what i need is something that can scan several files, determine the file type, and add an appropriate extension to it. I have found several to do so for music files but none for images. I am using Ubuntu 11.04 at the moment.
Any suggestions appreciated, also, if you know of a better way to change the login theme please tell me. Thank you

---

### Post by linuxinstalledfromhdd on 2011-05-30
Open each one in GIMP and then re-extension them manually.  Put them a folder to access for your wallpaper.  Done deal. :)

---

### Post by Toz on 2011-05-30
Or, if you're willing to get your elbows a little greasy on the command line, you could do something like this.

The **file** command can report back and tell you the type of file any given file is:```
$ file YouWouldntDownloadACar.png 
YouWouldntDownloadACar.png: PNG image data, 1920 x 1080, 8-bit/color RGBA, non-interlaced

```
You can also add the -b parameter to the file command and a simple cut command to cut out the first field to tell you only the file type:```
file -b YouWouldntDownloadACar.png | cut -d' ' -f1
PNG

```

Given that you know the file type, you can then script a solution that goes through the directory, identifying the files and change the file extensions to match the file type. Here's a sample of a bash script that I just threw together:```
#!/bin/bash

for file in *
do
	ty=`file -b "$file" | cut -d' ' -f1`
	case $ty in
		JPEG)
			mv "$file" "${file%\.*}.jpg"
			;;
		PNG)
			mv "$file" "${file%\.*}.png"
			;;
		*)
                ;;
	esac		
done
```

**DISCLAIMER:** I tested this on my system with my files. If you want to run this on your system, take some extra precautions to be safe:
- create a backup of the folder you are trying to manipulate (just in case something goes wrong)
- create a file (**mypicrenamer**) in the same directory as your graphics files with the contents as listed below
- change the permissions on that file to make it executable (**chmod +x mypicrenamer**) 
- execute ala (**./mypicrenamer**)

---

### Post by Vaphell on 2011-05-30
.

---

### Post by Toz on 2011-05-30
In addition to Ubuntu Tweak, GDM Tweaker is another application that can make modifications to the login screen: [http://www.webupd8.org/2011/05/change-gdm-theme-background-in-ubuntu.html](http://www.webupd8.org/2011/05/change-gdm-theme-background-in-ubuntu.html)

---

### Post by firefish5000 on 2011-06-01
Thanks, I managed to fix all the images.
I am trying the GDM tweak, it looks as though I may need to use Ubuntu tweak after i use this to fix the icon (customized it to match my theme, now a blue flame) but the GTK theme changer looks as though it will come in handy (going to play with my new toy after this) 

I have been slowly customizing my Ubuntu for the past 2 weeks, I have rid myself of the panel at the top, changed to desktop cube (i feel like an idiot for having such a hard time. each time it disabled unity and when enabling unity it gives an option of wall or cube, chose wall each time not knowing of the option) and now the login screen. last thing to do is the boot splash which i am currently re-scripting. (though i am clueless of the language i am typing in, i am editing using the old boot screen as a templet, changing only values such as pic location (x,y) and pic location(/lib/plymouth/...))
Thanks for your help.

---

