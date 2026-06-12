---
title: "trying to upload photo to website, browse can't &quot;see&quot; photo"
date: 2011-02-03
forum: General Help
---

### Post by oxf on 2011-02-03
Hi ,

I'm trying to upload a photo onto a website. Pretty standard procedure. The problem is when I use the "browse" function on the website and go to the directory on my PC where the photo is located it cant see it, i.e. the directory is empty!

I've checked permissions etc and can see nothing wrong. The "browse" function seems to be able to find all my other older photos OK so I can't figure out why it can't see these ones.
Any ideas what might be going on?

Thanks

---

### Post by Frogs Hair on 2011-02-03
Are the newer photos a different file type than the older ones and does the site have 
restrictions on what type of file can be uploaded ?
 
That is the first thing I would check , if  the browse function  does't see files or packages it is normally because it is an invalid file .

---

### Post by oxf on 2011-02-03
> **Frogs Hair said:**
> Are the newer photos a different file type than the older ones and does the site have 
restrictions on what type of file can be uploaded ?
 
That is the first thing I would check , if  the browse function  does't see files or packages it is normally because it is an invalid file .

This is very strange. They are basic photos of me, taken with the same camera I've used for all my other shots etc. Had my partner take them this morning so I could put them up on professional site where I need a profile. The same run of the mill .jpg 
So what different now???????

Anyway there's two sites actually. The first won't "see" the files as I described. The second does see the files but still wont upload them. A brief, and I mean 1/100 of a second or so, error flashes by. It so fast but I think it say something about incorrect file type/GIF. But is not, it a jpeg from the camera..:confused:

I've also tried reducing the file size pixels etc

---

### Post by tredegar on 2011-02-03
> It so fast but I think it say something about incorrect file type/GIF.
In that case, I'd try uploading a gif, to see if that worked.
The **gimp** will easily save a loaded jpg as a gif

---

### Post by oxf on 2011-02-03
Well I tried renaming the file and that worked!

---

### Post by oldfred on 2011-02-03
One of the photo sites my wife uploads to, does not see all the JPG files from the camera. But if I rename them to .jpg then it works. They assume windows where there is no difference between caps & small letters.

rename -v 's/\.JPG$/\.jpg/' *.JPG

---

### Post by Frogs Hair on 2011-02-03
Glad it worked !

---

### Post by tredegar on 2011-02-03
> Well I tried renaming the file and that worked!

Please clarify: You _renamed_ it as a gif or did you _recode_ it as a gif?

Or as a .JPG or .jpg?

This information just helps me help others, so a reply would be appreciated, as replies seem to have helped you.

Post the solution.

---

### Post by oxf on 2011-02-19
> **tredegar said:**
> Please clarify: You _renamed_ it as a gif or did you _recode_ it as a gif?

Or as a .JPG or .jpg?

This information just helps me help others, so a reply would be appreciated, as replies seem to have helped you.

Post the solution.

As I said I renamed it, thats all! No change of format involved.
e.g photo from camera "1234.jpg" renamed as something like "sunset.jpg"
Have no idea why this worked!

---

### Post by mommajx4 on 2011-06-16
This is exactly my problem and sounds like the solution is perfect.  I am not sure how to go about the renaming process.  I am new to Linux/Ubuntu.  Folders show up in browse but not individual photo files. Using Ristretto 0.0.91-2

***sites don't recognize JPG file renamed to jpg***

---

### Post by weyland42 on 2011-08-25
I have almost the reverse of the topic problem -- I have uploaded an image, and I can see it fine in the Profile dialogue, but it doesn't appear in posts. (It's within allowed specs, at 100x100 16kb.)

---

