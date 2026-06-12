---
title: "Terminal"
date: 2011-12-29
forum: General Help
---

### Post by optima4 on 2011-12-29
I fixed a major problem earlier with my networking so I will give this a shot even though I didn't find something in search for it. 

I let a friend of mine input a few commands in Terminal. He wanted to allow it to finish the command by memory once typing one or two letters and hitting 'Tab'. This would allow me to use Terminal faster.

However, instead, upon his leaving, and rebooting my PC, not only does the tab option not function, but now I have a short list of issues. 

Windows do not open over Terminal. No matter what window I click, Terminal is above them always. Even the option to close Terminal hides behind the Terminal window, so I have to move Terminal to find the exit button. 

I cannot copy and paste from, or to, Terminal any longer.

I guess that is my main issues right now. I thought there was one more, except right now it is not obvious to me. My friend is not sure what is going on. Also he can open tabs (like we can open tabs in firefox) in his Terminal. I would like that option, but is not happening.

What is the command?

---

### Post by pretty_whistle on 2011-12-29
As far as the tabbed window in Terminal, here's how-to:

Right click on a clear area inside the terminal window, you'll see "open in tab" as a choice in the menu.

---

### Post by yetiman64 on 2011-12-29
Are you using the same Ubuntu version as your friend (including release number etc) ? 

Just a side note about that question, the terminal in Xubuntu or Lubuntu is not the same program as used in the standard Ubuntu version and may explain some of the differences you are noting.

I just checked in gnome-terminal here and cannot find any option to keep the terminal above other windows etc also cannot get gnome-terminal to stay maximized (in case that was your problem) after shutting it down. This plus the lack of tabs in terminal tend to suggest to me a Release or Version difference between your system and your friends system. To open a tab (gnome-terminal), the keyboard combination is SHIFT+CTRL+T with the terminal window selected (active).

Please let us know what version/release you are using.

---

### Post by optima4 on 2011-12-30
Cool  "Shift+ Ctrl+T"  worked :P


He is using Debian

I am using 11.10 32 bit Lts

on a netbook so I know that is some of my issues.

It makes it difficult because I have 2 monitors, so I have lots of windows open every day, and then when I have Terminal I cant view anything, and forget about having 2 Terminals open sheesh, so that tab is really going to come in handy.

Well, hitting the "tab" key is something I would like to figure out and removing the window over everything. Then like you say having Terminal open to a preset size would be pretty useful. 

I cant right click anything on my Terminal, and I cant copy or paste anything like I used to. 

(Sry if this is not as clear as otherwise it would be, I am pretty exhausted atm)

Another issue I have is when my headphone jack is in use the regular computer speakers still have sound, and also my webcam has no sound when recording. But those are other issues, I am still trying to find answer to.

---

### Post by yetiman64 on 2011-12-30
Ok, it's good you can get a tab. Just noted you may have a problem a bit beyond me with regard to the tab completion **and** the right click menu not working. Note that any of the functions of the right click menu are also on the menu bar and you may need to go to the top of the screen to the global menu to access them in 11.10. This includes new window, new tab and copy and paste functions. Check you have all functions available there as well first.

With regard to copying and pasting the keyboard shortcuts used normally don't work in an xterm based terminal (like gnome-terminal). CTRL+C (copy) and CTRL+V (paste) BECOME SHIFT+CTRL+C (terminal copy) and SHIFT+CTRL+V (terminal paste) respectively.
Some examples of use, highlight some text/code in a normal window to copy it CTRL+C, to paste it into a terminal SHIFT+CTRL+V. Or alternatively to copy in terminal SHIFT+CTRL+C and then paste into a text document CTRL+V. Only use the shift key in the combinations with respect to the terminal itself, not to any copy/paste operation outside of the terminal.

Good luck with the rest, yetiman64

Edit: likely just a typo, but 10.04 was the last LTS (long term support) release and 12.04 is the next LTS release, 11.10 is a normal 18 month release only. Cheers. :-)

---

### Post by chipbuster on 2011-12-30
If you're using 11.10, try selecting the terminal and hitting ALT+SPACE. In Unity and KDE, that opens up a set of windows options which may be your issue. In particular, make sure that "Always on Top" is not enabled.

(The reason I say if is because of what yetiman said: the last LTS was 10.04 and I'm not sure which version you're actually using)

EDIT: Argh, I initially typed ALT+TAB by mistake. Stupid :<

---

### Post by pretty_whistle on 2011-12-30
SHIFT-CTRL-T works for me too.  Now I know of 2 ways I can do that.
:)

---

### Post by yetiman64 on 2011-12-30
> **pretty_whistle said:**
> SHIFT-CTRL-T works for me too.  Now I know of 2 ways I can do that.
:)
I know another one using only a mouse - easystroke and a quick flick of the wrist and that key combo is given to the system. :D  (I can scrawl cat in my handwriting on the desktop and a terminal opens, I scrawl cst across the terminal and a new tab pops up - full control with just a mouse :P) All it takes is to learn the keyboard shortcuts and program the strokes in for them.

---

### Post by optima4 on 2011-12-30
You know you guys are really something else ... You fixed it :P Welll my copy paste which is lovely to have back. 


> **chipbuster said:**
> If you're using 11.10, try selecting the terminal and hitting ALT+TAB. In Unity and KDE, that opens up a set of windows options which may be your issue. In particular, make sure that "Always on Top" is not enabled.

(The reason I say if is because of what yetiman said: the last LTS was 10.04 and I'm not sure which version you're actually using)


Where is the option to deselect "Always on Top"?

I'm using 11.10

oooo, not LTS sorry :KS

---

### Post by chipbuster on 2011-12-30
Wow. I'm stupid.

That was supposed to be **ALT+SPACE, not ALT+TAB.** Sorry about that, I was in the middle of trying to remove Wine, and I was tired as all heck.

---

### Post by ashwin_cse on 2011-12-30
> **optima4 said:**
> 
Where is the option to deselect "Always on Top"?

I'm using 11.10

oooo, not LTS sorry :KS

right click on the title bar and you will see the option checked next to Always on top. Uncheck it and it will behave normally.

---

### Post by optima4 on 2011-12-30
> **chipbuster said:**
> Wow. I'm stupid.

That was supposed to be **ALT+SPACE, not ALT+TAB.** Sorry about that, I was in the middle of trying to remove Wine, and I was tired as all heck.

No, not stupid at all. The only real stupid people are the ones who think they know everything. If you admit there is always something new to learn, then you are smart. :KS 

Also, noted in the following response my Terminal is on a whole new setting now, and tab seems to be working after all with this latest corruption in my desktop. So an update will be coming soon.

> **ashwin_cse said:**
> right click on the title bar and you will see  the option checked next to Always on top. Uncheck it and it will behave  normally.

Well aint that a conundrum, my desktop was restarted to be in shambles  (I just posted a thread on it) and now Terminal isnt automatically  "Always on Top" but if it happens again, I know what to do because I see  the option and while in another mode the issue isnt happening ...OF  COURSE right.

---

### Post by optima4 on 2012-01-01
Ya, Terminal is running like a peach now. Thread Solved and I appreciate all the instructions.

---

