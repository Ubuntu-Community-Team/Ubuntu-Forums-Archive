---
title: "Do env vars set in .bashrc not effect the gnome desktop?"
date: 2011-02-15
forum: General Help
---

### Post by Buttons840 on 2011-02-15
I've installed python2.7 and I want all those convenient python libs I've installed from the repos to work with python2.7, but the libs in the repos get installed to python2.6.

No problem, I'll just set the $PYTHONPATH env var so that python2.7 will look at the python2.6 libs.  I defined $PYTHONPATH as I wanted in the .bashrc file, and now python2.7 works as I desire when starting it from the shell.

The problem is when I start python2.7 from the gnome desktop (by clicking an application shortcut or button) it doesn't work.  My guess is that the env vars set in .bashrc do not effect the gnome desktop, and so my question is what can I do to set an env var on the desktop?

To demonstrate my problem.  If I open a bash shell and type "idle-python2.7 -n" idle will open, and I can "import twisted" without any problem in the idle python shell.  However, if I do alt-f2 and run "idle-python2.7 -n" idle will still open but sys.path is not set as I would like and I cannot "import twisted".  So there is clearly different behavior between an application started from the shell vs one started from the gnome desktop.

Environmental variables have long confused me, any help is appreciated.  I'm also open to other solutions to my "getting python2.6 libs to run in python2.7" problem.  Thanks.

FULL INSTRUCTION:

Both .bashrc and .gnomerc are located in your home directory.  Put the following at the end of both files:

export PYTHONPATH="$PYTHONPATH:/usr/local/lib/python2.6/dist-packages:/usr/local/lib/python2.6/site-packages:/usr/lib/python2.6/dist-packages:/usr/lib/python2.6/site-packages"

You should now be able to import the python libs installed from the repos in python2.7.

---

### Post by Buttons840 on 2011-02-15
It appears that .bashrc is for bash, while .gnomerc is for gnome.

I didn't know about .gnomerc, but when setting my env var in .gnomerc it will work from the gnome desktop.

Although I did have a syntax error in my .gnomerc and couldn't log in, I had to use a recovery console to fix it -- not a big deal.

Also, here in the general help forums a thread descriptively titled "please help" received more views and more assistance than I did from this thread (at least during the short time I have been working on this issue).  I will have to remember this naming style.

SOLVED.  Hopefully I can help another with my observations.

---

### Post by blueridgedog on 2011-02-15
Actually...your title is descriptive and well done.  Limited views means that only those who are familiar with the issue would view the thread due to your well written description.  I am glad you solved the issue.

---

