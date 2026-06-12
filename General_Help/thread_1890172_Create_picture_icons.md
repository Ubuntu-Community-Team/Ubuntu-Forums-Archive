---
title: "Create picture icons"
date: 2011-12-02
forum: General Help
---

### Post by Gordonisnz on 2011-12-02
[http://www.gimp.org/tutorials/Creating_Icons/](http://www.gimp.org/tutorials/Creating_Icons/)

hello. i'm following the above example - But its not telling me what I want to know...

I have an existing picture..

I have found the zoom function & can 'see' my new picture at 1:8 size. (smaller)..

How do I "save" the new icon / picture ?

I've saved it (changing the filename), but re-opened it & its the same size as the original.

My main target / goal us to reduce a 400KB file to 50KB or so.. - Shrink the KB size of it to create small icon pictures. (I have a number of pictures - different KB sizes

I do expect some loss in sharpness / clarity.

---

### Post by staf0048 on 2011-12-02
in gimp:

Select image/scale image

set your desired resolution and save

Hope that helps!

---

### Post by deonis on 2011-12-02
So you want to batch resize a few images, right? or do you want to create thumbnails of your images ? And what do you want it for ?

---

### Post by Gordonisnz on 2011-12-02
> **staf0048 said:**
> in gimp:

Select image/scale image

set your desired resolution and save

Hope that helps!

it helps a LOT :)

Thanks.

I tried it on one image 200KB, and  the icon is 14KB.

I'll work on the others now :)

---

### Post by Gordonisnz on 2011-12-03
> **deonis said:**
> So you want to batch resize a few images, right? or do you want to create thumbnails of your images ? And what do you want it for ?

Basically, I've got a website with a big picture in the middle of the screen & 8 'small' pictures at the top - Press a picture at the top & the big picture changes.

Currently the 'small' pictures use HTML tricks to display the pictures small. but i want the actual KB to e smaller too..

I'm creating icons / smaller pictures for the top area so the website doesn't load 1-2-3MB of pictures in one go.... - It will just download the smaller versions and the 1 big version.

---

### Post by deonis on 2011-12-03
Ok so you want something like that 

[http://dsn.yips.ca//index.php?option=com_content&task=view&id=43&Itemid=46](http://dsn.yips.ca//index.php?option=com_content&task=view&id=43&Itemid=46)

in my case I am doing this with PHP  but main principle is the same 

if so you might want to install gimp-plugin-registry it's in repo ... 
this will install: filter-> batch 

How to use it I think you will figure out :)

BTW, what you want is not an icon but thumbnail 

hope that help 

good luck

---

### Post by deonis on 2011-12-03
forgot to say that this plugin will allow you to resize, edit, etc multiple images!!!

---

