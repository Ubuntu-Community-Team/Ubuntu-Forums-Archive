---
title: "pyinstaller"
date: 2012-05-02
forum: General Help
---

### Post by angadarora on 2012-05-02
Hello guys,

      I want to create an executables of the python programmes so i am using pyinstaller 1.5.1 .Here i have tried runing "hello world" programme and its running successfully but programmes which i have wriiten for my application ,i am getting error in that. I mean executables are creating successfully but its not running.

Here are the steps which i am following to create an executable:

[COLOR=#444444][FONT=arial] Step 1 : Download the latest source version of pyinstaller
 Step 2 : Extract the tar.gz file
Step 3 : Copy your python file(s) to that folder and cd to this folder in ur terminal
Step 4 : In terminal $python Configure.py
Step 5 : $python Makespec.py test.py [Where test.py is your main python file ]
  Step 6 : Now copy the content of the folder test, back to the pyinstaller folder and run $python pyinstaller.py test.spec[/FONT][/COLOR]
[COLOR=#444444][FONT=arial]   Now go check the “dist” folder and you will find your standalone python application if everything went well.[/FONT][/COLOR]
[COLOR=#444444][FONT=arial]
[/FONT][/COLOR]
[COLOR=#444444][FONT=arial]and Here are the errors i am getting while running the executable file:[/FONT][/COLOR]
[COLOR=#444444][FONT=arial]
[/FONT][/COLOR]
[COLOR=#444444][FONT=arial]Traceback (most recent call last):
  File "<string>", line 3, in <module>
  File "/home/a3biomed/pyinstaller-1.5.1/iu.py", line 436, in importHook
    mod = _self_doimport(nm, ctx, fqname)
  File "/home/a3biomed/pyinstaller-1.5.1/iu.py", line 521, in doimport
    exec co in mod.__dict__
  File "/home/a3biomed/pyinstaller-1.5.1/build/pyi.linux2/tryftp/outPYZ1.pyz/os", line 398, in <module>
  File "/home/a3biomed/pyinstaller-1.5.1/iu.py", line 436, in importHook
    mod = _self_doimport(nm, ctx, fqname)
  File "/home/a3biomed/pyinstaller-1.5.1/iu.py", line 521, in doimport
    exec co in mod.__dict__
  File "/home/a3biomed/pyinstaller-1.5.1/build/pyi.linux2/tryftp/outPYZ1.pyz/UserDict", line 82, in <module>
  File "/home/a3biomed/pyinstaller-1.5.1/iu.py", line 436, in importHook
    mod = _self_doimport(nm, ctx, fqname)
  File "/home/a3biomed/pyinstaller-1.5.1/iu.py", line 521, in doimport
    exec co in mod.__dict__
  File "/home/a3biomed/pyinstaller-1.5.1/build/pyi.linux2/tryftp/outPYZ1.pyz/_abcoll", line 11, in <module>
ImportError: cannot import name ABCMeta
[/FONT][/COLOR]
[COLOR=#444444][FONT=arial]
[/FONT][/COLOR]
[COLOR=#444444][FONT=arial]guyss please help..!!!!!
[/FONT][/COLOR]

---

