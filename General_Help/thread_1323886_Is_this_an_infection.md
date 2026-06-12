---
title: "Is this an infection?"
date: 2009-11-12
forum: General Help
---

### Post by viking_maniac on 2009-11-12
I was searching for wallpapers this day, and I found one suitable. When I was about to click on the image, to get a full size image in Firefox for review and be able to "save as", I immediately got the download box to "save as", and the image was labelled as a "binary". Usually, this doesn't happen.

I downloaded the picture and it was a .jpg file that I could preview and open, just as any other jpeg file. Later I started thinking that maybe I did something that I shouldn't have done. Haha. I guess this is the Windows ghost that is hoovering over me, and I don't know how Linux works regarding spyware, viruses, and etc.

What do you think?

---

### Post by Commander_Keen on 2009-11-12
No.. not a virus.
I wouldn't worry about it.

---

### Post by Mark Phelps on 2009-11-12
While it IS possible to bury a virus in a jpeg file, the problem it will encounter is that it will not run on your system because Linux doesn't recognize .com or .exe files, nor is it able to run MS Windows executables.

So, as already said, don't worry about it.

But, to be safe, I wouldn't copy that file to an MS Windows box.

---

### Post by Giblet5 on 2009-11-12
All images, other than ASCII artwork, are binary files.

Still it's not to late to wave ones arms in the air and run in circles yelling 'O NOEZ! I gotz H1N1 in mah buntus!' cuz that'd be pretty funny.

OK... **I** would think that's pretty funny...

---

### Post by viking_maniac on 2009-11-13
The file in question came from this website:
[http://www.manywallpapers.com/](http://www.manywallpapers.com/)
I don't know what site this is anyway, I just found my wallpaper there trough Google images.
And it did have a .jpg extension at the end, not an exe or anything like that.

I'm just curious about why Firefox didn't show the picture as usual, and instead just opened the download window and calling it a "binary".

---

### Post by fluffman86 on 2009-11-13
It wouldn't matter if the extension was there anyway.  Only Windows actually cares about those stupid extensions.  You can have a file called picture.boogadeeboo and if the file looks like a jpg, it opens as a jpg.  And you can have a file called picture.jpg, but if it's actually a text file with bash scripting in it, it will open as a bash script.

---

### Post by lisati on 2009-11-13
> **Mark Phelps said:**
> While it IS possible to bury a virus in a jpeg file, the problem it will encounter is that it will not run on your system because Linux doesn't recognize .com or .exe files, nor is it able to run MS Windows executables.

So, as already said, don't worry about it.

But, to be safe, I wouldn't copy that file to an MS Windows box.

+1. 

<aside>I've seen MS-DOS .com files that are really .exe files in disguise. I've also read of a file that was simultaneously a valid .bat and a .com file, which involved some tricky machine language buried in a REM statement at the beginning of the file, so command.com could call it up as either type of file.</aside>

---

### Post by fluffman86 on 2009-11-13
I took a look around.  It appears that those files are safe, but it's asking you to open it differently because the link you click is something like "http://example.com/12387635987" so that people will actually download the file to keep instead of being confused with what to do with just viewing it online.

---

### Post by JBAlaska on 2009-11-13
> **Giblet5 said:**
> 
Still it's not to late to wave ones arms in the air and run in circles yelling 'O NOEZ! I gotz H1N1 in mah buntus!' cuz that'd be pretty funny.


Please post a video example on youtube and post link here..

---

### Post by viking_maniac on 2009-11-13
> **fluffman86 said:**
> I took a look around.  It appears that those files are safe, but it's asking you to open it differently because the link you click is something like "http://example.com/12387635987" so that people will actually download the file to keep instead of being confused with what to do with just viewing it online.

Thanks for your research! :)

---

### Post by SirBismuth on 2009-11-13
> **Giblet5 said:**
> All images, other than ASCII artwork, are binary files.

Still it's not to late to wave ones arms in the air and run in circles yelling 'O NOEZ! I gotz H1N1 in mah buntus!' cuz that'd be pretty funny.

OK... **I** would think that's pretty funny...

:D I also think it's funny, print that on the back of a shirt with "chmod +x......." on the front, the "all your base are belong to us" translation for the Linux command line, and I would buy it!

B

---

### Post by Olav on 2009-11-13
> **viking_maniac said:**
> The file in question came from this website:
[http://www.manywallpapers.com/](http://www.manywallpapers.com/)
I don't know what site this is anyway, I just found my wallpaper there trough Google images.
And it did have a .jpg extension at the end, not an exe or anything like that.

I'm just curious about why Firefox didn't show the picture as usual, and instead just opened the download window and calling it a "binary".

One reason could be that the server advertises the content type for the file as something different than "image/jpeg", like "application/octet-stream". When a browser can't handle a content type by itself, it will most often offer the option to save the file instead.

Learn something about MIME-types here: [http://en.wikipedia.org/wiki/Mime_type](http://en.wikipedia.org/wiki/Mime_type)

A web server may also set the Content-disposition header when it replies to a browser request. For instance: "Content-disposition: attachment; filename=wallpaper.jpg" is a suggestion to the browser not to attempt to display the file, but to save it (most of the times, through the Save as dialog). This should work in most browsers even if the Content-type is, say, "text/html".

These headers are part of HTTP communication, not part of HTML or af any file format. So they happen "behind the scenes" and most users aren't aware of them.

But since you asked...

---

