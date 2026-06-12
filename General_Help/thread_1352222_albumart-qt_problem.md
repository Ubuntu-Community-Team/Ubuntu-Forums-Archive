---
title: "albumart-qt problem"
date: 2009-12-11
forum: General Help
---

### Post by g.a. on 2009-12-11
Hi,

I'm trying to embed covers into mp3 in the most automatic way as possible. It seems that this is not possible within the repository software and I have found albumart-qt as possible solution.

Downloaded the deb file from:

```
http://www.unrealvoodoo.org/hiteck/projects/albumart/
```

and installed. I got a codification problem when running it. it seems to be well known and several posts say to change the first line (or second... sigh) of 

```
/usr/lib/albumart/albumart_images.py
```

with the code

```
#coding:utf-8
```

in my case it does not work. I still have problems:
```

 albumart-qt &
[1] 8156
gianluca@trinity:/usr/lib/albumart$ Reading the previous album directory was interrupted by the following exception:
Traceback (most recent call last):
  File "/usr/lib/albumart/albumart_dialog.py", line 121, in __init__
    self.walk(self.dir)
  File "/usr/lib/albumart/albumart_dialog.py", line 277, in walk
    for root, dirs, files in os.walk(path):
  File "/usr/lib/python2.6/os.py", line 284, in walk
    if isdir(join(top, name)):
  File "/usr/lib/python2.6/posixpath.py", line 68, in join
    path +=  b
UnicodeDecodeError: 'ascii' codec can't decode byte 0xe8 in position 30: ordinal not in range(128)

```

Any suggestion?

Thanks in advance,
g.

---

### Post by g.a. on 2009-12-12
in addition to the previous post. here is the list of file in that directory:

```
gianluca@trinity:/usr/lib/albumart$ ls
albumart_about_dialog_base.py          albumart_progress_widget.py          albumart_string_list_widget.py  id3
albumart_about_dialog.py               albumart.py                          albumart_target_freedesktop.py  items.py
albumart_configuration_dialog_base.py  albumart_recognizer_id3v2.py         albumart_target_generic.py      pixmap.py
albumart_configuration_dialog.py       albumart_recognizer_path.py          albumart_target_id3v2.py        process.py
albumart_dialog_base.py                albumart_source_amazon.py            albumart_target_windows.py      version.py
albumart_dialog.py                     albumart_source_buy.py               albumart_unattended_ui.py       yahoo
albumart_exception_dialog_base.py      albumart_source_walmart.py           amazon.py
albumart_exception_dialog.py           albumart_source_yahoo.py             config.py
albumart_images.py                     albumart_string_list_widget_base.py  event.py
```

and if I grep the word coding it seems the most of the files contains a  iso-8859-1 and not itf-8.

I do not know if this is normal.

g.

---

