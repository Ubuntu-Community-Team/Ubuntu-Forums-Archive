---
title: "How to batch resize images to keep under a certain size"
date: 2011-10-07
forum: General Help
---

### Post by webbber on 2011-10-07
Hi all,

I'd appreciate a bit of help on this. I have a collection of about 600 photos from my wedding. I will be uploading them to a photo website to make prints, and the photos need to be under 10mb.

I have been dabbling with mogrify and the gimp tools, but I have not been able to achieve what I would like to do, which is to batch resize a folder full of images with the scaling automatically determined so that the final image size is under 10mb. 

Anyone got any ideas? There may be a program that does this, or it may be a matter of scripting. 

Thanks 

Leigh

---

### Post by nothingspecial on 2011-10-07
You could try imagemagick.

I don't know if you can specify a size in mb but to reduce all the photo's by half

```
for p in *.jpg; do convert -resize 50% "$p" new_"$p"; done 
```

Use 75% or whatever is suitable for your requirements.

This assumes they all end with a .jpg extension, change that bit if they don't.

---

### Post by webbber on 2011-10-07
> **nothingspecial said:**
> You could try imagemagick.

I don't know if you can specify a size in mb but to reduce all the photo's by half

```
for p in *.jpg; do convert -resize 50% "$p" new_"$p"; done 
```

Use 75% or whatever is suitable for your requirements.

This assumes they all end with a .jpg extension, change that bit if they don't.

Thanks for the above. It was really something a bit more fancy whereby imagemagick or another program actually scaled automatically so that all final images were 10mb.

---

### Post by haqking on 2011-10-07
you can also do this from right click context menu in nautilus

sudo apt-get install nautilus-image-converter imagemagick

then select images and choose edit menu or right click

---

### Post by Bonster on 2011-10-08
try phatch

---

### Post by coldraven on 2011-10-08
+1 phatch
It has a maximum file size in the save options

---

### Post by tomek_wap on 2011-11-08
> **haqking said:**
> you can also do this from right click context menu in nautilus

sudo apt-get install nautilus-image-converter imagemagick

then select images and choose edit menu or right click

the above doesnt seem to work. there's nothing from the right click menu.

Phatch seems unusable.


but

"mogrify -resize 1024x800 -format -quality 85 jpg *" in terminal works perfectly :)

---

### Post by haqking on 2011-11-08
> **tomek_wap said:**
> the above doesnt seem to work. there's nothing from the right click menu.

Phatch seems unusable.


but

"mogrify -resize 1024x800 -format -quality 85 jpg *" in terminal works perfectly :)

that depends on what you are using, it is only good for nautilus and you need to log out and back in again first.

Anyways use what works for ya.

cheers

---

### Post by tomek_wap on 2011-11-08
Indeed :)
Needed to re-log in.
Works now. And qualitywise not bad either.
Thnx

---

### Post by haqking on 2011-11-08
> **tomek_wap said:**
> Indeed :)
Needed to re-log in.
Works now. And qualitywise not bad either.
Thnx

no worries, you are welcome.

---

