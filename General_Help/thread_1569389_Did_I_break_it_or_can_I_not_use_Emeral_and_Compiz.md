---
title: "Did I break it or can I not use Emeral and Compiz?"
date: 2010-09-06
forum: General Help
---

### Post by Adrienk on 2010-09-06
So I have this emerald theme I wanted to install on my Ubuntu 10.4 gnome installation that has compiz.
I didn't know how to do this so i looked at [http://ubuntuforums.org/showthread.php?t=495997](http://ubuntuforums.org/showthread.php?t=495997) to understand how to do this and when did the steps which you will see her shortly, I got some errors and my windows broke to the point you can move them, close them and all you see is the menu bar and then the rest of the window down.

```
adam@adam-laptop:~$ sudo -i
[sudo] password for adam: 
root@adam-laptop:~# compiz --replace -c emerald &
[1] 7435
root@adam-laptop:~# compiz (core) - Warn: Unknown option '-c'

OpenGL Warning: No pincher, please call crStateSetCurrentPointers() in your SPU
compiz (core) - Error: Couldn't load plugin 'emerald'
OpenGL Info: Using XSHM for GLX_EXT_texture_from_pixmap
compiz (core) - Error: Couldn't load plugin 'emerald'

```So.....I want to use this emerald theme, but when loading it into emerald, A there is no "Apply theme" button and following the link provided apparently breaks my window decorations.

---

### Post by Adrienk on 2010-09-06
Can I **please** get some help on this?

---

### Post by Adrienk on 2010-09-06
Bump

---

### Post by overdrank on 2010-09-06
Please be patient and bump your thread once a day.

Have you tried the command ```
emerald --replace
``` to activate the new theme.

---

### Post by Adrienk on 2010-09-06
The results are:

that works, do I have to do it for every time I log in/restart?
is there no way to set that command to auto so it starts when I log in?

Also How do I use the emerald theme manager since there is no "Apply this theme?"


And are you insane ,once a day? my thread will be on page 55.

---

### Post by realzippy on 2010-09-06
put in *Startup applications*  (menu)

---

### Post by Adrienk on 2010-09-06
**ACTUALLY NO ITS NOT**

I installed emerald, ran the command got the emerald windows decoration BUT in emerald there is no "apply this theme" or something like it to apply the themes I import

---

### Post by realzippy on 2010-09-06
Edited post,sorry.

---

### Post by Adrienk on 2010-09-06
> **Adrienk said:**
> 

I installed emerald, ran the command got the emerald windows decoration BUT in emerald there is no "apply this theme" or something like it to apply the themes I import

Also what am I putting in start up applications menu?

---

### Post by overdrank on 2010-09-06
> **Adrienk said:**
> 
And are you insane ,once a day? my thread will be on page 55.

No:D

---

### Post by Adrienk on 2010-09-06
So How do I apply themes imported into emerald, and how do I put the emerald --replace command into start up applications?

---

### Post by realzippy on 2010-09-06
Which theme is it?
think if you change the file extension to *.emerald* you can simply drag it into theme manager...

---

### Post by realzippy on 2010-09-06
> **overdrank said:**
> No:D


Membername includes this.

---

### Post by overdrank on 2010-09-06
> **Adrienk said:**
> So How do I apply themes imported into emerald, and how do I put the emerald --replace command into start up applications?
Once you select the theme it should activate then. If it does not then use the command.
You can go to system, preference, start up applications and add the command.

---

### Post by realzippy on 2010-09-06
Attached...







OUUUUPS!The line above ..sorry
**Put it in [B][COLOR="SeaGreen"]command[/COLOR]** not in [COLOR="Red"]comment[/COLOR]!!!![/B]

---

### Post by Adrienk on 2010-09-06
Ugh.

OK read **carefully** (this is so frustrating)

I **Have** Emerald theme manager installed, Compiz installed. I ran the command emerald --replace.

I need to have that command run every time I log into Ubuntu. **How do I do that?**

Next: the theme **CURRENTLY IMPORTED, ALREADY IN **and every other way you can describe something that is **IN** something else, is called: 

[http://gnome-look.org/content/show.php/Aurora+Leopard+BSM?content=92131](http://gnome-look.org/content/show.php/Aurora+Leopard+BSM?content=92131)

I downloaded the **EMERALD VERSION ONLY** there, I **imported it into emerald theme manager** now **how do I apply** it to my windows decorations? and why does  the theme manager not have a  **apply** button?

**SIDE NOTE:**

I didnt see you guys reply. Um it didn't apply the theme instead all my window decorations are like red and what not and not the screen shots shown and I followed there steps.

---

### Post by realzippy on 2010-09-06
"I Have Emerald theme manager installed, Compiz installed. I ran the command emerald --replace.
I need to have that command run every time I log into Ubuntu. How do I do that?"

Yes,I understand.Have you [CCSM]("http://wiki.compiz.org/CCSM") installed (?),then you can place the command there,so emerald will be started when compiz starts,

---

### Post by Adrienk on 2010-09-06
Thank you all for listening to me rage quit lol. I didn't install a required app, and now it all works. thanks again.

I do but where in CCM do I place it?

---

### Post by realzippy on 2010-09-06
sorry for confusing posting...  :D

---

### Post by Adrienk on 2010-09-06
> **realzippy said:**
> sorry for confusing posting...  :D

Thats ok but where in CCM do I place the command?

---

### Post by realzippy on 2010-09-06
*I do but where in CCM do I place it?*

..in windowdecorations or is it windowdecorator (?) 
as "Command"..

---

