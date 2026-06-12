---
title: "Ugly Skype"
date: 2005-02-20
forum: General Help
---

### Post by Deusiah on 2005-02-20
Why is it that skype looks so ugly? I have seen many applications that use this similar style. 

Is there anyway I can make skype look less ugly like the screenshots of it on the site?

Thanks.

---

### Post by kassetra on 2005-02-20
Skype is a qt/kde app, so if you're running a standard ubuntu/gnome install, most likely it will look pretty ugly.
 
 What you need to do is install some qt/kde [look and feel themes]("http://www.kde-look.org/index.php?xcontentmode=14&PHPSESSID=6d1db6cdf8effd63c9ce8014b93f4b35"). 
 
 Also, that's if you installed skype with the dynamic libraries and also installed the required qt libraries... if you installed the giant package that included qt statically linked, you may be stuck.

---

### Post by Jad on 2005-02-20
I'm not going to marry the application, so I don't care if its ugly.

---

### Post by Perfect Storm on 2005-02-20
[QUOTE=Jad]I'm not going to marry the application, so I don't care if its ugly.[/QUOTE]

 :mrgreen: ...You may now kiss the bride! **Applause from the audience**

---

### Post by blixtra on 2005-02-20
For me all qt app had really big fonts. It'll look a little better if you go to the KDE Control panel (Applcations-->Control Center) and reduce the size of all fonts. It'll look bearable then. As mentioned above, changing KDE themes (also in Control Center) will help, too.

Chris

PS: Control Center is only available if KDE is installed
PS2: I'm on Hoary

---

### Post by Deusiah on 2005-02-21
Thanks for your replys.

I had a feeling that the answer would lie in installing something KDE related :( Why is it that KDE has an option to make all QT use your KDE theme but Gnome has no such thing?

As for marrying the app, well I wasn't intending to do that either. I can live with it but I thought it was worth asking just incase there was some nice way I had not found to give QT/KDE apps a Gnome look.

I used to use KDE all the time and was never a Gnome fan, last time I tried Gnome was 5 years ago lol so I guess it was stupid of me to assume I still wouldn't like it. However after using Gnome for a day I was hooked on it only every now and again I keep finding areas where KDE has "the edge". Such as a print manager (Kprinter), theming QT apps, and Konsole (I prefer the extra features Konsole has).

---

### Post by ember on 2005-02-21
I think there's qtconfig available in universe, which allows you to control the appearance of qt-apps without installing KDE-related things.

---

### Post by Deusiah on 2005-02-21
Your right there is such an app but it only lets you change the look of QT apps to a selection of a few ugly QT style themes lol. I suppose the font setting it usefull but QT Anti-Aliasing does not work for me.

I find it odd that there is a program that can skin QT/KDE apps with GTK.

---

### Post by piedamaro on 2005-02-21
This is what I do to set my kde|qt themes up:
Use qtconfig to config fonts, skin and coilors for qt apps (like opera). I use qtindustrial from novell, then using a screenshot I can set the same color scheme as gtk human theme.
Same things applies for kde apps, but I use kcontrol instead of qtconfig. Hope  this helps.

p.s. 
Deusiah wrote:
"I prefer the extra features Konsole has"
I'd like to know what are these extra feature. (I'm not trolling, I really want to know :))

---

### Post by Deusiah on 2005-02-21
Can you download kcontrol without KDE?

As for the extra features of Konsole there are not a lot just a few more config options and perhaps my favorite. That drop down menu that pops up when you drag something on it. The 'cd' option being the most usefull of course, I frequently find myself dragging files into gnome terminal to cd to the files directory. Of course I have to add cd and delete the file name myself.

There are many more features that Gnome lacks of course. Perhaps Konsole was not such as good example but there are areas that let Gnome down in my opinion such as Bluetooth config, ACPI config and things like font management. Another thing that could really do with being added to nautilus is undo support. You know when you delete or copy a file and you just want to hit crtl+z?

---

### Post by piedamaro on 2005-02-21
[QUOTE=Deusiah]Can you download kcontrol without KDE?

As for the extra features of Konsole there are not a lot just a few more config options and perhaps my favorite. That drop down menu that pops up when you drag something on it. The 'cd' option being the most usefull of course, I frequently find myself dragging files into gnome terminal to cd to the files directory. Of course I have to add cd and delete the file name myself.

There are many more features that Gnome lacks of course. Perhaps Konsole was not such as good example but there are areas that let Gnome down in my opinion such as Bluetooth config, ACPI config and things like font management. Another thing that could really do with being added to nautilus is undo support. You know when you delete or copy a file and you just want to hit crtl+z?[/QUOTE]
 Gnome-terminal works the same with drag and drop. If you drag a folder on a terminal you have the path of that folder on the command line. No pop-up menu though.

---

### Post by Deusiah on 2005-02-23
[QUOTE=deusiah]I frequently find myself dragging files into gnome terminal to cd to the files directory.[/QUOTE]

Yes I know that :roll: lol.

How come applications like Firefox fit both Gnome and Kde?

---

### Post by piedamaro on 2005-02-23
[QUOTE=Deusiah]Yes I know that :roll: lol.

How come applications like Firefox fit both Gnome and Kde?[/QUOTE]
There is a standard specification for drag and drop at freedesktop: XDND

---

### Post by Deusiah on 2005-02-24
I'm confused, what's DND got to do with Firefox looking right on both Gnome and KDE?

Anyway this has all gone rather off-topic. I guess the answer to my question is, Skype is ugly becuase Gnome can't skin QT/KDE apps and to make it look better you need to mess about KDE.

I'd rather stick with ugly Skype than load up KDE libs in Gnome. Skype should make their program work the same way Firefox/Thunderbird works.

---

### Post by machiner on 2005-02-24
You can print the terminal output in konsole...a print-screen.

That's functionality!

---

### Post by Deusiah on 2005-02-25
Agreed, another one to add to the list ;)

---

### Post by piedamaro on 2005-02-28
Ah,ok, I misunderstood. That's because firefox uses xul for the interface.

---

### Post by Deusiah on 2005-03-01
OK no prob. Thanks for the info. I just wish Skype used XUL too.

---

### Post by marx1984 on 2005-03-01
[http://forum.skype.com/viewtopic.php?t=9689](http://forum.skype.com/viewtopic.php?t=9689) 

Check that out and read all of what charelke posts. I think he has a point. You're using ubuntu and as i've read it promotes freedom and openess something that skype does not.  Asterisk PBX on the other hand is open source and from what i've read on the forum above is more flexible and powerful than skype.

---

