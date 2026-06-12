---
title: "Entire pictures folder deletes itself?"
date: 2009-10-06
forum: General Help
---

### Post by akber on 2009-10-06
OK So i was installing some screenlets and trying to config the cube caps in compy (i mention these because they were the two major system alterations i made at the time of MY ENTIRE PICTURES FOLDER VANISHING). 

But to clarify, the folder is still there, but there is nothing in it. I didnt have anything of deathly importance in there, but i did actually have quite a few pictures and a LOT of wallpapers that i consistently use. 

Am i totally screwed? Is it gone forever? I tried running some searches for some of the picture titles i can remember in the folder but nothing comes up. 

Help me ubuntuforums.org, you are my only hope.

---

### Post by c0mput3r_n3rD on 2009-10-06
> **akber said:**
> OK So i was installing some screenlets and trying to config the cube caps in compy (i mention these because they were the two major system alterations i made at the time of MY ENTIRE PICTURES FOLDER VANISHING). 

But to clarify, the folder is still there, but there is nothing in it. I didnt have anything of deathly importance in there, but i did actually have quite a few pictures and a LOT of wallpapers that i consistently use. 

Am i totally screwed? Is it gone forever? I tried running some searches for some of the picture titles i can remember in the folder but nothing comes up. 

Help me ubuntuforums.org, you are my only hope.


Hey just a suggestion, try to be a little more formal and more detailed in your questions and people will be more obliged to to respond.

---

### Post by akber on 2009-10-07
Apologies, but there isnt much more detail than that. Everything in the folder simply vanished and i have never heard of anything like this. 

But perhaps that is a good place to start. 
Has this happened to anyone else? What could possibly cause this?

---

### Post by Roasted on 2009-10-07
So, more or less... you installed something and presto your pictures are... gone? Really?

Are they just hidden? If you view hidden files do you see anything in there?

---

### Post by akber on 2009-10-07
Yes as far as i can remember, i was just configuring conky cube caps, and installing some screenlets, i also edited a picture that was IN my pictures folder using gimp, and saved the edited picture in the pictures folder. If this is of any importance, i used both those pictures (the edited and the original) and set them as top and bottom cube caps, but they were png and couldnt be used, so i just changed the extension. Thats the last i remember of my pictures folder. 

And i tried the hidden folder viewing, no luck :(

---

### Post by akber on 2009-10-07
bump

---

### Post by booshire on 2009-10-07
what do you get with ls -l ~/pictures ?

---

### Post by akber on 2009-10-08
**** it, I have come to terms with the loss of all the pictures, just hope it doesnt happen again.

---

### Post by mechro on 2009-10-08
Have you checked Deleted Items/Trash?

---

### Post by akber on 2009-10-08
Yes, nothing.

---

### Post by CiaoCiao on 2009-10-08
IF you are certain that your photos are nowhere to be found, then alas, they are most likely gone.

If I was in your situation I would read up on something like this.  (Note : I have never done this with Ubuntu and have no experience with it on a Linux system.  )

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by skillllllz on 2009-10-08
Is it possible some other partition or device  has been mounted to that folder, thus obfuscating the contents of the folder?

---

### Post by mozkill on 2009-10-08
this is a problem where a simple command line search solves the day:

find / -name *.jpg 

or something like that...

thats what I would recommend.

---

