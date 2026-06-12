---
title: "Matplotlib and PyGTK: backend error"
date: 2012-10-10
forum: General Help
---

### Post by dernier_recours on 2012-10-10
I'm trying to include Matplotlib plots in a Python app I'm developing with Anjuta (updated Ubuntu 12.04, 64-bit). In a tutorial, I have to import "backends", i.e.

from matplotlib.backends.backend_gtkagg import FigureCanvasGTKAgg as FigureCanvas

And an error message is returned.

Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/local/lib/python2.7/dist-packages/matplotlib/backends/backend_gtkagg.py", line 10, in <module>
    from matplotlib.backends.backend_gtk import gtk, FigureManagerGTK, FigureCanvasGTK,\
  File "/usr/local/lib/python2.7/dist-packages/matplotlib/backends/backend_gtk.py", line 28, in <module>
    from matplotlib.backends.backend_gdk import RendererGDK, FigureCanvasGDK
  File "/usr/local/lib/python2.7/dist-packages/matplotlib/backends/backend_gdk.py", line 29, in <module>
    from matplotlib.backends._backend_gdk import pixbuf_get_pixels_array
ImportError: No module named _backend_gdk

I have search the web and the all answers converge to the following solution: "to locate your pygtk-2.0.pc file and then add that path to your PKG_CONFIG_PATH".
[http://matplotlib.1069221.n5.nabble.com/backend-gdk-not-found-td11083.html#a26514059](http://matplotlib.1069221.n5.nabble.com/backend-gdk-not-found-td11083.html#a26514059)

I found out that the pygtk-2.0.pc file is included in the package python-gtk2-dev, so I installed the latter. Then, I ran:
export PKG_CONFIG_PATH=/usr/lib/pkgconfig/python2.7/pygtk-2.0.pc

The problem persisted. I reinstalled matplotlib, python-gtk2 and numpy, but the error is still there. Is this a bug? Any idea how to correct this?

---

### Post by Colin Keenan on 2012-11-15
I'm also trying to use matplotlib and getting the same error. At first there was no error, but plots never displayed. I could save them and look at them with eog (Eye of Gnome which is the image viewer), but show() didn't do anything.

I discovered there's a configuration file for matplotlib where you can specify the backend. I chose GTK (or anything other than what it was to begin with) and get the same error you're getting. 

The thing is, pygtk is installed by default, which you can see by doing the following in interactive python:

import gtk
gtk.pygtk_version

So, the problem has nothing to do with python not being able to find gtk or pygtk.

However, if you take a closer look at the error message, the line that caused the error is:  
    from matplotlib.backends._backend_gdk import pixbuf_get_pixels_array

Which is line 29 of /usr/local/lib/python2.7/dist-packages/matplotlib/backends/backend_gdk.py

If you ls /usr/local/lib/python2.7/dist-packages/matplotlib/backends/, you'll probably discover what I did. There's a ton of backend .py files, but only one .so file: _backend_agg.so

Apparently, everything but AGG fails for this reason. So, we need _backend_gdk.so

I'll start trying to figure out how to get that.

---

### Post by Colin Keenan on 2012-11-15
OK, so I found a list of the files that are supposed to be included if you install matplotlib from the software manager. I had installed it using pip though. I thought I didn't have the proper .so files so just installed matplotlib from the software manager. But, I still got the same error. When I looked again at where the .so files are, I realized they're not where matplotlib is looking. So, I just copied them with this command:

cp /usr/lib/pyshared/python2.7/matplotlib/backends/* /usr/local/lib/python2.7/dist-packages/matplotlib/backends/

And now it works. There's probably a better way and this does seem like a bug.

---

