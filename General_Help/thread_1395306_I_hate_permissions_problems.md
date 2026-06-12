---
title: "I hate permissions problems"
date: 2010-01-31
forum: General Help
---

### Post by litlfrog on 2010-01-31
I want to use a template from the OpenOffice website, but I have no idea where applications are stored on the hard drive. I do a search for *.ots files, go to the opoenoffice.org webpage, and try to save the template to that directory, but I don't have permission to write to the folder (usr/lib/openoffice/[something]). How am I supposed to save the template file? Stuff like this is why I stopped using Ubuntu at home, but I'm still stuck with it at work.

---

### Post by todak on 2010-01-31
If you are using firefox to download, files will be saved in Downloads in your home directory. Move the desired downloaded template file into your Documents folder, which is where openoffice uses by default. If you right-clicked to download the template file, then browse to your Documents folder to save it there.

---

### Post by Morbius1 on 2010-01-31
It may have changed locations in Karmic but in Jaunty it's here:

/home/*your_user_name*/.openoffice.org/3/user/template

If you can't navigate to the hidden .openoffice.org folder you need to enable hidden files:

Nautilus > Edit > Preferences > Views > Show hidden and backup files

---

### Post by audiomick on 2010-01-31
if you can't write something somewhere, start nautilus with
```
gksu nautilus
```
Bear in mind that this gives you root privileges, which means you have the right to shoot down the system if you do something wrong.

---

### Post by Morbius1 on 2010-01-31
You know, there's even a slicker way to do this. Again this is in Jaunty:

Once you download your template, let's call it MySpreadsheet.ots

Copy it to **/home/your_user_name/Templates**
[COLOR=Blue]*This isn't the openOffice templates folder - it's a gnome templates folder*[/COLOR]

[COLOR=Blue]Edit: If the Templates folder isn't there you can create one yourself , just make sure you keep the caps on the "T" in Templates.[/COLOR]

Now Right Click an empty part of the Desktop
Select "Create Document"
You'll notice you have an entry called "MySpreadsheet"
Selecting that will create a MySpreadsheet.ots file on the desktop
Double click that and you're good to go.

Saves you the effort of opening up Open Office and selecting a template.

Just an idea.

---

