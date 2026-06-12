---
title: "How do i install a theme???"
date: 2006-05-16
forum: General Help
---

### Post by morbid_bean on 2006-05-16
I downloaded a theme from gnome-look.org and now i have a tar.gz file and in that there is a folder...and in that folder there are 8 files


1.xml file
2.unknown file
3.png file
4.jpg file
5.png file
6 png file
7. png file
8. png file

How do i install this....explain to me however is the easiest way...if you can do it with the terminal and the thing from system->Prefrences->Theme then please tell me both or however its done..

-THANKS!-

---

### Post by johnc4510 on 2006-05-16
I created a folder in my home file called Gnome Themes
I download the tar to my desktop then drag it to the folder
Then System>Preferences>Theme and click on install theme
Point the installation at you folder and that's all

---

### Post by morbid_bean on 2006-05-16
[QUOTE=johnc4510]I created a folder in my home file called Gnome Themes
I download the tar to my desktop then drag it to the folder
Then System>Preferences>Theme and click on install theme
Point the installation at you folder and that's all[/QUOTE]



I did that and got this error:    The file format is invalid

---

### Post by bman on 2006-05-16
yea thats what I get too???

---

### Post by morbid_bean on 2006-05-16
[QUOTE=bman]yea thats what I get too???[/QUOTE]


Yea...i wish i could figure this out?  :( :( :( #-o

---

### Post by aysiu on 2006-05-16
The file format will be invalid if you have already un-tarred the tar.gz.

---

### Post by morbid_bean on 2006-05-16
[QUOTE=aysiu]The file format will be invalid if you have already un-tarred the tar.gz.[/QUOTE]

What is untarred????is that mean after i open it???

---

### Post by aysiu on 2006-05-16
[QUOTE=morbid_bean]What is untarred????is that mean after i open it???[/QUOTE] A .tar.gz is a compressed file, much like a .zip file in Windows. When you "un-tar" it, you're unzipping it to see what's inside.

So, yes, after you open the .tar.gz, it's un-tarred.

Don't double-click the .tar.gz. Don't extract it to a folder. You take the raw .tar.gz (exactly the file you downloaded, untouched) and drag and drop it to the Theme Manager Window.

---

### Post by morbid_bean on 2006-05-16
Man.....i deleeted every trace of the file re downloaded it dragged it to a folder i store theme (or want to store them) and i did not open it and it still dose this???


Could it be possible that im tying to install a GDM theme for ubuntu because i dont know if thats what i need or the GTK one.

---

### Post by wbmj on 2006-05-16
System>Preferences>Themes....now drag the download to this window. If the file type is correct it will ask you to install....hit installbutton...all done

---

### Post by m4gnesium on 2006-05-16
I just tried this as well, getting the same invalid file format error. I'm not extracting the file first. So OP, you're not the only one, if that makes you feel better. :-?

---

### Post by aysiu on 2006-05-16
Can someone post a link to the actual theme?

---

### Post by m4gnesium on 2006-05-17
I was trying this one: [http://www.gnome-look.org/content/show.php?content=39314](http://www.gnome-look.org/content/show.php?content=39314)

---

### Post by aysiu on 2006-05-17
[QUOTE=m4gnesium]I was trying this one: [http://www.gnome-look.org/content/show.php?content=39314](http://www.gnome-look.org/content/show.php?content=39314)[/QUOTE] That's a GDM (login screen) theme, not a window decoration or user interface theme.

To install that, you go to System > Administration > Login Screen Setup and go to the Themed Background section and click "Install New Theme."

Once again, do not un-tar. Just select the .tar.gz just as you downloaded it.

If you want themes for your user interface, look at *GTK 1.x*, *GTK 2.x*, and *Metacity*.

---

### Post by m4gnesium on 2006-05-17
I see....

Once again the value of actually knowing what various TLAs mean is illustrated

---

### Post by aysiu on 2006-05-17
[QUOTE=m4gnesium]I see....

Once again the value of actually knowing what various TLAs mean is illustrated[/QUOTE] GDM stands for *GNOME Display Manager*, which is a bit of a misleading name, as you don't actually have to have Gnome installed to use it. You can use GDM with KDE or GDM with IceWM or GDM with XFCE.

In fact, GDM is the default display manager for Xubuntu (the XFCE flavor of Ubuntu).

It's also funny how it's called a *display manager* since, from the user perspective, all it manages is the login screen. Now, in actuality, behind the scenes, it probably manages more than that, but...

---

### Post by morbid_bean on 2006-05-17
ok thanks for the support...now how about removing the unwanted themes i dont like lol

---

### Post by zerocool on 2006-05-18
when I go system>preferences>theme, I get

The Application "gnome-theme-manager" has quit unexpectedly.

not sure what's wrong here...

*edit-needed to change session to gnome

---

### Post by morbid_bean on 2006-05-18
[QUOTE=zerocool]when I go system>preferences>theme, I get

The Application "gnome-theme-manager" has quit unexpectedly.

not sure what's wrong here...

*edit-needed to change session to gnome[/QUOTE]

I dont have much linux experience but the thing i would do is restart my computer. Maby that would help :-k

---

