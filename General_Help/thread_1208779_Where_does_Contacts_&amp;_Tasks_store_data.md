---
title: "Where does Contacts &amp; Tasks store data?"
date: 2009-07-09
forum: General Help
---

### Post by z0mbie on 2009-07-09
I started using these two applications and become dependent on them in Ubuntu. For the life of me I couldn't find where they stored all my data. Since these tools don't provide exporting features, I need to know the exact locations for backup purposes. 

Both of these applications are developed by: [http://www.pimlico-project.org/](http://www.pimlico-project.org/).

---

### Post by z0mbie on 2009-07-09
> **z0mbie said:**
> I started using these two applications and become dependent on them in Ubuntu. For the life of me I couldn't find where they stored all my data. Since these tools don't provide exporting features, I need to know the exact locations for backup purposes. 

Both of these applications are developed by: [http://www.pimlico-project.org/](http://www.pimlico-project.org/).

Never mind, I found it. It's located in the following home directory: 

```
~/.evolution
```

I guess it's part of Evolution thats why it's in that directory?

---

### Post by ratdog on 2009-11-15
Hello,

I am using the Contacts program as well.
Does anyone know what files I am looking for exactly.
I am trying to transfer my contacts from one computer to another and transfering the addressbook.db file from the old computer to the new one does not update my contacts.

Thanks a lot!

---

### Post by dcstar on 2009-11-15
> **ratdog said:**
> Hello,

I am using the Contacts program as well.
Does anyone know what files I am looking for exactly.
I am trying to transfer my contacts from one computer to another and transfering the addressbook.db file from the old computer to the new one does not update my contacts.

Thanks a lot!

Go into Evolution, select all the Contacts and then Save as vCard.

Move the file to the new PC and use the Evolution Import function.

---

### Post by drilow on 2010-02-14
Thanks very much dcstar, I also used contacts and didn´t know where its files where :p.

---

### Post by Manoel on 2011-08-21
I don't use Contacts but I do use Tasks.

I'm having [a problem]("http://ubuntuforums.org/showthread.php?t=1830001") now because I didn't take in mind task list data when making backups and now after an Ubuntu upgrade all this list seems to be lost!

I don't find an evolution directory, but have a /.config/tasks/ instead when all I can find is a file name windows which only contains configurations for windows sizes of the app.

---

### Post by Manoel on 2011-08-21
> **Manoel said:**
> 
I don't find an evolution directory, but have a /.config/tasks/ instead

Sorry. My search in Nautilus was hiding that directory. I have an /.evolution/ directory and a /tasks/ subdirectory. But absolutely no data within it right now after the upgrade? Was it supposed to be there where my task list was filed?

---

### Post by Manoel on 2011-08-21
> **Manoel said:**
> (...) have a /.config/tasks/ instead when all I can find is a file name windows which only contains configurations for windows sizes of the app.

BTW, this directory was created this very morning when I first opened Tasks app for the first time after upgrading. :confused:

---

