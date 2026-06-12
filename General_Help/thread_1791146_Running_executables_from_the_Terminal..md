---
title: "Running executables from the Terminal."
date: 2011-06-26
forum: General Help
---

### Post by Son Of Nova on 2011-06-26
Hey again ubuntu forums! 

I'm trying to run flasm from the terminal prompt but I don't really know what I'm doing. It may be an incompatible program for all I know but as I don't know how to run any .exe from the Terminal I have no way of knowing.

I've tried entering the directory, as in:

```
/home/homefolder/flasm
```

but it say's the directory doesn't exist. But it does...

```
/home/homefolder
``` <- This says "is a directory", and that is where the flasm folder is (in homefolder). 

A little guidance from the experts here would be awesome :)

Thanks loads. 
SON

---

### Post by dabl on 2011-06-26
How did you install flasm?  If you downloaded a tarball or something like that, open a terminal and issue:

```
sudo apt-get update && sudo apt-get install flasm
```

Then try running it again.

---

### Post by mendhak on 2011-06-26
Hi, directories are case sensitive, so when in terminal, use tabs to autocomplete the name for you.  Can you do 

ls /home/homefolder

and see flasm in the results there?


Another way you can do this is to open up Nautilus (the file explorer), go to the flasm folder, then press Ctrl+L.  You'll see a textbox appear at the top, and you can copy the path to the folder from there.  Right click and paste into your terminal window.

---

### Post by Bachstelze on 2011-06-26
> **Son Of Nova said:**
> 
I've tried entering the directory, as in:

```
/home/homefolder/flasm
```


Try [font=monospace]cd /home/homefolder/flasm[/font] ;)

---

### Post by Son Of Nova on 2011-06-26
Thanks all for coming through for me again! This is most helpful tech forum I've ever encountered!

Yeah I was'nt adding cd, and was ignoring the uppercase 'F' that I used when I named the folder myself :P 

I didn't know it was case sensitive though, thanks for that!

Apparently flasm is just an executable and doesn't need installing, and I got it working in the Terminal after entering

```
cd/home/homefolder/flasm
```

flasm$ ```
./flasm
```

Voila! I got the "./" thing from flasm's webpage, what does it mean though? Does it mean run or execute or something? Or is it like a filetype prefix? 

Just to make it clear, flasm.exe was in the folder named "flasm". (I renamed the folder using all lower case.)

---

### Post by Bachstelze on 2011-06-26
. is a shortcut for "current directory", so ./flasm refers to the file name flasm in the current directory. If you do

```
ls flasm
```

and

```
ls ./flasm
```

It will be the same file. However, when you execute a file, you must give ./flasm, just flasm will not work. It is a security measure, so that you don't accidentally run an executable you didn't want to run.

---

