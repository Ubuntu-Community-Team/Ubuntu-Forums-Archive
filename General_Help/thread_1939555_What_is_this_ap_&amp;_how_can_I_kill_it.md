---
title: "What is this ap &amp; how can I kill it?"
date: 2012-03-11
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2012-03-11
I'm trying to use fslint to get rid of some duplicates and I get an ap I don't recognise popping up at random very frequently and killing my trackball buttons. I can still move the pointer but there is no response. The only way I can get the system to notice me is to cntrl-alt-T for a terminal. But there isn't a whole lot I can do with the terminal. If I knew what the process was I could kill it. As it is the only thing I've been able to do to get my system back is &quot;killall Xorg&quot; and relog. I can't do a screenshot but I can describe it in the hope someone will recognise it and know what the name of the process is so I can at least killall it.  It looks to me like a file browser but not like any I use. It pops apropos of nothing with a title bar saying &quot;Blank page&quot;. The next panel has, from left to right: a back (left) arrow, &quot;Back&quot;, a downward pointing arrowhead of the sort usually indicating a dropdown menu,a forward (right) arrow, another dropdown menu arrowhead, a red stop icon, a reload tailchasing arrow, and an empty text field. Next comes tab panel with two tabs, the first being &quot;Blank page&quot;, the second being some directory. Below that is the message in black on yellow &quot;Do you want to recover the previous browser windows and tabs?&quot;, followed to the right by a &quot;Don't recover&quot; button and then a &quot;Recover session&quot; button. Below that panel is empty white space. It looks more like caja or old nautilus than anything else I am familiar with but neither &quot;killall nautilus&quot; or &quot;killall caja&quot; will kill it.   If anyone has a suggestion I'd appreciate it.    ps added by edit: If anyone knows why my quote marks aren't displaying correctly in this post please enlighten me. Thanks.  pps, ditto: Because I have episodic attacks of acute dumbass syndrome I forgot to say that problem is when I am using 32 bit Oneiric with Mate on an IBM board with a Pent.D and 2 gigs of RAM.

---

### Post by ankman on 2012-03-11
> **Dreamer Fithp Apprentice said:**
> I'm trying to use fslint to get rid of some duplicates and I get an ap I don't recognise popping up at random very frequently and killing my trackball buttons. I can still move the pointer but there is no response. The only way I can get the system to notice me is to cntrl-alt-T for a terminal. But there isn't a whole lot I can do with the terminal. If I knew what the process was I could kill it. As it is the only thing I've been able to do to get my system back is &quot;killall Xorg&quot; and relog. [...]

You can install "top" or "htop". Just typing this and hit enter shows you a list of processes. "Nasty" processes which might consume a lot of the CPU time or memory are usually listed on top. If you are owner of the process (or are root) you can terminate it.

Hit "k" <enter> and the process-ID (most left column) and <enter> again. The next thing is how you want to terminate it. The default is SIGTERM (15) that the process will be asked to terminate itself. Just hit <enter> again. That often works.

Some processes might not respond to that. Then you repeat it (k <enter> process-ID) and this time enter "9" before <enter>. "9" is for SIGKILL. That should terminate the process anyway. But it's a "brutal kill" so the process doesn't get the chance to clean up behind itself, which might or might not lead to other problems.

Without "top" you can also type "ps" and <enter> which is installed in any case already. That lists (your) processes with process-ID on the left. You can then type

kill process-ID

where "process-ID" is the number on the left.

---

### Post by Dreamer Fithp Apprentice on 2012-03-12
Ah! Thank you much. I tried top already but I only knew how to kill by process name. This is a great information about the process number. I'll need to reboot on a different partition before I can try replicating the error to try these techniques but I wanted to say thanks now.    In at least one case I found that the entry shown under the "command column" with top was not the full process name but either a truncated version of it that just happened to be truncated a point that looked deceptively natural so to speak by coincidence or maybe some sort of short name. Anyway I couldn't kill whatever it was (I forget now) with that name but I found the full name with system monitor and was able to kill it. I couldn't use that with my more recent problem because I didn't know how to get system monitor up from the command line with my trackball hors de combat.  I'll report back as soon as I can get on the other system and try this, and hopefully mark this solved.  Thanks.

---

### Post by Dreamer Fithp Apprentice on 2012-03-12
Well, I've made some progress. First of all, I was able to reproduce the problem on the system I'm on now, which is quite similar to the partition I was on when I had the problem. It seems that sometime when I select a file in fslint instead of merely being selected it causes it to be opened in some other ap, not necessarily an ap I would normally use to open that kind of file. This last time it was firefox opening a jpg. Then when I cntrl-alt-T and "killall firefox" and "killall firefox-bin" in the terminal the opened jpg disappeared but up popped the mystery ap that either killed my trackball buttons or popped as a side consequence of whatever did kill my trackball buttons. I was able to get a tiny amount of response out of the ap using alt with letter keys corresponding to the underlined letters in menu titles. Specifically trying to open the help menu this way (I was hoping to get an "about") did NOT open the menu but did elicit an error message from the mystery ap referring to itself as a web browser, but with maddening modesty failing to give its name. I've only got 3 installed asfaik so I cntrl-alt-T again to get a new terminal because once I used one of these terminals to open another ap I can't get back to that terminal even though it is still open. When I had enough open terminals to clutter the bottom panel I'd just open a new one and killall all of them including the one I used to killall them. Then I can open another. Anyway, I used a new terminal to killall Xorg and relogged in. Then I opened each of my installed web browsers. It was definitely epiphany, the gnome web browser. So the first part of my question is now answered. The mystery ap is epiphany. I'm still not sure what process controlled it because none of the ones I saw in top or htop seemed obviously connected and none of the ones I tried killall-ing did the trick. But anyway, for now I just uninstalled it. If I want to mess with it later, at least I'll have an idea where to start diagnosing any problems that occur. If you think about there are several weird things here:
1-why should fslint cause a file to be opened with another application just because I select it? That might be a hardware thing. My trackball is old and getting flaky and seems to issue a double click when I only click it sometimes. 
2-why should the ap that opens the file refuse to close normally so that I have to kill it from the command line? Durned if I know.
3-Why should killing that ap bring up Epiphany?
4-Why does Epiphany kill my trackball buttons?

Anyway I include these observations in case anybody with a similar problem comes to this thread from a search and might find a clue in them. As for my immediate problem, I'm hoping uninstalling Epiphany will have solved it, but since it was erratic anyway, I won't mark this solved until I've given it a good workout.

Thanks for the tips, Ankman.

---

### Post by Dreamer Fithp Apprentice on 2012-03-12
Nope, I was too optimistic. But I do now have a clearer handle on the pattern of the problem. What happens is that any time I open a file from it's listing in the output of fslint (which in my case often happens accidentally when my flaky trackball sends a double click signal when I try to single click to select, but that would seem beside the point) the file is opened normally but my trackball buttons are disabled from that point on until I finally have to relog by entering "sudo killall Xorg" in a terminal obtained with cntrl-alt-T. But in the meantime I can use the terminal to kill the ap that opened the file but the file is immediately opened by some other ap. When I kill that one it is opened by some other ap. For instance, it it is a text file it will open intially in Pluma, the next time in Cream, the next time in some other editor, etc, until I run out of editors and it continues to open in firefox after that. With a movie it opens in vlc for instance and when I "killall vlc" that disappears and it is promptly opened in totem. The series ends when I get to an ap I can't figure out how to kill. But the trackball buttons remain disabled until I kill Xorg and relog. So the problem seems to be a bug in fslint. As a practical matter, I need to get a new trackball and be very careful not to open files from fslint. I guess I need to report the bug when I figure out where to. Any insights will be read with interest but I don't really expect to solve this any more than I have.

---

