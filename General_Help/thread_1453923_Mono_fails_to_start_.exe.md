---
title: "Mono fails to start .exe"
date: 2010-04-13
forum: General Help
---

### Post by satimis on 2010-04-13
Hi folks,

Ubuntu 9.10
Mono 2.4.2.3


On running;

$ mone /path/to/.exe

following warning popup:```

Fatal Error System.ArgumentOutOfRangeException.  Argument is out of range Parameter name: index
at System Collections Generic List`1 [System String] get_item (int32 index) [0x00000] at Verse_of_the_Day.MainForm.ctor () [0x00000]
at (wrapper remoting-invoke_with-check) Verse of the_Day.MainForm.ctor ()
at Verse_of_the_Day.English.ReadWrite () [0x0000]

```

I have been searching around and could not find a solution.  Could you please shed me some light?  TIA


B.R.
satimis

---

### Post by zvacet on 2010-04-14
It look like you are trying to install .exe in Ubuntu.That doesn't work.Read [this]("http://mono-project.com/DistroPackages/Ubuntu#Mono_for_Ubuntu") for installing Mono in Ubuntu.

---

