---
title: "Bittorrent 5.3 GPL installition from its souce code"
date: 2010-01-23
forum: General Help
---

### Post by nmrcy on 2010-01-23
I have downloaded BitTorrent Mainline v5 from [http://www.bittorrent.com/opensource]("http://www.bittorrent.com/opensource") and tried to install but i could not :( 

when i try to create .deb pack
with
```
sh build_nix_pkg.sh deb
```

i get an error 

```
nomercy@nomercy-laptop:~/BitTorrent-5.3-GPL/python_bt_codebase$ sh build_nix_pkg.sh deb
build_nix_pkg.sh: 23: cdv: not found
Traceback (most recent call last):
  File "language_codes.py", line 15, in <module>
    from BTL.language import language_names
ImportError: No module named BTL.language
BitTorrent/GUI_wx/DownloadManager.py:1412: warning: 'msgid' format string with unnamed arguments cannot be properly localised:
                                                    The translator cannot reorder the arguments.
                                                    Please consider using a format string with named arguments,
                                                    and a mapping instead of a tuple for the arguments.
BitTorrent/GUI_wx/DownloadManager.py:1414: warning: 'msgid' format string with unnamed arguments cannot be properly localised:
                                                    The translator cannot reorder the arguments.
                                                    Please consider using a format string with named arguments,
                                                    and a mapping instead of a tuple for the arguments.
BitTorrent/GUI_wx/DownloadManager.py:1548: warning: 'msgid' format string with unnamed arguments cannot be properly localised:
                                                    The translator cannot reorder the arguments.
                                                    Please consider using a format string with named arguments,
                                                    and a mapping instead of a tuple for the arguments.
BitTorrent/GUI_wx/DownloadManager.py:1550: warning: 'msgid' format string with unnamed arguments cannot be properly localised:
                                                    The translator cannot reorder the arguments.
                                                    Please consider using a format string with named arguments,
                                                    and a mapping instead of a tuple for the arguments.
BitTorrent/GUI_wx/DownloadManager.py:1840: warning: 'msgid' format string with unnamed arguments cannot be properly localised:
                                                    The translator cannot reorder the arguments.
                                                    Please consider using a format string with named arguments,
                                                    and a mapping instead of a tuple for the arguments.
BitTorrent/GUI_wx/DownloadManager.py:2852: warning: 'msgid' format string with unnamed arguments cannot be properly localised:
                                                    The translator cannot reorder the arguments.
                                                    Please consider using a format string with named arguments,
                                                    and a mapping instead of a tuple for the arguments.
BitTorrent/GUI_wx/DownloadManager.py:3405: warning: 'msgid' format string with unnamed arguments cannot be properly localised:
                                                    The translator cannot reorder the arguments.
                                                    Please consider using a format string with named arguments,
                                                    and a mapping instead of a tuple for the arguments.
bittorrent-console.py:137: warning: 'msgid' format string with unnamed arguments cannot be properly localised:
                                    The translator cannot reorder the arguments.
                                    Please consider using a format string with named arguments,
                                    and a mapping instead of a tuple for the arguments.
bittorrent-console.py:140: warning: 'msgid' format string with unnamed arguments cannot be properly localised:
                                    The translator cannot reorder the arguments.
                                    Please consider using a format string with named arguments,
                                    and a mapping instead of a tuple for the arguments.
bittorrent-curses.py:95: warning: 'msgid' format string with unnamed arguments cannot be properly localised:
                                  The translator cannot reorder the arguments.
                                  Please consider using a format string with named arguments,
                                  and a mapping instead of a tuple for the arguments.
bittorrent-curses.py:258: warning: 'msgid' format string with unnamed arguments cannot be properly localised:
                                   The translator cannot reorder the arguments.
                                   Please consider using a format string with named arguments,
                                   and a mapping instead of a tuple for the arguments.
bittorrent-curses.py:261: warning: 'msgid' format string with unnamed arguments cannot be properly localised:
                                   The translator cannot reorder the arguments.
                                   Please consider using a format string with named arguments,
                                   and a mapping instead of a tuple for the arguments.
changetracker-console.py:35: warning: 'msgid' format string with unnamed arguments cannot be properly localised:
                                      The translator cannot reorder the arguments.
                                      Please consider using a format string with named arguments,
                                      and a mapping instead of a tuple for the arguments.
launchmany-curses.py:75: warning: 'msgid' format string with unnamed arguments cannot be properly localised:
                                  The translator cannot reorder the arguments.
                                  Please consider using a format string with named arguments,
                                  and a mapping instead of a tuple for the arguments.
launchmany-curses.py:233: warning: 'msgid' format string with unnamed arguments cannot be properly localised:
                                   The translator cannot reorder the arguments.
                                   Please consider using a format string with named arguments,
                                   and a mapping instead of a tuple for the arguments.
torrentinfo-console.py:30: warning: 'msgid' format string with unnamed arguments cannot be properly localised:
                                    The translator cannot reorder the arguments.
                                    Please consider using a format string with named arguments,
                                    and a mapping instead of a tuple for the arguments.
xgettext: Non-ASCII string at ./twisted/._copyright.py:1.
          Please specify the source encoding through --from-code or through a comment
          as specified in http://www.python.org/peps/pep-0263.html.
Traceback (most recent call last):
  File "<string>", line 1, in <module>
  File "BitTorrent/__init__.py", line 36, in <module>
    from BTL import BTFailure, InfoHashType
ImportError: No module named BTL

Building deb for Python 2.4...
Traceback (most recent call last):
  File "setup.py", line 23, in ?
    from BitTorrent.platform import install_translation
  File "/home/nomercy/BitTorrent-5.3-GPL/python_bt_codebase/BitTorrent/__init__.py", line 36, in ?
    from BTL import BTFailure, InfoHashType
ImportError: No module named BTL
cd: 121: can't cd to dist/
ls: cannot access BitTorrent-*.tar.gz: No such file or directory
mv: missing destination file operand after `bittorrent__python2.4'
Try `mv --help' for more information.
tar: option requires an argument -- f
Try `tar --help' or `tar --usage' for more information.
rm: missing operand
Try `rm --help' for more information.
sed: can't read ../debian/control: No such file or directory
dpkg-deb: no package information in `bittorrent__python2.4/DEBIAN/control'
Done with deb for Python 2.4.

```
I have all Prerequisites installed
Can somebody help me?

---

### Post by nmrcy on 2010-01-23
no one can?

---

### Post by lovinglinux on 2010-01-23
I'm not entirely sure, but looks like that thing is kind of old.

> From: [http://en.wikipedia.org/wiki/BitTorrent_%28software%29](http://en.wikipedia.org/wiki/BitTorrent_%28software%29)

Since version 6.0 the BitTorrent client has been a rebranded version of µTorrent. As a result, it is no longer open source, and this version of the program is now only available for Windows and Mac OS X 10.5.x.

Anyway, there are plenty of open source and up-to-date BitTorrent clients in the Ubuntu repositories. Much simpler to install and better than the original BitTorrent client.

I recommend Deluge and Ktorrent for Gnome and KDE respectively. But Ubuntu already comes with a client called Transmission.

[install deluge](apt:deluge)
[install ktorrent](apt:ktorrent)

I think you might be interested in the [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923).

BTW, is not polite to bump your thread just an hour after creating the thread. This is not instant messenger. Please wait at least 24 hours to ask for help again if nobody replies.

---

