---
title: "I'm trying to install a python program via setup.py."
date: 2010-04-14
forum: General Help
---

### Post by acousticcoupler on 2010-04-14
The install seems to go fine, but when I try to run I get command not found. I think maybe it isn't creating it's entry point for some reason.

Here is my console output:

```

root@PinkoCommie:/mnt/data/clperez/downloads/HLSPlayer-0.1# python setup.py install
running install
running bdist_egg
running egg_info
writing HLSPlayer.egg-info/PKG-INFO
writing top-level names to HLSPlayer.egg-info/top_level.txt
writing dependency_links to HLSPlayer.egg-info/dependency_links.txt
writing entry points to HLSPlayer.egg-info/entry_points.txt
reading manifest file 'HLSPlayer.egg-info/SOURCES.txt'
reading manifest template 'MANIFEST.in'
warning: no files found matching 'AUTHORS'
warning: no files found matching 'LICENSE'
warning: no files found matching 'README'
warning: no files found matching 'TODO'
writing manifest file 'HLSPlayer.egg-info/SOURCES.txt'
installing library code to build/bdist.linux-i686/egg
running install_lib
running build_py
creating build/bdist.linux-i686/egg
creating build/bdist.linux-i686/egg/hls
copying build/lib.linux-i686-2.6/hls/player.py -> build/bdist.linux-i686/egg/hls
copying build/lib.linux-i686-2.6/hls/m3u8.py -> build/bdist.linux-i686/egg/hls
copying build/lib.linux-i686-2.6/hls/fetcher.py -> build/bdist.linux-i686/egg/hls
copying build/lib.linux-i686-2.6/hls/__init__.py -> build/bdist.linux-i686/egg/hls
byte-compiling build/bdist.linux-i686/egg/hls/player.py to player.pyc
byte-compiling build/bdist.linux-i686/egg/hls/m3u8.py to m3u8.pyc
byte-compiling build/bdist.linux-i686/egg/hls/fetcher.py to fetcher.pyc
byte-compiling build/bdist.linux-i686/egg/hls/__init__.py to __init__.pyc
creating build/bdist.linux-i686/egg/EGG-INFO
copying HLSPlayer.egg-info/PKG-INFO -> build/bdist.linux-i686/egg/EGG-INFO
copying HLSPlayer.egg-info/SOURCES.txt -> build/bdist.linux-i686/egg/EGG-INFO
copying HLSPlayer.egg-info/dependency_links.txt -> build/bdist.linux-i686/egg/EGG-INFO
copying HLSPlayer.egg-info/entry_points.txt -> build/bdist.linux-i686/egg/EGG-INFO
copying HLSPlayer.egg-info/top_level.txt -> build/bdist.linux-i686/egg/EGG-INFO
zip_safe flag not set; analyzing archive contents...
creating 'dist/HLSPlayer-0.1-py2.6.egg' and adding 'build/bdist.linux-i686/egg' to it
removing 'build/bdist.linux-i686/egg' (and everything under it)
Processing HLSPlayer-0.1-py2.6.egg
removing '/usr/local/lib/python2.6/dist-packages/HLSPlayer-0.1-py2.6.egg' (and everything under it)
creating /usr/local/lib/python2.6/dist-packages/HLSPlayer-0.1-py2.6.egg
Extracting HLSPlayer-0.1-py2.6.egg to /usr/local/lib/python2.6/dist-packages
HLSPlayer 0.1 is already the active version in easy-install.pth

Installed /usr/local/lib/python2.6/dist-packages/HLSPlayer-0.1-py2.6.egg
Processing dependencies for HLSPlayer==0.1
Finished processing dependencies for HLSPlayer==0.1
root@PinkoCommie:/mnt/data/clperez/downloads/HLSPlayer-0.1# hls-player
hls-player: command not found
root@PinkoCommie:/mnt/data/clperez/downloads/HLSPlayer-0.1# 

```This is the program I am trying to install: [http://code.google.com/p/hls-player/](http://code.google.com/p/hls-player/)

---

