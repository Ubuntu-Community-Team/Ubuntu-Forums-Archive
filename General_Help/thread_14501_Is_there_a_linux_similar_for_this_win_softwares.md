---
title: "Is there a linux similar for this win softwares?"
date: 2005-02-07
forum: General Help
---

### Post by testament on 2005-02-07
I'm making the switch from windows and looking for similar linux softwares. I've already found many great programs but I still couldn't find linux similars for this win softwares:

Eraser - securely erases sensitive files.
CPU Idle - Software cooler.

---

### Post by Nis on 2005-02-07
wipe will fill in for Eraser.
No software cooling is necessary since Linux automatically sends a HLT command to the CPU when its idle, cooling it.

---

### Post by JoWilly on 2005-02-07
Similar to wipe, [BCWipe](http://www.jetico.com/index.htm#/bcwipe_unix.htm) from jetico.

---

### Post by tdell on 2005-02-09
[QUOTE=Nis]wipe will fill in for Eraser.
No software cooling is necessary since Linux automatically sends a HLT command to the CPU when its idle, cooling it.[/QUOTE]

That is what they say in the Windows groups to but my experience is it is just not true.

I use cooling software in XP and it brings my temps down 5-7C.  When I run Ubuntu my temps are 4-5C higher than in Windows.

Tom

---

### Post by gheorghe_pop on 2005-02-09
So you got a diference like 1 or 2 degrees.Tell me where is the problem?

---

### Post by tdell on 2005-02-09
[QUOTE=gheorghe_pop]So you got a diference like 1 or 2 degrees.Tell me where is the problem?[/QUOTE]

no as I stated the temps in Ubintu are 4-5C higher

Tom

---

### Post by lucus on 2005-02-09
so do you mean (in FAHRENHEIT) your temps go up about 40 degrees?

---

### Post by mendicant on 2005-02-09
You could look into cpufreqd (in universe/admin):

[http://cpufreqd.sourceforge.net/index.shtml](http://cpufreqd.sourceforge.net/index.shtml)

also interesting might by:

cpudyn (universe/admin) [http://mnm.uib.es/gallir/cpudyn/](http://mnm.uib.es/gallir/cpudyn/) 

gnome-cpufreq-applet (main/gnome)

cpuburn (universe/misc)

---

### Post by tdell on 2005-02-10
[QUOTE=lucus]so do you mean (in FAHRENHEIT) your temps go up about 40 degrees?[/QUOTE]

That wpuld be correct!

Tom

---

### Post by hoy_pogi on 2005-11-05
how does one use those programs? Ive installed gnome-cpufreq-applet but I cant even run it from the terminal. What does the powernowd daemon do? I think I have it installed by default.

---

### Post by poptones on 2005-11-05
In what world does +5C = +40F?

+5C=+9F...

---

### Post by bluecrayon on 2005-11-24
If you have an Athlon or Duron processor, you could try using a small utility called Athcool. My CPU temp went from around 50 to 40 degrees C, which is in line with what i get using CPU Idle in windows. Apparently certain athlon and duron processors dont respond correctly to HLT signal, so the STPGNT signal has to be used instead.

More information here: [http://members.jcom.home.ne.jp/jacobi/linux/softwares.html]("http://members.jcom.home.ne.jp/jacobi/linux/softwares.html")
[http://www.daniel.nofftz.net/linux/Athlon-Powersaving-HOWTO.html]("http://www.daniel.nofftz.net/linux/Athlon-Powersaving-HOWTO.html")

---

