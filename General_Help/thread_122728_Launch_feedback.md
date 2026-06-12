---
title: "Launch feedback"
date: 2006-01-28
forum: General Help
---

### Post by RichGuk on 2006-01-28
Hello,

Just thought I'd ask around here, I'm not a noob and have been using Kubuntu for ages now. But I can't seem to get the launch feedback option in kcontrol to remember my setting when I select it from that annoying "bouncy icon" to the no bounch option.

I've tried;
Running kcontrol via sudo, kdesu.
Deleteing kcontrolrc in my home directory, chmod it to 777.

But all seem to fail, kcontrol manages to save my other settings (although I only tried chaning the mouse setting) anyone got an ideas? I'm sure it'll be something simple that I've just failed to think of at the time.

Thanks,

Richard

---

### Post by chandra on 2006-01-28
Please take a look at:

[http://www.kubuntu.org/docs/kquickguide/C/ch03s07.html#panel-launchfeedback](http://www.kubuntu.org/docs/kquickguide/C/ch03s07.html#panel-launchfeedback)

or do:

System Settings -> Panel -> Launch Feedback

---

### Post by RichGuk on 2006-01-28
I know how to do it.. as I was saying it doesn't remember my setting (well seems to for root account but that doesn't apply to my session) everytime I set it it makes no effect and if I re-load the setting it's back to bouncy option.

---

### Post by RichGuk on 2006-01-30
I'll take that as no one knows?

---

### Post by RichGuk on 2006-01-30
Done it, just deleted the /home/<user>/.kde/share/config/klaunchrc file - must of had the wrong read/write permissions or something.

---

