---
title: "Theme Changes"
date: 2009-09-15
forum: General Help
---

### Post by HalfCrackedTech on 2009-09-15
OK I have downloaded a theme and it is a tar.gz.  How do i install that?

---

### Post by sunchiqua on 2009-09-15
[LIST=1]
[*]Right click on your Desktop and choose [COLOR=DimGray]Change desktop background[/COLOR]
[*]Navigate to [COLOR=DimGray]Theme[/COLOR] tab
[*]Drag-n-drop your tar.gz file into [COLOR=DimGray]Change desktop background[/COLOR] window
[/LIST]

---

### Post by HalfCrackedTech on 2009-09-15
I have done that and still nothing happens.  I also tried to drag it to the Themes tab and then it just closes.

---

### Post by sunchiqua on 2009-09-15
> **HalfCrackedTech said:**
> I have done that and still nothing happens.  I also tried to drag it to the Themes tab and then it just closes.

Assuming you've downloaded it to your home directory:
```

cd $HOME
tar xzvf file.tar.gz
sudo mv file /usr/share/themes
```** Replace file with your tar.gz file name

---

### Post by HalfCrackedTech on 2009-09-15
And I do that how?  Sorry I am a NOOB.

---

### Post by DoubleCross on 2009-09-15
Open up a terminal. Applications>Accessories>Terminal.

---

### Post by HalfCrackedTech on 2009-09-15
Ok I did that and nothing happened I finally just extracted it by right clicking it.

---

### Post by VCoolio on 2009-09-15
Put the extracted folder in ~/.themes (a hidden folder in your home folder), which is the same as 'installing' the theme would do. What theme are you trying to install? Do you have a link?

---

### Post by HalfCrackedTech on 2009-09-15
I got a few of them but from all different places the one that I installed and am using mimics OSX and I also installed Cairo dock.

---

### Post by Andertraaks on 2009-09-15
> **sunchiqua said:**
> 
[LIST=1]
[*]Right click on your Desktop and choose [COLOR=DimGray]Change desktop background[/COLOR]
[*]Navigate to [COLOR=DimGray]Theme[/COLOR] tab
[*]Drag-n-drop your tar.gz file into [COLOR=DimGray]Change desktop background[/COLOR] window
[/LIST]


Thank you very much, good thing I did a search on this. My Ubuntu looks fresh(er) now!

---

