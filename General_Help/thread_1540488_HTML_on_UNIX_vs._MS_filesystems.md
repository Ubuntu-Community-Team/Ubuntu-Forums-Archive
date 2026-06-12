---
title: "HTML on UNIX vs. MS filesystems"
date: 2010-07-27
forum: General Help
---

### Post by KWLLC on 2010-07-27
I am taking an HTML class and the text was written with the MS filesystem in mind. The discussion is about absolute vs. relative addressing of local files.
I can do absolute addressing of a file on another HD by writing 
<a src="/media/Data-Store/.../tutorial/image.jpg"
but I'm stumped about how to run the chain back up to /media/ and then down to the location of the image file like the text suggests.
src="../../../media/Data-Store/.../image.jpg" doesn't work.
so I tried using the <base href="/media/Data-Store/.../tutorial"> tag 
and src="image.jpg" /> but that doesn't work either.
How does one go about running the UNIX file system using relative paths and the BASE html tag?
I'm attaching the html source files and a quick and dirty of my file system layout if that helps any. 

TABIA!!

---

### Post by SoFl W on 2010-07-27
Is your data storage directory part of the web access group?  Are the permissions correct?

---

### Post by marshmallow1304 on 2010-07-27
From looking at the PDF, it looks to me like you're not getting all the way back up into the root of the FS.

[HTML]<img src="../../../../../media/Data-Store/MPTC/HTML-XML/StudentFiles/tutorial.02/tutorial/dube.jpg">[/HTML]


Also, wouldn't it be easier to copy the images and other necessary files to your working directory?

---

### Post by KWLLC on 2010-07-27
Thank you berry much for taking time to help me out. In answer to you KISS observation: Easier, yes. But then I still wouldn't have an understanding of why I couldn't make it work. I was a mainframer for 30+ years and the reason I became a widely known expert on CICS was by picking it apart until I grokked it. Having said that:
Are you saying that the number of ../s is the secret? That I just goofed on the count of directories backing up the chain? But then why didn't the <base href= not work? I gave it the exact path to the jpg and the <img src="filename" should have worked. I know I can get to the jpg since it displays correctly if I code the entire absolute filename in the <img tag. Any ideas?

---

### Post by KWLLC on 2010-07-27
I don't know what the web access group is, but if I code the <img with an absolute path, the page displays correctly and I thought the <path tag should have directed the http engine to look there so I only needed to refer to the filename.

---

### Post by marshmallow1304 on 2010-07-27
Got it!

I'd never used the <base> tag before, so it took some messing about, but I figured it out.  <base> expects a web address or a location.  To tell <base> that the target is local instead of on the web, you have to use file:// like so:

[HTML]<base href="file:///media/Data-Store/MPTC/HTML-XML/StudentFiles/tutorial.02/tutorial/">
...
<img src="image.jpg">[/HTML]

---

### Post by WorMzy on 2010-07-27
".." means parent directory, so if you were in /media/data-store/work/tutorials, .. would mean "work". From there, .. would mean "data-store", so "../../image.jpg" would be a relative link from "/media/data-store/work/tutorials" to "/media/data-store/image.jpg".

Relative paths are the same format on either Windows or Unix-based OS', it's only absolute paths which are different, due to fundamental differences in the filesystem.

---

### Post by KWLLC on 2010-07-27
aaahhhh!!! The light bulb ignites!! If my html is running from /media/home/waldo/tutorial then I would have to code ../../../ to get to media and /Data-Store/work/images/ to get to the jpg. Putting it together, I would code ../../../Data-Store/work/images/image.jpg to refer to it.
In z/VSE it only takes a JCL LIBDEF statement to set up a symbolic/relative path. I can see why UNIX and MS folks prefer to replicate data rather than deal with the addressing complexities that can arise.
BTW: The path information in the text was incomplete so I never even considered using the resource protocol file: to resolve it. There are subtleties to that solution that I need to understand.
Anyhoot...thanks to all for the help! Let me know if you ever need to use a mainframe and have any questions about how.

---

### Post by worksofcraft on 2010-07-28
While I know that in the Microsoft world people put all their documents in the documents folder and all the pictures in the pictures folder and all their videos in the video folder and so on... and I even know that some people think it is such a good idea that they do it on Linux too :D

However, IMHO you do much better keeping all files relating to each project in their own self contained file hierarchy. It will make much easier to archive and restructure and distribute that project as an entity.

Also be wary of going back up FSH tree like that because permissions may be restricted. When you REALLY want to have shared resources I think best practice is to create a link from the project specific folder to the shared entity ;)

---

