---
title: "Evolution Tasks Missing"
date: 2011-06-20
forum: General Help
---

### Post by mobius129a on 2011-06-20
Hello, 
Yesterday, I found that the majority of my tasks on Evolution (2.28.3) had just disappeared. I last did a backup of my system 2 weeks ago but in that time important data has been added to my tasks lists on Evolution. I've read around and found that the problem may be fixed by rebuilding evolution-data-server (see [here]("http://lists.freebsd.org/pipermail/freebsd-gnome/2007-January/016576.html")). However, if this means re-compiling evolution-data-server from the package manager, well, I don't seem to keen on doing that unless I can get confirmation of how to implement it, i.e. how do I rebuild evolution-data-server? 

I really need those tasks! So, any help much appreciated.

---

### Post by Zill on 2011-06-20
mobius129a:  Let's try the simple things first ;-)

Open Evolution Tasks.  Look for the check box in the Sidebar, probably called "Personal".  Uncheck the box.  Close Evolution completely.  Re-open Evolution Tasks.  Check the "Personal" checkbox in the Sidebar.

Have your tasks now returned?

---

### Post by mobius129a on 2011-06-20
> **Zill said:**
> mobius129a:  Let's try the simple things first ;-)

Open Evolution Tasks.  Look for the check box in the Sidebar, probably called "Personal".  Uncheck the box.  Close Evolution completely.  Re-open Evolution Tasks.  Check the "Personal" checkbox in the Sidebar.

Have your tasks now returned?

Hi Zill, 
I did as you said but included the other task lists I have in the sidebar. The first time: nothing. After that, I went to check the task settings files under ~/.evolution/tasks just to see whether I still had the .ics files for each task list: I did. Then, I re-opened Evolution and all the tasks were there! This isn't the first time that a few of my tasks have 'disappeared'. Do you know why this is happening, and what I can do to prevent these apparent disappearances? Thanks.

---

### Post by Zill on 2011-06-20
> **mobius129a said:**
> ...Then, I re-opened Evolution and all the tasks were there! This isn't the first time that a few of my tasks have 'disappeared'. Do you know why this is happening, and what I can do to prevent these apparent disappearances? Thanks.
I have no idea exactly *why* it happens but this is a long-standing "feature" of Evolution. ;-)

I have never heard of data actually disappearing and, as you discovered, it usually returns if you uncheck/check your various tasks boxes.  The same trick can be used with "disappearing" calandar entries.

---

### Post by mobius129a on 2011-06-20
Feature or bug?! Ok thanks for the info!

---

