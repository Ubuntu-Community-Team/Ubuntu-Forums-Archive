---
title: "Natty: Python Imaging Library in a virtualenv - no JPEG or PNG support"
date: 2011-05-06
forum: General Help
---

### Post by george@reilly.org on 2011-05-06
We build our Python webservices in a virtualenv with all external packages stored locally. This gives us reproducible results on a variety of Linux distros, Mac, and Windows, both for developer machines and production boxes.

I am quite unable to get JPEG and PNG support working in the Python Imaging Library. Here's a repro case in a clean virtual machine.

```

$ sudo apt-get install python-virtualenv
$ virtualenv --no-site-packages ~/venv
$ source ~/venv/bin/activate

$ mkdir -p ~/PIL ~/temp/site-packages
$ export PYTHONPATH=~/temp/site-packages/
$ cd ~/PIL
$ wget http://effbot.org/downloads/Imaging-1.1.7.tar.gz

$ sudo apt-get build-dep python-imaging
# sets up zlib1g-dev, libfreetype6-dev, libjpeg62-dev, liblcms1-dev, ...

$ easy_install -v --install-dir ~/temp/site-packages --find-links ~/PIL\
  --allow-hosts=None --always-unzip Imaging

...
--------------------------------------------------------------------
PIL 1.1.7 SETUP SUMMARY
--------------------------------------------------------------------
version       1.1.7
platform      linux2 2.7.1+ (r271:86832, Apr 11 2011, 18:05:24)
              [GCC 4.5.2]
--------------------------------------------------------------------
--- TKINTER support available
*** JPEG support not available
*** ZLIB (PNG/ZIP) support not available
*** FREETYPE2 support not available
--- LITTLECMS support available
--------------------------------------------------------------------

$ identify basketball.png flowers.jpg logo.gif 
basketball.png PNG 340x340 340x340+0+0 8-bit DirectClass 157KB 0.000u 0:00.000
flowers.jpg[1] JPEG 500x333 500x333+0+0 8-bit DirectClass 66.5KB 0.020u 0:00.019
logo.gif[2] GIF 276x110 276x110+0+0 8-bit PseudoClass 256c 8.56KB 0.000u 0:00.000

$ python
Python 2.7.1+ (r271:86832, Apr 11 2011, 18:05:24) 
[GCC 4.5.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import Image
>>> img = Image.open('basketball.png')
>>> img.load()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/home/georger/temp/site-packages/PIL-1.1.7-py2.7-linux-i686.egg/ImageFile.py", line 189, in load
    d = Image._getdecoder(self.mode, d, a, self.decoderconfig)
  File "/home/georger/temp/site-packages/PIL-1.1.7-py2.7-linux-i686.egg/Image.py", line 385, in _getdecoder
    raise IOError("decoder %s not available" % decoder_name)
IOError: decoder zip not available
>>> img = Image.open('flowers.jpg')
>>> img.load()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/home/georger/temp/site-packages/PIL-1.1.7-py2.7-linux-i686.egg/ImageFile.py", line 189, in load
    d = Image._getdecoder(self.mode, d, a, self.decoderconfig)
  File "/home/georger/temp/site-packages/PIL-1.1.7-py2.7-linux-i686.egg/Image.py", line 385, in _getdecoder
    raise IOError("decoder %s not available" % decoder_name)
IOError: decoder jpeg not available

```

Ideas?

---

### Post by Balinares on 2011-05-12
I don't know if this is a bug in PIL or a badly thought out move in Natty, but the issue is that PIL cannot find libjpeg.so.62 where Natty put it, that being /usr/lib/i386-linux-gnu.

As a workaround, you can:

1/ Call '[FONT="Courier New"]pip install -I pil --no-install[/FONT]' to download and unpack the PIL source into your build directory;
2/ Get into your build directory and edit setup.py;
3/ Find the line that says '[FONT="Courier New"]add_directory(library_dirs, "/usr/lib")[/FONT]' (line 214 here);
4/ Add the line '[FONT="Courier New"]add_directory(library_dirs, "/usr/lib/i386-linux-gnu")[/FONT]' afterwards;
5/ Call '[FONT="Courier New"]pip install -I pil --no-download[/FONT]' to finish the installation.

Having to fiddle manually with library paths is so 1990. I'm not amused. :/ I tried to google the rationale behind moving regular libs into /usr/lib/i386-linux-gnu (this is on an amd64 sys, mind) but couldn't find anything.

---

### Post by ratlaw on 2011-05-13
Rather than mess with the setup.py in PIL, you can also simply create symlinks to the libraries in /usr/lib (assuming you have sudo access).

I did this with the following commands:

```

sudo ln -s /usr/lib/x86_64-linux-gnu/libfreetype.so /usr/lib/
sudo ln -s /usr/lib/x86_64-linux-gnu/libz.so /usr/lib/
sudo ln -s /usr/lib/x86_64-linux-gnu/libjpeg.so /usr/lib/

```

Simply substitute "i386-linux-gnu" for "x86_64-linux-gnu" if you have an i386 architecture.

---

### Post by Balinares on 2011-05-13
True, Ratlaw's symlinking solution should work as well, and is simpler to boot. I tend to prefer not having to modify the system globally to solve an issue local to a single piece of software, but it's just me.

This being said, Ratlaw, I'm running amd64 and the files you list don't exist in the /usr/lib/x86_64-linux-gnu/ directory. libfreetype.so libjpeg.so are there with a version number, but libz.so isn't either way. I'm not sure what you and I did differently.

---

### Post by ratlaw on 2011-05-13
After checking with apt-file, the files I linked to are provided by the dev versions of the three libraries. For instance, installing zlib1g-dev creates the file /usr/lib/x86_64-linux-gnu/libz.so, which is a symlink to /lib/x86_64-linux-gnu/libz.so.1.2.3.4.

If you only installed the zlib1g, libjpeg62 and libfreetype packages then you'd want to run the following commands:

```

sudo ln -s /lib/x86_64-linux-gnu/libz.so.1 /lib/
sudo ln - /usr/lib/x86_64-linux-gnu/libfreetype.so.6 /usr/lib/
sudo ln -s /usr/lib/x86_64-linux-gnu/libjpeg.so.62 /usr/lib/

```

However, if Ubuntu moves to a newer version of these libraries, these links may break.

---

### Post by riverfr0zen on 2011-05-16
The solutions above work (thanks), but any idea why these symlinks aren't automatically created by the *-dev packages (which seemed to happen before natty)?

---

### Post by clekstro on 2011-05-16
Thanks everyone for the suggestions.  But this doesn't appear to work if --no-site-packages is set.  Any suggestions?

---

### Post by Balinares on 2011-05-16
> **clekstro said:**
> Thanks everyone for the suggestions.  But this doesn't appear to work if --no-site-packages is set.  Any suggestions?

It works here. You need to install PIL *inside* the virtualenv. That is, create your virtualenv with the --no-site-packages option, *activate it*, and then run the steps above.

---

### Post by clekstro on 2011-05-17
Sorry, I must have misunderstood.  The way things are described, it seems like these changes can simply be made post-install as if no reinstall were necessary. 
Thanks!

---

### Post by george@reilly.org on 2011-05-17
> **ratlaw said:**
> Rather than mess with the setup.py in PIL, you can also simply create symlinks to the libraries in /usr/lib (assuming you have sudo access).

I did this with the following commands:

```

sudo ln -s /usr/lib/x86_64-linux-gnu/libfreetype.so /usr/lib/
sudo ln -s /usr/lib/x86_64-linux-gnu/libz.so /usr/lib/
sudo ln -s /usr/lib/x86_64-linux-gnu/libjpeg.so /usr/lib/

```

Simply substitute "i386-linux-gnu" for "x86_64-linux-gnu" if you have an i386 architecture.

Thanks, Ratlaw et al. This is what I did.

---

### Post by airtonix on 2011-12-19
or : 

```

sudo apt-get install libjpeg8.dev
virtualenv ~/Dev/python-virtualenv/project-name
workon project-name
(project-name) cd ~/Dev/python-virtualenv/project-name/
(project-name) ln -s /usr/lib/x86_64-linux-gnu/libz.so ./lib/
(project-name) ln -s /usr/lib/x86_64-linux-gnu/libjpeg.so ./lib/
(project-name) ln -s /usr/lib/x86_64-linux-gnu/libfreetype.so ./lib/

```

For some reason I'm feeling Déjà vu

---

