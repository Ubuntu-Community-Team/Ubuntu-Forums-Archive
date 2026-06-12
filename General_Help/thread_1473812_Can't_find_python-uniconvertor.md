---
title: "Can't find python-uniconvertor"
date: 2010-05-05
forum: General Help
---

### Post by Coco999 on 2010-05-05
I have just updated to 10.04 and was searching in "Get Software" for an ai translator. It returns this result, described as a Universal vector graphics translator, which might be good to me. It shows it as installed and even offers me to remove it if I want. But I can't find the launcher and it is not shown in the list of Installed Software. How do I do to open this program? Do I have to remove it and install it anew?

---

### Post by gordintoronto on 2010-05-05
Open accesories/terminal and try this command:

man uniconvertor
(if it opens the manual, you can press "q" to quit.)
uniconvertor

Or have a look at its home page:
[http://sk1project.org/modules.php?name=Products&product=uniconvertor](http://sk1project.org/modules.php?name=Products&product=uniconvertor)

---

### Post by Coco999 on 2010-05-05
Thank you, gordintoronto. It is a command line tool. I wonder whether there are other command line programs installed in my version of Ubuntu, unknown to me and utterly unfindable. Also the command looks like this
```
uniconvertor [input file] [output file]
```

I would have to know where is uniconvertor to place there the input (and receive the output) file. Alternatively, I should give the paths, but how far must I go? An example would be handy.

---

### Post by gordintoronto on 2010-05-05
There are at least 100 command-line programs installed in your Ubuntu. There is a magazine called Full Circle Magazine, a free download in PDF form. It has a monthly column called "Command and Conquer." It began in issue 20; you might have a look at the first half-dozen columns, which give an introduction to the command line.

One command is "cd" to move to a folder. Another is "ls" to list folders and files. If you open the terminal, you can say:
cd Documents
(note the upper case "d"!)
Then, to convert a file in the Documents folder you could say:
uniconvertor inputfilename outputfilename
To move "up" in the folder tree, the command is:
cd ..

I suspect you also need to tell uniconvertor the input and output file formats, although it might be able to figure out the input format for itself.

Good luck!

---

### Post by Coco999 on 2010-05-05
It would be fine to know what these command line programs are and what do they do, but knowing that they exist is half the way to them. I'll see as suggested Full Circle Magazine. Command line resembles DOS, which I used years ago, but no doubt it is easier to work with a GUI. 

Thanks again!!!

---

### Post by engine on 2011-05-01
Step 1: use Synaptic to install uniconvertor for Ubuntu 10.04

Step 2: cd to directory containing graphics files

Step 3: uniconvertor, to make sure it's accessible from this directory &#8210; it is

Step 4: uniconvertor file.ps file.svg

Step 5: stare uncomprehendingly at extensive system messages :-{

```
me@here:~/mup/klijk$ uniconvertor agnus.ps agnus.svg
Cannot list directory /home/me/.uniconvertor:[Errno 2] No such file or directory: '/home/me/.uniconvertor'
ignoring it in font_path
Cannot list directory /home/me/.uniconvertor:[Errno 2] No such file or directory: '/home/me/.uniconvertor'
ignoring it in font_path
/usr/lib/pymodules/python2.6/uniconvertor/app/utils/locale_utils.py:9: DeprecationWarning: The popen2 module is deprecated.  Use the subprocess module.
  from popen2 import popen2
No plugin-type information in /usr/lib/pymodules/python2.6/uniconvertor/app/plugins/Filters/__init__.py
Traceback (most recent call last):
  File "<string>", line 1, in <module>
  File "/usr/lib/pymodules/python2.6/uniconvertor/__init__.py", line 82, in uniconv
    doc = load.load_drawing(input_file)
  File "/usr/lib/pymodules/python2.6/uniconvertor/app/io/load.py", line 364, in load_drawing
    return load_drawing_from_file(file, filename)
  File "/usr/lib/pymodules/python2.6/uniconvertor/app/io/load.py", line 346, in load_drawing_from_file
    raise SketchLoadError(_("unrecognised file type"))
app.events.skexceptions.SketchLoadError: unrecognised file type

```

Step 6: Hope someone can help! has something failed at installation? dependencies?

---

