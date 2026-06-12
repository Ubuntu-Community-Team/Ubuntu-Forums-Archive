---
title: "Update-manager not working--possible python problem"
date: 2010-05-02
forum: General Help
---

### Post by haloony on 2010-05-02
Hi All,

Recently, I have been having a strange and rather abrupt problem. I am unable to run programs such as update-manager, dropbox and terminator. I do not recall doing any major changes that would cause this. When I try to run update-manager from terminal, this is what I get:```
hal@hal-laptop:~$ update-manager 
Traceback (most recent call last):
  File /usr/bin/update-manager, line 29, in <module>
    import gtk
  File /usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py, line 40, in <module>
    from gtk import _gtk
ImportError: /usr/lib/pymodules/python2.6/gtk-2.0/gtk/_gtk.so: undefined symbol: gtk_text_view_scroll_mark_onscreen
Error in sys.excepthook:
Traceback (most recent call last):
  File /usr/lib/python2.6/dist-packages/apport_python_hook.py, line 100, in apport_excepthook
    os.O_WRONLY|os.O_CREAT|os.O_EXCL), 'w')
OSError: [Errno 2] No such file or directory: '/var/crash/_usr_bin_update-manager.1000.crash'

Original exception was:
Traceback (most recent call last):
  File /usr/bin/update-manager, line 29, in <module>
    import gtk
  File /usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py, line 40, in <module>
    from gtk import _gtk
ImportError: /usr/lib/pymodules/python2.6/gtk-2.0/gtk/_gtk.so: undefined symbol: gtk_text_view_scroll_mark_onscreen

```

I have searched google and ubuntuforums and could not find any help for this issue. Figuring that it was a python issue, I went into synpatic and just reinstalled all software with python in its name. That did not help. Any help would be much appreciated.

Thanks,
Hal

Edit: I forgot to give some of my system's specs. I have Ubuntu Karmic installed but installed it as a cli install. I went on to install fluxbox on top of that.

---

