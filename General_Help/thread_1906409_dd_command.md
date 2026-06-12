---
title: "dd command"
date: 2012-01-09
forum: General Help
---

### Post by LindaVermeulen on 2012-01-09
Hi 

I am currently trying to create a image file to load on a CF Card using the dd command. but for some reason it firstly created a blank image file and now it is creating no image file. 

What I am trying to do is the following: I downloaded a embcop file and then also three plugins to add to this program. I placed the files of the plugins under tools of the main file, embcop, as I would like to create one image file (now firstly I do not know if this is the correct place to put the plugins). Now I have saved the file on my Desktop, with the New Folder that I would like to place it in. I typed in the following:

sudo dd if=/home/anesh/Desktop/NacBox of=/home/anesh/Desktop/NACBox.gz

Now it reads it but this is the response I get:
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.000435447 s, 0.0 kB/s

meaning that it is not detecting any files and not writing any records

Then after I created this image file I must now load it onto the CF Card.

Can any one please assist me with some advise as to how to get this thing working.

Thank you so much

---

### Post by Derek Karpinski on 2012-01-09
'if' means INPUT FILE........and you haven't designated a file.  You've only pointed at a directory.

I don't think you can use wildcards with dd either.

I am still a bit lost on what you're trying to do.  Are you just trying to create a gzip file?

---

### Post by LindaVermeulen on 2012-01-09
Yes I am trying to create a gzip file, but everything in that diectory/file needs to be created into a image file

---

### Post by LindaVermeulen on 2012-01-09
Yes I am trying to create a gzip file, but everything in that diectory/file needs to be created into a image file

---

### Post by mörgæs on 2012-01-09
Please don't use 'PLEASE HELP!!!!' in the title.

---

### Post by LindaVermeulen on 2012-01-09
It is on the work Buntu, an =d just started here a week ago and I am new to this whole thing

---

### Post by mcduck on 2012-01-09
> **LindaVermeulen said:**
> Yes I am trying to create a gzip file, but everything in that diectory/file needs to be created into a image file

If you want to create a gzip file, then the tool you need to use is gzip, not dd. ;)

(and quite likely you'll need tar as well, since gzip only compresses single files...)

---

