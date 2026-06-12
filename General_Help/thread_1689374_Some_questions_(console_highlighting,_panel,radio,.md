---
title: "Some questions (console highlighting, panel,radio, scanner...)"
date: 2011-02-16
forum: General Help
---

### Post by trebi on 2011-02-16
Hi,

I'm considering option to set Ubuntu as my main OS, but I need to solve some issues before I made this choice. 

[LIST=1][*]**Scanner** - My scanner is Konica Minolta magicolor 1680MF. Printer is working natively, but scanner was not detected (by application *simple-scan*). What should I do? Is it possible to run it (if no other choice, trough VM)?
[*]**Radio** - I have got run RadioSure trough Wine, but I cannot connect to most of stations. Rythmbox is quite nice, but I need to search by Genere and also ability to record.
[*]**Panel** - I've got used to new Windows 7 Panel - windows of 1 program are in one group and represented only by icon. Also ability to drag them will be really useful.
[*]**Snipping** - I've found guide hw to set up windows snipping like in Windows 7 here: [http://www.omgubuntu.co.uk/2009/11/get-aero-snap-in-ubuntu/](http://www.omgubuntu.co.uk/2009/11/get-aero-snap-in-ubuntu/) ... but It's completely not working for me. It also resize if I have focused window and just move cursor to the egde, and width of windows snipped to side won't return.
[*]**Highlighting in console** - why is user@machine white as well as other text? It is hard to recognize where the long output of script begun then. I'd like bright green like in Gentoo, is it possible?


[/LIST]
Than you for your answers!

---

### Post by jerrrys on 2011-02-17
here's whats i found on your printer

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Konica+Minolta+magicolor+1680MF&as_qdr=all&sa=Google+Search&lang=en#909](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Konica+Minolta+magicolor+1680MF&as_qdr=all&sa=Google+Search&lang=en#909)

give Banshee a try for multimedia, its in the software center

the way you change your panels around is unlimited just about. this should be a thread by itself; also

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=change+desktop&as_qdr=all&sa=Google+Search&lang=en#863](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=change+desktop&as_qdr=all&sa=Google+Search&lang=en#863)

play around with system>preferences>appearance

---

### Post by Habitual on 2011-02-18
Grep in color:

add this to your .bashrc:

```
export GREP_OPTIONS='--color=auto' GREP_COLOR='7;31'
```

After editing reload with:
```
source ~/.bashrc
```

Now go grep something!

7;31 is a big RED highlighted box around the word.

Pick your poison here for additional color options.
[http://tldp.org/HOWTO/Bash-Prompt-HOWTO/x329.html](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/x329.html)

---

