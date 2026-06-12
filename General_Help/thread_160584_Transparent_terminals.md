---
title: "Transparent terminals"
date: 2006-04-15
forum: General Help
---

### Post by PriceChild on 2006-04-15
Hey, i saw [https://wiki.ubuntu.com/TransparentTerminals](https://wiki.ubuntu.com/TransparentTerminals) and thought that the it looked pretty cool so gave it a try.

However, it won't work :( I've done it method 2 and got all the way through, but nothing happens when i launch the script.

Please help, Pricey

---

### Post by sands on 2006-04-15
try this
>Open terminal
>go to Edit menu->profiles
>Select a profile an hit edit button
>Then go to effects tab and enable transparent background

---

### Post by localzuk on 2006-04-15
What graphics card do  you have?

---

### Post by localzuk on 2006-04-15
Also, have you taken a look at the info here: [http://www.ubuntuforums.org/showthread.php?t=81727](http://www.ubuntuforums.org/showthread.php?t=81727)

---

### Post by sands on 2006-04-15
I've done nothing as in the tutorial..
But I'm having transparency..
Here is my screenshot
[URL=http://esms.tk][IMG]http://img149.imageshack.us/img149/170/screenshot7lx.png[/IMG]

---

### Post by Ramses de Norre on 2006-04-15
That's just setting the background to follow your wallpaper. I guess the topic starter wants some more advanced transparency.

---

### Post by sands on 2006-04-15
What do u mean by advanced transparency..
I did'nt got u..

---

### Post by Ramses de Norre on 2006-04-15
If you place another window behind your terminal and wallpaper, you'll still see your wallpaper as terminal background. With composite you'll see the window behind the terminal.

---

### Post by sands on 2006-04-15
Yeah..Its advanced..
I must giv a try.

---

### Post by PriceChild on 2006-04-15
That's exactly what i want Ramses.

localzuk, that's the same tutorial, just on the forums instead of the wiki.

The script doesn't work, but i never get any error messages at all.

Anyone any ideas before i undo it all?

Pricey

---

### Post by Ramses de Norre on 2006-04-15
Don't you get an extra icon in your notification area? When you click on it (or double click or whatever) you'd see the terminal.

---

### Post by PriceChild on 2006-04-15
Nope, don't even get the notification :(

---

### Post by Ramses de Norre on 2006-04-15
Can you run it without the transset line? So only alltray is executed.

EDIT: maybe dumb question but did you replace [geometry] and [opacity] with correct values?

---

### Post by PriceChild on 2006-04-15
No difference without the transet line.

And yes, i have changed the values :P

```
#!/bin/bash
a=`ps -aef | grep -i xcompmgr | awk ' {if ($8 == "xcompmgr"){printf "2"}} '`
if  [[ $a = "" ]]
then
        exit
else
#!/bin/bash
alltray -x -st -g +377+329 "gnome-terminal --window-with-profile=tterm" & sleep 1
transset-df -n "tterm (AllTray)"  0.7

fi
```

---

### Post by Ramses de Norre on 2006-04-15
Can you just run ```
alltray -x -st -g +377+329 "gnome-terminal --window-with-profile=tterm" & sleep 1
``` in terminal and see if that works?

---

### Post by PriceChild on 2006-04-15
uuu... now we're getting somewhere! That worked.

---

### Post by Ramses de Norre on 2006-04-15
Then try closing alltray and run the command again adding ```
&& transset-df -n "tterm (AllTray)"  0.7
``` behind it.
By the way, is xcompmgr running? What's the output of ```
ps -aef|grep -i xcompmgr
```

---

### Post by PriceChild on 2006-04-15
```
alltray -x -st -g +377+329 "gnome-terminal --window-with-profile=tterm" & sleep 1 && transset-df -n "tterm (AllTray)"  0.7
```
Does exactly the same.

&

```
1000     11265 11251  0 18:02 pts/0    00:00:00 grep -i xcompmgr
```
Is produced

---

### Post by Ramses de Norre on 2006-04-15
I think there is a bug in the second line of the script, a is set to the same value whether the process is running or not..
So I'd advice to skip the xcompmgr determining section (I don't now awk good enough to correct it).
Use ```
#!/bin/bash
alltray -x -st -g +377+329 "gnome-terminal --window-with-profile=tterm" & sleep 1
transset-df -n "tterm (AllTray)"  0.7
``` as script.

---

### Post by PriceChild on 2006-04-15
That only creates an opaque terminal with no borders or menu etc. :S

---

### Post by Ramses de Norre on 2006-04-15
The lines that were omitted were only useful to determine whether compiz is running or not, if positive the rest of the script is executed, if negative the script is aborted.
So if compiz is running and you run that script you should get the right result.. otherwise you've done something wrong somewhere else..

---

### Post by localzuk on 2006-04-15
[QUOTE=PriceChild]
localzuk, that's the same tutorial, just on the forums instead of the wiki.
[/QUOTE]

I know, but there is a lot of discussion there also... Have you read through that?

---

### Post by Ramses de Norre on 2006-04-15
```
In the second method, if the terminal occasionally pops up in the wrong position or does not have true transparency, try setting a value of 2 or 3 after the "sleep" command in the scripts in step 9. 
```

---

### Post by PriceChild on 2006-04-15
> By [nchase]("http://www.ubuntuforums.org/member.php?u=55860")
Other apps lauched on startup:
```
xcompmgr -fF -I-.002 -O-.003 -D3 -cC -t-5 -l-6 -r5 
[LEFT] order 41[/LEFT]
 
```    
I haven't done anything like this....

UPDATE

Ok, i simply started xcompmgr by just typing it into a terminal. Suddenly my windows would go over my panels, my gedit went transparent!!!!!!!!!!!!! but not my terminals :( Oh and my system went very unstable and wouldn't do much, requiring a ctrl+alt+backspace

I think it's just going to be best if i leave it alone and uninstall everything :)

---

