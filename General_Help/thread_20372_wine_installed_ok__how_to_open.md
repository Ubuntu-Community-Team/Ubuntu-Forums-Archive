---
title: "wine installed ok??  how to open?"
date: 2005-03-16
forum: General Help
---

### Post by johnpicken on 2005-03-16
running latest ubuntu on a cheapy (but OK) ECS G320 laptop so a newbie

Installed wine from winehQ - 20050310,  using apt-get install wine having first done update as per wine hq  faq
then run wine.  All seams OK.  Wine shows as hidden files with windows structure in my home directory.   I appear to be able to install a windows programme autoroute2000 and ciclotour for example but then cannot find them.  No start menu, nothing on desktop.  Go to the hidden exec file and it won't load - but did not expect it to.  Obviously I am missing something.       So I think my question is:
If I have a windows programme installed how do I launch the programme??
or am i missing something else? :sad:

---

### Post by KLineD on 2005-03-16
Try launching from the command line
suppose that you program installed in you home directory, under the /.fake_windows/myprogram directory

```
wine ~/.fake_windows/myprogram/program.exe
```

And see if the program launches or what's displayed in the console.

In case that the program is installed to a folder with spaces, you have to escape the spaces using the following:

```
wine ~/.fake_windows/Program\ Files/My\ Program/program.exe
``` 

Hope this helps

---

### Post by WW on 2005-03-16
[QUOTE=KLineD]
In case that the program is installed to a folder with spaces, you have to escape the spaces using the following:

```
wine ~/.fake_windows/Program\ Files/My\ Program/program.exe
``` 
[/QUOTE]
Or you can use double quotes, but then I don't think you can use ~:
```
wine "/home/your_user_name/.fake_windows/Program Files/My Program/program.exe"
```

---

