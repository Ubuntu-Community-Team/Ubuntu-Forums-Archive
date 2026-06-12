---
title: "putty - missing funcitions"
date: 2011-01-07
forum: General Help
---

### Post by nagileon on 2011-01-07
Hi there
I don't believe I'm saying this but putty under Windows works so great and I'm very disappointed with it's performance under linux. I'm talking specifically about three functions that I'm missing from Windows world and could not find them in any terminal program in Linux.

1. When you select text in putty window the text is being automatically copied to clipboard - very useful.
2. When I move the cursor to another putty window and right click inside it - the text is being automatically pasted inside this window.
3.When I click on a putty window with session running I can say: "duplicate session" - so great.

Those three little functions are so helpful.
Why o why can't I get those in any Linux terminal ?!
I thought I will can get this wit CrossOver but surprisingly the Windows version of putty does not work under linux as it supposed to?

Any idea how to fix this, any chance that the Ubuntu development team can do something about it ?

Regards
Peter

---

### Post by seawolf167 on 2011-01-07
_Copy/paste_

You can highlight the text in a terminal, right click and select copy

You can cat to a file

```
cat file1 > ~/Desktop/file2.txt
```


_"Duplicate_"

By far the best "duplicate" program to use from terminal is [screen]("http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/")


[U]Misc
[/U]
From your linux box you should be using ssh in a terminal, not putty

---

### Post by efflandt on 2011-01-07
Just curious why you would use PuTTY in Linux?  Normally you would simply use **ssh** (or **telnet** for other things unless PuTTY has some special terminal type you need to use or you are using it under Wine).

Although, by default the terminal does not understand MS Windows shortcuts, since those are used for other things by default in some terminal programs.  So the normal X way to copy something from a terminal, is to **highlight** it with the mouse, go to the other window and **middle click** or click scroll wheel (or both mouse buttons on 2 button mouse) to paste.  Or you can right click and select **copy**, then right click in another terminal and select **paste**.  Although, for other applications like gedit, once you copy something you can use Ctrl+V to paste into gedit.

With a little practice (or if nothing happens) it becomes second nature.

---

### Post by nagileon on 2011-01-07
That's my point, putty under windows is automatically copying whatever text I select  - I don't have to do ctrl-v or right click and choose copy/paste. 
All you have to do if you want to copy text from one putty window to another is this:

1. Select text
2. Move the cursor to another window
3. Right click to paste

versus

1.Select text
2.Right click
3.Choose the copy option
4.Move to another window
5.Right click
6.Choose the paste option

Do you see my point now ? 
It's 100% increase in number of operations required to perform the same simple task. And if you get use to it it drives you mad if it's not there. Especially if you install and play with a lot of machines at the same time.

Regards
Peter

---

### Post by bodhi.zazen on 2011-01-07
In linux, select text -> move to new location -> middle mouse button (push mouse wheel down) to paste.

Windows does not have this behavior, so Putty emulates it with the behavior you are used to.

---

### Post by binoplaza on 2011-01-07
Alternatively you can copy / paste using <ctrl + shift + c / p>

---

### Post by bodhi.zazen on 2011-01-07
> **binoplaza said:**
> Alternatively you can copy / paste using <ctrl + shift + c / p>

"Standard" hot keys on most apps on most OS

ctrl -c = copy
ctrl - x = cut
ctrl- v = paste
ctrl - a = select all
ctrl -z = undo

ctrl-p = print
ctrl -f = find
ctrl -r = replace

---

### Post by nagileon on 2011-01-07
Thanks :)
Both methods are working great )
Regards
Peter

---

### Post by binoplaza on 2011-01-07
You can use <ctrl + shift + t> for a new tab, sort of like a new session ..

---

