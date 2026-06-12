---
title: "Which package manager???"
date: 2010-02-02
forum: General Help
---

### Post by Barriehie on 2010-02-02
Hey All,
So there's apt-get, synaptic/apt, and dpkg.  They all do the same thing!  I'm leaning towards CLI and dpkg, seems to have more/better options!  Any reasons to use one over the other?

TIA,
Barrie

---

### Post by scouser73 on 2010-02-02
I don't think there's a specific reason to use a particular package manager, I use Synaptic Package Manager and Apt-Get.  Go with what you like really I'd have thought.

---

### Post by ajgreeny on 2010-02-02
One big advantage that I think synaptic has is the ability to see the history of packages added and removed, which can be done with apt and dpkg, I'm sure, but is a lot faster if you can't remember commands with Synaptic -> File -> History.  This also shows all the updates that have been done with the Update-manager.

It is, of course, as always with ubuntu and linux, a matter of personal choice, and what you prefer may be different from my preferences.

---

### Post by Barriehie on 2010-02-02
> **ajgreeny said:**
> One big advantage that I think synaptic has is the ability to see the history of packages added and removed, which can be done with apt and dpkg, I'm sure, but is a lot faster if you can't remember commands with Synaptic -> File -> History.  This also shows all the updates that have been done with the Update-manager.

It is, of course, as always with ubuntu and linux, a matter of personal choice, and what you prefer may be different from my preferences.

Yes, the history is a good thing!  I've found that /root/.synaptic/log is the dir. containing the history files and I've a cron job that concatenates that into a big list once a month and puts it in my ~/.

---

### Post by ajgreeny on 2010-02-02
Oh wow!  Thanks for that information.  I have looked and looked for it but never found it before, so that is a very useful bit of information that I shall also use to do more or less what you are doing; send the info to my home folder.

I shall write a script after lunch today!.

---

### Post by Barriehie on 2010-02-02
> **ajgreeny said:**
> Oh wow!  Thanks for that information.  I have looked and looked for it but never found it before, so that is a very useful bit of information that I shall also use to do more or less what you are doing; send the info to my home folder.

I shall write a script after lunch today!.

With emacs and gawk I've got a cuisinart... 8)

---

