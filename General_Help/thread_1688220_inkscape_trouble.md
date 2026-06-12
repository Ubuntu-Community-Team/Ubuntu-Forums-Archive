---
title: "inkscape trouble"
date: 2011-02-15
forum: General Help
---

### Post by profeta81 on 2011-02-15
dear all,

I have a problem with Inkscape. This is quite tiresome because it makes the application completely useless when it happens and I'm using inkscape quite intensively.

One way to to "trigger" the problem is to start the application, add a pixel image (png, jpg, I usually do this by dragging the image on the inkscape window) and wait few seconds (sometimes minutes). Usually the images get imported correctly, but at some point after adding the image inkscape begins to pop up three windows in sequence once every two or three seconds. The popups don't stop regardless of whether I click on the OK button or not: if I do click on the ok, they disappeare and reappeare few seconds later, if i dont, they duplicate themselves cluttering all the desktop area and eventually crashing the application (while I was writing this post, inkscape popped up about twenty dialog windows). the first popup says:

> 
Inkscape has received additional data from the script executed.  The script did not return an error, but this may indicate the results will not be as expected.

UniConvertor failed:

Cannot list directory /home/myname/.uniconvertor:[Errno 2] No such file or directory: '/home/myname/.uniconvertor'
ignoring it in font_path
Cannot list directory /home/myname/.uniconvertor:[Errno 2] No such file or directory: '/home/myname/.uniconvertor'
ignoring it in font_path
/usr/lib/pymodules/python2.6/uniconvertor/app/utils/locale_utils.py:9: DeprecationWarning: The popen2 module is deprecated.  Use the subprocess module.
  from popen2 import popen2
No plugin-type information in /usr/lib/pymodules/python2.6/uniconvertor/app/plugins/Filters/__init__.py
No plugin-type information in /usr/lib/pymodules/python2.6/uniconvertor/app/plugins/Filters/__init__.py
Cannot load plugin module sk1saver
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/uniconvertor/app/plugins/plugins.py", line 73, in load_module
    desc)
  File "/usr/lib/pymodules/python2.6/uniconvertor/app/plugins/Filters/sk1saver.py", line 249, in <module>
    from app.Graphics.image import CMYK_IMAGE
ImportError: cannot import name CMYK_IMAGE
When importing plugin sk1saver
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/uniconvertor/app/plugins/plugins.py", line 190, in __call__
    module = self.load_module()
  File "/usr/lib/pymodules/python2.6/uniconvertor/app/plugins/plugins.py", line 73, in load_module
    desc)
  File "/usr/lib/pymodules/python2.6/uniconvertor/app/plugins/Filters/sk1saver.py", line 249, in <module>
    from app.Graphics.image import CMYK_IMAGE
ImportError: cannot import name CMYK_IMAGE
Traceback (most recent call last):
  File "<string>", line 1, in <module>
  File "/usr/lib/pymodules/python2.6/uniconvertor/__init__.py", line 88, in uniconv
    saver(doc, output_file)
  File "/usr/lib/pymodules/python2.6/uniconvertor/app/plugins/plugins.py", line 194, in __call__
    % {'name':self.module_name})
app.events.skexceptions.SketchError: Cannot load filter sk1saver



The second:

> 
Inkscape has received additional data from the script executed.  The script did not return an error, but this may indicate the results will not be as expected.

No matching node for expression: /svg:svg/@sodipodi:docname
Traceback (most recent call last):
  File "/usr/share/inkscape/extensions/gimp_xcf.py", line 173, in <module>
    e.affect()
  File "/usr/share/inkscape/extensions/inkex.py", line 207, in affect
    self.effect()
  File "/usr/share/inkscape/extensions/gimp_xcf.py", line 37, in effect
    docname = self.xpathSingle('/svg:svg/@sodipodi:docname')[:-4]
TypeError: 'NoneType' object is unsubscriptable



and the third has some postscript options:

"restrict to postscript"
"convert text to path"
"rasterise filter effect"
"resolution for rasterisation (dpi)"
"export area is drawing"
"export area is page"
"limit the export to the object with id"


Inkscape version:
Inkscape 0.47pre4 r22446 (Oct 14 2009)
(just reinstalled from main repository)

Ubuntu version:
Ubuntu 9.10 - the Karmic Koala

cheers everyone

---

### Post by profeta81 on 2011-02-15
this happens when opening an svg file created by xfig

btw, I reinstalled both inkscape and univonvertor and deleted all configuration directories in my home... still problem persists

again, this is very troublesome...

---

### Post by mastablasta on 2011-02-15
this doesn't seem to have anyhting to do with Ubuntu. Perhaps Inkscape forums hold the answer?
 
never had htis problme btw. have you tried importing images through menu?

---

