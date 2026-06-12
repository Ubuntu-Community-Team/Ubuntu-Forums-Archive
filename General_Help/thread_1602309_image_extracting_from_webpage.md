---
title: "image extracting from webpage"
date: 2010-10-21
forum: General Help
---

### Post by vinay nadig on 2010-10-21
hi, I recently saved a large number of web pages from a website on my computer and all of them contains images.
I needed help extracting all the images from the webpages(all of them)
there are about 17000 saved webpages in the folder and all of them have images. I am not sure how to extract images from webpage in batch. google search dint turn up anything.. :(
is there lika a tool or something for the job or should a script be written for it??
any help would be appreciated..
Thnx in advance.. :)

---

### Post by ironic.demise on 2010-10-21
Are all the webpages in html format or a single web page archive?
If they are html all the images should be under a seperate directory (i.e. /webpage/images/header.jpg)

---

### Post by pavel989 on 2010-10-21
> **ironic.demise said:**
> Are all the webpages in html format or a single web page archive?
If they are html all the images should be under a seperate directory (i.e. /webpage/images/header.jpg)

if they are in a seperate folder, you can cd to the website dir

and run "rm -i *.jpg *.png *.bmp" etc, i dont know if this will move through directories, but im afraid to put -r in there as it might delet directories

---

### Post by vinay nadig on 2010-10-21
> **ironic.demise said:**
> Are all the webpages in html format or a single web page archive?
If they are html all the images should be under a seperate directory (i.e. /webpage/images/header.jpg)

nope, the images are not saved in separate folders..
otherwise i would have done what pavel989 has told.
i downloaded all the pages using wget.
i have attached 3 files for u guys to have a look.
Thnx for such a quick reply.. :)

PS : i have renamed the files to .txt format.
but they should open with a web browser.

---

### Post by polki@mac.com on 2010-10-21
Right-click and click "Save pic as". Worked for me!

---

### Post by ironic.demise on 2010-10-21
He wanted a shell script to do the job though...
can't you ```

wget *url*/{*.jpg,*.png,*.bmp,*.gif}
```
 
The same way that some shell scripts only wget .deb files or .zip files?

---

### Post by pavel989 on 2010-10-21
have a look at [http://www.grymoire.com/Unix/Sed.html]("http://www.grymoire.com/Unix/Sed.html")

---

### Post by vinay nadig on 2010-10-21
> **polki@mac.com said:**
> Right-click and click "Save pic as". Worked for me!

lol.. i have around 17000 files.. :P i seriously am not gonna do dat manually one by one..
Whats the use of having a comp then? ;)
but thanx for the try anyway.. :)

@ironic.demise
nope, i tried that.. but it did not work.
here s what i had done to retrieve the webpages..

for x in {1..99999}; do wget --wait=05 --random-wait http://500px.com/photos/$x; done

@pavel989
i checked out the link and tried to follow it.. but got lost after the first few lines.. :(
i dont have much experience with linux.
i ll probably give it another shot later.. :)

---

### Post by pavel989 on 2010-10-21
ultimately, i was recommending to macro a file editor.

but have a look at something like this instead: [http://www.ehow.com/how_7310377_extract-between-tags-html-pages.html](http://www.ehow.com/how_7310377_extract-between-tags-html-pages.html)

google around for a text extractor from a webpage. i searched "extract text from a webpage"

---

### Post by wild hedgehog on 2010-11-01
I suggest a different approach when downloading the site:
Re-download the website using [HTTrack]("http://www.httrack.com/"). (A very powerful tool.) This will give you a complete off-line copy, depending on the selected options, including all the images (instead of txt-files created by wget.) After creating the off-line copy, you may then simply collect the jpgs from your local drive.

---

