---
title: "n00b at wit's end!!"
date: 2011-05-25
forum: General Help
---

### Post by .psd on 2011-05-25
omg ubuntu........please help! The install process appeared to work, using:

$ sudo apt-get install python-yaml python-webkit python-chardet
$ sudo python setup.py install --record files

I can't find the application on my machine. Even when I type in rednotebook to bring up a list of things like that, all that comes up is the journal.py and readme that are in the download folder, not having to do with anything installed.

So basically, where did it install the application to, and where can I find the launcher to the application so I can launch it from the Unity dock?

---

### Post by gandaran on 2011-05-25
> sudo python setup.py install --record files
this command doesn't install or run anything, can you be more clear as to what you trying to do?

---

### Post by .psd on 2011-05-25
> **gandaran said:**
> this command doesn't install or run anything, can you be more clear as to what you trying to do?
Technically I was trying to follow the readme, which I did because it's pretty simple and I used cut and paste.

All I'm trying to do is install rednotebook 1.1.6, and be able to launch it. Then I want to add it's launcher to the unity dock.

The text of the readme, pardon me for not knowing a better way to show this:

=====  Short Instructions  =====

$ sudo apt-get install python-yaml python-webkit python-chardet
$ python rednotebook/journal.py




===== Detailed Instructions =====

There are many packages available for different distributions, so you might
want to check the Downloads page first.

It is recommended to install the distribution's appropriate package,
but of course sometimes you want to try out the bleeding edge, hot new stuff.

In order to not mess with your distribution's package system, you might
want to just **run the program, without installing it**.

==== REQUIREMENTS ====
  - Python (2.5/2.6) ([www.python.org](www.python.org))
  - PyYaml (>=3.05) ([www.pyyaml.org](www.pyyaml.org))
  - PyGTK (>=2.13) ([www.pygtk.org](www.pygtk.org))
  - pywebkitgtk (>=1.1.5) ([http://code.google.com/p/pywebkitgtk/](http://code.google.com/p/pywebkitgtk/))

  - OPTIONALLY:
    - python-chardet ([http://chardet.feedparser.org](http://chardet.feedparser.org))
      Better recognition of file encodings

    === Ubuntu/Debian ===
    $ sudo apt-get install python-yaml python-webkit

    === Fedora ===
    $ yum install python-devel PyYAML pywebkitgtk


==== RUNNING WITHOUT INSTALLATION ====
To run RedNotebook without installing run the following command in a terminal:
$ python rednotebook/journal.py


==== INSTALL ====
Please pay attention: Installing is very easy, uninstalling however can only be
done by removing the installed files manually.

$ sudo python setup.py install --record files
(installs into path-to-python/site-packages/ and saves a list of installed
files in "files" to make an uninstallation easier)

---

### Post by marshag63 on 2011-05-25
I just installed by choosing "ubuntu" from this link:  [http://rednotebook.sourceforge.net/downloads.html](http://rednotebook.sourceforge.net/downloads.html)
Python apps end with *.py

It appears you were trying to install from source?

You would need to extract the *.tar *.zip file into a directory, then through console type these commands:

$ cd rednotebook
$ sudo apt-get install python-yaml python-webkit python-chardet
$ python rednotebook/journal.py


Try typing in a console window:  python rednotebook/jounal.py

I'm guessing you may have extracted it into your home directory (its hard to know if a zip file will make its own directory when you extract or not).

Are you using Gnome desktop?


mdg

---

