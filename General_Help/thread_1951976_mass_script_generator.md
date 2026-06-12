---
title: "mass script generator?"
date: 2012-04-03
forum: General Help
---

### Post by sr_guy on 2012-04-03
I have hundreds of .zip N64 games. I want to write small scripts for each one but all at once using this line in each script:

Is there a program that will create a script with that command in each script with the proper .zip filename, and then will name the script the same as the .zip filename?

i.e.

1. scans mortalcombat.zip (file)

2. inputs in script, mupen64plus --fullscreen --nogui --noosd /mnt/tera/roms/mortalcombat.zip

3 names the script mortalcombat.sh

---

### Post by Vaphell on 2012-04-03
you forgot
4 chmod +x mortalcombat.sh (besides it was kombat) ;-)

you can create a script that would act an universal launcher, let's say run_game.sh
```
#!/bin/bash

echo mupen64plus --fullscreen --nogui --noosd "$1"
```

or an alias in your shell configuration - probably the best option
gedit ~/.bashrc , find the section with aliases and add your own
```
alias run_game='mupen64plus --fullscreen --nogui --noosd'
```

you would run it like **run_game mk2.zip** (and shell would help you if you tapped tab to autocomplete to existing file names)

if you want to generate scripts for each existing zip
```
for z in *.zip; do scr="${z%.zip}.sh"; echo $'#!/bin/bash\n\nmupen64plus --fullscreen --nogui --noosd "'"$z"'"' > "$scr"; chmod +x "$scr"; done
```

---

### Post by sr_guy on 2012-04-03
Thanks for the help Vaphell. Something I did not mention though, I am launching these games via shell script with a launching app from within XBMC. The media center PC is hooked directly to my TV so I am trying to make what I can as automated as possible using vnc, ssh, & Streamzap remote control. 

1. I have setup my Streamzap remote control, using lirc, to restart gdm with a push of a button if necessary.

2. Streamzap remote control can kill active windows with a push of a button.

3. Streamzap remote control can start XBMC.

4. Runs FreePBX/Asterisk. Kind of an all-in-one box.

Adding and automating emulator games is a bit more labor intensive though :p

Shell scripting & .bashrc editing are not my strong points though :p

---

### Post by Vaphell on 2012-04-03
so what exactly do you need to do in order to launch a game?


.bashrc aliases are as straightforward as it gets. they are simple text substitutions
alias a='bbb ccc ddd'
you type 'a list of parameters' and shell executes 'bbb ccc ddd list of parameters' so aliases are perfect when you want to create a shorthand version of some parameter heavy command

---

### Post by sr_guy on 2012-04-04
I think I have the .bashrc portion straightened out, thanks. One last thing, however. All the N64 Rom files have both spaces, and characters in the filename which after running your command to generate a script file I still cannot execute the game with the launcher because of the extra characters. All the file names appear like this:

Polaris SnoCross (U) [!].zip

I found a script that removes the spaces, and replaces the spaces with underscores, so the last part I need is a script that removes:

(U) & [!] characters from the filename.

---

### Post by Vaphell on 2012-04-05
yes, spaces are best to be avoided.
you can have spaces in names, you just need to quote them to preserve integrity
for example *rungame 'Polaris SnoCross (U) [!].zip'*

you may use \ to escape spaces, eg *rungame Polaris\ SnoCross\ (U)\ [!].zip*, forcing shell to ignore them when cutting supplied command into pieces.

you may also use tab to fill the names for you, autoescaped just like that, all you need to do to provide few chars if there is any ambiguity. As a bonus you don't have typos.


Can you provide more samples of troublesome file names so the general solution can be found?

---

