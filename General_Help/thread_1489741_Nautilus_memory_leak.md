---
title: "Nautilus memory leak"
date: 2010-05-21
forum: General Help
---

### Post by afrodeity on 2010-05-21
[http://paste.ubuntu.com/437412/](http://paste.ubuntu.com/437412/)

This is the valgrind debug log, showing memory leak with nautilus.

gksudo nautilus does nothing. nautilus crashes whenver I click on a folder.

---

### Post by glinsvad on 2010-05-26
Yes I'm seeing serious memory leaks in Nautilus on Karmic as well. For me, browsing is normal until the memory is used up and the swap is full.

Steps to reproduce:

[LIST=1]
[*]Install debug packages
```
sudo apt-get install --no-install-recommends valgrind gnome-dbg libc6-dbg nautilus-open-terminal
```
[*]Kill Nautilus
```
nautilus -q
```
[*]Debug Nautilus through Valgrind
```
valgrind --tool=memcheck --leak-check=yes --num-callers=20 nautilus
```
[*]Go to File menu and click Open in Terminal
[INDENT]*(This causes a substantial leak every time.)*[/INDENT]
[*]Kill Nautilus
```
nautilus -q
```
[/LIST]

Points 3 through 5 all have memory leaks in the MB range. I've pastebinned the contributions for _[initialization]("http://pastebin.com/04Ne48KJ")_, _[terminal spawning]("http://pastebin.com/pk8ZNv5K")_ and _[forced exit]("http://pastebin.com/GZeDstWQ")_ respectively (ignoring leaks < 10KB). I'm seeing a lot of **Brasero** except for in the latter stage.

---

### Post by afrodeity on 2010-05-27
I have another valgrind log following the example above.

[http://paste.ubuntu.com/440366/](http://paste.ubuntu.com/440366/)

---

### Post by afrodeity on 2010-05-27
I have another valgrind log following the example above.

[http://paste.ubuntu.com/440366/](http://paste.ubuntu.com/440366/)

---

### Post by ibuclaw on 2010-05-27
Wouldn't it be better raising a bug report on this?

I can't see how the forum can help... And sometimes Valgrind can be a bit of a red heron in what it reports, so be weary.

---

### Post by glinsvad on 2010-05-27
> **ibuclaw said:**
> Wouldn't it be better raising a bug report on this?

I can't see how the forum can help... 

We're comparing cliff notes, experiences and debugging output before filing a bug report. There has already been 2 on LaunchPad, which were remotely related (one regarding video thumb-nailing); I'm thinking that we need to gather plenty of momentum so that we can submit a meaningful report that won't be overlooked or dupe-marked.

> **ibuclaw said:**
> And sometimes Valgrind can be a bit of a red heron in what it reports, so be weary.

I'm not entirely sure what you're implying but the memory leaks are very real. My estimate is that Valgrind catches about 2/3 of the leaks.

---

### Post by afrodeity on 2010-05-28
Yes, otherwise we will end up misfiling the bug and it will get ignored.

---

### Post by LewRockwellFAN on 2011-01-14
Seems like this a recalcitrant problem with Nautilus. People have been talking about it quite a while now. If someone can fix it we'll all stand up and cheer 'em. But in the meantime, I see two work-arounds. Either:

1-
Use a different file manager. I've made a Thunar launcher that launches in the directory I most frequently use, gave it an icon created in gimp, and put it on the top panel (if that is the right term for the thing across the top of the desktop with Applications ... etc. drop down menus). There are threads here on making a different file manager be the default one in some circumstances. Seems it is hard to get rid of Nautilus completely since it is the default desktop manager as well. So if you go whole hog on this approach, which I have not, you need to switch desktop managers as well. Using a launcher on the top panel is a convenient way to check out alternate file browsers long enough to decide if you want to switch. I'm switching around trying several atm. So far I like Thunar the best of those I've tried but Roxy-flier is pretty good also. Thunar offers a great way to add stuff to the context menus but doesn't offer tabs. 

or

2-
Make a script that runs every minute or so (there is a gui ap in synaptic that makes it easier to schedule scripts. I think it is called gnome-schedule) and tests free memory and if it drops below some threshold you set pops up a window on top of everything that reports the problem and offers to run "killall nautilus". I'd like to try this approach but I haven't figured out how to write the conditional if statement or how to make it pop up a dialogue box or anything like that. If anyone can point me in the right direction on this that would be really cool.

---

### Post by afrodeity on 2011-01-14
My problem got fixed somewhere along the line. Fix was released for the issue and completely forgot about this posting, but still other problems with nautilus.Apparently Elementary OS are working on a new browser called Dash.

---

### Post by LewRockwellFAN on 2011-01-14
[sorry, forum was acting flaky and I double posted the above -nothing here, please ignore]

---

### Post by LewRockwellFAN on 2011-01-14
Thanks. I wish I could say the same. Possibly it's because I'm running Narwhal, 11.04, which is after all, really still considered a beta, I think. Probably I shouldn't have posted this in a thread marked solved. I just picked the most recent thread that came up searching [ nautilus memory leak ]. Well, if nobody points me toward proper syntax for my work around #2 above and I still have this problem, I'll try again in anew thread later.

---

### Post by ibuclaw on 2011-01-14
That you will, in the Natty Narwhal forum no doubt. :)

Closing Thread.

---

