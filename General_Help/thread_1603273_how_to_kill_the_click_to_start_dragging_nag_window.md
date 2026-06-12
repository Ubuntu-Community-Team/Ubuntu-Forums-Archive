---
title: "how to kill the click to start dragging nag window"
date: 2010-10-22
forum: General Help
---

### Post by macem29 on 2010-10-22
like the title says, that popup is annoying, don't know what it refers to and can't seem to turn it off, anyone successfully get rid of the click to start dragging nag?

---

### Post by macem29 on 2010-10-23
replying to myself again, I've started a few threads here only after reading tons, always tried to be
as specific in the titles and body as possible, and posted in the right section, I must be writing in
an invisible font...I'll continue to read here to  get some information, but I'm done posting I think...
maybe I just seem to have uninteresting problems to fix? no drama, no remove my account BS....seeya

---

### Post by chewearn on 2010-10-23
Dude, you aren't being clear at all.  I have used ubuntu for a long time, but I am still unable to comprehend what you are referring to as "click to start dragging nag window".  Perhaps a screen shot will make it clear.

---

### Post by macem29 on 2010-10-23
ok, thanks man, you're right, a pic is a good idea

---

### Post by Jebtrix on 2010-10-23
Weird I dont get that but here is a possible solution:

Hit Alt-F2 and run **gconf-editor**

Drill down the tree to /apps/panel/global and uncheck tooltips_enabled

---

### Post by Jebtrix on 2010-10-23
I jumped the gun, your problem is with the workspace switcher. Not sure about that one yet..

---

### Post by macem29 on 2010-10-23
cool, I tried your last idea, restarted gnome and it's still there, my nag, but that exercise
before your edit was worthwhile, in leaning another way to manipulate the panels, and I
agree this is related to the workspace switcher, switching desktops produces the nag, I
really appreciate the help, thanks

---

### Post by stoneage on 2010-10-23
> **macem29 said:**
> like the title says, that popup is annoying, don't know what it refers to and can't seem to turn it off, anyone successfully get rid of the click to start dragging nag?

It is telling you you can drag applications from one workspace to another.

---

### Post by macem29 on 2010-10-23
> **stoneage said:**
> It is telling you you can drag applications from one workspace to another.

it may be...but I don't want to be told that :)....moving the cursor over the the popup makes it
disappear, but it's a pain, often obscures something in window that I want to see,
I use a few different work spaces a lot of the time so this thing is always popping up

---

### Post by Jebtrix on 2010-10-23
There is way to do it if you use compiz

Just in case you dont have it:
sudo apt-get install compizconfig-settings-manager

Enable the [Opacity, Brightness, and Saturation] Plugin
Add a new Window Specific Setting with these parameters:
  Windows= **type=tooltip & name=wnck-applet**
  Windows Value= **0**

Otherwise you may be sol without hacking/recompiling the applet itself.

---

### Post by macem29 on 2010-10-23
> **Jebtrix said:**
> There is way to do it if you use compiz

Just in case you dont have it:
sudo apt-get install compizconfig-settings-manager

Enable the [Opacity, Brightness, and Saturation] Plugin
Add a new Window Specific Setting with these parameters:
  Windows= **type=tooltip & name=wnck-applet**
  Windows Value= **0**

Otherwise you may be sol without hacking/recompiling the applet itself.

thread marked solved, this is the solution, many thanks Jebtrix

---

