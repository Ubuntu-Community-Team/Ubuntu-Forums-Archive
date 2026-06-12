---
title: "how to mass convert .tif &#8594; .jpg"
date: 2006-06-07
forum: General Help
---

### Post by Bou on 2006-06-07
Hi. I scanned around 500 pictures today, and I can't rotate them or do anything else. None of my programs except for GIMP -not gthumb, not f-spot- can convert them to .jpg.

Is there a way that I can batch convert them? Thanks in advance guys.

---

### Post by jazzgossen on 2006-06-07
Sure. Have a look at "convert -h".

---

### Post by marcog on 2006-06-07
You'll first need to install imagemagick:

```
apt-get install imagemagick
```

[http://www.imagemagick.org](http://www.imagemagick.org)

---

### Post by Bou on 2006-06-07
[QUOTE=jazzgossen]Sure. Have a look at "convert -h".[/QUOTE]

Thanks, but I get "command not found"... shall I install some package?

---

### Post by musicinmybrain on 2006-06-07
If you use mogrify instead of convert, you won't have to specify output filenames, which makes batch processing easier. Mogrify is also part of imagemagick; it takes the same options as convert. It will make jpegs out of your tiff files without deleting the original files.

While you should look through the output of mogrify -h to get an idea of what imagemagick can do, the options you need are something like:

```
mogrify -format jpg -quality 90 *.tif
```

Of course, replace 90 with whatever quality factor suits you.

Then, if you're satisfied with the output and don't want to keep the tiffs, you can rm *.tif.

---

### Post by Bou on 2006-06-08
[QUOTE=musicinmybrain]If you use mogrify instead of convert, you won't have to specify output filenames, which makes batch processing easier. Mogrify is also part of imagemagick; it takes the same options as convert. It will make jpegs out of your tiff files without deleting the original files.

While you should look through the output of mogrify -h to get an idea of what imagemagick can do, the options you need are something like:

```
mogrify -format jpg -quality 90 *.tif
```

Of course, replace 90 with whatever quality factor suits you.

Then, if you're satisfied with the output and don't want to keep the tiffs, you can rm *.tif.[/QUOTE]

Thanks a buch, I managed it this way. You guys are pure gold.

---

### Post by lonoy on 2007-10-27
Hi, 

I have had a good look through the above and I still can't get a bunch of TIF files to convert to JPEG.

I have ImageMagick installed and have tried the command posted above. When I do nothing happens so i expect I must set up something before hand. 

If I have, for example, a folder named photos on my desktop containing 20 TIF files I wish to batch convert to JPEG format what would be the actual sequence I would need to use. I can understand what the command is trying to do but when I use it in the terminal nothing happens.

I am a novice regarding terminal use and guess I must direct it somehow to the "photos" folder.

Thanks

---

### Post by musicinmybrain on 2007-10-27
Before using the command ```
mogrify -format jpg -quality 90 *.tif
``` you must be in the correct folder. To change to the photos folder on your desktop, type ```
cd ~/Desktop/photos
```

"cd" is the change directory command, "~/" refers to the home folder of the user issuing the command (that's you), and the "Desktop/photos" path should be self-explanatory. Equivalently, you could have typed ```
cd /home/your_user_name/Desktop/photos
```, replacing your_user_name with your actual user name.

---

### Post by lonoy on 2007-10-27
Thanks a million for the reply, that worked once I followed your instructions.

Problem now is that I am getting two JPEG photos after the batch convert per one TIFF. Can the command be modified so I just get one JPEG per TIFF and then the original  TIFF files are then deleted?

---

### Post by musicinmybrain on 2007-10-27
Are they multipage tiffs? What is the difference between the two JPEGs?

When you're sure you don't want the tiffs any more, you can type ```
rm *.tif
```. This doesn't move files to the trash, though; they're gone for good! So make sure you don't delete something you didn't want to by accident.

---

### Post by lonoy on 2007-10-27
Thanks

The command I used was:

```
:~/Desktop/photos$ mogrify -format jpg -quality 100 *.tif
```

The first JPEG was compressed to 355 KB while the second came in at 24 KB.

---

### Post by musicinmybrain on 2007-10-27
What are the names of the files?

What probably happened is that the files were actually a multipage TIFF with a thumbnail and a large version for some reason. But I don't really know because when you don't provide specifics it's hard to figure out what's happening. For example, earlier you said "nothing happened" when you tried to convert the tiffs in the wrong directory, whereas really you would have got the error message "mogrify: unable to open image `*.tif': No such file or directory." The more precise detail you can include, the more people can help you.

Now, I don't know whether the files have the same images and what their file names are (are they sequentially numbered).

---

### Post by lonoy on 2007-10-27
Thanks

Folder name is "photos"

Files are named as follows:

Untitled - 1.tif

which are converted to:

Untitled - 1-0.jpg

Untitled - 1-1.jpg

The second jpg is a thumbnail as you suggested. Yes they are sequentially numbered.

This error message appears:

:~/Desktop/photos$  mogrify -format jpg -quality 100 *.tif
mogrify: Untitled - 5.tif: unknown field with tag 317 (0x13d) encountered. `TIFFReadDirectory'.

Before it appeared only on Untitled 7. When I deleted Untilted 7 it now appears only on Untitled 5. There are only/were 7 tifs in the folder.

---

### Post by musicinmybrain on 2007-10-27
If the second jpeg in each pair is a thumbnail, you can delete the thumbnails with ```
rm *-1.jpg
``` If you want to check your wildcard expression before actually deleting, list files matched by it by typing ```
ls *-1.jpg
```

Does the error actually stop the file from converting? Frequently, ImageMagick encounters things like unknown fields, prints a warning message, and converts the file anyway. If you got a jpeg for that image, then you can ignore the message.

---

### Post by lonoy on 2007-10-27
Thanks

The file still converts okay. 

Your script works to remove the extra jpeg. Would you have a script that would remove all the tifs plus the -1 jpeg please. It's just that I have around 50 folders with over 2000 photos.

Is there anyway of combining a total script that would:

convert from tif to jpeg then
remove tif then
remove -1 jpeg

Sorry if I am sounding greedy:(

---

### Post by lonoy on 2007-10-27
```
 rm *tif rm *-1.jpg
```

The above will remove the tif plus the extra jpeg even though it comes back with a error message.

Would still like to work out a way of doing both the conversion and deleting within the same command.

---

### Post by musicinmybrain on 2007-10-28
In this command, the remove step occurs only if the mogrify step succeeded (but what you call errors probably do not count as failures).

```
mogrify -format jpg -quality 90 *.tif && rm *.tif *-1.jpg
```

If you wanted to delete the tiffs even if the mogrify failed (probably not a good idea) you could do this:

```
mogrify -format jpg -quality 90 *.tif; rm *.tif *-1.jpg
```

---

### Post by lonoy on 2007-10-28
That works great thanks, just what I need:)

At present I am using:

cd ~/Desktop/photos/

then your command as above with the Terminal. I have numerous sub directories under the photos folder. Is there anyway to set the command  to convert everything inside the "photos" folder including subdirectories and their subdirectories? 

By that I mean one massive batch convert.

Thanks.

---

### Post by musicinmybrain on 2007-10-28
```
cd ~/Desktop/photos; for i in *; do cd "$i" && mogrify -format jpg -quality 90 *.tif && rm *.tif *-1.jpg && cd ../; done
```

That should work for immediate subdirectories of photos; for deeper recursion of folders, you'll have to talk to someone with a little more bash scripting knowledge than I. I could whip up a Python script to do it, but that would take a little more time than I have now.

---

### Post by lonoy on 2007-10-28
Thanks again.

 It worked great on the the first sub folder but made no changes to the second folder that was on the same level, though I think that was what you thought I was asking for. Photos has numerous sub folders on the same level eg mollecreek, photos for this example:

lonoy@Neptune:~$ cd ~/Desktop/photos; for i in *; do cd "$i" && mogrify -format jpg -quality 90 *.tif && rm *.tif *-1.jpg && cd ../; done
mogrify: unable to open image `*.tif': No such file or directory.
bash: cd: photos: No such file or directory
bash: cd: Untitled - 01-0.jpg: No such file or directory
bash: cd: Untitled - 01.tif: No such file or directory
bash: cd: Untitled - 1-0.jpg: No such file or directory
bash: cd: Untitled - 111-0.jpg: No such file or directory
bash: cd: Untitled - 1.tif: No such file or directory
bash: cd: Untitled - 2-0.jpg: No such file or directory
bash: cd: Untitled - 2.tif: No such file or directory
bash: cd: Untitled - 3-0.jpg: No such file or directory
bash: cd: Untitled - 3.tif: No such file or directory
bash: cd: Untitled - 4-0.jpg: No such file or directory
bash: cd: Untitled - 4.tif: No such file or directory
bash: cd: Untitled - 5-0.jpg: No such file or directory
bash: cd: Untitled - 5.tif: No such file or directory
bash: cd: Untitled - 6-0.jpg: No such file or directory
bash: cd: Untitled - 6.tif: No such file or directory
bash: cd: Untitled - 7-0.jpg: No such file or directory
bash: cd: Untitled - 7.tif: No such file or directory
lonoy@Neptune:~/Desktop/photos/mollecreek$ 

The mollecreek folder converted and deleted, the photos folder (inside the photos directory) was not changed.

---

### Post by musicinmybrain on 2007-10-28
I assumed all of the folders would have tiffs in them. That doesn't seem to be the case anymore. I guess you could try this. Make sure you have another copy of your photos folder somewhere else just in case this messes up.

```
cd ~/Desktop/photos; for i in *; do cd "$i"; mogrify -format jpg -quality 90 *.tif; rm *.tif *-1.jpg; cd ../; done
```

---

### Post by lonoy on 2007-10-29
That works brilliantly for the above example, thanks again. The time you have spent on this is very appreciated,

Some of the folders have tif files named as either tif or TIF. Can this be included in the code to both convert those files and then deleted them as well please.

The reason for the *-1.jpg is due to the conversion form my old tif files which came across from my Windows system. I noticed that any images saved as a tif in Gimp don't produce a second file after conversion.

Cheers and thanks again, I will frame that code:)

---

### Post by musicinmybrain on 2007-10-29
```
cd ~/Desktop/photos; for i in *; do cd "$i"; mogrify -format jpg -quality 90 *.tif *.TIF; rm *.tif *.TIF *-1.jpg; cd ../; done
```

It would be a good idea to [study basic Bash scripting](http://tldp.org/LDP/abs/html/) at some point, especially [basic Linux commands](http://tldp.org/LDP/abs/html/basic.html), so you can do things like this yourself.

---

### Post by lonoy on 2007-10-29
Thank again. Much appreciated. Will look into the above links.

---

### Post by stani on 2008-02-01
You can also use Phatch (PHoto bATCH processor):
[http://photobatch.stani.be](http://photobatch.stani.be) > free download

It can convert any format to another format and handles subfolders too. You could create a droplet with it and drag&drop all your folders or images which need to be converted.

At the moment there is no delete action, but I could add one easily if you want.

Stani

---

