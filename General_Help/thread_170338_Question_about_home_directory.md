---
title: "Question about /home directory"
date: 2006-05-04
forum: General Help
---

### Post by Hoffmann on 2006-05-04
Hello:

I intend to upgrade Ubuntu Breezy to Ubuntu Dapper soon. I am starting thinking about my home directory. I have a WindowsXP/Ubuntu dual boot system, and I have no separated home partition. I mean, my /home directory is part of the Ubuntu partition.
My question is: What should I do in order to keep my data?

Thanks,
Hoffmann

---

### Post by nanotube on 2006-05-04
[QUOTE=Hoffmann]Hello:

I intend to upgrade Ubuntu Breezy to Ubuntu Dapper soon. I am starting thinking about my home directory. I have a WindowsXP/Ubuntu dual boot system, and I have no separated home partition. I mean, my /home directory is part of the Ubuntu partition.
My question is: What should I do in order to keep my data?

Thanks,
Hoffmann[/QUOTE]
well, backing it up on a cd or something seems like a good idea to start with.
but really, when dapper is officially released, you will be able to just upgrade to it through the update manager, and it should preserve all your stuff in the home dir.

---

### Post by Al3xanR0 on 2006-05-04
I agree with nanotube upgrading should not affect the contents of your home dir (at least not files you created), but if you have any apprehensions back-up the data.

---

### Post by Hoffmann on 2006-05-04
[QUOTE=nanotube]well, backing it up on a cd or something seems like a good idea to start with.
but really, when dapper is officially released, you will be able to just upgrade to it through the update manager, and it should preserve all your stuff in the home dir.[/QUOTE]

Wow. Upgrading through update manager seems great!
So, for the final (Dapper) release we won't need to use command line? I mean, all we need to do is to use the (graphical interface) update manager? [No "aptitude" or "apt-get" command will be needed?]

---

### Post by Hoffmann on 2006-05-04
[QUOTE=Al3xanR0]I agree with nanotube upgrading should not affect the contents of your home dir (at least not files you created), but if you have any apprehensions back-up the data.[/QUOTE]


Just a stupid question now: What about the hidden files of my /home dir, such as .mozilla. If I copy my /home directory to a CD, are they going to be there?

---

### Post by Ramses de Norre on 2006-05-04
If you copy them too, yes ;)

mv and cp [-R] do copy hidden files, when you're using nautilus press ctrl+h to see them and select them among the others.

---

### Post by Cirrocco on 2006-05-04
similar question, but more generally speaking.

I would like to backup my /home directory before reinstalling breezy(or dapper) fresh off a cd.  once I get back to my desktop, whats the best way to restore my /home dir?  should I log in as a different user and the copy that stuff over to the other profile?

also: does gnome-panel information (placement, opacity, contents) all get stored in the /home dir such that restoring it would put your visual preferences back the way they were?

---

### Post by nanotube on 2006-05-04
[QUOTE=Hoffmann]Wow. Upgrading through update manager seems great!
So, for the final (Dapper) release we won't need to use command line? I mean, all we need to do is to use the (graphical interface) update manager? [No "aptitude" or "apt-get" command will be needed?][/QUOTE]
yes, that is my understanding of how it's going to be.

---

### Post by nanotube on 2006-05-04
[QUOTE=Cirrocco]similar question, but more generally speaking.

I would like to backup my /home directory before reinstalling breezy(or dapper) fresh off a cd.  once I get back to my desktop, whats the best way to restore my /home dir?  should I log in as a different user and the copy that stuff over to the other profile?

also: does gnome-panel information (placement, opacity, contents) all get stored in the /home dir such that restoring it would put your visual preferences back the way they were?[/QUOTE]

well, first your second question - yes, those preferences are stored in your home dir, so if you restore your home dir, the panel and other preferences get restored, too.

as to your first question - i would say the best way is to log in from the console, without having X and Gnome running, and then copy your home dir back. because otherwise some files may be locked by X or Gnome, and prevent you from copying everything. (maybe that is not the case, but it never hurts to be safe, i'd say. )

---

### Post by Cirrocco on 2006-05-05
that makes sense.

Thanks, nanotube

---

