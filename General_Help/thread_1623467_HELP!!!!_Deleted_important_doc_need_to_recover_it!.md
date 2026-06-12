---
title: "HELP!!!! Deleted important doc need to recover it!!"
date: 2010-11-16
forum: General Help
---

### Post by Jonny87 on 2010-11-16
Some please help!!
I've deletd an important document by accident and Urgently need to recover it. It was a 5 or 6 page report that was almost finnished and is due friday. Usually I'd have it backed up but I didn't get a chance this time round.

Can some one help please is there a way to recover it. It is an ODT file.

---

### Post by wojox on 2010-11-16
How did you delete it? Did you look in the trash?

---

### Post by deconstrained on 2010-11-16
If you don't have any applications open and linked to the file, hunt for its name in your system's logs using grep. If somehow you manage to find the inode of the document, you might try the second half of the procedure described here:
[http://www.linux.com/archive/articles/58142](http://www.linux.com/archive/articles/58142)

That's the only remotely possible way I can think of recovering a deleted file in Unix. If you shut down the computer between when you deleted it and now, there's most likely no chance of recovering it.

---

### Post by Jonny87 on 2010-11-16
Yes I deleted it byond the trash used "shift+delete" and hit eneter straight after (flaming force of habbit :mad: ). But I did check there just incase.

I thought I had another file selected, which I did but it was the wong window that was active. Basically it was one of the moments where you loose concertration for just a moment and it stuffs up your entire day... wait nope.. week.

Now I'm frantically looking up ways to recover it. Came across "extundelete" but that wasn't installed and the only copy I found was to be compiled and I couldn't compile it, apparantly its because i need other software install (I've never needed to compile stuff, always use synaptic).

---

### Post by Ancanus on 2010-11-16
Please take a look at the Ubuntu Data Recovery [documentation]("http://help.ubuntu.com/community/DataRecovery#Extract individual files from recovered image").

For future references, you might want to make use of a [sync application]("http://www.dropbox.com/") to keep copies of your files in case something happens.

---

### Post by WorMzy on 2010-11-16
Also a good idea with important docs is to "save as" every time you save, and give the file a slightly different name each time you save it. e.g.
Report-0.1
Report-0.2
Report-0.3
etc

That way, if you ever accidentally delete your most recent document, you have the last version to work from.

---

### Post by wojox on 2010-11-16
I know Foremost and scalpel are pretty popular. Have a look at [DataRecovery]("https://help.ubuntu.com/community/DataRecovery")

---

### Post by Jonny87 on 2010-11-16
Ok thanks for you help people. I've tried looking at those programs foremost and scalpel but unless I'm mistaken they don't seem to accept odt formats.

> If you don't have any applications open and linked to the file, hunt for its name in your system's logs using grep. If somehow you manage to find the inode of the document, you might try the second half of the procedure described here:
[http://www.linux.com/archive/articles/58142](http://www.linux.com/archive/articles/58142)

That's the only remotely possible way I can think of recovering a deleted file in Unix. If you shut down the computer between when you deleted it and now, there's most likely no chance of recovering it. 

I've tried this but I can't seem to get it to show the inode number. can someone possible talk me though the steps to make sure I'm doing it right.

---

### Post by wojox on 2010-11-16
Photorec can do it. Scroll down [Photorec]("http://linux.softpedia.com/get/System/Recovery/Photorec-12060.shtml")

---

### Post by Ancanus on 2010-11-16
As noted in the [documentation]("http://help.ubuntu.com/community/DataRecovery#Extract individual files from recovered image"), you would use zip to recover ODT files.

```

sudo foremost -t zip -i /dev/YOUR_DRIVE -o OUTPUT_FOLDER
```

---

### Post by Jonny87 on 2010-11-16
> **Ancanus said:**
> As noted in the [documentation]("http://help.ubuntu.com/community/DataRecovery#Extract%20individual%20files%20from%20recovered%20image"), you would use zip to recover ODT files.

```

sudo foremost -t zip -i /dev/YOUR_DRIVE -o OUTPUT_FOLDER
```

Ok I've given it a try and it seem to running fine so far but I've noticed that all the files have numbers and stuff for names, is there an effective way to find the one document that I'm looking for amoungst the rest?

---

### Post by MarkAlter on 2010-11-23
I strongly suggest you do not do anything on your PC for avoiding overwritten.
You'd better do not install any data recovery software to the PC. You should uninstall the hard drive of the PC you've restored and connect it to another PC running windows as an external device. And then install a data recovery tool to the same PC. Here I recommend you Kernel for Linux, because I'm sure it can recover lost data.

---

