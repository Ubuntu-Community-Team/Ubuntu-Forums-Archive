---
title: "is there a python interpreter for ubuntu that works?!"
date: 2010-07-12
forum: General Help
---

### Post by capitalfear on 2010-07-12
okay look i code python and am trying to use eclipse with no success...i just want something i can code and run my python in i want py 2.5 or 2.7 and i tried to install and unpack it but something in the terminal later on rejects it...thank you

---

### Post by geirha on 2010-07-12
Very little information to go on here.

Is this about python or eclipse? Why aren't you installing from the repositories? and what's the actual error message you get?

---

### Post by Exp HP on 2010-07-12
Ubuntu ships with Python 2.6.5, fully functional and with a lot of modules included.  In fact, some of Ubuntu's included programs are written in Python. (so Ubuntu wouldn't fully work without Python)

I'm assuming you're having trouble with Eclipse and you're asking if Ubuntu has Python, because you shouldn't have any trouble getting Python to work in Ubuntu.  It should work out of the box.  Same with Perl and Ruby, if I'm not mistaken.

---

### Post by capitalfear on 2010-07-12
im not getting an error its just not working its about python i just need a python debugger

---

### Post by capitalfear on 2010-07-12
> **Exp HP said:**
> Ubuntu ships with Python 2.6.5, fully functional and with a lot of modules included.  In fact, some of Ubuntu's included programs are written in Python. (so Ubuntu wouldn't work without Python)

I'm assuming you're asking if Ubuntu has Python, because you shouldn't have any trouble getting Python to work in Ubuntu.  It should work out of the box.

okay...well i downloaded it from python.org and tried to unpack it and it didnt work

---

### Post by Exp HP on 2010-07-12
If you download source from a website, you'll need to compile it.

The linux way of getting a new app would be simply typing this in the terminal:

```
sudo apt-get python
```

---

### Post by capitalfear on 2010-07-12
i did sudo apt-get install Python2.7
ill try that tho...

---

### Post by capitalfear on 2010-07-12
> **Exp HP said:**
> If you download source from a website, you'll need to compile it.

The linux way of getting a new app would be simply typing this in the terminal:

```
sudo apt-get python
```

didnt work

---

### Post by Exp HP on 2010-07-12
What error did you get?

---

### Post by Exp HP on 2010-07-12
I guess I should also mention how to run a python script (because like I said, if you are using Ubuntu, you already have Python installed).  The easiest way is by using a terminal:

Open a terminal, use "cd *foldername*" to go to the folder with your script, then use "python *scriptname.py*" to run the script. Note that you don't have to  type that up every time you test it.  After you test it once, you should  be able to press Up in the terminal to repeat the last command when you want to test it again, so long as you keep the terminal open.

Also, 2.6.5 and 3.1 are the only versions of Python you'll be able to get by using any of the Ubuntu program installers (Software Center, apt-get, aptitude, etc).  2.7 is not in the repositories yet.

---

### Post by capitalfear on 2010-07-12
so and so : sudo apt-get python
E: Invalid operation python

---

### Post by geirha on 2010-07-12
This will list the available python versions in the repository
```
aptitude search '^python[0-9.]+$'
```

To install a package (e.g. python3.1) from the command-line, you run
```
sudo aptitude install python3.1
# or
sudo apt-get install python3.1
```

Now, it appears python2.6 is the only python2 version in the package repositories for Ubuntu 10.04. You said you wanted 2.5 or 2.7. Any particular reason you don't want 2.6 (which is installed by default in Ubuntu 10.04)?

---

### Post by capitalfear on 2010-07-12
no 2.6 is fine i just use 2.5 and know it quite well...but anyways im trying to unpack the 2.6...sigh...

---

### Post by capitalfear on 2010-07-12
where can i freakin write python and debug it and run it!!! aghhhh!!!:o

---

### Post by Exp HP on 2010-07-12
Sorry, that was my bad, I forgot the word "install" when I suggested using apt-get.

The easiest way to write and debug python is, as I said, edit it with a text editor (like gedit), and test it in a terminal.  This is something you can do right out of the box with Ubuntu, without downloading anything.  You can use Alt-Tab to easily switch between the two (though what I like to do is set my workspace switcher to have a 2x2 set of desktops, put the editor and the console in adjacent desktops, and then switch between them with Ctrl+Alt+arrow keys).

Right now, though, it sounds to me like you would much rather have a program where you can write code and debug it in one place (like an IDE)?  If you really want, I could look around to see if one exists in the repositories...

---

### Post by oldfred on 2010-07-12
I like geany as it is easy to run the python code, but it does not have a debugger. I just add print statements for any variables I want and then comment them out until I might need them again.

---

### Post by geirha on 2010-07-12
```
$ vi hello # tap tap tap tap tap backspace backspace tap tap tap tap
$ cat hello
#!/usr/bin/env python
print "Hello, World!"
$ chmod -v +x hello
mode of `hello' changed to 0755 (rwxr-xr-x)
$ ./hello
Hello, World!

```

---

