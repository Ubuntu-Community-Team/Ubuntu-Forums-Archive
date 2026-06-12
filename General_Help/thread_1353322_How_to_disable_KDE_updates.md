---
title: "How to disable KDE updates?"
date: 2009-12-12
forum: General Help
---

### Post by aniplox on 2009-12-12
Hello, for my desktop environment I'm set with gnome, and my window manager as openbox. However I want to disable ALL KDE updates, and remove anything of the KDE environment.

How do I do this?

---

### Post by zvacet on 2009-12-13
In synaptic find KDE apps and mark them>apckage tab>lock version.I don´t know how smart this id bewcause if you get kde updates that mean you have kde apps installed.Why don´t keep them updated?

---

### Post by slakkie on 2009-12-13
```

rm-metapkg () {
        local i
        for i in "$@"
        do
                sudo aptitude markauto $(apt-cache depends $i | egrep -v "Conflict|Replaces" | sed -e 's/[<>]//g' | tail -n +2| awk '{print $NF}')
        done
}

```

then run rm-metapkg kubuntu-desktop

And you might also want to run after that:
```

sudo aptitude remove $(dpkg -l | grep kde | awk '{print $2}')

```

That is how I removed Gnome from my system.

---

### Post by aniplox on 2009-12-13
> **zvacet said:**
> In synaptic find KDE apps and mark them>apckage tab>lock version.I don´t know how smart this id bewcause if you get kde updates that mean you have kde apps installed.Why don´t keep them updated?
I'm set with gnome.
And slakkie thank you very much.

---

### Post by aniplox on 2009-12-15
actually soem programs I use require KDE so I guess I'll keep it, what can I do to reverse what I did?

---

