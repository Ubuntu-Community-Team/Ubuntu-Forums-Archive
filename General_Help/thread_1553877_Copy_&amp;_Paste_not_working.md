---
title: "Copy &amp; Paste not working?"
date: 2010-08-15
forum: General Help
---

### Post by JoeFriday49 on 2010-08-15
I have a weird problem...  Whenever I'm in a forum I can't copy & paste text from an Evolution email message without first pasting the text into an editor like gedit or a word processor and recopying it a second time...  Then it works fine...  I thought the problem may have been a Delphi forum specific problem, but it also does the same thing on this board...

I running 10.04 with the default Evolution mail program...  Any idea's?

BTW on Delphi I can turn off the wysiwyg editor and paste as "source" and it works just fine without the paste and recopy step...

---

### Post by JoeFriday49 on 2011-02-09
Don't work on 10.10 either...

---

### Post by wojox on 2011-02-09
Are you leaving Evolution open when you copy and paste?

If not try that.

Also install glipper:

```
sudo apt-get update: sudo apt-get install glipper
```

---

### Post by corncob on 2011-02-09
I don't use Evolution but have the same problem with other things like Firefox.  I just assumed that was how it worked -- you had to keep the page you copied from open until the material was pasted, although I don't remember having to do this with Windows.
Glipper sounded interesting and I installed it from the Software Center but I can't find it in the menus and when I tried to run it from the terminal I got
```
tux@eeepc:~$ glipper
No command 'glipper' found, did you mean:
 Command 'klipper' from package 'klipper' (main)
glipper: command not found
tux@eeepc:~$ 
```

---

### Post by wojox on 2011-02-09
> **corncob said:**
> I don't use Evolution but have the same problem with other things like Firefox.  I just assumed that was how it worked -- you had to keep the page you copied from open until the material was pasted, although I don't remember having to do this with Windows.
Glipper sounded interesting and I installed it from the Software Center but I can't find it in the menus and when I tried to run it from the terminal I got
```
tux@eeepc:~$ glipper
No command 'glipper' found, did you mean:
 Command 'klipper' from package 'klipper' (main)
glipper: command not found
tux@eeepc:~$ 
```

There is no menu item:

```
ojox@wojox-desktop:~$ whereis glipper
glipper: /usr/lib/glipper /usr/lib64/glipper /usr/share/glipper

```

---

### Post by JoeFriday49 on 2011-02-09
<A man is driving down the road and breaks down near a monastery.>

I just pasted the line above from an email, but I have to click the little icon in the upper right of this frame that says "switch Editor Mode" before it will paste.  I assume that it is turning off HTML...  The email I copied it from was formatted as HTML...  

Just an annoyance that cropped up with the installation of the 2010 series of software...  Maybe it will be all better when 11.04 hit's the shelves...

---

### Post by corncob on 2011-02-10
Now that you mention it, it seems like the problem shows up when I try pasting HTML to plain text.

```
whereis glipper
```
found similar files but still don't know what to do with them.  Maybe I actually have to have copied and pasted something. The website in the Software Center didn't work for me and, I admit, I haven't yet googled it.

So what happened at the monastery?:D

---

### Post by JoeFriday49 on 2011-02-10
> **corncob said:**
> 

So what happened at the monastery?:D
LOL...  Can't tell you because you ain't a Monk...

I usually receive several dozen emails a day most of which are old jokes I've got a hundred times before...  ) :

---

