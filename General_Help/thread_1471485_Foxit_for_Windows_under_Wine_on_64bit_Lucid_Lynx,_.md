---
title: "Foxit for Windows under Wine on 64bit Lucid Lynx, steps that should work"
date: 2010-05-03
forum: General Help
---

### Post by Dvomedo on 2010-05-03
I wanted Foxit for Windows since I needed something that can deal with annotations.

** Issue:** Foxit Reader (3.2) for Windows did not work on 64bit Ubuntu Lucid (10.04 LTS) under Wine (1.1.43). Foxit for Windows was needed because Foxit for Ubuntu lacks desired functionality.

These are rough **steps** to make it work:


[LIST=1]
[*]**Install Wine.** (if you don't have it already)
[*]**Download Foxit Reader** (take download options and download zip instead of exe, I am not sure if this is necessary but that resolved some issues previously, feel free to test if you want)
[*]**Unpack** that zip to (for example) /home/username/.wine/dosdevices/c:/Program Files/Foxit/
[*]right click the exe, properties>permissions and select "**Allow executing** file as program"
If you just try to run it, it will do something (shows that it's busy) and then just close. If you try to run it from the terminal using "wine start 'c:\File location\Filename.exe' (you will see that it complains about odbc32.dll)Run winetricks to get that i.e.
[*]**Install/Run winetricks** [edit: not true that it is installed as I thought see the post from Benjaminz below how to install)], just type winetricks in the terminal) and **take** the:
[LIST]
[*][edit: not needed (Sepiraph checked)] native_mdac  (override odbc32...) (maybe could be skipped try it, I'm just presenting it because that's  what I did, but I'm not sure it is needed, because it worked only after I added mdac25) and
[*]**mdac25** (Microsoft ODBC drivers, you'll have to go through license agreement)
[/LIST]
 
[*]???
[*]Profit!
[/LIST]
 It should work after step 5, it did for me. Good luck.


Hope this saves someone a bit of time.  =)
**tl;dr Install mdac25 using winetricks**

---

### Post by Benzjaminz on 2010-05-13
Hi Dvomedo

Thanks for the post. Very helpful.

One comment though. winetricks was not automatically installed for me when wine was installed but just requires:

wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)

and then

sh winetricks

to run it

(see [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks))

---

### Post by Dvomedo on 2010-05-13
Hi, thanks for the feedback.

I think you're right. After making the post above I remembered that I actually might have installed winetricks myself before to solve some other issue.

---

### Post by Sepiraph on 2010-06-19
Thanks for the post Dvomedo.  It worked for me without installing native_mdac (I installed mdac25 1st).

---

### Post by osfight.de on 2010-09-04
Worked for me too, thanks. 

I posted a German translation here: [http://www.osfight.de/?lang=de](http://www.osfight.de/?lang=de)

---

