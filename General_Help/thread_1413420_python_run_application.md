---
title: "python run application"
date: 2010-02-22
forum: General Help
---

### Post by artheus on 2010-02-22
Hi!

I've just made a small python "Run" app.. Just like the "Run" application in Windows for those of you who are familiar with that...

The only thing bothering me about it, is that the "Run" app window will not close until i shut down the program i started with my run app. Is it possible to make it close before the os.system() command is sent?

Here's the code

```

#!/usr/bin/env python

import wx
import os

__author__="artheus"
__date__ ="$Feb 22, 2010 4:38:32 PM$"

class bucky(wx.Frame):
    
    def __init__(self,parent,id):
        wx.Frame.__init__(self,parent,id,'Run', size=(350,110), pos=(545,375))
        panel=wx.Panel(self)
        button=wx.Button(panel,label="Run",pos=(270,60),size=(60,30))
        self.textfield=wx.TextCtrl(panel, style=wx.TE_LEFT, pos=(20,20), size=(310,25))
        self.textfield.SetFocus()

        self.textfield.Bind(wx.EVT_KEY_DOWN, self.enterkey)
        self.Bind(wx.EVT_BUTTON, self.runbutton, button)
        self.Bind(wx.EVT_CLOSE, self.closewindow)

    def enterkey(self, event):
        keyCode = event.GetKeyCode()
        if keyCode == 13:
            self.run(self.textfield.GetValue())
        event.Skip()

    def runbutton(self, event):
        self.run(self.textfield.GetValue())


    def closewindow(self, event):
        self.Destroy()

    def run(self, command):
        if command == "calc":
            command = "gcalctool"

        os.system(command)
        self.Destroy()


if __name__ == "__main__":
    app=wx.PySimpleApp()
    frame=bucky(parent=None,id=-1)
    frame.Show()
    app.MainLoop()

```

Cheers,
Artheus

---

### Post by doas777 on 2010-02-22
you will probably have to separate your UI from the main  flow of your app. do all your work without an interface, and only throw up the gui when you need it. that way your app can close the gui without aborting itself.

---

### Post by raffaele181188 on 2010-02-22
I don't really know wx (why not Qt? Or maybe Gtk+..)
Anyway, I think your app behavior being normal: your Destroy() gets called once os.system() returns (it's a "blocking" call). To get the desired behavior you should use [subprocess]("http://docs.python.org/library/subprocess.html") to spawn a new process
```

subprocess.Popen(command)

```

---

### Post by artheus on 2010-02-22
> **raffaele181188 said:**
> I don't really know wx (why not Qt? Or maybe Gtk+..)
Anyway, I think your app behavior being normal: your Destroy() gets called once os.system() returns (it's a "blocking" call). To get the desired behavior you should use [subprocess]("http://docs.python.org/library/subprocess.html") to spawn a new process
```

subprocess.Popen(command)

```

Thank you! This solved my problem.

Well.. I've just started GUI programming in python.. So I don't know much about the different... But I read that wxPython has got great support for alpha-channeling which I really want to use in some upcoming projects of mine.

Thanks again,
Artheus

---

