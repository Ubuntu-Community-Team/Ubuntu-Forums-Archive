---
title: "Change BASH shortcut keys"
date: 2010-02-13
forum: General Help
---

### Post by LordKelvan on 2010-02-13
Hi:

I've currently mapped Ctrl-C/V to copy/paste in Gnome-Terminal because I come from a Windows background.  This causes an obvious problem because Ctrl-C is also used to send the SIGINT signal to the currently running process in the terminal.  Is there a way for me to use a different shortcut to send the SIGINT signal?  If there currently is no way, which component would I have to modify for this functionality?

Cheers,
LK

---

### Post by jwbrase on 2010-02-13
Ctrl-C does the same thing on the Windows console as it does on the Linux console, it sends SIGINT (or whatever the equivalent signal is in Windows) to the running program. The difference is that you've probably never tried Ctrl-C in a Windows terminal. The default settings for gnome-terminal for copy and paste are shift-ctrl-C and shift-ctrl-V. Outside of a terminal, Ctrl-C and V will copy and paste just like they do on Windows.

---

### Post by Pelgar on 2010-02-13
I would really like an answer to LordKelvan's question too. I realize as I imagine LoardKelvan does that DOS uses ctrl-c for break too. I'm very seldom in a DOS console so it's not much of a problem there. In Ubuntu the Terminal seems to get some serious use and I'm having a really hard time training my fingers, they think ctrl-c is copy!
I'd like to know if it would be difficult to swap the functionality of ctrl-c and ctrl-shift-c. I very seldom need a break function but quite often need to copy text.

---

### Post by jwbrase on 2010-02-13
As far as I know it's not possible, at least, not without mucking around with bash's source code.

Then again, while I've picked up using the command line alot since switching to Ubuntu, I don't think it's really as necessary as some people think. There are very few things I can think of that can't be done through the GUI.

---

### Post by falconindy on 2010-02-13
Cold truth: You're not on Windows anymore. Evolve and adapt!
Easy solution: Use Gnome-Terminal's default of ctrl-shift-{c,v}.

As with any program in Linux, you also have the ability to highlight text and paste it using mouse button 3, which is the middle mouse button if you have it, or both left and right buttons at the same time.

---

### Post by jwbrase on 2010-02-13
> **falconindy said:**
> Cold truth: You're not on Windows anymore. Evolve and adapt!

True enough, except for the fact that the problem here is that in this case Linux is behaving exactly like Windows...

---

### Post by falconindy on 2010-02-13
> **jwbrase said:**
> True enough, except for the fact that the problem here is that in this case Linux is behaving exactly like Windows...
Quite right, but my implication (or suggestion) was to use the Gnome-Terminal standard rather than trying to duplicate Windows behavior.

---

### Post by LordKelvan on 2010-02-14
Well, I work in both environments, so you can see why muscle-memory might be an issue.  While it is true that on a Windows console Ctrl-C also terminates programs, you can't actually copy/paste text with Ctrl-C/Ctrl-V (I'm not saying this is an upside, just saying why people have never encountered the issue on Windows). 

Thanks for the replies.  I had a sinking suspicion that this would not be possible (without modifying bash source code).

---

### Post by Pelgar on 2010-02-14
According to a post at [http://www.matt-helps.com/ubuntu-ctrl-c-no-longer-works-in-terminal ]("http://www.matt-helps.com/ubuntu-ctrl-c-no-longer-works-in-terminal")You could actually use ctrl-c and ctrl-v for copy and paste in the terminal prior to Ubuntu 9.04. It seems that if you set ctrl-c to copy in the setup the terminal would copy text if there was text selected or issue the SIGINT signal if no text was selected. 

I am a bit confused about the whole "This is not Windows" issue. Every app I use in Ubuntu, except the Terminal, allows me to use these key combinations for copy and paste!
I'd just like uniformity within Ubuntu. I fully agree with jwbrase it seems to me that forcing ctrl-c = break in Terminal is exactly duplicating Windows behavior.

I have been able to duplicate a little windows behavior in the Terminal. I modified the ~/.bashrc file to where cd.. = cd .. I did this because my fingers still remember cd.. as back one dir. and I got tired of an error every time I used it. If I knew what SIGINT actually did it seems there is a good chance it could be redirected in the .bashrc file as well. Can anyone help with that?

---

### Post by schmidtbag on 2010-02-14
like what was mentioned before, you have to keep in mind that ctrl-c was intended to end programs.  if this is changed to copy, then what if you're running a script and want to end it?  sure theres ctrl-x and ctrl-d but those have different functionalities, and if you want to do ctrl-c for copy, then you'd want ctrl-x for cut, so its not that simple.

ctrl-c and ctrl-x were designed to end programs before they were used as copy and cut.  if you want to use a keyboard to cut and paste in terminal but don't want to memorize the commands, you could either go for a different terminal program, go for a different shell, or try using the menu key on the keyboard and select paste from there, which is a little faster than using the mouse

---

### Post by LordKelvan on 2010-02-15
Pelgar:  
Hmm, I thought I saw a bug report pertaining to this as well.  Good to see I'm not the only one experiencing this.  For me, I actually use Ctrl-C for both purposes.  It was kind of funny, because recently in 9.10 I noticed Ctrl-C wasn't "working" for killing a program, but took some time before I realized I was using the shortcut for 2 different purposes :)  

schmidtbag:
I don't know about "intended" - I thought the point of customization was so I could change the software to adopt to me, rather than the other way around.  And this doesn't seem to be a difficult change - when you receive Ctrl-C, check if text has been selected, and based on that answer you can either copy text or send SIGINT.  The old implementation seemed like the best of both worlds.

---

### Post by Pelgar on 2010-02-17
LordKelvan said:
> Hmm, I thought I saw a bug report pertaining to this as well. Good to see I'm not the only one experiencing this. For me, I actually use Ctrl-C for both purposes. It was kind of funny, because recently in 9.10 I noticed Ctrl-C wasn't "working" for killing a program, but took some time before I realized I was using the shortcut for 2 different purposesI'd really like to know if this functionality was intentionally removed or if, as you say, it's a bug.

Pelgar said:
> I'd like to know if it would be difficult to swap the functionality of ctrl-c and ctrl-shift-cAfter 3+ days of reading Bash scripting tutorials and the Bash Reference Manual, with no luck at all, I accidentally discovered that when you reassign ctrl-c ctrl-shift-c is automatically reassigned to send SIGINT! I know this is not the preferred solution but for me it is an acceptable solution.

---

### Post by llawwehttam on 2010-02-17
Linux is NOT Windows.
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Adapt. Linux is after all superior in every way.......... in my opinion.

---

### Post by Pelgar on 2010-02-17
llawwehttam said:
> Adapt. Linux is after all superior in every way.......... in my opinion.
Adapt to WHAT! Did you even read any of these post???

---

