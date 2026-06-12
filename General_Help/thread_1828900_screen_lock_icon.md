---
title: "screen lock icon"
date: 2011-08-19
forum: General Help
---

### Post by &#1593;&#1603;&#1608;&#1586; &#1576;&#1603;&#1608;&#1586; on 2011-08-19
At first I apologize if the subject was in the wrong place
 The reason is that I do not speak English
 And enlisted Google to translate can I register and add this topic :smile:
[COLOR=Red]  I have a question:[/COLOR]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=200386&stc=1&d=1313792154[/IMG]

---

### Post by jfed on 2011-08-19
I have never used Unity before, but I presume it still has the "add to panel" feature. Right click on the panel, and select "add to panel" Then scroll to where it says "Lock Screen" and click and drag it into the spot you want.

If it still doesn't work, it may be because you locked the other launchers to the panel, try right clicking all of them, and unchecking "lock to panel", then adding the screen lock app.

---

### Post by &#1593;&#1603;&#1608;&#1586; &#1576;&#1603;&#1608;&#1586; on 2011-08-19
> **jfed said:**
> I have never used Unity before, but I presume it still has the "add to panel" feature. Right click on the panel, and select "add to panel" Then scroll to where it says "Lock Screen" and click and drag it into the spot you want.

If it still doesn't work, it may be because you locked the other launchers to the panel, try right clicking all of them, and unchecking "lock to panel", then adding the screen lock app.

The problem is when I click on launcher I can not add any options. Also, when the pressure on the top panel I can not add any options.

Thank you my brother

---

### Post by wojox on 2011-08-19
Did you try this as your [command]("http://ubuntuforums.org/showpost.php?p=10802115&postcount=4")?

---

### Post by jfed on 2011-08-19
No no, you don't click on "application launcher"

In the small menu that appears after clicking "add to panel" you scroll down and find the choice that says "lock screen"

You could also select "custom application launcher" and where it says "code" type in

```
gnome-screensaver-command --lock
```
just like wojox suggested.

---

### Post by &#1593;&#1603;&#1608;&#1586; &#1576;&#1603;&#1608;&#1586; on 2011-08-19
Thank you
 But can you tell me where I find  "custom application launcher"

---

### Post by jfed on 2011-08-19
[IMG]http://img94.imageshack.us/img94/2337/screenshot2fu.png[/IMG]

Right click on that bar, and select "add to panel"

A menu should pop up that looks like this
[IMG]http://img842.imageshack.us/img842/8379/menu1c.png[/IMG]

Then scroll down to here, click on Lock Screen, then click the button on the bottom that says "add"
[IMG]http://img197.imageshack.us/img197/725/menu2r.png[/IMG]

That will add a button to lock your screen on the top bar.

I hope this helped.

---

### Post by &#1593;&#1603;&#1608;&#1586; &#1576;&#1603;&#1608;&#1586; on 2011-08-19
Unfortunately this property does not work in Ubuntu Unity 11.04

---

### Post by Iowan on 2011-08-19
It's not a quick-click, but the lock option is available by clicking the power icon (top right corner), then selecting "Lock Screen".

---

### Post by wojox on 2011-08-19
Right click your desktop

Select Create Launcher...

Create the custom Launcher as you want to.

Open your Home Folder. Press Ctrl + H to show hidden files if necessary.

Browse to .local/share/applications

Drag and drop your Launcher from Desktop to that folder.

Now drag and drop your launcher from .local/share/applications to the Launcher Bar on the left on your Screen.

You can now delete your custom Launcher on the Desktop if it's still there.

---

### Post by &#1593;&#1603;&#1608;&#1586; &#1576;&#1603;&#1608;&#1586; on 2011-08-19
> **Iowan said:**
> It's not a quick-click, but the lock option is available by clicking the power icon (top right corner), then selecting "Lock Screen".

[COLOR=Red]Thank you my brother .. [/COLOR][COLOR=Red]I found

[/COLOR]I also found a solution to add in launcher

 This is the solution:

> That is easy!  
  **1)** Right click on the Desktop and choose "Create Launcher".  
  **2)** For the name you choose what you want. "Lock Screen" for example.  
  **3)** At command you paste this: gnome-screensaver-command -a  
  **4)** Then drag it to the Launcher.  
  [IMG]http://i.stack.imgur.com/UK2bM.png[/IMG]
  Enjoy ;-)
 


---

### Post by zaabi1995 on 2011-08-19
&#1605;&#1576;&#1585;&#1608;&#1608;&#1608;&#1603; &#1581;&#1576;&#1608;&#1608;&#1608;&#1576;

---

