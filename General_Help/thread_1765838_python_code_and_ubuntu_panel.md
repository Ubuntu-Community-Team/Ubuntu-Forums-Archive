---
title: "python code and ubuntu panel"
date: 2011-05-23
forum: General Help
---

### Post by AgentZ86 on 2011-05-23
Hi all

see comment in the code, it seems like the code is ok so not sure why it's doing this

Please advise

I'm using ubuntu 10.10 maverick 

See code here:
[http://paste.pound-python.org/show/7066/](http://paste.pound-python.org/show/7066/)

THanks

---

### Post by ashekarema@gmail.com on 2011-05-23
To my knowledge there is no Background color for static text.  I'm not sure what effect you want.
    If you want a blue square behind the white text then one way to do this is to place a blue panel behind it.
   If you are wanting a blue border around the text, then you can make two blue static texts and place one of them one pixel up and one pixel to the right and the other one pixel down and one pixel to the left.  Over the top of these you can then place a white static text giving the appearance of white text with a blue outline.

-----------------
[http://www.dotdeb.com](http://www.dotdeb.com) is a great place to find deb packages.

---

### Post by AgentZ86 on 2011-05-24
> **ashekarema@gmail.com said:**
> To my knowledge there is no Background color for static text.  I'm not sure what effect you want.
    If you want a blue square behind the white text then one way to do this is to place a blue panel behind it.
   If you are wanting a blue border around the text, then you can make two blue static texts and place one of them one pixel up and one pixel to the right and the other one pixel down and one pixel to the left.  Over the top of these you can then place a white static text giving the appearance of white text with a blue outline.

-----------------
[http://www.dotdeb.com](http://www.dotdeb.com) is a great place to find deb packages.

Thanks for the input on this

Here is the backround of where I got this code
Initially I watched a video on Youtube that taught this code and about the Static Text here:
[http://www.youtube.com/watch?v=qYVf09MVY14](http://www.youtube.com/watch?v=qYVf09MVY14)

He appears to be using windows, and his code produces the blue panel backround and mine does not for some reason.
Additionally I cannot seem to move my text around on the screen (see my code comments) it appears to be locked to the left of the panel/window

I don't feel there is anything wrong with the code however, I really don't know since I'm so new to programming.

Perhaps this is something to do with ubuntu forcing the screen to match my desktop settings or something I can only speculate.

If there is indeed something wrong with the code, I'm not sure I understand what that is or why ?
I'll rework the code a bit to mimick his screen but I do not understand why it's different.

I'm using default ubuntu 10.10 maverick with default python2.6 which is what I believe this old vid was using
And the default wxPython included on ubuntu by default.

Thanks for reading my post

---

### Post by ashekarema@gmail.com on 2011-05-24
I'm not sure.  There are a few features in windows that cannot be done in linux.  When programming in wx, you will run into this from time to time.  To get an idea of what is available on linux you can download a bunch of demos from: [http://sourceforge.net/projects/wxpython/files/wxPython/2.8.10.1/wxPython-demo-2.8.10.1.tar.bz2/download](http://sourceforge.net/projects/wxpython/files/wxPython/2.8.10.1/wxPython-demo-2.8.10.1.tar.bz2/download)

Once you have extracted the contents, you can run them by entering the following command, replacing zach with your own user name:

python '/home/zach/Downloads/wxPython-2.8.10.1/demo/demo.py'

While scrolling through the demos, sometimes this will give you a message like "Sorry, only available for windows"

---

### Post by AgentZ86 on 2011-05-26
> **ashekarema@gmail.com said:**
> I'm not sure.  There are a few features in windows that cannot be done in linux.  When programming in wx, you will run into this from time to time.  To get an idea of what is available on linux you can download a bunch of demos from: [http://sourceforge.net/projects/wxpython/files/wxPython/2.8.10.1/wxPython-demo-2.8.10.1.tar.bz2/download](http://sourceforge.net/projects/wxpython/files/wxPython/2.8.10.1/wxPython-demo-2.8.10.1.tar.bz2/download)

Once you have extracted the contents, you can run them by entering the following command, replacing zach with your own user name:

python '/home/zach/Downloads/wxPython-2.8.10.1/demo/demo.py'

While scrolling through the demos, sometimes this will give you a message like "Sorry, only available for windows"

Ahhh , great thanks

I suspected something like this but since I'm new I did not want to draw a conclusion from lack of information.

Thanks

---

