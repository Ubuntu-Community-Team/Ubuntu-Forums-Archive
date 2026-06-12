---
title: "Problem with Docky"
date: 2011-04-01
forum: General Help
---

### Post by TimmyK. on 2011-04-01
Every time I start up Docky, it blacks out the bottom part of the screen, and gives me a notice that says, "Docky requires compositing to work properly. Please enable compositing and restart Docky." How would I do this? Thanks in advance.

---

### Post by |{urse on 2011-04-01
Yeah, you need to enable compositing. What flavor of Ubuntu are you running?

For Ubuntu you need to run this command in the terminal.

gconftool-2 -s --type bool /apps/metacity/general/compositing_manager true

For Kubuntu it's trickier.

---

### Post by TimmyK. on 2011-04-01
Thank you, that fixed the Docky problem, but now all of my Windows are very dark. Any ideas? I am using a dual-monitor setup, if that's any help.

---

### Post by TimmyK. on 2011-04-01
Strange thing is, when I set the monitors to show mirror images of each other, the problem goes away. How do I fix this?

---

### Post by |{urse on 2011-04-01
Odd! I suggest starting a new thread on that. I've never seen it happen personally.

---

### Post by TimmyK. on 2011-04-01
Yes, it is. I have the laptop monitor on 1280x800 and the external one on 1024x768. Funny thing is, the problem goes away when I reset the laptop to the same resolution as the monitor. 

If I should ever want to disable this, how would I do that?

---

### Post by luishasbon on 2011-04-01
Maybe you should insall ccsm  thats compiz advanced composite manager. or just compiz :). though it should be already installed by default, otherwise be sure you have best effects in the appeareance tab.

---

### Post by |{urse on 2011-04-01
> **TimmyK. said:**
> If I should ever want to disable this, how would I do that?

It would be

> gconftool-2 -s --type bool /apps/metacity/general/compositing_manager false

---

### Post by Sina_RJ on 2011-04-02
search for thread docky problem
if you use search engine of site you'll find it easily
it's started by me,I had the same problem
i fix that with restarting compiz,it's all said in that thread

---

