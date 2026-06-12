---
title: "Paste text strings with hotkeys"
date: 2011-04-23
forum: General Help
---

### Post by playful_geometer on 2011-04-23
Hey folks, some time ago, I developed an easy way to put commonly used strings of text into my clip board to be pasted into emails and such.  I thought it might be helpful to some of you folks who get tired typing the same URL, etc. over and over again.  I figured it out thanks to some other posts of a similar nature here.

  I first created a script of file name "pasties" in my home directory:

> #!/bin/bash
TEXTARR[0]="http://www.flickr.com/photos/playful_geometer/"
TEXTARR[1]="http://sites.google.com/site/cosmicspacecrafts/"
TEXTARR[2]="http://playful-geometer.deviantart.com/"
TEXTARR[3]="http://www.openprocessing.org/portal/?userID=4655"
TEXTARR[4]="http://www.facebook.com/group.php?gid=150658771621486"
TEXTARR[5]="http://cosmic-spacecrafts.blogspot.com"
echo ${TEXTARR[$1]} | xclip -selection "clipboard"Then in System->Preferences->Compiz->Commands I created a series of shortcuts i.e. Shift+Ctrl+F1 : ./pasties 0.  

So now I can press that hotkey and the first link will go into my cllip board to be pasted.  It would be great if Glipper could do something like that for those who aren't so geeky though. 

Take a look at my digital art in the links above if you will.  I owe it all to Open Source software !

Cheers,
~The Playful Geometer~

---

### Post by Habeouscorpus on 2011-04-23
That's.... pretty cool. 

I'm saving this, do you mind? I'll only use it for framework.

---

### Post by playful_geometer on 2011-04-25
Shared in the spirit of Software Freedom ;)

---

### Post by Ropes on 2012-08-14
Hey thanks for the nice trick! :popcorn:  

The only thing I'd like to add to this is a way to have have the text get pasted immediately to the cursor's location.   If I find a way to do it elegantly I'll post it!

---

### Post by Habitual on 2012-08-14
> **playful_geometer said:**
> Take a look at my digital art in the links ...

+2, 1 for Mad Art and 1 for a Mad script.

Edit: and what a [difference 727 days]("http://ubuntuforums.org/showpost.php?p=9735558&postcount=4") makes :wink:

---

### Post by GrouchyGaijin on 2013-01-10
> **playful_geometer said:**
> Hey folks, some time ago, I developed an easy way to put commonly used strings of text into my clip board to be pasted into emails and such.  I thought it might be helpful to some of you folks who get tired typing the same URL, etc. over and over again.  I figured it out thanks to some other posts of a similar nature here.

  I first created a script of file name "pasties" in my home directory:

Then in System->Preferences->Compiz->Commands I created a series of shortcuts i.e. Shift+Ctrl+F1 : ./pasties 0.  

So now I can press that hotkey and the first link will go into my cllip board to be pasted.  It would be great if Glipper could do something like that for those who aren't so geeky though. 

Take a look at my digital art in the links above if you will.  I owe it all to Open Source software !

Cheers,
~The Playful Geometer~

This is pretty cool, bummer that I can't seem to get it to work.
I tried the commands as you have them.
```
./pasties 0
```
and I also put a copy of the script in my preferred folder which is called scripts (~/scripts).
I tried running the commands with the script there and changing the command in Compiz to both:
```
~/scripts/pasties 0
``` and
```
home/john/pasties 0
```
but I can't copy the url from the pasties script by pressing the keys I assigned.

---

### Post by stinkeye on 2013-01-10
Works here with **~/scripts/pasties 0** as the command.
Make sure the script is executable and you have **xclip** installed.

Glipper now has a snippets plugin where you can add often used phrases.

---

### Post by GrouchyGaijin on 2013-01-10
> **stinkeye said:**
> 
Make sure the script is executable and you have **xclip** installed.

Dou!!
I works so much better if you have all the components installed.
My mistake

---

### Post by stinkeye on 2013-01-10
> **GrouchyGaijin said:**
> Dou!!
I works so much better if you have all the components installed.
My mistake
. #-o ;)

---

### Post by avsprasad on 2013-01-14
Is there any Text Editor which has a built-in clipboard monitor? Instead of using a clip manager. In Windows, there is Editplus, Exdor etc. I use autocopy add-on in Firefox and keep the clipboard monitor on in the Text editor. So I just need to keep selecting text in the browser, and it keeps pasting in the background on my Text editor. I can edit the text anytime, put separators, dates, add text etc in the Text Editor every once in a while. Would love to see such a feature in some Text Editor in Ubuntu.

---

