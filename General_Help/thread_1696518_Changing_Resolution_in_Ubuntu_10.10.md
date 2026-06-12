---
title: "Changing Resolution in Ubuntu 10.10"
date: 2011-02-27
forum: General Help
---

### Post by DallasJR on 2011-02-27
Hi, I'm a total noob to the whole Linux thing. And I just installed Ubuntu, hoping to try things out. (so could you please put this in terms that's I'll be able to understand? :p)

My resolution is really screwed up. On Windows I use 1920x1080 (the monitors normal setting), but Ubuntu won't recognise the resolution. (it sets me at 1024x768 ) I've tried a couple of different guides but none of them worked.

It only shows four different default resolutions: 

1024x768 (4:3)
800x600 (4:3)
848x480 (16:9)
640x480 (4:3)

 I'm using a NVIDIAGTS8800 video card, if that helps.

Thanks in advance!

-Dallas

---

### Post by mIXpRo on 2011-02-27
have you tried installing it driver : 
[http://www.nvidia.com/object/linux_display_ia32_169.07.html](http://www.nvidia.com/object/linux_display_ia32_169.07.html)

---

### Post by DallasJR on 2011-02-27
> **mIXpRo said:**
> have you tried installing it driver : 
[http://www.nvidia.com/object/linux_display_ia32_169.07.html](http://www.nvidia.com/object/linux_display_ia32_169.07.html)I feel like an idiot for not trying that first. XD

Though, once I downloaded it and tried to input the code recommended on the site I got this error message: sh: Can't open NVIDIA-Linux-x86-169.07-pkg1.run

Any help with this?

---

### Post by DallasJR on 2011-02-27
Just bumping my thread to make sure it doesn't fall off the first page.

---

### Post by rolandrock on 2011-02-27
You might not be in the same directory as the .run file.  Use the ls command to list files in the current directory.  If it is not there, try to cd to the Downloads directory and see if it is in there.

---

### Post by mIXpRo on 2011-02-28
if for instance you have downloaded the file to Downloads directory in /home/username/Downloads

you would do this :
```
 
cd ~/Downloads or 
cd /home/"username"/Downloads 
then you want to make sure that .run file is have the execute permission by 
chmod u+x ./NVIDIA-Linux-x86-169.07-pkg1.run
then run the file from terminal by ./NVIDIA-Linux-x86-169.07-pkg1.run

```

---

