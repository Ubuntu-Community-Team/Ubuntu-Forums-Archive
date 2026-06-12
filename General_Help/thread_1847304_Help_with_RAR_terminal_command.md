---
title: "Help with RAR terminal command"
date: 2011-09-20
forum: General Help
---

### Post by wpf999 on 2011-09-20
Hi,

I have a directory containing about 20 files and I wish to put them into separate RAR archives. If I type the following command, it creates one big archive of the directory contents:

rar a Documents.rar Documents

I've been trying hard to find a switch that would let me create separate rar archives for each file in the directory but haven't found anything.

Can anyone help, please?

Thanks in advance.

---

### Post by magsnus on 2011-09-20
Well you can try:

rar a Documents.rar Documents/*
Will add all files in the Documents folder.

---

### Post by blueridgedog on 2011-09-20
Not tested:

```
for f in /home/USER/Documents/*;do rar a &#8220;$f&#8221;.rar "$f";done
```

Change USER or path as required...full paths are preferred.

---

### Post by wpf999 on 2011-09-20
> **magsnus said:**
> Well you can try:

rar a Documents.rar Documents/*
Will add all files in the Documents folder.

Thanks, but that adds them all in ONE file. I want all the files in separate files (one for each file contained in the Documents directory)

---

### Post by wpf999 on 2011-09-20
> **blueridgedog said:**
> Not tested:

```
for f in /home/USER/Documents/*;do rar a “$f”.rar "$f";done
```

Change USER or path as required...full paths are preferred.

Sorry but I didn't quite understand the command I should send.

If I have say file1, file2 and file3 in the Documents directory, what single command would give me the result of file1.rar, file2.rar and file3.rar?

Thanks

---

### Post by blueridgedog on 2011-09-20
> **wpf999 said:**
> If I have say file1, file2 and file3 in the Documents directory, what single command would give me the result of file1.rar, file2.rar and file3.rar?


This is one command that will give you file1.rar, file2.rar and file3.rar:

```
for f in /home/USER/Documents/*;do rar a &#8220;$f&#8221;.rar "$f";done
```

```
james@james-VirtualBox:~/Documents$ pwd
/home/james/Documents
james@james-VirtualBox:~/Documents$ ls
file1  file2  file3
james@james-VirtualBox:~/Documents$ for f in /home/james/Documents/*; do rar a "$f".rar "$f";done

Creating archive /home/james/Documents/file1.rar

Adding    /home/james/Documents/file1                                 OK 
Done

Creating archive /home/james/Documents/file2.rar

Adding    /home/james/Documents/file2                                 OK 
Done

Creating archive /home/james/Documents/file3.rar

Adding    /home/james/Documents/file3                                 OK 
Done
james@james-VirtualBox:~/Documents$ ls
file1  file1.rar  file2  file2.rar  file3  file3.rar
james@james-VirtualBox:~/Documents$ 

```

---

### Post by seawolf167 on 2011-09-20
Then just use a

```
mv /source/*.rar /destination/directory
```

to separate out all your newly created .rar files

---

### Post by wpf999 on 2011-09-20
> **blueridgedog said:**
> This is one command that will give you file1.rar, file2.rar and file3.rar:

```
for f in /home/USER/Documents/*;do rar a “$f”.rar "$f";done
```

```
james@james-VirtualBox:~/Documents$ pwd
/home/james/Documents
james@james-VirtualBox:~/Documents$ ls
file1  file2  file3
james@james-VirtualBox:~/Documents$ for f in /home/james/Documents/*; do rar a "$f".rar "$f";done

Creating archive /home/james/Documents/file1.rar

Adding    /home/james/Documents/file1                                 OK 
Done

Creating archive /home/james/Documents/file2.rar

Adding    /home/james/Documents/file2                                 OK 
Done

Creating archive /home/james/Documents/file3.rar

Adding    /home/james/Documents/file3                                 OK 
Done
james@james-VirtualBox:~/Documents$ ls
file1  file1.rar  file2  file2.rar  file3  file3.rar
james@james-VirtualBox:~/Documents$ 

```

Oh I see now. Brilliant. Sorry for being slow but I'm new to RAR commands. Thanks so much for the explanation. I'd been searching high and low for that.

Cheers

---

### Post by blueridgedog on 2011-09-20
It is not a RAR command exactly, it uses the power of the bash shell to string commands and assemble loops on a single command line.  Shell scripting and bash commands are the true reason for Linux's amazing ability to tackle most any file processing chore simply and quickly.

---

### Post by wpf999 on 2011-09-20
> **seawolf167 said:**
> Then just use a

```
mv /source/*.rar /destination/directory
```

to separate out all your newly created .rar files


Great. Thanks for that :-)

---

### Post by wpf999 on 2011-09-20
> **blueridgedog said:**
> It is not a RAR command exactly, it uses the power of the bash shell to string commands and assemble loops on a single command line.  Shell scripting and bash commands are the true reason for Linux's amazing ability to tackle most any file processing chore simply and quickly.

Thanks again bluedog. You've given me the urge to look into bash commands! :)

I'd only been looking for RAR commands and there doesn't seem to be one for separating the files out individually.

---

### Post by seawolf167 on 2011-09-20
> **wpf999 said:**
> You've given me the urge to look into bash commands! :)

If you want to start learning Bash - take a look at [this guide]("http://mywiki.wooledge.org/BashGuide").

---

### Post by wpf999 on 2011-09-20
> **seawolf167 said:**
> If you want to start learning Bash - take a look at [this guide]("http://mywiki.wooledge.org/BashGuide").

Thanks. I will :)

---

