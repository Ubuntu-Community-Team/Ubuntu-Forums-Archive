---
title: "How do  access newly installed aplcations?"
date: 2010-08-30
forum: General Help
---

### Post by mike0liver on 2010-08-30
I recently upgraded to V 10,04 LTS and think it is great. However, only a few of my aplications show up under my "Applications" menu on the task bar - none of those I recently installed from the Synaptic Package Manager seem to be there. One of the applications that should have shown up was "Python" which the SPM indicated was already installed - there is no sign of it.

Have I missed something or is there some fault that I need to repair? Is there some other method for getting applications to run?

Cheers,

Mike

---

### Post by ean5533 on 2010-08-30
> **mike0liver said:**
> I recently upgraded to V 10,04 LTS and think it is great. However, only a few of my aplications show up under my "Applications" menu on the task bar - none of those I recently installed from the Synaptic Package Manager seem to be there. One of the applications that should have shown up was "Python" which the SPM indicated was already installed - there is no sign of it.

Have I missed something or is there some fault that I need to repair? Is there some other method for getting applications to run?

Cheers,

Mike

Not every application that you install comes with a default menu entry. Python, the programming language, is one of them. If you want to run the python interpreter, open up a terminal (Applications->Terminal) and type "python" then press enter.

Are there any other applications that you're missing?

---

### Post by hhoyt on 2010-08-30
If that is the run-time, he will not show.

Bring up your terminal (applications/Accessories) and enter
'python &"
control-c to exit.

Howard

---

### Post by mike0liver on 2010-08-30
Thanks - I did this and some process seemed to be going on in the terminal but the Python interpreter did not appear. I got a message to type in "help", "licence" or "copyright" but nothing else.

I also tried "Python &" but with the same result.

Cheers,

Mike

---

### Post by ean5533 on 2010-08-30
> **mike0liver said:**
> Thanks - I did this and some process seemed to be going on in the terminal but the Python interpreter did not appear. I got a message to type in "help", "licence" or "copyright" but nothing else.

I also tried "Python &" but with the same result.

Cheers,

Mike

That's all the python interpreter does, it waits for you to type python commands and spits out the result. It does not have a graphical user interface, it just runs through the command line. Try typing 'python' again (and pressing enter), then after those messages appear try typing 'help' (and pressing enter). You'll see that you are interacting with the python interpreter.

What exactly are you trying to do?

---

### Post by brettdunnam on 2010-08-30
> **mike0liver said:**
> Thanks - I did this and some process seemed to be going on in the terminal but the Python interpreter did not appear. I got a message to type in "help", "licence" or "copyright" but nothing else.

I also tried "Python &" but with the same result.

Cheers,

Mike
Yeah there is no GUI for the Python interpreter. If you just elaborate on what it is you are trying to do, the community will be of a lot more help. Maybe you have Python confused with another program that you wanted to install?

---

### Post by mike0liver on 2010-08-31
Ah, I see now. I am migrating from Windows to Ubuntu and was hoping to find a programming language like Visual Basic that would enable me to write simple applications for Linux.

The GUI is pretty well essential and it has to be an OOL. I'd also need an installer so that friends could use my progs (which will be fairly specialised but which I'll be happy to offer free to anyone else who's interested).

Can you direct me to something that would fill this bill, please?

Cheers,

Mike

---

### Post by 3rdalbum on 2010-08-31
Take a look at Quickly - it's a trinity of Glade, Python and Bazaar. Glade is the user interface designer, Python is the underlying language you use, and Bazaar provides version control. Glade itself is a GUI, and although Quickly is a command-line program it is very simple to get it to save your project, build an Ubuntu package, upload to Launchpad etc.

If you want something really similar to Visual Basic then try Gambas - it's similar, but not a clone.

---

### Post by ean5533 on 2010-08-31
> **mike0liver said:**
> Ah, I see now. I am migrating from Windows to Ubuntu and was hoping to find a programming language like Visual Basic that would enable me to write simple applications for Linux.

The GUI is pretty well essential and it has to be an OOL. I'd also need an installer so that friends could use my progs (which will be fairly specialised but which I'll be happy to offer free to anyone else who's interested).

Can you direct me to something that would fill this bill, please?

Cheers,

Mike

My favorite GUI toolkit is [Qt (maintained by Nokia)]("http://qt.nokia.com/products"). It's cross-platform and comes with a fantastic IDE. The has bindings for multiple programming languages, but C++ is the best one to work with (which is an object-oriented language). The IDE comes with a form designer similar to what you're used to seeing for Visual Basic, so it should be an easy transition for you.

Note: You don't need to pay for the commercial Qt license. You can make and sell programs just fine with the free LGPL-licensed version, just as long as you don't make any changes to the Qt libraries themselves (hint: you won't).

---

