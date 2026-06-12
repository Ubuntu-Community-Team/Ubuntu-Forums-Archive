---
title: "Remove a font and replace it with a better one."
date: 2012-01-02
forum: General Help
---

### Post by bill23 on 2012-01-02
I have a font I would  like to remove an replace with a better model. The font in question is  "Italian Cursive, 16c" It does not look anything like it should. At the  site 'fontspace' I found the same font looking as it should. I tried to  install it, thinking I would get an option to keep the current font of  that name or replace it with the newer one. It's a zip file an reads as:  "lord-kyl-mackay_italian-cursive-16th-c.zip" When I opened and  extracted it, it shows this: "Italian Cursive, 14th c.TTF. When I tried  to install it I get 'installation failed'. 


I went to /usr/share/fonts to see if it could be remove from there but I  was not able to track it down? I checked out /usr/local/share/fonts but  that turned out to be empty. 

If anyone can give me a hand with this, thanks are on their way.

bill23

---

### Post by hhh on 2012-01-03
Have a look in the hidden folder .fonts in your home folder.

---

### Post by bill23 on 2012-01-03
I would look there if I knew how to find the .hidden fonts folder? So far it has eluded me?

---

### Post by gandaran on 2012-01-03
> **bill23 said:**
> I would look there if I knew how to find the .hidden fonts folder? So far it has eluded me?
go to menu bar » view » show hidden files, create the .fonts folder if you don't find any there in the hidden home directory and move your new font to the folder.

---

### Post by bill23 on 2012-01-03
I found it just where you said it would be. I deleted the font there and again from the Trash as well. Then installed the font 'Italian Cursive, 16th C' from  "lord-kyl-mackay_italian-cursive-16th-c.zip" extracted it, then installed it. However when I went to my Mozilla Thunderbird to test it out. It showed the same font as before, which was not what I was hoping for. It looked more like a Times New Roman instead of a Cursive font. The thumbnail in the .fonts folder looks as it should but when I go to use it, that is another story and or font that I see?

Don't know why this happened? I had the same problem with the original font and now it is just repeating the problem? Going to try something if it works I will let you know, if not... I shall be back.

Tried removing that 'font' and installing it from a different site but result was the same a generic font but no cursive. The thumbnail looked good but when it came to use it, it was quite different from advertised.

---

### Post by hhh on 2012-01-04
I think you'd need to logout/login to activate the font, and to change it for Thunderbird try these links (In Linux, the settings won't be under Tools>>Options but rather Edit>>Prefernces)...
[http://email.about.com/od/mozillathunderbirdtips/qt/et_default_font.htm](http://email.about.com/od/mozillathunderbirdtips/qt/et_default_font.htm)
[http://www.freeemailtutorials.com/mozillaThunderbird/displayOptionsFonts.cwd](http://www.freeemailtutorials.com/mozillaThunderbird/displayOptionsFonts.cwd)
[https://addons.mozilla.org/en-us/thunderbird/addon/theme-font-size-changer/](https://addons.mozilla.org/en-us/thunderbird/addon/theme-font-size-changer/)

---

### Post by oldos2er on 2012-01-04
You need to update the font cache after adding or removing fonts. ```
sudo fc-cache -fv
```

---

### Post by bill23 on 2012-01-04
I don't necessarily want to make the font 'Italian Cursive,16th C' my default font for Thunderbird but I would like to use it as it is meant to be seen not as some generic new roman or what have you Mr Smith?  The image is what the Font in question looks like. 
    Is this a sixteenth century Italian Cursive Font?
   
       
                                                                                              

[FONT=Italian Cursive, 16th c.][SIZE=4]
[/SIZE][/FONT]
  

[FONT=Italian Cursive, 16th c.][SIZE=4]
[/SIZE][/FONT]
  

[IMG]http://i65.photobucket.com/albums/h239/Belquad/Screenshot-01042012-095826PM.png[/IMG]

---

### Post by bill23 on 2012-01-05
[SIZE=3][FONT=Franklin Gothic Medium]I have used both AbiWord as well as LibreOffice to check on This is getting to be a very strange font. I am going to write the same words using the two word processors and you'll see a marked difference.[/FONT][/SIZE]

                       #toc, .toc, .mw-warning { border: 1px solid rgb(170, 170, 170); background-color: rgb(249, 249, 249); padding: 5px; font-size: 95%; }#toc h2, .toc h2 { display: inline; border: medium none; padding: 0pt; font-size: 100%; font-weight: bold; }#toc #toctitle, .toc #toctitle, #toc .toctitle, .toc .toctitle { text-align: center; }#toc ul, .toc ul { list-style-type: none; list-style-image: none; margin-left: 0pt; padding-left: 0pt; text-align: left; }#toc ul ul, .toc ul ul { margin: 0pt 0pt 0pt 2em; }#toc .toctoggle, .toc .toctoggle { font-size: 94%; }body { font-family: 'Times New Roman'; color: rgb(0, 0, 0); widows: 2; font-style: normal; text-indent: 0in; font-variant: normal; font-weight: normal; font-size: 12pt; text-decoration: none; text-align: left; }table {  }td { border-collapse: collapse; text-align: left; vertical-align: top; }           [FONT= ]If at first you don’t succeed, quit![/FONT]

[FONT= ][/FONT]
   	 	 	 	 	 	 	 	 	 	   
   	 	 	 	 	 	   
[FONT=Italian Cursive, 16th c.][SIZE=4]If at first you don't succeed, quit![/SIZE][/FONT]


[FONT=Italian Cursive, 16th c.][SIZE=4][SIZE=3]You can see the difference. I can write something using AbiWord copy and paste it in an email and send it but when it is received it looks like what you see in line two.[/SIZE][/SIZE][/FONT]


[FONT=Italian Cursive, 16th c.][SIZE=4][SIZE=3]I did use the command Ann suggested and will mark it for future reference.[/SIZE][/SIZE][/FONT]


[FONT=Italian Cursive, 16th c.][SIZE=4][SIZE=3]bill23[/SIZE]
[/SIZE][/FONT]

---

### Post by bill23 on 2012-01-05
Okay, that whole series of strange words is not what I saw when I had pasted those few words from AbiWord. I saw the Italian Cursive as it was meant to be seen. Not this gobbledegook.

bill23

---

### Post by bill23 on 2012-01-12
*I guess there is no point in continuing this thread so why not call this the end.*

---

