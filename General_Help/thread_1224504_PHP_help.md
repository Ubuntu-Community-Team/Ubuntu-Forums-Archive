---
title: "PHP help"
date: 2009-07-27
forum: General Help
---

### Post by Cyked on 2009-07-27
Not sure where to post this....

Looking for some "clean" PHP code for a very light photo album.  

Right now I have something that is almost 1500 lines of code that calculates and displays several fields (image size, original size, resized size, image description, etc.) along with the thumbnail preview.   

I'm looking for something that would be lighter and pretty much only displays a clickable thumbnail (no text, no frames/borders with a numbered bar at the top/bottom.

---

### Post by Cyked on 2009-07-28
Anyone know of anything?

---

### Post by hessiess on 2009-07-28
Generally the words `cleen' and `php' don't go together;) I don't know of any simple php image managers, though what you describe wouldn't be hard to implement.

---

### Post by Cyked on 2009-07-28
> **hessiess said:**
> Generally the words `cleen' and `php' don't go together;) I don't know of any simple php image managers, though what you describe wouldn't be hard to implement.

Implement as in write the code in the first place?

At any rate, thanks for the info. I guess I'll just stick with what I have.  I can tweak things to make it work the way I want.  i.e. the end product looks good.  I'd just assume have cleaner code that wouldn't do processing for XYZ function, because in the end all I'm doing is commenting out the output lines.

Thanks hessiess.  Anyone else feel free to chime in though. :D

---

### Post by hessiess on 2009-07-28
Depending on how well written the application is, you should be able to strip out the image size calculating code relitavly easily.

---

### Post by Cyked on 2009-07-28
> **hessiess said:**
> Depending on how well written the application is, you should be able to strip out the image size calculating code relitavly easily.

And also taking into account I have the ability to do so. 
Thanks for the vote of confidence though :)

At any rate, I can probably muck around in the code for a few hours and figure it out.  Its not even 1500 lines.  I'll probably learn something in the process as well. :D

---

### Post by s.fox on 2009-07-28
Hi,

If you run into coding troubles we may be able to assist you in the [Programming Subforum]("http://ubuntuforums.org/forumdisplay.php?f=39"). :D

Hope you get on okay,

-Silver Fox

---

### Post by Cyked on 2009-07-28
> **Silver_fox_ said:**
> Hi,

If you run into coding troubles we may be able to assist you in the [Programming Subforum]("http://ubuntuforums.org/forumdisplay.php?f=39"). :D

Hope you get on okay,

-Silver Fox

Thanks.  I almost posted this there originally.  Not sure why I didn't.  I think my original inclination was that that sub-forum was for something specific to the OS.   I probably hadn't had enough coffee when I posted. :D

---

### Post by Diabolis on 2009-08-02
I need a something like that too, the best I've found is this: [https://sourceforge.net/projects/ck-gallery/](https://sourceforge.net/projects/ck-gallery/) The main script has only 277 lines of code.

If you need the GD library:
```
sudo apt-get install php5-gd
sudo /etc/init.d/apache2 restart
```

However I haven't managed to see the thumbs correctly, I'll post back if I get it to work properly. Thickbox isn't working for me, the load bar hangs and nothing happens.

EDIT: The problem was that I placed the "gallery" folder outside of my apache folder. :redface:

---

### Post by satish_j on 2009-08-02
If you undestand the code you have,you can tweak it around to work it the way you want.
silver_fox is right.You should seek some help from Programming subforum.

---

### Post by Cyked on 2009-08-03
> **Diabolis said:**
> I need a something like that too, the best I've found is this: [https://sourceforge.net/projects/ck-gallery/](https://sourceforge.net/projects/ck-gallery/) The main script has only 277 lines of code.

If you need the GD library:
```
sudo apt-get install php5-gd
sudo /etc/init.d/apache2 restart
```

However I haven't managed to see the thumbs correctly, I'll post back if I get it to work properly. Thickbox isn't working for me, the load bar hangs and nothing happens.

EDIT: The problem was that I placed the "gallery" folder outside of my apache folder. :redface:

I snagged the code from [weatimages]("http://nazarkin.name/projects/weatimages/"), but have used many others... Plugger, [SPGM]("http://spgm.sourceforge.net/"), as well as others I didn't like as well.

satish_j, If I knew the code well enough I wouldn't need to post. :D  I haven't played around with code for years, in any language.  I think I need to open the code in a real text editor and look at it so I can see full sections of code at a time, rather than via putty.

---

