---
title: "Please Help! Documents Folder Gone"
date: 2010-03-17
forum: General Help
---

### Post by seanbw on 2010-03-17
**Please Help! Documents Folder Gone** 			
 			 			 		   		 		 		I was working  on an ebook and went back to get a document when the bookmark will not  show up. I then went into Nautilus and tried to find my documents folder  - its gone. 
Even under Windows - crappy as that was, my Documents folder had never  disappeared. Please my proposal is in there and I need it. How can I  recover my Documents folder?
Presumably as long as I don't shut down, it can't really disappear?
I have done a search for the folder but no luck. I have done locate  /home/seanbw/Documents/ and got nothing.
I have also done: dmesg | sudo grep -r "DB Agric*" and got nothing
I am very afraid of doing anything else.
  Please can someone help me. I am desperate.

---

### Post by llamabr on 2010-03-17
from a terminal, do:

```
cd Documents
```

what happens?

Possibly, if you deleted it in gnome, you'll find your document in the trash:

```
cd ~/.local/share/Trash/
ls
```

and then look around.  You're right not to shut down or log off yet.

---

### Post by seanbw on 2010-03-18
> **llamabr said:**
> from a terminal, do:

```
cd Documents
```what happens?

```
bash: cd: Documents: No such file or directory
``` This is what I get


Possibly, if you deleted it in gnome, you'll find your document in the trash: What happens if I have KDE as well but was using a gnome window manager?

```
cd ~/.local/share/Trash/
ls
```and then look around.  You're right not to shut down or log off yet.

```
files  info
```  This is what I get but I don't know what it means

---

### Post by seanbw on 2010-03-18
bump! HELP

---

### Post by wojox on 2010-03-18
Just open Places > Home Folder, Hit Ctrl+H. Go to .local/share/Trash/files and then info folders and see if they are in there.

---

### Post by seanbw on 2010-03-18
> **wojox said:**
> Just open Places > Home Folder, Hit Ctrl+H. Go to .local/share/Trash/files and then info folders and see if they are in there.
I have done that both using the terminal and nautilus. It seems to have disappeared. Have you got any other ideas ? Is there any controls on these folders (they were created by ubuntu) or are they symlinked to another section of the operating system?

---

### Post by seanbw on 2010-03-18
> **seanbw said:**
> I have done that both using the terminal and nautilus. It seems to have disappeared. Have you got any other ideas ? Is there any controls on these folders (they were created by ubuntu) or are they symlinked to another section of the operating system?
Both Nautilus and terminal seemed incapable of accessing .local/share/Trash/file although I can access the wastebasket via the file managerbut terminal keeps saying the directory does not exist. Any more ideas will be appreciated. I am beginning to stress out now. Please Help!

---

### Post by seanbw on 2010-03-18
Does anyone know how to interrogate /usr/share/doc/xdg-user-dirs-gtk to try and follow up on the changes to the bookmarks? maybe it can tell me where the Documents folder went.

---

### Post by seanbw on 2010-03-18
bump! anyone get  ideas?

---

### Post by ajgreeny on 2010-03-19
In my /usr/share/docs/xdg - - -  folder there are 5 files, three of which are text and two gz archive files, which both extract to text files I can read with gedit.  There seems to be little in there that will help you sort your problem of a lost Documents folder.  Perhaps you need to try something like testdisk and photorec.

Sorry I can't help more.

---

### Post by seanbw on 2010-03-19
I have just installed testdsk which seems to have given me photorec. will read up and see what it can do. I will post the results. thanks for the tip.

---

### Post by lian1238 on 2010-03-19
Are other folders in your home folder still there?

Edit: your Documents folder is not a symlink. It's a folder in **/home/yourname/** which is the same as **~/** which means "home folder".
I hope you get your files back.

---

### Post by seanbw on 2010-03-19
I have run testdisk but I cant get an undelete from the options. The  missing folder is Documents and I really don't know where it disappeared  to. Is there any script I can run  
I have looked at xdg--- but I don't see anything to help but I am not  technical so I wont know if it is not explicitly stated.

---

### Post by seanbw on 2010-03-19
> **lian1238 said:**
> Are other folders in your home folder still there?

Edit: your Documents folder is not a symlink. It's a folder in **/home/yourname/** which is the same as **~/** which means "home folder".
I hope you get your files back.
Yes its only the Documents folder that disappeared. I don't get it. If I deleted it in error, surely it should be in my trash especially as I did not enable the Nautilus option of deleting without using the trash.

---

### Post by lian1238 on 2010-03-19
try crawling your whole filesystem with the command:

```

ls / -Ra | grep Documents

```

I'm not a bash guru, so if someone has a better command, please say so.

---

### Post by mridkash on 2010-03-19
you can also use a find command to find the files you saved recently.

```

find /home -mtime 1

```
finds all files modified since 24  hrs (1 day).

---

### Post by seanbw on 2010-03-19
> **lian1238 said:**
> try crawling your whole filesystem with the command:

```

ls / -Ra | grep Documents

```

I'm not a bash guru, so if someone has a better command, please say so.
Thank you. I found the folder here: /root/.local/share/Trash/files/Documents/
How can I restore it as I cant find it graphically as Nautilus cant access it.
Any script to restore will be appreciated. Thanks

---

### Post by lian1238 on 2010-03-19
> **seanbw said:**
> Thank you. I found the folder here: /root/.local/share/Trash/files/Documents/
How can I restore it as I cant find it graphically as Nautilus cant access it.
Any script to restore will be appreciated. Thanks

You can run nautilus as root and do it graphically:
```
gksudo nautilus
```

Or you can move it back to your home from the commandline:```
sudo mv /root/.local/share/Trash/files/Documents/ ~/
```

---

### Post by seanbw on 2010-03-19
> **seanbw said:**
> Thank you. I found the folder here: /root/.local/share/Trash/files/Documents/
How can I restore it as I cant find it graphically as Nautilus cant access it.
Any script to restore will be appreciated. Thanks
Nautilus can find /root/.local/share/Trash/files/* but no Documents in that folder just as trash does not show  the Documents folder as well. What is going on and how can I restore what I can't see?

---

### Post by lian1238 on 2010-03-19
> **seanbw said:**
> Nautilus can find /root/.local/share/Trash/files/* but no Documents in that folder just as trash does not show  the Documents folder as well. What is going on and how can I restore what I can't see?

Try to cd to that folder and see what's there:

```

sudo -i
cd /root/.local/share/Trash/files/
ls . -a

```

---

### Post by seanbw on 2010-03-19
> **lian1238 said:**
> You can run nautilus as root and do it graphically:
```
gksudo nautilus
```

Or you can move it back to your home from the commandline:```
sudo mv /root/.local/share/Trash/files/Documents/ ~/
```
How can I delete a file or folders that are duplicated? Is there a  delete command that uses the -u option that I can use? No that works  with cp or mv but I don't know how to script that?

---

### Post by seanbw on 2010-03-19
I am really grateful for everybody that helped. I've got my folder back.Thank you very much all of you.

---

### Post by anksush on 2010-03-19
do you want to try this
gksudo nautilus
then in nautilus goto goto view and select Show hidden files.

Now browse your way through to Trash - .local/share/Trash/files

you should now be able to see and copy paste it in graphical mode...

HTH !!!

---

### Post by lian1238 on 2010-03-20
> **seanbw said:**
> I am really grateful for everybody that helped. I've got my folder back.Thank you very much all of you.

I'm so relieved for you! :D

But it's weird that root deleted your files though. A security issue or malicious program/script? You might want to run history and see what commands were executed that caused this.

---

### Post by seanbw on 2010-03-21
How do I run history? What script do I run? I am now very well scared that I am now nightly backing to a separate hdd. I was also thinking of automating the backup but I need to open a separate thread for that.

---

### Post by lian1238 on 2010-03-21
The command is just "history". Run it in a terminal and see if you can find any command that has "Documents" that was run before you started trying to find your Documents folder. Backing up is a good idea. I shall do the same. :D

---

### Post by llamabr on 2010-03-21
I doubt it was something malicious.  In fact, if you show us your history, we'll show you where you went wrong.  Much more likely that you're running something as root that you don't need to, or else running root commands that you don't understand.

---

### Post by cornelldekgm5 on 2011-01-06
> ** said:**
> *Anybody can answer it? I'm still [[COLOR=#000000]waiting[/COLOR]](http://www.changeformat.net/change-avi-format/change-avi-to-iriver-u10.html) for the answer.

---

### Post by seanbw on 2011-03-30
I apologiise. Should have marked thread solved. Got the docs back. I did not run the history on time and could not get what went wrong but I suspect it is my pc.
Now I have five tgz files that  I can "see" but are not there. I can't delete it using nautilus or dolphin or terminal even at root level.
Will mark thread solved.
This community is great. Sean

---

