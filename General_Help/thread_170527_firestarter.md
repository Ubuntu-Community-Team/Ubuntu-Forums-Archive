---
title: "firestarter"
date: 2006-05-04
forum: General Help
---

### Post by Face1 on 2006-05-04
Hi, I'm an ubuntu (gnome) user who recently installed KDE, and I think that this is where I'll stay (I like the eyecandy).  Back in Gnome, I used firestarter for my firewall.  Firestarter automatically started with my gnome session, so I didn't have to worry about it.  Now, I could easily have it automatically start with KDE (well actually, how would I do this?), but if I don't need to, then I'd rather not.  So my question is, will my firewall configured and used with firestarter still be up when the firestarter program is not running?  Thanks.

---

### Post by louis_nichols on 2006-05-04
definitely yes

the gui is just for changing settings. They are automatically applied at startup. In fact you can actually see that in the usplash screen: something like "applying firestarter rules".

Firestarter is in fact not a firewall. It is just a GUI to the powerful iptables firewall, which is actually integrated in every Linux kernel. You could very well use it without firestarter, using some commands in terminal. Info [here]("https://wiki.ubuntu.com/IptablesHowTo?highlight=%28iptables%29"), if you're interested.

So... don't worry! Just start firestarter when you need to open some port or something.

---

### Post by Parkotron on 2006-05-04
You might also be interested in [Guarddog]("http://www.simonzone.com/software/guarddog/"). Like Firestarter, Guarddog is a configuration front end for iptables, but it's native to KDE. I've never used Firestarter, so I don't know if they do things differently, but Guarddog meets my needs, personally.

---

### Post by ComplexNumber on 2006-05-04
[quote=Parkotron]You might also be interested in [Guarddog]("http://www.simonzone.com/software/guarddog/"). Like Firestarter, Guarddog is a configuration front end for iptables, but it's native to KDE. I've never used Firestarter, so I don't know if they do things differently, but Guarddog meets my needs, personally.[/quote]
i would recommend guarddog too. its very good.

---

### Post by Face1 on 2006-05-05
Okay, thanks guys (or maybe girls, I don't know!).  louis_nichols, that is what I thought, but I wasn't sure.  I thought that maybe those iptables rules were only in place when the program was open.  But I guess not!

Also, I'll check out guarddog...you don't really notice how many gtk apps you use until you start using kde, and everything looks like windows 3.1, so I'll be happy to take one off that list.

---

### Post by louis_nichols on 2006-05-05
Guarddog is ok too. very different in use compared to firestarter, but somewhat more user-friendly, I'd say.

As a side note, you can make your gtk apps look like KDE, using gtk2-engines-gtk-qt.

---

### Post by ComplexNumber on 2006-05-05
> Guarddog is ok too. very different in use compared to firestarter, but somewhat more user-friendly, I'd say. i don't think i would agree with that. from what i remember, firestarter was the more user friendly and less intimidating, but guarddog was probably overall slightly more configurable.

---

### Post by louis_nichols on 2006-05-05
[QUOTE=ComplexNumber]i don't think i would agree with that. from what i remember, firestarter was the more user friendly and less intimidating, but guarddog was probably overall slightly more configurable.[/QUOTE]

well... that's obviously a matter of personal opinion. I ended up using Firestarter, too, although I use many KDE apps within Ubuntu. I'm not really sure why I chose firestarter.

At first, guarddog seemed better, since it already had a list of commonly used ports and only required checking some options here and there.

---

