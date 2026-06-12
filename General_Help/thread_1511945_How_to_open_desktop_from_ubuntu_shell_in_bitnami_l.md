---
title: "How to open desktop from ubuntu shell in bitnami lampstack?"
date: 2010-06-17
forum: General Help
---

### Post by mertnuhoglu on 2010-06-17
I installed bitnami lampstack for vmware. When I run it, the vmware starts in ubuntu shell. How can I open the gui desktop of ubuntu from there?

There is a [similar thread]("http://ubuntuforums.org/showthread.php?t=711932"). 

I tried the suggestions in that thread. 

I first tried

```
startx
```

Shell said: 

```
Command not found.
```

Then I tried:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Shell said:

```
Package 'xserver-xorg' is not installed.
```

What should I do?

Or do you know any vmware ready package for LAMP with graphical user interface already installed?

Here is the screenshot of my shell session 

[IMG]http://i48.tinypic.com/140yg7d.png[/IMG]

---

### Post by K.J. on 2010-06-17
That's a server install, i.e. no GUI.  You can apt-get install ubuntu-desktop if you need that.  It's not typically used on servers because they tend to run headless and it consumes resources.

---

