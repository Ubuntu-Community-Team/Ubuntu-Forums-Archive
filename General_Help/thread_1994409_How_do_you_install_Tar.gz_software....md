---
title: "How do you install Tar.gz software...?"
date: 2012-06-02
forum: General Help
---

### Post by robertcoulson on 2012-06-02
Hi guys

Sorry to bother you but I find lots of **Tar.gz** software, but have no idea how to install it in Ubuntu.

Thanks

---

### Post by inashdeen on 2012-06-02
tar.gz is not an installation file. it is a zipper, similar to .zip or .rar .
however, most source are packaged as such, and you need to extract them before you can compile them. on the other hand, some applications allow you to directly use them to install themes. so what is the package actually, if you don't mind...

---

### Post by robertcoulson on 2012-06-02
Hi **inashdeen**

It is a microscope analysis program called:


Slicer-4.1.0-linux-amd64.tar.gz

---

### Post by inashdeen on 2012-06-02
May I have a look at the file?

---

### Post by robertcoulson on 2012-06-02
ahhhh..How do I do that...?

Here is the link

[http://download.slicer.org/]("http://download.slicer.org/")

---

### Post by inashdeen on 2012-06-02
gimme link to where you get the file :)

---

### Post by robertcoulson on 2012-06-02
[http://download.slicer.org/]("http://download.slicer.org/")

---

### Post by traditionalist on 2012-06-02
> **robertcoulson said:**
> ahhhh..How do I do that...?

Here is the link

[http://download.slicer.org/](http://download.slicer.org/)


[http://slicer.kitware.com/midas3/item/859](http://slicer.kitware.com/midas3/item/859)

  if you download a tar.gz file  and then click on it it will open in the "Archive manager" by default.  Then you can see what is in it and if it is installable etc.

---

### Post by inashdeen on 2012-06-02
I didnt download because the size is huge and my net is slow. but juding by the style, i suppose you first need to extract it, then, you may need to press on an install.sh file, is that present?

---

### Post by robertcoulson on 2012-06-02
Extracted the files and double clicked and it opened ok but don't know how to install it on my computer.

---

### Post by traditionalist on 2012-06-02
> **robertcoulson said:**
> Extracted the files and double clicked and it opened ok but don't know how to install it on my computer.

I am downloading it now. As soon as I have it I will tell you how to install it, will take a few minutes..............

---

### Post by robertcoulson on 2012-06-02
Thanks for your help guys...I will just have to live the extracted files in a folder and double click on it to open it, even if I can't down load it.

Thanks again

---

### Post by traditionalist on 2012-06-02
> **robertcoulson said:**
> Thanks for your help guys...I will just have to live the extracted files in a folder and double click on it to open it, even if I can't down load it.

Thanks again

I have it half downloaded now. In a few minutes I will tell you how to install it, just a little patience.........................

---

### Post by robertcoulson on 2012-06-02
**patience**...I have lots of **traditionalist**

---

### Post by mc4man on 2012-06-02
You really don't need to install, just place the folder wherever you wish & create a launcher
If you are using unity you can do something like this, adjust blue to match your path exactly, & find yourself a decent icon somewhere, attaching a crappy one, if you now gimp could be improved or use whatever you want

For Icon= use full path or place the icon in /usr/share/pixmaps & just use name, no extension

For unity - replace blue to match your path exactly
```
gedit ~/.local/share/applications/slicer.desktop 

```
```
[Desktop Entry]
Type=Application
Version=1.0
Name=Slicer
Comment=[COLOR="Red"]Whatever you want[/COLOR]
Exec=[COLOR="Blue"]/home/doug/Downloads/Slicer-4.1.0-linux-amd64/Slicer[/COLOR] %U
Categories=Application;Education;Science;
Icon=[COLOR="Blue"]/home/doug/Pictures/3DSlicer.png[/COLOR]
Path=[COLOR="Blue"]/home/doug/Downloads/Slicer-4.1.0-linux-amd64/[/COLOR]
StartupWMClass=SlicerQT-real
```

Then just browse to ~/.local/share/applications/ & drag to launcher or after a log out in open the Dash > apps menu > search or 'Filter > science and ...

---

### Post by zkhalapyan on 2012-06-02
You probably want to unzip/uncompress the downloaded file before continuing. 
From your terminal, navigate to the folder that has the downloaded file then type in ```
tar -zxvf backup.tar.gz
```

Now access the uncompressed folder and try to find a script for installing the application or a README file with more information.

Hope that helps.

---

### Post by robertcoulson on 2012-06-02
That's exactly what I have done...OK, that will work for me.

Thanks guys

---

### Post by linux653 on 2012-06-02
[FONT=Arial]A tar.gz file normally contains source code that you need to **compile **before being able to run the software. While some people extract these files from the terminal, I just use the archive manager.

1. Double click the tar.gz
2. Extract it
3. Open into the terminal
4. Type: [/FONT][FONT=Courier New][FONT=Arial][FONT=Courier New]cd [folder where you extracted files][/FONT]
[/FONT][FONT=Arial]5. Type: [FONT=Courier New]ls[/FONT][/FONT]
[FONT=Arial]6. If you see:

* A readme file:

Open it and follow instructions

*configure:

Type: [FONT=Courier New]./configure
[FONT=Arial]If everything goes successfully, type [FONT=Courier New]make[/FONT]. If not, download the correct dependencies (the configure program will tell you)

* makefile:

[FONT=Courier New][FONT=Arial]Type: [FONT=Courier New]make[/FONT]
Then try: [FONT=Courier New]sudo make install[/FONT]

I hope that's helpful
[/FONT][/FONT][/FONT][/FONT][/FONT][/FONT]

---

### Post by robertcoulson on 2012-06-02
Thanks **linux653**

I will try that to see if it will install on my drive.

Thanks

---

### Post by traditionalist on 2012-06-02
> **robertcoulson said:**
> **patience**...I have lots of **traditionalist**

That archive contains a directly executable file.

OK.  Make a folder called "Slicer".

Copy the archive into it, and then click on the archive. Select "extract here".

If you now click on "Slicer" the executable file in that folder;

[[IMG]http://img40.imageshack.us/img40/1055/selection001s.th.png[/IMG]]("http://img40.imageshack.us/i/selection001s.png/")

the program will run;

[[IMG]http://img811.imageshack.us/img811/2830/3dslicer410001.th.png[/IMG]]("http://img811.imageshack.us/i/3dslicer410001.png/")

that was it.

Please take note, the above is not always the case. Zipped files like a  tar.gz  may contain all sorts of things.

You can get some training stuff for that program here;

[http://www.slicer.org/slicerWiki/index.php/Slicer3.6:Training](http://www.slicer.org/slicerWiki/index.php/Slicer3.6:Training)

It's a little bit more than a microscopy program!  :)

---

### Post by robertcoulson on 2012-06-02
Thanks a lot for that link **traditionalist**...It will come in handy.

---

### Post by inashdeen on 2012-06-03
could you tell me what is in the file. just name what you see

---

