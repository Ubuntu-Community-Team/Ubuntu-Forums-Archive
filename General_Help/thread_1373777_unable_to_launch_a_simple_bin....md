---
title: "unable to launch a simple bin..."
date: 2010-01-06
forum: General Help
---

### Post by batmars on 2010-01-06
Hello,

I am unable to launch a bin... 

```
$ ./CellDesigner-4.0.1-linux-installer.bin
```

It is very weird ... there is no error message and nothing happen... (normally a window is displayed).

The program is normally build for fedora but I succeed to install it in ubuntu 9.04. Now I am working on 9.10.

if I use /bin/bash :

```
$ /bin/bash CellDesigner-4.0.1-linux-installer.bin 
CellDesigner-4.0.1-linux-installer.bin: CellDesigner-4.0.1-linux-installer.bin: cannot execute binary file
```


if I use sh:
```

sudo sh CellDesigner-4.0.1-linux-installer.bin
CellDesigner-4.0.1-linux-installer.bin: 1: Syntax error: "(" unexpected
```



I downloaded the file two times, it is not corrupted... the permission are set also...

I think it can be due to the 3D effect or something like that (when I succeed to install it I had no visual effect option setted). I tried to supress all this stuffs but I am still unable to launch the installer...


Do you have any idea ?

Thanks in advance !

- batmars

---

### Post by kellemes on 2010-01-06
Is it executable?
```
chmod +x <filename>
```

---

### Post by mcduck on 2010-01-06
It's a binary file, not a shell script, so you shouldn't try to launch it with a shell.

Try this:
```
./CellDesigner-4.0.1-linux-installer.bin
```

---

### Post by batmars on 2010-01-06
[HTML]Is it executable?[/HTML]

Yes...

[HTML]It's a binary file, not a shell script, so you shouldn't try to launch it with a shell.

Try this:
 	Code: 	./CellDesigner-4.0.1-linux-installer.bin [/HTML]

first thing I have done. not work, no error message & no window displayed...

maybe it is because it is a redhat program not debian.... but I succeed to install it in a older version of ubuntu....



- Martial

---

### Post by batmars on 2010-01-06
I have the same problem on the mac ... Actually i have a dual boot mac os X snow leopard, ubuntu9.10. So, in snow leo, I dld the installer, set the permission with chmod, launch the app ... and nothing happen... no window is displayed... no error message... nothing... the same thing as in ubuntu...

I do not know... mabe it can be a clue for u....

---

### Post by pbrane on 2010-01-06
> **batmars said:**
> 

if I use sh:
```

sudo sh CellDesigner-4.0.1-linux-installer.bin
CellDesigner-4.0.1-linux-installer.bin: 1: Syntax error: "(" unexpected
```

- batmars

This .bin file is most likely a shell script with a binary file concatenated to the end of it. That syntax error is telling you something. With a hex editor you can copy just the script to a text file and see if you can fix it. The hex editor will also be a good way to see if I'm right about this file. Sometimes you can even do what the script does manually and do a successful install.

---

### Post by howefield on 2010-01-06
From the install readme.


> 1.3.3    Linux
      1. Open a shell and, cd to the directory where you downloaded the installer.
      2. At the prompt, type,
         % chmod u+x CellDesigner-4.0-linux-installer.bin
         % ./CellDesigner-4.0-linux-installer.bin
      3. The installer window should open, and follow the message therein.

---

### Post by 3rdalbum on 2010-01-06
> **batmars said:**
> I have the same problem on the mac ... Actually i have a dual boot mac os X snow leopard, ubuntu9.10. So, in snow leo, I dld the installer, set the permission with chmod, launch the app ... and nothing happen... no window is displayed... no error message... nothing... the same thing as in ubuntu...

I do not know... mabe it can be a clue for u....

Mac OS X doesn't read the ELF executable format that Linux uses.

---

### Post by batmars on 2010-01-06
Thanks for your answers.

@howefield: 
Thanks for having searching on the website.
Actually I started by following this tuto. And nothing happen: I mean no error message, no window displayed...

@3rdalbum:
Sorry to not be clear. CellDesigner has a installer specific for mac also.

@pbrane
I just opened it with mc. It is a complete bin file !! I see no human-readable piece !

Do you have other suggestions ? In the french ubunzu forum, they gave up !!

---

### Post by rnerwein on 2010-01-06
hi
please post the output of the file command to see what kind of file it really is 
 file ./CellDesigner-4.0.1-linux-installer.bin

---

### Post by batmars on 2010-01-06
Voici,

```

~/Local$ file ./CellDesigner-4.0.1-linux-installer.bin
./CellDesigner-4.0.1-linux-installer.bin: ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), statically linked, stripped

```

---

### Post by darkksyde on 2010-01-06
The file you downloaded could be bad, have u tried checksumming it or redownloading it to see if that fixes it

---

### Post by pbrane on 2010-01-06
batmars:

the first thing you see is something like this?
```

00000000   7F 45 4C 46  02 01 01 00  00 00 00 00  00 00 00 00  .ELF............

```
if so then it is an executable. I'm not sure what would cause a syntax error in what you typed on the command line. That's odd. If you really need this app then you may try it in wine with the windows version.

---

### Post by batmars on 2010-01-06
>  		The file you downloaded could be bad, have u tried checksumming it or redownloading it to see if that fixes it 	

It was already done.

I solved the problem on mac. I will be able to use it anyway...

Thanks to everybody for the help.

bye

---

### Post by bha on 2013-01-20
# file ./CellDesigner-4.1-linux-installer.bin

./CellDesigner-4.1-linux-installer.bin: data

---

### Post by howefield on 2013-01-20
Old thread closed.

---

