---
title: "MyPaint Ate My Painting!  HELP"
date: 2011-05-24
forum: General Help
---

### Post by belkinsa on 2011-05-24
Is this error fixable:

> Traceback (most recent call last):
  File "/usr/share/mypaint/gui/application.py", line 91, at_application_start(*trash=())
                    else:
                        self.filehandler.open_file(fn)
  variables: {'fn': ('local', '/home/svetlana/Documents/Dropbox/Pictures/Vladimir the fox.ora'), 'self.filehandler.open_file': ('local', <bound method FileHandler.wrapper of <gui.filehandling.FileHandler object at 0x42f1510>>)}
  File "/usr/share/mypaint/gui/drawwindow.py", line 41, wrapper(self=<gui.filehandling.FileHandler object>, *args=('/home/svetlana/Documents/Dropbox/Pictures/Vladimir the fox.ora',), **kwargs={})
            try:
                func(self, *args, **kwargs)
            finally:
  variables: {'self': ('local', <gui.filehandling.FileHandler object at 0x42f1510>), 'args': ('local', ('/home/svetlana/Documents/Dropbox/Pictures/Vladimir the fox.ora',)), 'func': ('local', <function open_file at 0x2594758>), 'kwargs': ('local', None)}
  File "/usr/share/mypaint/gui/filehandling.py", line 166, open_file(self=<gui.filehandling.FileHandler object>, filename='/home/svetlana/Documents/Dropbox/Pictures/Vladimir the fox.ora')
            try:
                self.doc.load(filename)
            except document.SaveLoadError, e:
  variables: {'self.doc.load': ('local', <bound method Document.load of <lib.document.Document instance at 0x4619320>>), 'filename': ('local', '/home/svetlana/Documents/Dropbox/Pictures/Vladimir the fox.ora')}
  File "/usr/share/mypaint/lib/document.py", line 276, load(self=<lib.document.Document instance>, filename='/home/svetlana/Documents/Dropbox/Pictures/Vladimir the fox.ora')
            try:
                load(filename)
            except gobject.GError, e:
  variables: {'load': ('local', <bound method Document.load_ora of <lib.document.Document instance at 0x4619320>>), 'filename': ('local', '/home/svetlana/Documents/Dropbox/Pictures/Vladimir the fox.ora')}
  File "/usr/share/mypaint/lib/document.py", line 423, load_ora(self=<lib.document.Document instance>, filename='/home/svetlana/Documents/Dropbox/Pictures/Vladimir the fox.ora')
            tempdir = tempfile.mkdtemp('mypaint')
            z = zipfile.ZipFile(filename)
            print 'mimetype:', z.read('mimetype').strip()
  variables: {'zipfile.ZipFile': ('global', <class zipfile.ZipFile at 0x21d32f0>), 'z': (None, None), 'filename': ('local', '/home/svetlana/Documents/Dropbox/Pictures/Vladimir the fox.ora')}
  File "/usr/lib/python2.6/zipfile.py", line 696, __init__(self=<zipfile.ZipFile instance>, file='/home/svetlana/Documents/Dropbox/Pictures/Vladimir the fox.ora', mode='r', compression=0, allowZip64=False)
            if key == 'r':
                self._GetContents()
            elif key == 'w':
  variables: {'self._GetContents': ('local', <bound method ZipFile._GetContents of <zipfile.ZipFile instance at 0x4a01f80>>)}
  File "/usr/lib/python2.6/zipfile.py", line 716, _GetContents(self=<zipfile.ZipFile instance>)
            try:
                self._RealGetContents()
            except BadZipfile:
  variables: {'self._RealGetContents': ('local', <bound method ZipFile._RealGetContents of <zipfile.ZipFile instance at 0x4a01f80>>)}
  File "/usr/lib/python2.6/zipfile.py", line 728, _RealGetContents(self=<zipfile.ZipFile instance>)
            if not endrec:
                raise BadZipfile, "File is not a zip file"
            if self.debug > 1:
  variables: {'BadZipfile': ('global', <class 'zipfile.BadZipfile'>)}
BadZipfile: File is not a zip file

---

