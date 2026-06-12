---
title: "Noobie Tryin to Keymap busted key"
date: 2011-06-26
forum: General Help
---

### Post by (LDSG) J-A on 2011-06-26
Hi all, Im pretty new to linux, running Ubuntu 11 on my MSI wind netbook

So the period key on my keyboard broke sometime ago and hence its really rather difficult to end a sentence

How can I map the menu key (the one that brings up the right click features and is located next to the right alt key) to the period key

Any help would be greatly appreciated, 

I'm not too savy on terminal commands

I did try one program called xmod or something like that but it couldn't detect the new key I wanted to map too

Thanks much

---

### Post by gmargo on 2011-06-26
This is relatively easy to do with **xmodmap(1)** and **xev(1)**.

On my netbook, the menu key is just to the right of the right-alt, and just below the period.  xev shows a keycode of 135 mapped to keysym "Menu".

Put the following text in a file:
```

keycode 135 = period greater period greater

```Now run the command
```

xmodmap filename-with-keycode-from-above

```Did that work for you?  
If not, perhaps your menu key has a different keycode; use **xev(1)** to find the correct one.

Hope.to.see.periods.from.you!

---

### Post by (LDSG) J-A on 2011-06-27
Yahoo!!!!  It Worked!  Thanks to gmargo.  Now I can end sentences.  


[COLOR="Gray"]Just for clarification for any other noobs who might run across this in the future.  Here is what I did

Use Text Editor to make a file with the command that gmargo provided, nothing more or less should be in the file

Put it where ever but you need to navigate to it so I put it in the temp folder.  I named the file "key135"

In Terminal:
cd /tmp
xmodmap key135

Then it worked like magic! 

If you need to know the keycode number or names of functions you can use the following

cd /usr/bin
xmodmap -pke

Of course, the CD navigation and using Sudo or whatever might not be needed.  I don't know cause I'm a noob but with this and with the help gmargo gave me I got it to work.[/COLOR]

---

### Post by (LDSG) J-A on 2011-06-28
To my dismay - my original excitment is gone

My work didnt save after rebooting

ne ideas how to make it permenant?

---

### Post by gmargo on 2011-06-28
What **xmodmap(1)** does is change the X server's in-memory keycode translation table, so any changes will be lost when you log out and back in. To make it "permanent" really just means you have to arrange for that xmodmap command to run when you log in.  

It is traditional to save that file in $HOME/.Xmodmap or $HOME/.xmodmaprc.  On some desktop systems, that file will be detected and used automagically by the startup scripts.  But I'm not sure if that's the case on 11.04 Natty.  What desktop are you using?  The default Unity desktop?

There's also another issue.  If you desire to use the text console, then the menu key will not produce periods (since xmodmap just changes the X server).  I believe we can tackle that by adjusting the kernel's scancode-to-keycode translation table (which does not seem to carry over to the X server).

---

### Post by gmargo on 2011-06-28
I've tested this under 11.04 Natty with the Unity desktop:  
Create that file with the name **$HOME/.Xmodmap**
Log out/in.

Interesting sidenote:  I had multiple files in my $HOME directory that had "xmodmap" in the name (capital and lower case); and I got a pop-up asking which ones to load.  With only a single matching file, it is loaded silently.

---

