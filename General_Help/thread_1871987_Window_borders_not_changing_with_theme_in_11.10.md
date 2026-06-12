---
title: "Window borders not changing with theme in 11.10"
date: 2011-10-29
forum: General Help
---

### Post by alquery on 2011-10-29
Ever since I upgraded to 11.10 from 11.04, something has been subconsciously bothering me about windows. I finally figured out that it was because my window borders did not fit with the theme. Now, I realize that I can't change the borders, regardless of which theme I select. Screenshots of a window with all four themes selected are attached.

How do I get the window borders to change with the theme, or at least make them fit with the theme I am currently using (Ambiance?)

---

### Post by Rasa1111 on 2011-10-29
install gnome tweak tool.
```
sudo apt-get install gnome-tweak-tool
```Then you can change/mix/match themes.

once installed, its called "advanced settings".

---

### Post by alquery on 2011-10-29
> **Rasa1111 said:**
> install gnome tweak tool.
```
sudo apt-get install gnome-tweak-tool
```Then you can change/mix/match themes.

once installed, its called "advanced settings".

I can't seem to find how to do that. On a related note, "Shell Extensions" window is empty. Is this normal?

---

### Post by Rasa1111 on 2011-10-29
Normal for a fresh, default install, yeah. 

Do you have gnome shell installed yet?
The extensions are just used for gnome shell.
So if you want to get all the extensions for gnome shell.
This is what you want to do.. [http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html](http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html)

If you can't install tweak tool through a terminal..
just open the ubuntu software center, and search for "advanced settings"
When it shows in the list, just click "install".

Click the "Theme" selection on the left side once installed. 
[ATTACH]205824[/ATTACH]
window theme, gtk theme, shell theme, etc. 
Hope it helps.
good luck

---

### Post by alquery on 2011-10-29
> **Rasa1111 said:**
> Normal for a fresh, default install, yeah. 

Do you have gnome shell installed yet?
The extensions are just used for gnome shell.
So if you want to get all the extensions for gnome shell.
This is what you want to do.. [http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html](http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html)

No, I'm not using gnome-shell, just unity.

> **Rasa1111 said:**
> 
Click the "Theme" selection on the left side once installed. 
[ATTACH]205824[/ATTACH]
window theme, gtk theme, shell theme, etc. 
Hope it helps.
good luck

I'm not sure what I'm supposed to do now. Nothing I do changes anything, except for changing the icon theme and the gtk+ theme, both of which are not my intention. I don't even have the theme that matches my window borders anymore, so I change the gtk+ theme to use that. The shell theme option is grayed out, but I'm pretty sure that that's because I'm not using gnome-shell. In addition to my previous problem, I now find that I can't change any of the variables on the Windows section. Any ideas?

---

### Post by vasa1 on 2011-10-29
> **alquery said:**
> ... Any ideas?

If ideas = unsolicited advice then ...

Take it step-by-step, make sure you've preserved the originals, try to record the changes you make.

*Slightly off-topic*: I'm not bothered so much about the borders of windows since I use my main apps maximized. It's the internal content of the windows that was the challenge for me. Thanks to hints dropped here and there, I've managed to get the internal content, for the larger part, appear the way I like.

By the way, you could look at this:
[http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html](http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html)
There's a bit about "frames". I'm not sure that that's the same as "borders". In any case, it's a good read.

---

### Post by alquery on 2011-11-01
> **vasa1 said:**
> 
By the way, you could look at this:
[http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html](http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html)
There's a bit about "frames". I'm not sure that that's the same as "borders". In any case, it's a good read.


Thanks, but this isn't really what I'm talking about - I want the theme to applied to the titlebar every time I change themes using the GUI, and I don't think that using the XML config files is going to help fix the problem. It's strange, no one else seems to be seeing this. I can't believe I'm the only one.

> **vasa1 said:**
> If ideas = unsolicited advice then ...

Take it step-by-step, make sure you've preserved the originals, try to record the changes you make.


I'm a bit confused by this statement: are you saying I should do this when I'm trying to fix the problem, or whenever I make future changes to my configuration, or both?

---

### Post by cbowman57 on 2011-11-01
With gnome shell you have to restart the shell before the changes take effect, I can't remember if Unity is the same or not.

---

### Post by veroslav on 2011-11-02
I had the same problem and managed to solve it by installing the latest Ubuntu Tweak (Alpha) and setting the theme from there.

It worked perfectly.

Regards,
Veroslav

---

### Post by alquery on 2011-11-02
> **cbowman57 said:**
> With gnome shell you have to restart the shell before the changes take effect, I can't remember if Unity is the same or not.

](*,)

You're right, all I had to do is restart my computer, man I feel stupid now... If anyone is wondering, I had changed the 'Window theme' and the 'GTK+ theme to the same thing, and it looks fine.

---

### Post by Script Warlock on 2011-11-02
> **alquery said:**
> ](*,)

You're right, all I had to do is restart my computer, man I feel stupid now... If anyone is wondering, I had changed the 'Window theme' and the 'GTK+ theme to the same thing, and it looks fine. geez let me help you ](*,)](*,)](*,)

---

### Post by cbowman57 on 2011-11-02
It's going to take us all some time to get up to speed. :)

---

### Post by Rasa1111 on 2011-11-02
> **alquery said:**
> ](*,)

You're right, all I had to do is restart my computer, man I feel stupid now... If anyone is wondering, I had changed the 'Window theme' and the 'GTK+ theme to the same thing, and it looks fine.

lol, glad you got it.

next time..
a simple log out/log in will do it.
No need for fresh reboot.

---

### Post by cbowman57 on 2011-11-02
Or a simple alt+f2 r enter

Never mind, I was thinking gnome shell.

---

### Post by Rasa1111 on 2011-11-02
> **cbowman57 said:**
> Or a simple alt+f2 r enter

that's in gnome shell though.
not unity, if im correct?

---

### Post by cbowman57 on 2011-11-02
> **Rasa1111 said:**
> that's in gnome shell though.
not unity, if im correct?

Doh!  You're right. :)

---

