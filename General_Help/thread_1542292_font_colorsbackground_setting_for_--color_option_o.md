---
title: "font colors/background setting for --color option of ls"
date: 2010-07-30
forum: General Help
---

### Post by rawlins02 on 2010-07-30
OS is Lucid, Gnome desktop.  I'm using the --colors option for ls. This is giving me blue font on a green background for directories. Hard to read. The default background is black which is fine.  Is there a simple way to turn the green option off? I believe the text files are in .gconf.  Couldn't sort out settings using gconf-editor.  dircolors command has lots of good stuff, but looking to simply turn of backlighting.  Generally use tcsh, if that matters.

---

### Post by gmargo on 2010-07-30
Relatively simple but may require a bit of experimentation.

"ls" makes a distinction between several types of directories based on their permissions, and there are separate color settings for each.  You can use the LS_COLORS environment variable to change these colors.

Map of LS_COLORS strings to directory type, with default colors (derived from "dircolors -b" and "dircolors --print-database"):
```

di = DIR 01;34 # directory
tw = STICKY_OTHER_WRITABLE 30;42 # dir that is sticky and other-writable (+t,o+w)
ow = OTHER_WRITABLE 34;42 # dir that is other-writable (o+w) and not sticky
st = STICKY 37;44 # dir with the sticky bit set (+t) and not other-writable

```Available color codes (from "dircolors --print-database"):
```

# Below are the color init strings for the basic file types. A color init
# string consists of one or more of the following numeric codes:
# Attribute codes:
# 00=none 01=bold 04=underscore 05=blink 07=reverse 08=concealed
# Text color codes:
# 30=black 31=red 32=green 33=yellow 34=blue 35=magenta 36=cyan 37=white
# Background color codes:
# 40=black 41=red 42=green 43=yellow 44=blue 45=magenta 46=cyan 47=white

```Now the one that bugs you is "blue font on green background", which corresponds to the OTHER_WRITABLE setting (ow=34;42 - 34 is blue text, 42 is green background).

So in order to remove the green background (42) from the OTHER_WRITABLE setting but keep the same text color, set the LS_COLORS environment variable in your $HOME/.bashrc:

```

export LS_COLORS="ow=34"

```Or in tcsh syntax for your $HOME/.tcshrc:
```

setenv LS_COLORS "ow=34"

```

---

### Post by rawlins02 on 2010-07-30
Thanks gmargo. I've been playing with dircolors.

Say I want files with an .eps extension to have a certain color. I believe there is a file with the dircolor -c (for tcsh) settings. Is that right?

---

### Post by gmargo on 2010-07-30
> **rawlins02 said:**
> Say I want files with an .eps extension to have a certain color. I believe there is a file with the dircolor -c (for tcsh) settings. Is that right?

There is no actual file to reference; I just checked the sources to make sure - the translation is embedded in the binaries.  But you can generate your own file with the --print-database option.

To add an additional file extension, all you should have to do is add a "*.eps=XX;YY" type expression to your LS_COLORS.  So just for fun let's make a really annoying one :p.  Here's an addition to LS_COLORS for blinking blue text on red background!

```

export LS_COLORS="ow=34:*.eps=05;34;41"

```

---

### Post by Cavsfan on 2010-07-30
> **gmargo said:**
> Relatively simple but may require a bit of experimentation.

"ls" makes a distinction between several types of directories based on their permissions, and there are separate color settings for each.  You can use the LS_COLORS environment variable to change these colors.

Map of LS_COLORS strings to directory type, with default colors (derived from "dircolors -b" and "dircolors --print-database"):
```

di = DIR 01;34 # directory
tw = STICKY_OTHER_WRITABLE 30;42 # dir that is sticky and other-writable (+t,o+w)
ow = OTHER_WRITABLE 34;42 # dir that is other-writable (o+w) and not sticky
st = STICKY 37;44 # dir with the sticky bit set (+t) and not other-writable

```Available color codes (from "dircolors --print-database"):
```

# Below are the color init strings for the basic file types. A color init
# string consists of one or more of the following numeric codes:
# Attribute codes:
# 00=none 01=bold 04=underscore 05=blink 07=reverse 08=concealed
# Text color codes:
# 30=black 31=red 32=green 33=yellow 34=blue 35=magenta 36=cyan 37=white
# Background color codes:
# 40=black 41=red 42=green 43=yellow 44=blue 45=magenta 46=cyan 47=white

```Now the one that bugs you is "blue font on green background", which corresponds to the OTHER_WRITABLE setting (ow=34;42 - 34 is blue text, 42 is green background).

So in order to remove the green background (42) from the OTHER_WRITABLE setting but keep the same text color, set the LS_COLORS environment variable in your $HOME/.bashrc:

```

export LS_COLORS="ow=34"

```Or in tcsh syntax for your $HOME/.tcshrc:
```

setenv LS_COLORS "ow=34"

```

You are good! :D  This is pretty amazing stuff.

---

### Post by rawlins02 on 2010-07-30
This indeed changes colors for .eps file. Sweet!  Blue on red, but no blinking here after sourcing .cshrc with this added:

```

setenv LS_COLORS="ow=34:*.eps=05;34;41"

```

No need to debug that :-)

I'm surprised no rc file. I keep seeing mention of  option for ~/.dircolors file.  In previous versions of, perhaps it was Fedora Core, there was a text file with the designations.

---

