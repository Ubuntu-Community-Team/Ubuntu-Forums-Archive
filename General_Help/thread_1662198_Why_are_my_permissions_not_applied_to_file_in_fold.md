---
title: "Why are my permissions not applied to file in folder?"
date: 2011-01-07
forum: General Help
---

### Post by sofasurfer on 2011-01-07
I have a folder which contains an image file. I right click the folder and change permission to "access only". I also click on "apply to enclosed files". However, the file is NOT protected. It is still in a "read and write" state. I am, however, not able to delete the file. I don't get it. Please explain.

---

### Post by CandidMan on 2011-01-07
Hi there,

I'm looking at my folder permission options in Nautilus and there are two drop-down lists: one for folder access and for file access

Have you selected file access also?

---

### Post by sofasurfer on 2011-01-07
I right click the folder. Open permissions tab. 
Folder access=access files
File access=nothing
I change file access to read only and close window. When I open the permission tab again the file access to still set to nothing.

With that said I will now add this...
I changed folder access to create and delete. Then change file access to read only. You must remember to click on "apply to enclosed files". The locks the files.

It looks like you can only have the folder locked or the files locked. You can not have them both locked. So if the files are locked, you can not tell by just looking at the folder. It does not have a padlock icon if the files in it are locked. So if I am looking at a pile of folders I can not tel which ones have locked files. I do not like that. I thought that the padlock on the folder would tell me that the files in it were safe.
Sorry for rambling. Hope I didn't make it more confusing than it is.

---

### Post by CandidMan on 2011-01-07
How comfortable are you with the command-line? 
Because it sounds like using the chmod command would be simpler than trying the permission tab on Nautilus

Something like:
chmod -R a=r /My\ Folder/

---

### Post by CandidMan on 2011-01-07
As an alternative, you could try the "chattr +i" command and option

In theory it makes the file unchangeable even to the administrator

That could be simpler

---

### Post by JC Cheloven on 2011-01-07
Hi,
What type of filesystem are your files on?  
If it's ntfs, the usual linux permissions scheme will not work, as that filesytem doesn't support it. But you can create a mask for permissions, what is needed is called ```
umask
```

---

### Post by sofasurfer on 2011-01-07
ext 3 or 4

---

### Post by WorMzy on 2011-01-07
What is the current ownership and permissions on the file?

(if you're unsure, open a terminal (Applications -> Accessories -> Terminal) and type ```
ls -l
```
followed by a space, then drag the file from nautilus into the terminal, then press Enter.

(by the way, that "l" is a lower case "L", not a "one".)

Alternatively, just type the location of the file after "ls -l". e.g.

```
ls -l /home/sofa/thisfile.txt
```

---

### Post by JC Cheloven on 2011-01-07
> **sofasurfer said:**
> ext 3 or 4
OK, then permissions should work. Trying to figure out what the problem is, ownership comes to mind. Are you the owner of the folder/files?

To let us collect ideas, please open a terminal, go to the folder under question (using the cd command) and type ```
ls -al
```
It can also be of help seeing the permissions and ownership of the folder itself. So, go a step backwards (cd ..) and type again the above "ls -al" command.

---

