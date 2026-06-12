---
title: "vim shell and vim file browser plugin"
date: 2009-11-21
forum: General Help
---

### Post by cybo on 2009-11-21
does anyone know if there is a way to get a shell window in vim? i would like to have the capability to see my code and the shell at the same time. something like Kate editor does ([http://en.wikipedia.org/wiki/File:Kate3.png]("http://en.wikipedia.org/wiki/File:Kate3.png")) the only thing i found online was [http://www.wana.at/vimshell/]("http://www.wana.at/vimshell/") and it requires reinstallation of vim (if i understood it correctly). i cannot do it since i use a preinstalled version of vim at work and my university. 

i also don't like the default file browser that comes with vim so i started looking for plugin. i need really basic file browser, something similar to what Kate has ([http://en.wikipedia.org/wiki/File:Kate3.png]("http://en.wikipedia.org/wiki/File:Kate3.png"), it is on the left hand side of the picture). i tried googling it but i couldn't find what i was looking for.

can anyone help me out? any help is appreciated.

---

### Post by DaithiF on 2009-11-21
for the first one, why not split your terminal into 2, have vim in one and a real shell in the other.  You can do this in lots of ways -- screen is one, using terminator would be another.

---

### Post by cybo on 2009-11-21
> **DaithiF said:**
> for the first one, why not split your terminal into 2, have vim in one and a real shell in the other.  You can do this in lots of ways -- screen is one, using terminator would be another.

can you explain in detail what what do you mean by screen and terminator?

---

### Post by DaithiF on 2009-11-22
Here is an introduction to screen: [http://www.kuro5hin.org/story/2004/3/9/16838/14935](http://www.kuro5hin.org/story/2004/3/9/16838/14935)
If you use the command line more than a little then its probably the single most useful utility there is!

---

### Post by cybo on 2009-11-22
i went through screen documentation but was not able to find a way to split a terminal into 2. can you recommend how i should do it? i also tried installing the terminator, but i'm not able to do it, since i don't have admin rights to do it, and the admin won't do it, since machines belong to the university.

---

### Post by marshag63 on 2009-11-22
Perhaps stopping by asking at #vim (irc.freenode.com) could shed some light on the best ways to achieve this.

MarshaG.

---

### Post by DaithiF on 2009-11-22
starting in your terminal, 
step 1, run screen
step 2, screen command to split screen in 2:  Ctrl-a, then S.  the terminal window will divide in 2
step 3, run vim in the current window:  vim somefile
step 4, do something in the bottom window:  Ctrl-a, then Tab to move to the bottom window, then Ctrl-a c to create a new shell session in that window
step 5, move between top + bottom windows with Ctrl-a + tab
step 6, Ctrl-a + X deletes the current window to bring you back to just 1 window

Ctrl-a + n  and Ctrl-a + p are the other important commands, for cycling between your open terminal windows.

---

### Post by cybo on 2009-11-22
DaithiF thanks for the commands. it really helped and what more importantly worked.

---

### Post by cybo on 2009-11-22
> **marshag63 said:**
> Perhaps stopping by asking at #vim (irc.freenode.com) could shed some light on the best ways to achieve this.

MarshaG.

thanks for the tip about vim irc channel. i didn't know one existed.

---

### Post by cybo on 2009-11-23
i have another question. does anyone know if there is a way in screen to switch between the windows that are split with a mouse, instaead of Ctrl-a Tab ?

---

