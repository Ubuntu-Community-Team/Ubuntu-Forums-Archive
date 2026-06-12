---
title: "can;t delete a file"
date: 2010-11-06
forum: General Help
---

### Post by skag on 2010-11-06
Hi,
Im using Kubuntu 10.04 with KDE 4.4.2.
I just downloaded a file thinking it was an e-book. It was in a zip archive I extracted and tried to open it but okular wrote me a message that it doesnt exist... After that i tried to delete it but i get this message: The file or folder /home/<user>/Desktop/&#426; &#65533;&#1518;&#65533; - &#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#1390;&#65533;&#65533;&#65533;.pdf does not exist.


When trying to delete it with sudo rm i get this:
rm: cannot remove `/home/<user>/Desktop/&#426;': No such file or directory
rm: cannot remove `&#65533;\327\256&#65533;': No such file or directory
rm: cannot remove `-': No such file or directory
rm: cannot remove `&#65533;&#65533;&#65533;&#65533;&#65533;': No such file or directory
rm: cannot remove `&#65533;&#1390;&#65533;&#65533;&#65533;.pdf': No such file or directory


its name is weird but i can't rename it either.... what can i do??? plz help because it's on my desktop :P :/ thnx :)

---

### Post by m4tic on 2010-11-06
Restart the computer. You may want to check your disk for errors, boot from the recovery mode

---

### Post by skag on 2010-11-07
tried but did nothing... I think the problem is on the name.. It's in greek and the encoding in utf-8... thats why it cant read it and takes it as deleted file... any ideas?

---

### Post by gsocker on 2010-11-07
When you tried deleting it from the command line, did you put single quotes  around the file name?
```
sudo rm 'file name here.ext' 
```If you run ```
rm file name here.ext
``` without the quotes, it will treat each word as a separate file - the same effect as if you ran
```

 rm file 
rm name 
rm here.ext

```Looking at the output, this appears to be what happened.

---

### Post by tredegar on 2010-11-07
It might be easiest to delete the file by its inode number.
First, find what the inode number is
```
cd Desktop
ls -i *
```
Make a note of the inode number of the greek file.
Now remove it:
```
find . -inum *inodenumber* -exec rm -i {} \;
```
Obviously, replace *inodenumber* with the number you noted down earlier.

---

### Post by skag on 2010-11-08
it worked with the inode number ;) thnx :D i tried with ' ' at first but it said the same... thnx again :)

---

