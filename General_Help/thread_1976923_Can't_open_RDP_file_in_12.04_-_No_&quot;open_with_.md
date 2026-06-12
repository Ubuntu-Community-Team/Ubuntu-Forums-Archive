---
title: "Can't open RDP file in 12.04 - No &quot;open with custom&quot; button anymore"
date: 2012-05-09
forum: General Help
---

### Post by ingramproductions on 2012-05-09
My company has a folder of RDP files on our FTP server that we use to connect to different servers. Using 10.10, I could open the files and tell it to open with "tsclient" or whatever remote desktop client I wanted. In 12.04, the "open with cutsom" option has been removed. I've installed grdesktop and remmina, but the don't show up in list of other applications, so I can't open them.

Bugs are reported [here]("https://bugzilla.gnome.org/show_bug.cgi?id=650284") and [here]("https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/853061") about the "open with custom" problem, but it doesn't look like they are going to add that feature back for some reason...

Meanwhile, I'm stuck not being able to open RDP files. Has anyone found a way to do this?

Thanks

---

### Post by Paddy Landau on 2012-05-10
Solution found. See [thread="1976921"]alternative thread[/thread].

---

### Post by ingramproductions on 2012-05-16
> i've seen claims that some apps refuse to show in the other apps dialog if their .desktop file lacks %u in their Exec= line.
I've added ***%u*** to the end of the "Exec=" line in the .desktop files for remmina and grdesktop. It does add the applications to the list of "Other Applications", but when I choose one of them I get the following error message:

```
Could not find application
Could not find 'grdesktop%u'
```

---

### Post by Paddy Landau on 2012-05-16
> **ingramproductions said:**
> ```
Could not find application
Could not find 'grdesktop%u'
```
There must be a space before the %u, as:
```
grdesktop %u
```

---

### Post by ingramproductions on 2012-05-16
> **Paddy Landau said:**
> There must be a space before the %u, as:
```
grdesktop %u
```

Ahh...

Ok, works now. Thanks

---

