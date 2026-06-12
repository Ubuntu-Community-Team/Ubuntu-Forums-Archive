---
title: "Terminal size.."
date: 2005-02-14
forum: General Help
---

### Post by Jaivaz on 2005-02-14
I'm sorry but I couldn't find a forum to put this in so..I guessed this one. Sorry if it's in the wrong one.

I got ADOM to work, it's a game and I need to run it in the terminal..which works just fine, but it needs the window to be at least "25 x 77" and..It's apparently too small, I can do without fixing this but...I don't wanna. 

So, does anyone know of a way of making the terminal window apear bigger by default?

---

### Post by scoon on 2005-02-14
Hey there, 

If you are using gnome-terminal, you can set up the size of it in its preferences. 

scoon

---

### Post by SlugO on 2006-01-13
Actually, you can't.

Gnome-terminal's default size can only be changed by hacking it :-|

I'm trying to set up a launcher that resizes the terminal and then starts ADOM in it: ```
gnome-terminal --geometry=80x25 && /home/janne/.adom/adom
``` The problem is that it starts ADOM in the old "unresized" terminal (so ADOM won't start) :P

Any idea how I could get it working?

P.S.
Using Ubuntu 5.10 ;)

---

### Post by scoon on 2006-01-13
[QUOTE=SlugO]Actually, you can't.

Gnome-terminal's default size can only be changed by hacking it :-|

I'm trying to set up a launcher that resizes the terminal and then starts ADOM in it: ```
gnome-terminal --geometry=80x25 && /home/janne/.adom/adom
``` The problem is that it starts ADOM in the old "unresized" terminal (so ADOM won't start) :P

Any idea how I could get it working?[/QUOTE]

Hey there, 

gnome-terminal --help 

will give you a bunch of switches that you can use. 

the -x switch is prolly the one you are most interested in.

regards, 
scoon

---

### Post by 23meg on 2006-01-13
[QUOTE=SlugO]Actually, you can't.

Gnome-terminal's default size can only be changed by hacking it :-|
[/QUOTE]
Wrong; after setting your preferred size in your profile you can use the --command option followed by the command you want to run in the terminal. If you don't want to use your default profile, you can set one up with the preferred size and invoke it with the --window-with-profile option.

---

### Post by SlugO on 2006-01-13
Okay, I changed the command to```
gnome-terminal --geometry=80x25 -x /home/janne/.adom/adom
```But now I get this error message:```
/*
 * ADOM session aborted due to an external problem.
 * Problem Description: ADOM is either already running or the file
                        '/home/janne/.adom.data/.adom.prc' was not removed.
                        Unable to start.
 */

```
Any idea why it doesn't like to be started with -x? :???:

---

### Post by Kanji_Man on 2007-10-26
I am sorry to dust off such an old thread, however I continually come accross this when performing google searches to find out how to change the default terminal size.

The gnome-terminal uses a termcap file for its basic settings. To change these:
```
sudo gedit /usr/share/vte/termcap/xterm
```

Now look for a line about 1/3 of the way down the file that looks like this:
```
	:co#80:it#8:li#24:\
```

To change the number of columns, change the co# number, in this case 80.
To change the number of rows, change the li# number, in this case 24.
So as an example if you want a terminal window of 132x25:
```
	:co#132:it#8:li#25:\
```

You must exit all gnome-terminal proceses before the changes take effect.

---

### Post by s.victor on 2007-11-08
> **Kanji_Man said:**
> I am sorry to dust off such an old thread, however I continually come accross this when performing google searches to find out how to change the default terminal size.

The gnome-terminal uses a termcap file for its basic settings. To change these:
```
sudo gedit /usr/share/vte/termcap/xterm
```

Now look for a line about 1/3 of the way down the file that looks like this:
```
	:co#80:it#8:li#24:\
```

To change the number of columns, change the co# number, in this case 80.
To change the number of rows, change the li# number, in this case 24.
So as an example if you want a terminal window of 132x25:
```
	:co#132:it#8:li#25:\
```

You must exit all gnome-terminal proceses before the changes take effect.

Thank you! You've been very helpful.

---

### Post by Excalibre on 2007-11-17
This changed my default terminal size but for whatever reason my launcher for adom ('gnome-terminal -e adom') still only works about one time in ten. That's the weird thing - sometimes the game runs fine, but usually it gives the same complaint about the screen size. It reliably works fine when I open a terminal and run it from the command line, though.

---

### Post by poojac20 on 2008-05-27
This should fare much higher in google results. 

sudo gedit /usr/share/vte/termcap/xterm
:co#80:it#8:li#24:

!

---

