---
title: "installing themes from gnome-look.org"
date: 2010-11-28
forum: General Help
---

### Post by astm on 2010-11-28
[SIZE=4]
hello

i want to ask abut how i can install this themes

[http://gnome-look.org/content/show.php/Moomex-Theme?content=57063](http://gnome-look.org/content/show.php/Moomex-Theme?content=57063)

in ubuntu 10.10  ?   :D
[/SIZE]

---

### Post by stinkeye on 2010-11-28
Open system > preferences > Appearance 
and drag and drop the downloaded file(57063-Moomex.tar.gz) into the themes window. 
Be aware that some themes on gnome-look contain other stuff in the compressed
file in which case you have to extract first to get to the actual theme you want.

You can also install themes by extracting the theme folder(eg in this case, the Moomex folder) from the archive and placing in 
**~/.themes**
which is a hidden folder in your home directory.
You can create a **.themes** folder if you don't have one.
Remember to include the preceding "**.**" in the name.

On that same page you linked to there is an emerald theme.
Emerald is a window decorator and only changes the appearance of the title bar and border, and only works when running compiz as your window manager.
To use emerald themes you need to install **Emerald Theme Manager**.
Search in the software centre for emerald.
Once installed you will need to import your emerald theme and select it.
It won't use the emerald theme until you change your window decorator.

Alt + F2 and enter
```
emerald --replace
```


To return to the gtk window decorator enter
```
gtk-window-decorator --replace
```

If your using compiz, install **fusion-icon** to easily switch between 
Window managers and decorators.(Search software centre)

---

