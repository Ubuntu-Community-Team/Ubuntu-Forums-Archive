---
title: "problems getting older python program to install/run"
date: 2009-11-08
forum: General Help
---

### Post by rebeltaz on 2009-11-08
I know this is an old program, but I am trying to install gXiso, an XBox ISO extraction/FTP program. It is a python-based program. In the README file, it says to install it with the command:

```
python setup.py install
```

as root. When I do that, I get the following warnings:

```
src/gxiso.py:892: warning: 'msgid' format string with unnamed arguments cannot be properly localized:
                           The translator cannot reorder the arguments.
                           Please consider using a format string with named arguments,
                           and a mapping instead of a tuple for the arguments.
src/gxiso.py:1015: warning: 'msgid' format string with unnamed arguments cannot be properly localized:
                            The translator cannot reorder the arguments.
                            Please consider using a format string with named arguments,
                            and a mapping instead of a tuple for the arguments.
src/gxiso.py:1111: warning: 'msgid' format string with unnamed arguments cannot be properly localized:
                            The translator cannot reorder the arguments.
                            Please consider using a format string with named arguments,
                            and a mapping instead of a tuple for the arguments.
src/gxiso.py:1185: warning: 'msgid' format string with unnamed arguments cannot be properly localized:
                            The translator cannot reorder the arguments.
                            Please consider using a format string with named arguments,
                            and a mapping instead of a tuple for the arguments.
...... done.
...... done.
/usr/lib/python2.6/distutils/dist.py:266: UserWarning: Unknown distribution option: 'windows'
  warnings.warn(msg)
running install
running build
running build_py
running build_scripts
running install_lib
running install_scripts
changing mode of /usr/local/bin/gxiso.py to 755
running install_data
copying po/tmp/fr/gxiso.mo -> /usr/local/share/locale/fr/LC_MESSAGES
copying po/tmp/it/gxiso.mo -> /usr/local/share/locale/it/LC_MESSAGES
running install_egg_info
Removing /usr/local/lib/python2.6/dist-packages/gxiso-1.5.egg-info
Writing /usr/local/lib/python2.6/dist-packages/gxiso-1.5.egg-info
```

I saw somewhere on here where someone had installed the python2.6-dev (2.4 in their case) package and that solved a similar install problem that they had so I tried that with no effect. I did notice that there was now a BUILD directory that wasn't there before I ran the setup. Since I could not find any other way to attempt to run the program, I went in there and under a directory called scripts-2.6, I found a file called gxiso.py. I ran that with:

```
python gxiso.py
```

as root and I got a graphical error box complaining that the data directory could not be found. I assume that that is because the program didn't install correctly to begin with.

Can someone help me figure out what I am doing wrong? Thanks....

---

### Post by rebeltaz on 2009-11-08
I swear... sometimes just asking for help helps me figure out the answer on my own!

After rereading the setup programs output for the nteenth time, I noticed that gxiso.py was also placed in the /usr/local/bin directory. So I tried issuing the command:

```
python /usr/local/bin/gxiso.py
```

The program ran and the interface came up. I appreciate the help! ):P

---

