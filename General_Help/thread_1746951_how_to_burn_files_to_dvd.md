---
title: "how to burn files to dvd"
date: 2011-05-02
forum: General Help
---

### Post by theVenerable on 2011-05-02
Hi.
Im trying to burn video ts files to dvd.. but cant install the software.
as im not used to this command prompt stuff,and it just seems relentless with anything i try to install, im unsure what to do, or what might go wrong.

> [http://www.k3b.org/](http://www.k3b.org/)




I think i'd rather just convert it to an .iso in my windows, then burn it on ubuntu with a .iso burner.
can you recommend a good iso burner on ubuntu, that can be installed straight from the software center.
thanks

---

### Post by yetiman64 on 2011-05-02
You may very well have burner software already installed go to Applications > Sound and Video > Brasero Disc Burner. Open it and use Data Project. **Edit**: You can write a project to an iso file in here or burn an image to disc from an iso.

Another way to use it (easier) is to associate it with blank dvds. 

To do this open any nautilus window (eg. your home folder), Edit > Preferences > Media Tab, under "Other media" use the side arrow to get a drop down box, under "Type" select "blank dvd disc", and ensure "Action" is set to "Open cd/dvd creator".

Now any time you insert a blank dvd in your drive a window will pop up for you to drag files into. There is a button in the top right of this window for writing the files to disc.

---

### Post by theVenerable on 2011-05-02
Thanks, 
I dont have a 'sound and video' option in my applications , but its ok, i found brasero anyway.

I dont want to 'write a project to iso', i find that software ive used thus far on ubuntu for this isnt as effective as convertxtodvd on windows.
 ive allready got the file written in  ts folder.
I need to convert the ts vob files to an iso, so i can burn the iso with the software on ubuntu. but as i cant do this on ubuntu, i'll have to convert from windows software, then bring it bak to ubuntu to burn it lol, becasue my virutal xp box running inside ubuntu wont allow me to burn discs.. 
this really begs the question.. why am i using ubuntu? lol
it looks nice, but at the moment, for me  it just a hinderance.

thanks tho, i'll use that one if it does a good job

---

### Post by SeijiSensei on 2011-05-02
If you're trying to write a DVD from existing video files, take a look at **DeVeDe** (in the repositories).  It will take the files and build an ISO image that you can burn with K3b or a similar burning application.  DeVeDe handles multiple audio tracks and subtitles and can build simple DVD menus if you'd like.

---

### Post by theVenerable on 2011-05-02
im not sure the results are quite up the the convertxtodvd standard.
I tried dvdstyler also, but it just kept crashing

Its ok, i managed to get k3 installed, and can burn ts or iso folders/files with that.
thanks

---

