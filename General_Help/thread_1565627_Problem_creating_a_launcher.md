---
title: "Problem creating a launcher"
date: 2010-09-01
forum: General Help
---

### Post by rmcellig on 2010-09-01
I am having a problem creating a launcher. It doesn't launch the file I want. Is it something in the command that I did wrong?

---

### Post by MooPi on 2010-09-01
I'm just guessing but your ext is for a Microsoft format and may not work. Is this an executable file ? Or are you just trying to open a document ? The launcher mechanism is meant for executable file or applications. Just creating a link to a file doesn't work that way

---

### Post by atomizer on 2010-09-01
file.xlsx is not a linux executable file. You need a program to open it with.

---

### Post by rmcellig on 2010-09-01
What I am trying to do is. Under the Applications menu, I created a menu caled my stuff. In that menu I want to put files that I access fequently and this is the only way I can think of to have quick access to them. Is this not the right way to do it or is there a better way?

Also, it would be neat to have a menu on my Panel so that when I click on it, I can have my frequently accessed files listed to choose from.

I am using 10.04

---

### Post by MooPi on 2010-09-01
You could create a symbolic link to the folder in question to your desktop.

---

### Post by realzippy on 2010-09-01
*Also, it would be neat to have a menu on my Panel so that when I click on it, I can have my frequently accessed files listed to choose from.*

...right click panel/add to panel/add drawer

Edit:
if you want quick access to a folder (E.G. you create a folder named"FrequentlyAccessedFiles" in your home directory,open nautilus and simply drag and drop this folder to your panel to create an alias there.
-------------------------------------------------
Can you open your .xlsx file with OpenOffice?Or how opening your .xlsx files usually?

---

### Post by rmcellig on 2010-09-01
Thanks realzippy!! That really gives me food for thought!! I open my .xlsx files with Open Office Spreadsheet with no problems at all. I just need to find a quick way to access those files.

Adding the drawer to the panel sounds like a good idea but I don't think I can just drop a link to the file I want to access in the drawer. I keep getting errors because maybe it doesn't have an application in the command?

---

### Post by jakupl on 2010-09-01
> **rmcellig said:**
> Thanks realzippy!! That really gives me food for thought!! I open my .xlsx files with Open Office Spreadsheet with no problems at all. I just need to find a quick way to access those files.

Adding the drawer to the panel sounds like a good idea but I don't think I can just drop a link to the file I want to access in the drawer. I keep getting errors because maybe it doesn't have an application in the command?
yes that's why. Make a custom application launcher, call it what you want and in the "command" field, enter

```
ooffice -calc /path/to/file.xlsx
```

---

### Post by rmcellig on 2010-09-01
Bingo! That worked great!! Thanks so much!! How would I know what to put for a specific application into the command. You put ooffice -calc in my case, where do you find this? So that if I want to put other applications, I will have it entered in the command area properly.

---

### Post by realzippy on 2010-09-01
...ugly (but fast) workaround to see an menu's application command without gconftool is to drag that application (temporarely) in the panel,where you can "right-click/properties" it to see it's command.

Or open terminal:
```
man *yourapplication*
```

---

### Post by jakupl on 2010-09-01
> **rmcellig said:**
> Bingo! That worked great!! Thanks so much!! How would I know what to put for a specific application into the command. You put ooffice -calc in my case, where do you find this? So that if I want to put other applications, I will have it entered in the command area properly.

The user most user friendly way is probably. to find the program that you need - in this case open office spreadsheet, right click it and add it to desktop.
Now right click the icon on the desktop, press "Properties" and you will see the command under the "command" field

EDIT: ugh! beaten.

---

### Post by rmcellig on 2010-09-01
Thanks. That's easy!! I will try that out. Love your desktop!!

Is there a GUI tool that would display that informatiuon as well?

---

### Post by jakupl on 2010-09-01
> **rmcellig said:**
> Thanks. That's easy!! I will try that out. Love your desktop!!

Is there a GUI tool that would display that informatiuon as well?

what information?

---

### Post by rmcellig on 2010-09-01
The command information and maybe more info on a particular application?

---

### Post by Vaphell on 2010-09-01
one can use **gnome-open** to automatically open the file without deeper knowledge about the associated app.

gnome-open something.mp3 will run totem (or whatever the default app is), gnome-open something.jpg will run pic viewer

---

### Post by realzippy on 2010-09-01
running

```
man *yourapplication*
```

in the terminal is a GUI..    ;-)

---

