---
title: "Could not display &quot;trash:&quot;. The file is of an unknown type"
date: 2011-03-03
forum: General Help
---

### Post by highspider on 2011-03-03
Some how I broke the trash can....  Yes after laughing at me realize its possible and please help.

if I try to open it, its message boxs says     
 ```
Could not display "trash:".
The file is of an unknown type

[select application]  [ok]

```I can drag and drop and file show in 
```
ls .local/share/Trash/files
temp.tar.gz  Desktop.png  new file (another copy)  dragons.png coolcar.png

```I rebuilt a new trash.desktop The icon shows up and can drag and drop with same error
```
cat Trash.desktop 

[Desktop Entry]
Comment=Contains removed files
EmptyIcon=trashcan_empty
Encoding=UTF-8
Icon=trashcan_full
Name=Trash
Name[en_US]=Trash
Type=Link
URL=trash:/

```
I made a temp user added trash with and get the same error
```
gconf-editor
```Guessing File permission error but the drag and drop still works.

same problem with volumes_visible aka drives and computer_icon_visible

---

### Post by TeoBigusGeekus on 2011-03-03
[This]("http://forums.fedoraforum.org/showthread.php?t=229185") perhaps? (It's from fedora though)

---

### Post by highspider on 2011-03-03
cool beans, 
   link helped but i wasn't going to sacrifices the whole lib,  
```

sudo mv /usr/local /usr/OLDlocal

```logout and login 
trash and drives worked 

but thats the whole local 

I made a new /usr/local fired up root file manger "cool trick"
```

mkdir /usr/local
sudo nautilus
```and began moving OLDlocal files back to local in the processes of elimination 

The evil file that killed the trashcan 
/usr/local/lib/libgio-2.0.so.0.2800.0
I found that with this file trash and drives don't work with above error. I don't what it does or if its needed but its gone and now things work

---

### Post by TeoBigusGeekus on 2011-03-03
Glad to hear that. Don't forget to mark the thread as solved.

---

