---
title: "help installing python program from source"
date: 2010-12-16
forum: General Help
---

### Post by boarder428 on 2010-12-16
I downloaded this programs source and I'm having a hard time figuring out how to install it.  Was wondering if someone could help?  I assume it is python source? I tried downloading the debian file but could not figure out how to install it aswell.  Any help would be greatly appreciated.
[IMG]http://img684.imageshack.us/img684/5784/pyscreenshot1.png[/IMG]


I downloaded the software from [http://www.unrealvoodoo.org/hiteck/projects/albumart/]("http://www.unrealvoodoo.org/hiteck/projects/albumart/")

---

### Post by VastOne on 2010-12-16
If install is a python file then

```
python install.py 
```

from it's directory...

But it looks like you need...

```
python setup.py 
```

Form it's directory

to actually make it run

---

### Post by nothingspecial on 2010-12-16
Why not just download and install the deb
```

wget [http://www.unrealvoodoo.org/hiteck/projects/albumart/dist/albumart_1.6.6-1_all.deb](http://www.unrealvoodoo.org/hiteck/projects/albumart/dist/albumart_1.6.6-1_all.deb)
sudo dpkg -i albumart_1.6.6-1_all.deb
```

---

### Post by oldos2er on 2010-12-16
Your screenshot contains the answer: ```
cd Downloads/albumart
python setup.py install
```

---

### Post by nothingspecial on 2010-12-16
There is a deb on the page the OP links

[ATTACH]178587[/ATTACH]

Sorry for the cli stuff,

Just click that.

No need to compile :D

***edit*** Due to my child-like image manipulation, I should point out that it is the debian thingy you need to click.  Or just copy and paste the stuff in m first post :)***edit***

---

### Post by boarder428 on 2010-12-17
Working on it.  Thanks for the replies!

---

### Post by boarder428 on 2010-12-19
ok, I figured out how to run the program but seem to have other errors.  I have meet all the dependencies and the site has no forum so I am just going to assume that this piece of software is probably not worth installing.  
```
corey@corey-HP-Pavilion-dv7-Notebook-PC ~ $ albumart-qt
Traceback (most recent call last):
  File "/usr/local/bin/albumart-qt", line 154, in <module>
    sys.exit(runGui())
  File "/usr/local/bin/albumart-qt", line 86, in runGui
    import albumart_dialog
  File "/usr/local/lib/albumart/albumart_dialog.py", line 37, in <module>
    from albumart_dialog_base import AlbumArtDialogBase
ImportError: cannot import name AlbumArtDialogBase

```
I hate to say it but I have decided to go the Windows route and install media monkey to tag my music collection.  I have heard people say Amarok is the way to go but have not had much success with it getting album art.  I love using Linux but there just are some things that Linux does not do well.  If I was any good at developing I would jump on the bandwagon but I don't have the skills necessary to develop a media management program like media monkey for linux.  Thanks for all the efforts!

---

### Post by nothingspecial on 2010-12-19
You should have said in your title - something like

"How to tag my music collection in linux"

or similar.

I came to help you install an app.

I could have told you how to sort out your tags 3 days ago.

Anyway, if you`ve gone the windows way, good luck to you. :D

---

### Post by boarder428 on 2010-12-19
> **nothingspecial said:**
> You should have said in your title - something like

"How to tag my music collection in linux"

or similar.

I came to help you install an app.

I could have told you how to sort out your tags 3 days ago.

Anyway, if you`ve gone the windows way, good luck to you. :D

I guess that's my fault, I was'nt clear,  I was trying to install the application to tag my Music files.  I have spent hours on forums trying to find a way to successfully tag music mostly with album art in Linux. The program was just another program I was trying to use to get the job done. I would still like to learn how to do so successfully in Linux. I would love more than anything to alienate windows but I have to figure out how to handle all my tasks on Linux before doing so. I have only been using Linux about a year and a half. My Library is very large, (100+GB) and stored on a Windows Home Server. Alot of the album art shows up in iTunes and Windows media player but when I open it up in Rhythmbox or Amarok none of the art is picked up even when it's enabled in the preferences.  I know both programs have had that problem and there are many forums out there that discuss the problem but none have had any success on my system(s)

---

### Post by nothingspecial on 2010-12-20
Give easytag and guayadeque a go.

---

### Post by boarder428 on 2010-12-20
> **nothingspecial said:**
> Give easytag and guayadeque a go.

Thanks! I'll do so.
btw, I love your quote! there is so much truth to that! :)

---

### Post by VastOne on 2010-12-20
> **boarder428 said:**
> Thanks! I'll do so.
btw, I love your quote! there is so much truth to that! :)

Clementine and EasyTag would be a better choice and use a lot less memory and cpu

---

### Post by boarder428 on 2010-12-29
thanks VastOne, I'll look into those!

---

