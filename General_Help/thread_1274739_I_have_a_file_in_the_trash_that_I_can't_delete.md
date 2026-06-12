---
title: "I have a file in the trash that I can't delete"
date: 2009-09-24
forum: General Help
---

### Post by BigCityCat on 2009-09-24
I was trying to install this program with cmake. I had to start over and this file I deleted will not empty out of trash.

It says 

could not delete file 

/home/paul/.local/share/trash/files/nameoffile/build/cmakecache.txt

---

### Post by tuxxy on 2009-09-24
Try and remove from terminal, cd to your trash then remove the file, it will look like this below but you may need to add your specific information slightly

```
cd /home/paul/.local/share/Trash/files
``````
rm -rf cmakecache.txt
```

---

### Post by BigCityCat on 2009-09-24
okay I did what you said but it didn't do anything.

---

### Post by Vaphell on 2009-09-24
use tab (autocomplete) and double-tab (showing all options)
cd ~/.local/share
cd [tab][tab]
and you will see all objects in that directory. it certainly helps to produce valid paths

---

### Post by tuxxy on 2009-09-24
> **BigCityCat said:**
> I tried cd Trash and cd trash, but it says no such file or directory.

Your trash location is /home/paul/.local/share/trash/files/

To delete the file cmakecache.txt just enter this command;

```
rm -rf /home/paul/.local/share/Trash/files/nameoffile/build/cmakecache.txt     
```

---

### Post by renkinjutsu on 2009-09-24
probably the permissions are wrong.
```
ls -l ~/.local/share/Trash/files
```
and if it's owned by root, you'd have to delete it with root

---

### Post by BigCityCat on 2009-09-24
I did this


rm -rf /home/paul/.local/share/Trash/files/smooth-tasks-src-wip-2009-09-21111/build/cmakecache.txt


 and it didn't do anything. The name of the file is absolutely correct.

---

### Post by bigboy_pdb on 2009-09-24
If the file didn't get deleted, it might be because there's information stating that the file still exists in the trash folder.

Open your file manager and open the directory "/home/dave/.local/share/Trash". There should be other folders other than the "file" folder in there. You might need to delete a file in the "info" folder (if I remember correctly).

**EDIT**: You can try to delete the file in the "file" folder directly instead of typing it into the command line.

**EDIT**: You can also try it as root (using 'sudo rm ...' or by opening the file manager as root).

---

### Post by BigCityCat on 2009-09-24
> **renkinjutsu said:**
> probably the permissions are wrong.
```
ls -l ~/.local/share/Trash/files
```
and if it's owned by root, you'd have to delete it with root

here is the output from your command

total 4
drwxr-xr-x 5 paul paul 4096 2009-09-24 21:23 smooth-tasks-src-wip-2009-09-21111

---

### Post by akakingess on 2009-09-24
Like the previous poster stated, if it is owned by root, you will need to add "sudo" (without the quotation marks) in the front of the command, then it will prompt you for a password and that should work, if that is in fact the issue.

---

### Post by BigCityCat on 2009-09-24
> **akakingess said:**
> Like the previous poster stated, if it is owned by root, you will need to add "sudo" (without the quotation marks) in the front of the command, then it will prompt you for a password and that should work, if that is in fact the issue.

I tried sudo rm -rf /home/paul/.local/share/Trash/files/smooth-tasks-src-wip-2009-09-21111/build/cmakecache.txt

and nothing.

---

### Post by BigCityCat on 2009-09-24
> **Vaphell said:**
> use tab (autocomplete) and double-tab (showing all options)
cd ~/.local/share
cd [tab][tab]
and you will see all objects in that directory. it certainly helps to produce valid paths

I don't understand tab auto complete and double tab

---

### Post by bigboy_pdb on 2009-09-24
When you say "nothing", do you mean the cursor returns and the file is still there? If you're viewing the file in a file browser, you should refresh the folder (F5). If you used ls to list the files then it would still be there.

It's possible that a process is using the file and it can't be deleted as a result of that so you might want to close all windows (or at least those that could be accessing the file) and reopen them. However, if there was a problem deleting the file then an error should be displayed.

---

### Post by BigCityCat on 2009-09-24
The answer to your question is. In the terminal....There was no output. The folders were all closed and the file is still in the trash.






I went into the file I deleted all the contents except it wont let me delete the folder build.

I was using root when I was trying to install this. I think Cmake is still trying to use it but I did killall cmake. that didn't work.

When i try and delete build which is a directory inside of the file. It says access denied.

---

### Post by tuxxy on 2009-09-24
ok do this and ti should go, open a terminal and type

```
gksudo nautilus /home/paul/.local/share/Trash/files/
```

Your trash will appear so navigate to it and delete the file as normal with the mouse.

---

### Post by BigCityCat on 2009-09-24
> **tuxxy said:**
> ok do this and ti should go, open a terminal and type

```
gksudo nautilus /home/paul/.local/share/Trash/files/
```

Your trash will appear so navigate to it and delete the file as normal with the mouse.

well I'm using Kubuntu so should I do gksudo dolphin?

---

### Post by tuxxy on 2009-09-24
oh yes heh I forgot about that.  Yes use your file managers name instead

---

### Post by BigCityCat on 2009-09-24
That worked with Dolphin. Thanks man

---

### Post by tuxxy on 2009-09-24
hey your welcome man, case closed as they say :lolflag:

---

### Post by BigCityCat on 2009-09-24
no doubt. I will update solved. Peace

---

### Post by renkinjutsu on 2009-09-24
> **BigCityCat said:**
> here is the output from your command

total 4
drwxr-xr-x 5 paul paul 4096 2009-09-24 21:23 smooth-tasks-src-wip-2009-09-21111

hmm .. sorry, that just got the permissions of the directory, but the problem is the permissions set on the file inside that directory.. your folder seems fine

try this ```
ls -l ~/.local/share/Trash/files/smooth-tasks-src-wip-2009-09-21111/build
``` i think that's your directory right? .. just to see if the cmake-whatever file is owned by you "paul" and not "root" .. if it's owned by root, then the solution's simple.. like the previous poster said, just ```
sudo rm -r ~./local/share/Trash/files/smooth-tasks-src-wip-2009-09-21111
```

---

### Post by renkinjutsu on 2009-09-24
EDIT:
wait... that's a bad idea, don't delete recursively (just in case)
instead, do this
```
sudo chown -R paul ~/.local/share/Trash/files
```
and then empty the trash like you normally would.


EDIT: brainfart.. thought i had clicked the edit button.

---

### Post by BigCityCat on 2009-09-24
Thanks for your help all. Great community as usual. I got it thanks.

---

