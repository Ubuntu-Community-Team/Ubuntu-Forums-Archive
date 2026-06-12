---
title: "How to copy files via terminal?"
date: 2012-10-04
forum: General Help
---

### Post by Chelidze on 2012-10-04
This might sound silly for some people but I'm new to Linux and don't know how to use it as good as other people, yes I rad about copying files with terminal but these examples will help me a lot.

So here is what I want to do:

Examples: I want to copy folder ,,my documents'' from this directory [/media/sda3/SkyDrive]("http://i.imgur.com/yviyH.png") 
 to this directory [/media/levan/PENDRIVE]("http://i.imgur.com/KokiM.png") but do not want to delete any thing in /media/levan/PENDRIVE 


 Thank you in advanced

---

### Post by windscape on 2012-10-04
Hi,

Try this command: 

```
cp -av "/media/sda3/SkyDrive/My Documents" /media/levan/PENDRIVE
```

---

### Post by drmrgd on 2012-10-04
It's fairly straightforward, and the copy command, 'cp' works pretty much how you might anticipate it to.  To copy a file from one location to another, you would use:

```
cp /location1/file /location2/
```

In the case of folders (or directories as they're often referred to in Linux), you need to add the '-r' option to work recursively.  So, if you want to copy a folder from location 1 to location 2, it becomes:

```
cp -r /location1/folder/ /location2/ 
```

One other thing to note is that the command line is case-sensitive ('documents' is not the same as 'Documents'), and every character is considered part of the command.  So, if you have a file called 'My Documents', the space will tell the system that there are two folders or files, one called 'My' and one called 'Documents'.  The best way around that is to surround the file or folder with quotation marks.  So, back to your original case, to copy 'my documents' to '/media/levan/PENDRIVE', you would run:

```
cp -r "/media/sda3/SkyDrive/my documents" /media/levan/PENDRIVE/
```

To find out more about the functionality of the cp command, you can run:

```
man cp
```

That will give you the manual for the copy command and how to use it.  You could also have a look at the Commandline documentation here for more tips and advice:

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Hope that helps!

---

### Post by Chelidze on 2012-10-04
> **windscape said:**
> Hi,

Try this command: 

```
cp -av "/media/sda3/SkyDrive/My Documents" /media/levan/PENDRIVE
```

Thank you, for the reply if you do not mind can i ask you a question.

 what does ,,av" stands for they told me to use (-i or -b)and ( " " ) do i need to use " or there is a special occasion when i need to use it 

**drmrgd** thank you for the  details but i tried using cp (-i or -b)did not work and i do not know why

---

### Post by drmrgd on 2012-10-04
Again, have a quick look at the man pages for cp, as that will help you determine what the options are for.  In this case, the -a option is for 'archive' (I'm not 100% on the functionality of that...have to look it up myself!), and -i is for interactive which will prompt you to answer yes or no for each file that you copy if it's going to replace the same file in the target location.

Also, in order to help more effectively, when you run a command and get an error, please post the error message here.  Please use code tags (the # button at the top of the window you type in), so that it's easier to read and we can see what went wrong.

---

### Post by Wim Sturkenboom on 2012-10-04
> **Chelidze said:**
> **drmrgd** thank you for the  details but i tried using cp (-i or -b)did not work and i do not know whyIf you post the exact command that you used and the error message(s), we might be able to help further.

Use code tags in your post as it makes it easier to read

Type [noparse]```
[/noparse], paste your command and messages after that and at the end of the pasted text type [noparse]
```[/noparse]

It will look like below
```

wim@i3-2120:~$ cp -R *.wim.abc /mnt
cp: cannot stat `*.wim.abc': No such file or directory
wim@i3-2120:~$ 

```

---

### Post by nsturdev on 2012-10-04
Chelidze,

av is actually a & v, a is the option for archive which basically means everything. v is the option for verbose which means that  it will tell you each step as its doing it (ie. copying file.txt, copying file2.txt)

as for the quote that denotes a string literal.  file systems don't like spaces so using "s allows you to type the actual path

for example:

say you had a folder in your user director call (test files) the path that unix sees is /home/username/test\ files/
\ telling the computer to use the space as a space and not the beginning of a new argument.

if you want to specify that folder without the \ you would just surround the path with ""  i.e. "/home/username/test files/"  that tells the computer you mean that path letter for letter so it will automatically translate that to the path with the \ symbol.

it sounds like based on the thread so far however that you are looking at backup of files (-b and -i options )

may i suggest you take a look at rsync as an alternative for that.

to copy but no overwrite files you might look at rsynch -u it will copy files that don't exist in the destinatino folder and update files in the destination folder if the file in the originating folder is newer ( -u option)

rsync -u location1/file location2/

for directories 

rsync -ru location1/ location2/

---

### Post by Chelidze on 2012-10-04
> **Wim Sturkenboom said:**
> If you post the exact command that you used and the error message(s), we might be able to help further.

Use code tags in your post as it makes it easier to read

Type [noparse]```
[/noparse], paste your command and messages after that and at the end of the pasted text type [noparse]
```[/noparse]

It will look like below
```

wim@i3-2120:~$ cp -R *.wim.abc /mnt
cp: cannot stat `*.wim.abc': No such file or directory
wim@i3-2120:~$ 

```



 for example 

```
levan@Saturn:~$ cp -i /media/sda2/Documents and Settings/Dreamcast/Desktop/Outerspace Rainbowness.wmv /media/levan/PENDRIVE/test
cp: cannot stat `/media/sda2/Documents': No such file or directory
cp: cannot stat `and': No such file or directory
cp: cannot stat `Settings/Dreamcast/Desktop/Outerspace': No such file or directory
cp: cannot stat `Rainbowness.wmv': No such file or directory
levan@Saturn:~$ 



```

[http://i.imgur.com/DosSu.png](http://i.imgur.com/DosSu.png)

file and folder screenshot

---

### Post by nsturdev on 2012-10-04
try ```
 cp -i "/media/sda2/Documents and Settings/Dreamcast/Desktop/Outerspace Rainbowness.wmv" /media/levan/PENDRIVE/test/ 
```

also ensure that you have a test folder under /media/levan/PENDRIVE/ before you try to copy.

```
 mkdir /media/levan/PENDRIVE/test 
```

---

### Post by drmrgd on 2012-10-04
> **Chelidze said:**
> for example 

```
levan@Saturn:~$ cp -i /media/sda2/Documents and Settings/Dreamcast/Desktop/Outerspace Rainbowness.wmv /media/levan/PENDRIVE/test
cp: cannot stat `/media/sda2/Documents': No such file or directory
cp: cannot stat `and': No such file or directory
cp: cannot stat `Settings/Dreamcast/Desktop/Outerspace': No such file or directory
cp: cannot stat `Rainbowness.wmv': No such file or directory
levan@Saturn:~$ 



```

[http://i.imgur.com/DosSu.png](http://i.imgur.com/DosSu.png)

file and folder screenshot

As I said above, you have to be careful with spaces in filenames.  The error say, "can't find /media/sda2/Documents" because a folder called "Documents" does not exist.  Same thing for a folder called "And", and a folder called "Settings".  As I said, spaces are interpreted by the system as individual items, and the system has no way to know that you intended a filename with spaces to be all together.  You by pass that by adding the quotation marks around everything so that the system knows you means "Documents And Settings" instead of "Documents", "And", and "Settings".  Does that make sense?

---

### Post by Chelidze on 2012-10-04
> **nsturdev said:**
> try ```
 cp -i "/media/sda2/Documents and Settings/Dreamcast/Desktop/Outerspace Rainbowness.wmv" /media/levan/PENDRIVE/test/ 
```

also ensure that you have a test folder under /media/levan/PENDRIVE/ before you try to copy.

```
 mkdir /media/levan/PENDRIVE/test 
```

Thank you it worked just adding '' did the trick 
yes i had test folder 

have to read **nsturdev** post more careful he explained this in details

 thank you

**drmrgd**
```
As I said above, you have to be careful with spaces in filenames. The error say, "can't find /media/sda2/Documents" because a folder called "Documents" does not exist. Same thing for a folder called "And", and a folder called "Settings". As I said, spaces are interpreted by the system as individual items, and the system has no way to know that you intended a filename with spaces to be all together. You by pass that by adding the quotation marks around everything so that the system knows you means "Documents And Settings" instead of "Documents", "And", and "Settings". Does that make sense?
```

thank you 

thank you every one for the help. :KS
god bless you

---

### Post by Wim Sturkenboom on 2012-10-05
Just a note:

bash has an auto-complete function. After typing e.g. "cp -i /media/sda2/Docu", you can press <tab> and if "Documents and Settings" is the only file or directory, it will automatically complete it to
```

cp -i /media/sda2/Documents\ and\ Settings/

```

---

