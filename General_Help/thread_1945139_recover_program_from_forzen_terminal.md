---
title: "recover program from forzen terminal"
date: 2012-03-22
forum: General Help
---

### Post by alphaamanitin on 2012-03-22
Hey Guys,

For all those who don't know I am a molecular biologist.  Anyway, some of the programs I run show you progress in the terminal, then when they finished dump the output to a text file.  Well, my terminal froze, but I know from experience if I kill the terminal the programs will continue to run.  How do I get back to the status updates?  I tried moving the program to the front, no luck.  I can see the process is still running, and the job number, but I cannot get it back into a terminal.

AlphaA

---

### Post by papibe on 2012-03-22
> **alphaamanitin said:**
> I tried moving the program to the front, no luck.  I can see the process is still running, and the job number, but I cannot get it back into a terminal.
Hi alphaamanitin.

What command do you use to see the jobs?
What command have you tried to bring the program to the front?
Could you post the results of those commands?

Regards.

---

### Post by alphaamanitin on 2012-03-22
Just found this thread:

[http://ubuntuforums.org/showthread.php?t=1142399](http://ubuntuforums.org/showthread.php?t=1142399)

Apparently, nothing will bring it back into the current terminal session, plus I think the computer is crashing anyway...  At least, it seems to be slowing down and not responding to mouse movements for 10 minutes or more.

AlphaA

---

### Post by imachavel on 2012-03-22
computer is crashing? Man with windows I would assume it's a virus. But since it's not, wonder wtf is going on. Hardware issue? I wish I knew some ways to trouble shoot not great at trouble shooting linux. If it was windows I'd think it's possible it may be a memory paging error :confused:

---

### Post by jerrrys on 2012-03-22
> **alphaamanitin said:**
> Just found this thread:

[http://ubuntuforums.org/showthread.php?t=1142399](http://ubuntuforums.org/showthread.php?t=1142399)

Apparently, nothing will bring it back into the current terminal session, plus I think the computer is crashing anyway...  At least, it seems to be slowing down and not responding to mouse movements for 10 minutes or more.

Are you using the desktop terminal or tty?  Asking because just sounds like tty may work better for you.

**Switch to Console mode**

 The usual method of command-line access in Ubuntu is to start a terminal (see [the section called “Starting the Terminal”]("https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/linux-basics.html#starting-a-terminal") above) , however sometimes it is useful to switch to the real console:
 
[LIST]
[*]Use the **Ctrl**+**Alt**+**F1**     shortcut keys to switch to the first console.
[*]To switch back to Desktop mode, use the **Ctrl**+**Alt**+**F7**     shortcut keys.
[/LIST]
                                             There are six consoles                 available. Each one is accessible with the shortcut keys                 **Ctrl**+**Alt**+**F1** to                 **Ctrl**+**Alt**+**F6**.                  
As for your slow down, check to see if something is eating up memory.

---

### Post by alphaamanitin on 2012-03-22
> **jerrrys said:**
> Are you using the desktop terminal or tty?  Asking because just sounds like tty may work better for you.

**Switch to Console mode**

 The usual method of command-line access in Ubuntu is to start a terminal (see [the section called “Starting the Terminal”]("https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/linux-basics.html#starting-a-terminal") above) , however sometimes it is useful to switch to the real console:
 
[LIST]
[*]Use the **Ctrl**+**Alt**+**F1**     shortcut keys to switch to the first console.
[*]To switch back to Desktop mode, use the **Ctrl**+**Alt**+**F7**     shortcut keys.
[/LIST]
                                             There are six consoles                 available. Each one is accessible with the shortcut keys                 **Ctrl**+**Alt**+**F1** to                 **Ctrl**+**Alt**+**F6**.                  
[COLOR=Red]As for your slow down, check to see if something is eating up memory.[/COLOR]

lol, oh I know what is eating up memory.  I am running a HUGE analysis of dna sequence alignments.  I am not at work anymore, but I will give your suggestions a try tomorrow if the computer hasn't just completely crashed.

Thanks.

AlphaA

---

### Post by VCoolio on 2012-03-23
Run your stuff inside tmux. That way if your terminal crashes or even if you logout and back in, you can reattach to your tmux session and continue reading output.

---

### Post by alphaamanitin on 2012-03-23
> **VCoolio said:**
> Run your stuff inside tmux. That way if your terminal crashes or even if you logout and back in, you can reattach to your tmux session and continue reading output.


Thanks!  I'll try that next time.  Doesn't matter now though as the computer did crash overnight.  Not sure if it got too hot or ran it out of memory or something, but it went down.

Should I make the thread as solved or something?

AlphaA

---

### Post by VCoolio on 2012-03-23
> **alphaamanitin said:**
> Should I make the thread as solved or something?



If your question is answered or problem solved, yeah. [Howto mark as solved](http://ubuntuforums.org/showpost.php?p=4527051&postcount=6).

---

### Post by drmrgd on 2012-03-23
What are the specs of your computer, and what NGS platform are you working with?  It sounds to me like you need to be doing that analysis on a dedicated server rather than your workstation.  If you're just running some small analysis on one of the personal genome platforms (MiSeq, Ion Torrent, etc.), you can get away with running on a workstation with a Core i7 and as little as 3 or 4 gigs of RAM (even if aligning to the whole human genome).  If you're trying to run with something like HiSeq data, you'll brick your workstation almost every time I would guess.

---

### Post by alphaamanitin on 2012-03-23
> **VCoolio said:**
> If your question is answered or problem solved, yeah. [Howto mark as solved]("http://ubuntuforums.org/showpost.php?p=4527051&postcount=6").


I was more asking, does every one think this is "solved?"  I don't know if I would say the problem is solved, and I wouldn't want to waste peoples time trying to solve this same issue coming here thinking it is solved.

Yes, I was unsure if the computer would run this alignment (5 gene, ~35000 bp).  I have ran similar things before, but not quite this many taxa (~400).  Anyway, time to use some free servers.

Thanks guys,

AlphaA

---

### Post by drmrgd on 2012-03-23
> **alphaamanitin said:**
> I was more asking, does every one think this is "solved?"  I don't know if I would say the problem is solved, and I wouldn't want to waste peoples time trying to solve this same issue coming here thinking it is solved.

Yes, I was unsure if the computer would run this alignment (5 gene, ~35000 bp).  I have ran similar things before, but not quite this many taxa (~400).  Anyway, time to use some free servers.

Thanks guys,

AlphaA

Hmmm...yeah, that could potentially be too big of a load for your workstation (without knowing your specs and just what kind of analysis you're running).  I always feel better going with a workhorse server to do the job anyway - that is if I can get my hands on one.  There's not much more disappointing than coming in the next morning to find your analysis crashed and you have to start it over!

---

