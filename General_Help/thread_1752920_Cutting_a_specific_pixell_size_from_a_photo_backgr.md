---
title: "Cutting a specific pixell size from a photo background"
date: 2011-05-08
forum: General Help
---

### Post by AmpersUK on 2011-05-08
I have the "Unite" Theme in Drupal which provides a slide show at the top of the website and I need to produce photographs at 938 pizels x 340 pixels.

Now I know how to do this in two operations, but have quite a lot of photographs, and wonder if there is any software where I can do it in one.

Picasa for windows (uggh) shows the pixel count to the right of the "manual" choice but my linux version isn't that sophisticated.

Each photo is different so I don't need a template, just to set up those pixel sizes and have the cutter show this each time.

QUESTION
Does anyone know of a Linux program where I can do this in one operation per photograph?

---

### Post by Matt__ on 2011-05-08
[ImageMagick](http://www.imagemagick.org/script/index.php) should be able to handle that in batches from a terminal :P

```
sudo apt-get install imagemagick
```

then use something like this to resize
```
mogrify -resize 938x340! *.jpg
```
or to preserve the original + make a new scaled copies
```
convert -geometry 938x340! *.jpg 
```

you can get a  graphical interface by:
```
display image.jpg
```
and left click the image to get menu. displays bounding box and its pixel count under the edit tab.

---

### Post by AmpersUK on 2011-05-08
> **Matt__ said:**
> [ImageMagick]("http://www.imagemagick.org/script/index.php") should be able to handle that in batches from a terminal :P

```
sudo apt-get install imagemagick
```

Am I missing something here.

First of all I tried the sudo command and am told I have the latest version.
Then I found I can't see it anywhere in my programs.
Then I went to the website clicked on Download Unix to have a nose around, and came to the three logo.gifs test. On display I see the logo.

How on earth do I get access to the program?

confused dot com :-)

---

### Post by Matt__ on 2011-05-08
open a terminal and navigate to the directory containing the images.
in said terminal type ```
display image.jpg
```  (replace image.jpg with the name of one of your images) for the graphic version
Or use above edited commands with wildcards (*) to resize multiple images



links
[http://www.imagemagick.org/Usage/resize/](http://www.imagemagick.org/Usage/resize/)
[http://www.imagemagick.org/Usage/crop/](http://www.imagemagick.org/Usage/crop/)

---

### Post by AmpersUK on 2011-05-08
> **Matt__ said:**
> open a terminal and navigate to the directory containing the images.
in said terminal type ```
display image.jpg
```  (replace image.jpg with the name of one of your images) for the graphic version
Or use above edited commands with wildcards (*) to resize multiple images
links
[http://www.imagemagick.org/Usage/resize/](http://www.imagemagick.org/Usage/resize/)
[http://www.imagemagick.org/Usage/crop/](http://www.imagemagick.org/Usage/crop/)

This is going to take me ages as the photographs are all over the hard disk, some in directories seven or eight deep.

I need a graphics program I think.

But thanks for your help anyway. I may use this for one offs later once I have got the set done.

It looks like I will have to use Picasa, do the horizontas first and then the verticles. But it is still going to be a real headache.

I may have to re-install microsoft windows as I have several programs that will do it there. Ah well, where's my VirtualBox :-(

---

### Post by QLee on 2011-05-08
[QUOTE=AmpersUK]I have the "Unite" Theme in Drupal which provides a slide show at the top of the website and I need to produce photographs at 938 pizels x 340 pixels.

Now I know how to do this in two operations, but have quite a lot of photographs, and wonder if there is any software where I can do it in one.

Picasa for windows (uggh) shows the pixel count to the right of the "manual" choice but my linux version isn't that sophisticated.

Each photo is different so I don't need a template, just to set up those pixel sizes and have the cutter show this each time.

QUESTION
Does anyone know of a Linux program where I can do this in one operation per photograph?[/QUOTE]

If I have understood you correctly, The GIMP would be able to do what you have detailed by setting the x and y size in the Rectangle Select tool, then using the tool to copy what you haven chosen to select and then paste it to a new file of just your selection.

[Edit] What I have described would normally be called "cropping" and it seemed to me from your description that is what you want, rather than a resize of the whole picture. However, if resize is what you want, The GIMP could resize to scale your pictures for you too.

---

### Post by Matt__ on 2011-05-08
sorry its no help.

Ive been trying to make you a nice script using zenity, but I seem to have forgotten more than I know lol.
All my dialog boxes are working, it just wont execute the mogrify command.

_Any uber-buntu user out there willing to take over?_

a nice little zenity dialog that allows selection of a directory and converts all images within it to the specified size.

> **QLee said:**
> If I have understood you correctly, The GIMP would be able to do what you have detailed by setting the x and y size in the Rectangle Select tool, then using the tool to copy what you haven chosen to select and then paste it to a new file of just your selection.

[Edit] What I have described would normally be called "cropping" and it seemed to me from your description that is what you want, rather than a resize of the whole picture. However, if resize is what you want, The GIMP could resize to scale your pictures for you too.

gimp does one image at a time, the op has multiple images that need crop/resize


[COLOR="Navy"]///edit
there is a batch plugin for Gimp [**here**](http://members.ozemail.com.au/~hodsond/dbp.html) that can do crop/resize/sharpen/rotate and more[/COLOR]

---

### Post by QLee on 2011-05-08
[QUOTE=Matt__]...gimp does one image at a time, the op has multiple images that need crop/resize[/QUOTE]

Yes, I realise that, he also wrote "Each photo is different so I don't need a template, just to set up those pixel sizes and have the cutter show this each time."

---

### Post by Mozai on 2011-05-08
> **AmpersUK said:**
> ...I need to produce photographs at 938 pizels x 340 pixels... quite many photographs... Each photo is different so I don't need a template, just to set up those pixel sizes and have the cutter show this each time.

I'm not sure what you mean by "have the cutter show this each time.

I'm going to assume you mean "I have many photographs, and I need to change their sizes to 938 pixels wide by 340 pixels high."

If this is what you want to do, I can suggest something to try on the command line:

```
cd directory_of_photos
mkdir ../938x340
# assuming all your photos are JPEG images
find -name '*.jpg' -exec convert "{}" -resize '938x340!' "../938x340/{}" \; -print
```

Explained:
- change current working directory to where your photos are
- make a directory to hold the resized photos (just in case you don't like what happens, you will still have the originals).
- find all the files with names that match '*.jpg', 
-- and for each one found, execute 'convert' 
-- with all the parameters before the '\;' mark, 
-- and replace any '{}' marks with the name of each file found.

The '!' in the size parameter will force the image to stretch to fit the size.  If you don't wish the image to be stretched, and just scaled to the maximum size that will fit inside a 938 wide by 340 high box, omit the '!'.

If you want something pointy-clicky to do operations on many images at a time, look among your image-viewing programs for a feature called "batch operations."  Sorry I can't recommend one, since I don't use pointy-clicky stuff when I have to process more than one picture.

---

### Post by AmpersUK on 2011-05-09
> **Mozai said:**
> I'm not sure what you mean by "have the cutter show this each time.

I'm going to assume you mean "I have many photographs, and I need to change their sizes to 938 pixels wide by 340 pixels high."

No, I meant that I wanted the cropper (not cutter - sorry) to be permanently (for this operation only of course) fixed at the size quoted, so I could choose what part of the photo to crop.

I loaded Windows 7 into VBox and downloaded Picasa. The crop tool allows me to choose the size the cropper blade comes to, in the customs part of the sub-menu. Then as I looked at each photo and pressed crop, it just cut to that size. So simple.

One only needs to look at this thread to see how a simple job such as this opens up a whole minefield with Linux - which I am 100% for by the way.

I wonder why Google left that part of the crop tool out in the Linux version?

No matter, the job has been done now.

Thank you to everyone who has tried to help, I am truly grateful to you.

---

### Post by QLee on 2011-05-09
[QUOTE=AmpersUK]...
One only needs to look at this thread to see how a simple job such as this opens up a whole minefield with Linux - which I am 100% for by the way.
...[/QUOTE]

Huh? How can people's confusion about what someone else meant by their question be attributed to "Linux" or any operating system?  People trying to help have only what is written to go on.

The GIMP will do exactly what your Windows program will do, it just requires learning a different interface than Picassa. 

I do understand that a job is easier to do if one uses tools that one is familiar with but once one has learned how to use a new tool, the job can often be done just as easily.

---

### Post by AmpersUK on 2011-05-09
> **QLee said:**
> Huh? How can people's confusion about what someone else meant by their question be attributed to "Linux" or any operating system?  People trying to help have only what is written to go on.

The GIMP will do exactly what your Windows program will do, it just requires learning a different interface than Picassa. 

I do understand that a job is easier to do if one uses tools that one is familiar with but once one has learned how to use a new tool, the job can often be done just as easily.

Of course I looked at Gimp but it won't do what I want in one operation.

Perhaps if I explain, I have 50 photos I need to cut an area of 938x340 pixels and a further 70/75 photos I need to cut an area of 888x223 pixels. It was faster to load Windows, search and load Picasa and do the job, than it would have been to use the Gimp.

However I am willing to be told if you could explain how I can cut a different area from each photo in one operation? In Picasa for windows, I set the size once only, click on crop and crop. Job done.

---

### Post by coldraven on 2011-05-09
In Gimp do this (screenshot)
Then select your  portion, Ctrl+C ,Shift+Ctrl+V, Ctrl+S

---

### Post by AmpersUK on 2011-05-09
> **coldraven said:**
> In Gimp do this (screenshot)
Then select your  portion, Ctrl+C ,Shift+Ctrl+V, Ctrl+S

Ah! I see where I went wrong.

I pulled down the menu on the side, and added 938 as the width and 340 as the height.

I notice that I have to click off the fixed, select the wide area of the photo, then click on fixed and I get the area I want.

I then hit return but it did nothing. As you say, I should get to know it and I am sure I could create a new picture with just another half dozen key strokes.

But I am a working editor of a newspaper and I guess I don't have that sort of time available,

but thanks for your help

I do use Linux for my hobby and when I have time will look further into the gimp. But the present Picasa system does it so smoothly and quickly, I did all 125 photos in less than thirty minutes (care had to be taken in choosing the area to cut out).

I do everything else for the paper in Linux by the way.

---

### Post by SeijiSensei on 2011-05-09
In GIMP, choose the Rectangle Select tool, enter the desired size in the menu as coldraven explained, then place the selection box over the area of the image you want to preserve.  Choose Image > Crop to Selection.  Done.

---

### Post by AmpersUK on 2011-05-09
> **SeijiSensei said:**
> In GIMP, choose the Rectangle Select tool, enter the desired size in the menu as coldraven explained, then place the selection box over the area of the image you want to preserve.  Choose Image > Crop to Selection.  Done.

Yes I know that, now!

But as I mentioned, this didn't work exactly as Picasa does.

I use large files and the pixel count of my photos are huge I am not sure exactly but about 4,500 x 3000.. So the rectangle becomes very, very small. By unticking the "fixed" box, it becomes a proportion I can expand or contract so I can include all I want. Then by clicking fixed again, it presumably uses the large picture I have chosen and reduces the size when I cut and save it.

But all I am saying is, too many operations when I can do what I want with one or two button presses.

Please, lets end it there as Google will eventually put this in the Linux version and quite honestly, this is a one off operation for me for two specific slide shows in a Drupal theme.

---

### Post by QLee on 2011-05-09
[QUOTE=AmpersUK]...
But as I mentioned, this didn't work exactly as Picasa does.
...
But all I am saying is, too many operations when I can do what I want with one or two button presses.

Please, lets end it there as Google will eventually put this in the Linux version and quite honestly, this is a one off operation for me for two specific slide shows in a Drupal theme.[/QUOTE]

If your avatar is a real picture of you then it looks like I am in the same age range, often as people age they become resistant to change if it requires learning a different way of doing what they "already know how to do" (meaning they have worked out a procedure to use the tools they understand). Nothing wrong with that as long as they remain open to the fact that there are "other" ways to accomplish a task and I certainly understand how one might not want to learn for a "one off".

Please mark the thread as solved if you want to end it there, if it remains in the forum without being marked solved you might get more posts (including some that will only read your first post and reply with a answer, without noticing that you've solved your issue.

---

### Post by AmpersUK on 2011-05-09
> **QLee said:**
> If your avatar is a real picture of you then it looks like I am in the same age range, often as people age they become resistant to change if it requires learning a different way of doing what they "already know how to do" (meaning they have worked out a procedure to use the tools they understand). Nothing wrong with that as long as they remain open to the fact that there are "other" ways to accomplish a task and I certainly understand how one might not want to learn for a "one off".

Please mark the thread as solved if you want to end it there, if it remains in the forum without being marked solved you might get more posts (including some that will only read your first post and reply with a answer, without noticing that you've solved your issue.

Ha! I edit a local newspaper and am 71. Each day bears no resemblance to the day before. But my problem is, I am so busy I need to do anything like this quickly and easily. I was an IT Journalist for nearly thirty years and slated any software which wasn't intuitive. I wasn't too liked with software houses but my readers liked me otherwise I wouldn't have survived. 

I also edit a community website and write a blog. When I am not doing that I help my local community My day stretches between 8am and 8pm and I often work weekends.

Not too set in my years yet. But I am sure there will come a time... :)

Not too sure how I can mark this solved? But I will have a closer look around after I have posted this.

---

### Post by QLee on 2011-05-09
[QUOTE=AmpersUK]Ha! I edit a local newspaper and am 71. Each day bears no resemblance to the day before. But my problem is, I am so busy I need to do anything like this quickly and easily. I was an IT Journalist for nearly thirty years and slated any software which wasn't intuitive. I wasn't too liked with software houses but my readers liked me otherwise I wouldn't have survived. [/QUOTE]

Well, in my opinion, "intutive" varies somewhat from person to person and is related to what one already "knows". Thankfully, I don't have the problem you do with "busy", I retired in 2007.

[QUOTE=AmpersUK]
...
Not too sure how I can mark this solved? But I will have a closer look around after I have posted this.[/QUOTE]

It used to be as easy as clicking thread tools but if that no longer works you could amend the subject line of your first post.

[Edit] I wouldn't normally mention spelling, however, since you are an editor you would probably want to be informed that pixel only has one letter "l".

---

