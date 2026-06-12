---
title: "gnome-terminal slow to launch"
date: 2010-02-27
forum: General Help
---

### Post by mrmoney on 2010-02-27
gnome-terminal has become god-awfully slow to launch. This never used to be the case and I'm not sure at what point exactly this started, so I have really no idea what could have changed to cause this.

Is there anyway I can diagnose what is going on here? I am running Ubuntu 9.04

Thanks for any help

---

### Post by Ozymandias_117 on 2010-02-27
Have you tried a different terminal emulator?

---

### Post by cjhabs on 2010-02-27
Have you edited your .bashrc recently? I have seen this where it is looking at networked resources that are not currently available such as paths pointing to unmounted file systems.

You can try renaming your .bashrc and seeing if that is the cause of the problem.

---

### Post by n0dix on 2010-02-27
Try with xterm:
 Alt+F2, write 'xterm' and Enter.

---

### Post by mrmoney on 2010-02-28
Hey, thanks for the help.

xterm launches quickly. Though gnome-terminal will also _sometimes_. The majority of the time it is dog slow.

I've not edited my .bashrc recently, and don't see anything I could suspect in there.

I did install dropbox and it's daemon, which I do believe was right before this started happening. Though I don't really want to blame dropbox, I can't think of anything else other than the regular ubuntu updates. Even without Dropbox running though my terminal launch is slow.

---

### Post by n0dix on 2010-02-28
Do you have a process consuming CPU process?

---

### Post by mrmoney on 2010-02-28
No, nothing really.

---

### Post by n0dix on 2010-02-28
Disabled compiz and try it again.

---

### Post by mrmoney on 2010-05-29
> **cjhabs said:**
> Have you edited your .bashrc recently? I have seen this where it is looking at networked resources that are not currently available such as paths pointing to unmounted file systems.

You can try renaming your .bashrc and seeing if that is the cause of the problem.

Hey you were right, I narrowed it down to a bash alias I had added (though dont remember doing so)

This was the culprit:
alias lowerall="for i in `find * -depth`; do (mv $i `echo $i | sed 's%[^/][^/]*$%%'``echo $i | sed 's!.*/!!' | tr [:upper:] [:lower:]`); done"

Got rid of it and my terminal is back to being speedy

---

