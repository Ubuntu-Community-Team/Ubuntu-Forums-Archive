---
title: "Installing Python 2.5.4 and Commands in General"
date: 2012-04-26
forum: General Help
---

### Post by U8UNTU on 2012-04-26
My goal is to learn Linux commands and install Python 2.5.4 (not any other version because I need this specific one for a class). Here's the [link for the download page with instructions]("http://www.python.org/download/releases/2.5.4/"). Under "Other Platforms" on that page is the file and instructions for Linux. It provides the command:
```
tar -zxvf Python-2.5.4.tgz
```I wouldn't feel like I accomplished anything by if I just copied and pasted from the tutorial. I wanted to know what each parameter means. After looking up the parameters on the manual page, I tried the command:
```
tar -vxfz Python-2.5.4.tgz
```Oddly, my command is exactly the same but with the parameters in a different order. Mine did not work. The first command I quoted did. I am puzzled. Why didn't my work? Why does order matter? How could I have know the correct order on my own? I do not want to just copy commands without known what they mean and why some work but not others. 

Next, the tutorial states to type the three commands "./configure", "make", and "make install". The first two commands worked fine. The "make install" command gave me an error when I entered it. It returned the message:
> /usr/bin/install -c python /usr/local/bin/python2.5
/usr/bin/install: cannot create regular file `/usr/local/bin/python2.5': Permission denied
make: *** [altbininstall] Error 1


---

### Post by papibe on 2012-04-26
Hi U8UNTU. Welcome to the forums!

To actually make the install you need admin privileges (which you already have). Use the command 'sudo' to run the installation command as an admin:
```
sudo make install
```
Your password will be prompted as a security measure.

I hope that helps, and tell us how it goes.
Regards.

---

### Post by U8UNTU on 2012-04-26
Nice! That worked to grant me permission and successfully run the command. I am lost on the next step. I can not find IDLE or otherwise figure out how to open Python and use it. Also, do you know why the parameter order matters for those first two commands in the first post?

---

### Post by papibe on 2012-04-26
You can write python scripts, or run python interactively on the terminal:
```
python
```
Is that what you are looking for?
Regards.

---

### Post by U8UNTU on 2012-04-26
I am looking for [IDLE](http://en.wikipedia.org/wiki/IDLE_%28Python%29). It automatically installed when I ran the .EXE file on Windows 7, so I assumed it would do the same in Linux too. I hope there is a way to use IDLE without using WINE to run an EXE.

---

### Post by papibe on 2012-04-26
Ohh, I see.

There is a native version for Linux, but it is not installed with python. It is a different package.

You can install IDLE using the 'Software Center'.

Regards.

---

### Post by U8UNTU on 2012-04-27
The closest I could get that was available in Ubuntu Software Center was IDLE 2.7.3. Maybe there is no IDLE 2.5.3 for Linux?

---

### Post by sftrabbit on 2012-04-27
Regarding the order of the options in the tar command: the -f option gives the name of the archive to work with, like '-f [name]'. The -f option must therefore come last if you are going to put the file at the end.

To make your ordering work:

```
tar -vxf Python-2.5.4.tgz -z
```

---

### Post by oldfred on 2012-04-27
If you just run python at command line it will run the default version you have installed with Ubuntu. And do not uninstall the default version as that will destroy Ubuntu, many parts of Ubuntu run on the default version of python.

I know with python3 you can just install it and run it with the command:
python3

So I think you can run your python 2.5 with
python2.5

But all that depends on how the links are set up in the python folders.

---

