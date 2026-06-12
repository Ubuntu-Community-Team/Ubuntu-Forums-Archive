---
title: "goto command not recognised??"
date: 2009-09-27
forum: General Help
---

### Post by louis_h27 on 2009-09-27
Hi everyone, I have recently downloaded a driver for my sound card which is a creative Sound Blaster X-Fi. However I have been unable to install it, when I read the readme file it says I need to type the following command in the terminal:

1. Goto source directory
2. execute make command as route
make
make install.

When I type command 1, i get a message stating that the goto command cannot be found?
Why is this?

---

### Post by wojox on 2009-09-27
They mean to go to whatever directory you downloaded it to.

For example if it's on your Desktop, open the terminal and type:

```
cd Desktop
```

Then run:

```
make
```

Followed by:

```
make install
```

---

### Post by louis_h27 on 2009-09-27
> **wojox said:**
> They mean to go to whatever directory you downloaded it to.

For example if it's on your Desktop, open the terminal and type:

```
cd Desktop
```Then run:

```
make
```Followed by:

```
make install
```

Tried that, now I'm getting another problem:

when i type in make
*** No targets specified and no makefile found. Stop.

---

### Post by StuartN on 2009-09-27
> **louis_h27 said:**
> when i type in make
*** No targets specified and no makefile found. Stop.

I assume you downloaded a .tar.gz compressed archive file, and extracted the files in it. And the extracted are not on your Desktop. You need to change directory to where you extracted the files, and in that directory should be a file called makefile - if you find makefile then you are probably in the right place.

When you extracted the files it probably created a new folder wherever you normally download to. From within Firefox if you go to Tools-Downloads, then you can right-click on the download and "Open containing folder" to see where it downloaded to.

---

### Post by wojox on 2009-09-27
Try:

```
./configure
```

---

### Post by louis_h27 on 2009-09-27
> **StuartN said:**
> I assume you downloaded a .tar.gz compressed archive file, and extracted the files in it. And the extracted are not on your Desktop. You need to change directory to where you extracted the files, and in that directory should be a file called makefile - if you find makefile then you are probably in the right place. 

I had done what you had suggested and it worked, I did download a .tar.gz compressed archive file so I just placed all files extracted to the desktop.

Then I loaded the terminal and typed:

1. cd Desktop
2. make
3. make install.

I am now getting the following message:

louis@louis-desktop:~/Desktop$ make install
Copy module files...
rm: cannot remove `/lib/modules/2.6.28-15-generic/kernel/drivers/ssound/ctxfi.ko': Permission denied
make: *** [install] Error 1

---

### Post by StuartN on 2009-09-27
> **louis_h27 said:**
> rm: cannot remove `/lib/modules/2.6.28-15-generic/kernel/drivers/ssound/ctxfi.ko': Permission denied

Linux prevents its users from accidental self-harm - in this case the make procedure is trying to delete a driver, which is protected by root permissions. In order to allow this to happen (which in this case is what you want, because you are replacing the driver) you need to run the make command as root (or super user) and you do this with **sudo make** and then **sudo make install**

In future you could extract files into a separate folder, because it makes cleaning up much easier - e.g. make a "temp" directory using Firefox when you download, then cd ~/Desktop/temp, and do all the make within that, so you can delete it all once the driver is installed.

---

### Post by louis_h27 on 2009-09-28
hi, I have done what you have suggested, but now I get the following message....sorry I don't know what to do it is my first time on linux let alone Ubuntu.


louis@louis-desktop:~/Desktop/temp$ sudo make install
Copy module files...
Update module dependency relationships...

---

### Post by StuartN on 2009-09-28
> **louis_h27 said:**
> now I get the following message
Copy module files...
Update module dependency relationships...

Those messages look quite friendly, especially if there was not the word "error". Did your new software work?

---

### Post by louis_h27 on 2009-09-28
Unfortunately it hasn't worked, I still can't hear any sound.

---

### Post by wojox on 2009-09-28
Now open a terminal and try:

```
alsamixer
```

make sure everything is turned up.

---

