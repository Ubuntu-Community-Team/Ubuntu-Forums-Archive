---
title: "How to make print-screen key save automatically ?"
date: 2012-05-16
forum: General Help
---

### Post by Docmero on 2012-05-16
[CENTER]
[CENTER]Hi ,
How to make the print-screen button save automatically to a specific folder ?
I have ubuntu 11.10
I need this feature because I take pictures of my screen alot !! 
I really mean it , lol :lolflag:
[/CENTER]
Thanks
[/CENTER]

---

### Post by stinkeye on 2012-05-16
Use scrot as the command for the print key to run.
Need to install **scrot**.

Eg: From **man scrot**
> scrot '%Y-%m-%d_$wx$h.png' -e 'mv $f ~/shots/' 
 This would create a file called something like 2000-10-30_2560x1024.png and move it to your shots directory.

If you take a lot of just fullscreen screenshots probably better to take out the size and replace with time.
eg
```
scrot '%F_%H.%M.%S.png' -e 'mv $f ~/shots/'
```
will create a file something like ```
**[COLOR="Magenta"]2012-05-16[/COLOR]_[COLOR="DarkOrange"]20.15.40[/COLOR].png**
```
[COLOR="magenta"]Year-Month-Day[/COLOR]_[COLOR="darkorange"]Hour.Minute.Second[/COLOR]

---

### Post by ads52 on 2012-08-13
Perhaps add in a *--quality* option as by default scrot takes an image with a quality of 75:

```

-q, --quality NUM
   Image quality (1-100) high value means high size, low compression.  Default:
   75. (Effect differs depending on file format chosen).

```

I usually capture the screen with *-q 100 *and then rework the image with gimp.

---

### Post by Buntu Bunny on 2012-08-13
> **Docmero said:**
> 
Hi ,
How to make the print-screen button save automatically to a specific folder ?


I'd like to know the answer to this as well. In Lucid, I had the option to choose where the screenshot was saved. In Precise, it automatically saves it in my pictures folder. Of course I only know this because I'm using Gnome Classic No Effects (because I can't find anything with Unity :o ) I'd rather save a screenshot to desktop where I can edit as needed and then save to the folder of my choice. Anybody have any ideas how to do this?

---

### Post by stinkeye on 2012-08-13
> **Buntu Bunny said:**
> I'd like to know the answer to this as well. In Lucid, I had the option to choose where the screenshot was saved. In Precise, it automatically saves it in my pictures folder. Of course I only know this because I'm using Gnome Classic No Effects (because I can't find anything with Unity :o ) I'd rather save a screenshot to desktop where I can edit as needed and then save to the folder of my choice. Anybody have any ideas how to do this?
Use **shutter** as your screenshot tool.
In preferences choose how to name new screenshots and where to save, and enable the keyboard shortcuts.
Using a 3 to 4 second delay is also useful.
Also has an inbuilt basic editor.

---

### Post by Buntu Bunny on 2012-08-13
Stinkeye, thanks! Sounds like just what I need. I agree about the delay, very useful.

---

### Post by philinux on 2012-08-13
> **Buntu Bunny said:**
> I'd like to know the answer to this as well. In Lucid, I had the option to choose where the screenshot was saved. In Precise, it automatically saves it in my pictures folder. Of course I only know this because I'm using Gnome Classic No Effects (because I can't find anything with Unity :o ) I'd rather save a screenshot to desktop where I can edit as needed and then save to the folder of my choice. Anybody have any ideas how to do this?

Se these.
[https://bugs.launchpad.net/ubuntu/+source/gnome-screenshot/+bug/977228](https://bugs.launchpad.net/ubuntu/+source/gnome-screenshot/+bug/977228)

[http://askubuntu.com/questions/114429/default-save-directory-for-gnome-screenshot](http://askubuntu.com/questions/114429/default-save-directory-for-gnome-screenshot)

---

### Post by Buntu Bunny on 2012-08-13
> **philinux said:**
> Se these.
[https://bugs.launchpad.net/ubuntu/+source/gnome-screenshot/+bug/977228](https://bugs.launchpad.net/ubuntu/+source/gnome-screenshot/+bug/977228)

[http://askubuntu.com/questions/114429/default-save-directory-for-gnome-screenshot](http://askubuntu.com/questions/114429/default-save-directory-for-gnome-screenshot)

Philinux, thanks. I'm taking a look and trying the suggested tweaking. Hopefully I'll get it set the way I want.

---

### Post by ads52 on 2012-08-13
Like many small things of this kind it can be done very easily in fluxbox. On my system xev reveals Print Screen as 170 and then I add the following to *$HOME/.fluxbox/keys*:

```

# Screenshot:

107 :ExecCommand scrot -q 100

```

With the option of course to add something like:

```

-e 'mv $f $HOME/Desktop'

```

to move the completed image to the Desktop. Unfortunately I am not sure how this would translate to a standard GNOME/Unity desktop :(.

---

