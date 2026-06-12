---
title: "Way To Make a Program Start at a certain size"
date: 2006-05-10
forum: General Help
---

### Post by eyebrowman92 on 2006-05-10
The program in question, Nicotine 1.0.8, is always a certain width and height when you open it. I'm wondering if there is someway in the config file (Program written in Python BTW) to make it open at a selected width and height. Anyone have any ideas?

---

### Post by louis_nichols on 2006-05-11
KDE can do this, But I don't think Gnome can. What you're asking is a feature of the window manager. You could actually replace metacity with kwin.

Do a search on the forum for keyword knome and read a post by poofyhairguy about stealing KDE's eye-candy.

---

### Post by Gustav on 2006-05-11
You could try looking for an entry fo nicotine in gconf-editor.

Some programs have that kind of options stored there.

---

### Post by kabus on 2006-05-11
Or you could use devilspie.

---

### Post by eyebrowman92 on 2006-05-12
I'm actually not sure where to start. Nicotine has a config file in ~/.nicotine. Is there something i could somehow add to it to make it start at a certain height and width?

EDIT: I'm using blackbox, btw.

---

### Post by eyebrowman92 on 2006-05-16
Anyone ..

---

### Post by RikoW on 2006-05-17
you can try to start nicotine from the command line with the -geometry option. It should be recognized by the window manager:

```
> nicotine -geometry 100x200 &
```

where NxM is the size in x (N) and y (M). Try whateve fits you.

If that does work, you can add this option to the menu entry of nicotine (if any) by using the Application Menu Editor under system tool.

Hope that helps,

             Riko

---

### Post by mcduck on 2006-05-17
like kabus wrote, devilspie allows you to configure what size program windows are, on what desktop they open etc..

---

### Post by eyebrowman92 on 2006-05-17
Ok I installed devilspie, but when i try running it from the command-line i get the following error:

```
$ devilspie
No s-expressions loaded, quiting

```

---

### Post by eyebrowman92 on 2006-05-19
Does anyone know what the error means or know how to fix it?

---

### Post by mcduck on 2006-05-19
[QUOTE=eyebrowman92]Does anyone know what the error means or know how to fix it?[/QUOTE]
you need to make a configuration file foe devilspie, and then start it with 'devilspie /path/to/your/configfile'

Here's a nice guide for you: [http://wiki.foosel.net/linux/devilspie]("http://wiki.foosel.net/linux/devilspie")

---

