---
title: "untarring help"
date: 2011-03-07
forum: General Help
---

### Post by slomo5793 on 2011-03-07
Hi

i want to install skippy on my laptop
i have the tar.bz2 file but when i do

```
tar -xjf skippy-0.5.0.tar.bz2
```

i get an error: 


```
tar (child): skippy-0.5.0.tar.bz2: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
```


the exact name of the file is that
i also tried to put the file in my desktop and write 
Desktop/skippy-0.5.0.tar.bz2
but i dont get any return in the command
is that supposed to happen?

---

### Post by tordeu on 2011-03-07
The command is correct. Are you in the correct directory when you execute tar?
I mean, if you downloaded skippy to your Downloads folder, did you do change to that folder first? Like this:
```

cd ~/Downloads
tar -xjf skippy-0.5.0.tar.bz2

```

---

### Post by slomo5793 on 2011-03-07
it didnt say anything after i wrote that

does that mean it happened?

---

### Post by WorMzy on 2011-03-07
The location that you run the command from is very important. By default, when you open a terminal, your shell will be in your home directory (/home/username). You need to "cd" (change directory) to the folder where the tar file is before running "tar -xjf skippy-0.5.0.tar.bz2".

e.g.

```
cd Downloads
tar -xjf skippy-0.5.0.tar.bz2
```

This will extract the content of the archive to your Downloads folder.

Alternatively, you can state the file's location relative to your shell's current location, like you did in your second command. Assuming you haven't used "cd" to move away from your home directory, this will work:

```
tar -xjf Downloads/skippy-0.5.0.tar.bz2
```

and will extract the content of the archive to your home folder. Using an absolute path will have the same effect:

```
tar -xjf /home/username/Downloads/skippy-0.5.0.tar.bz2
```

Despite the terminal not displaying any output, the archive is being extracted. If you want to see that something is happening, add the -v flag to the tar command:

```
tar -xvjf /home/username/Downloads/skippy-0.5.0.tar.bz2
```

That will make the command verbose, and all the files affected by the command will be listed in the terminal.

---

### Post by jcolyn on 2011-03-07
Here is an easy way to do it. Create a temp folder in your /home folder. Now go to the downloaded file and right-click it and choose extract to then choose to the temp folder you created. Now open a terminal and cd to that folder and type 
```
./configure
``` at the prompt type 
```
make
``` then finally 
```
sudo make install
```

---

### Post by tordeu on 2011-03-07
> **slomo5793 said:**
> it didnt say anything after i wrote that

does that mean it happened?

Yes, if tar did not produce an error this time, it should have worked and there should be a folder name skippy-0.5.0 in your downloads folder now. If a program does not say anything, it is usually a good sign, meaning that there was no problem.

---

### Post by slomo5793 on 2011-03-07
@WorMzy,  thanks for the really nice explanation :]

and @jcolyn,  after i cd to the folder, i type in./configure  and it says


```
bash: ./configure: No such file or directory
```

---

### Post by tordeu on 2011-03-07
Just found an compiling/installation instruction [here]("http://ubuntuforums.org/showthread.php?t=30510&highlight=skippy"). It is almost 6 years old, but it is about skippy 0.5.0, so it might help you.

---

