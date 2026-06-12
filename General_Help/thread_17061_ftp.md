---
title: "ftp ?"
date: 2005-02-25
forum: General Help
---

### Post by ThePainter on 2005-02-25
Hi,
Heres a strange problem I have just found a work around for but I would like someone to explain what the problem was.
Im using warty with gnome.

I have a web site which was written in XP and works OK.
I have just added a page to it tonight.
I wrote the html file in gedit and I created 6 jpg's in gimp.
I transfered them to my server at blueyonder with gftp.
The site opens OK apart from that new page ? 
It gives the Access Denied error.
I fiddled around and found that when I transfer the html files with gftp they error but if I transfer them with the Nautilus file manager they open OK.
But It is the opposite with the larger jpg'.s
I made 3 wallpapers and 3 thumbnails of them.
The thumbnails transfer OK with Nautilus but the wallpapers go all stripy and the colours get messed up but when I transfer them with gftp they open OK ?

Any ideas what is going on here ?

And I hope this helps anyone else who has this problem.

Also when I view directories there are duplicate files with a ~ after the extension but I cant see them in my directory even with hidden files unhidden.
What are they ?
Ive seen them before and you can only view them via certain programs via their open file dialogue boxes.

[HERE](http://www.thepainter666.pwp.blueyonder.co.uk)  is the site if anyone fancies a browse.

---

### Post by ThePainter on 2005-02-25
Hi,
Sorry, I keep putting things in the wrong message boards, thatnks for moving it.

Ive been fiddling about a bit more and have found that If I make a wallpaper as a gif then firefox wont load it at all but when I use small ones as buttons they are OK ?

This is similar to the jpgs that are messed up when transfered with nautilus, the small thumbnails are OK and the large wallpapers get messed up.

I dont think it is the size with the gif's because I tried a gif and a png both about the same size and transfered them both with gftp and the gif wouldnt load but the png was OK.

I hate to say this but I had none of this trouble in XP  :-({|=

---

### Post by ThePainter on 2005-02-26
Hi,
OK Ive done a controlled experiment (if anyones interested)

Ive put the same 4 pics in 5 different folders and uploaded them to my site using different methods and viewed them all in 3 diferent browsers and got the same results.

Browsers: IE6 (in XP and via Crossover office in UBUNTU) , Konqueror (in UBUNTU) and Firefox (in UBUNTU)

Links to each folder uploaded with :

Nautilus file browser  [HERE](http://www.thepainter666.pwp.blueyonder.co.uk/NAUT/UB.html) 
Pics messed up

GFTP  ftp client  [HERE](http://www.thepainter666.pwp.blueyonder.co.uk/GFTP/UB.html) 
Wont load

KONQUEROR   browser/file manager [HERE](http://www.thepainter666.pwp.blueyonder.co.uk/KONQ/UB.html)
Wont load

IE6 in XP cos IE6 in Cross over Office wont ftp ? [HERE](http://www.thepainter666.pwp.blueyonder.co.uk/IE/UB.html) 
Works fine

And this one I transfered the pics with GFTP and the html file with Nautilus  
[HERE](http://www.thepainter666.pwp.blueyonder.co.uk/FIXED/UB.html)
Works fine

Please try these on your system and see what results you get. 
There must be a bug in UBUNTU because I cant believe there is the same bug in gftp, konqueror and Nautilus and the UBUNTU system is the only constant associated with the problem during the transfer.

I am using UBUNTU Warty which I ran upgrade all in synaptic the other day so it has the  2.6.8.1-5-386 kernel now.

---

### Post by ThePainter on 2005-02-27
Bump

---

### Post by jobezone on 2005-05-12
I can't help with this, since my small jpeg 3k images I send to ftp via nautilus work fine. Since you've compiled so much information on what is clearly a bug, why not report it at bugzilla.ubuntu.com ?

You'll need to register first.
Then, search for this bug on the program nautilus . If you find someone has already reported this bug, add your experiments to the bug's comments. If not, create a new bug report on the package.

Sorry I can't be of more help, but there seems to be bad bugs around ftping in nautilus.

---

