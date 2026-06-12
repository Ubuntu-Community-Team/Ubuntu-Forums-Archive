---
title: "adding programs to startup from terminal"
date: 2011-10-01
forum: General Help
---

### Post by hotshot247 on 2011-10-01
does anybody know how to add a program to the startup applications from the terminal? the reason why i want to do this is that i'm writing a shell-script to automate certain things and i'd like to do that as well. thanks in advance.

---

### Post by prodigy_ on 2011-10-01
If you mean Gnome session, the launchers are in ~/.config/autostart folder. Examine existing ones and mimic them. :)

P.S. Not sure if it's still true for Unity but probably it is.

---

### Post by spiky001 on 2011-10-01
I have just doe a script to start on start up but not with terminal, I wrote the script then put it in home/users/bin then added it to startup applications if this helps.

---

### Post by WasMeHere on 2011-10-01
I made a talking date-clock for my mother and installed it into an old laptop with Ubuntu. Just for fun I also made a script that installs it so that it auto-starts. Actually, the computer is dedicated to that task, so from power-on it becomes a talking date-clock. So far it is a one-off, but it would be easy to make the next one :-)

Here is the script. The comments are in Swedish, and the files to be copied with [FONT="Courier New"]cp -p * ~/.vistid[/FONT] are not shown, but I think that you get the idea, so that you can make your auto-starter.

*Nota Bene*, this application installs only to the user's own session. If you want a global auto-starter: Identify where it should be installed and install with sudo!

```
#!/bin/bash
#
echo 'Datumklockan är utprovad för Ubuntu 10.04.1 LTS och bör fungera där'
echo 'gnome används som grafiskt användargränssnitt'
if test -d ~/bin
then
 cp -p datumklockans-konsol ~/bin
elif test -f ~/bin
then
 echo '~/bin är en fil, så datumklockans-konsol hamnar inte i PATH'
else
 mkdir ~/bin
 cp -p datumklockans-konsol ~/bin
fi

if ! test -d ~/.config
then
 mkdir ~/.config
fi
if ! test -d ~/.config/autostart
then
 mkdir ~/.config/autostart
fi
dkd=datumklockans-konsol.desktop
#[s]cat $dkd | sed s/'$USER'/"$USER"/ > ~/.config/autostart/$dkd[/s]
sed s/'$USER'/"$USER"/ "$dkd" > ~/.config/autostart/"$dkd"

if ! test -d ~/.vistid
then
 mkdir ~/.vistid
fi
cp -p * ~/.vistid
echo "Vid nästa inloggning (gnome-session) av denna användare, $USER,"
echo 'ska datum-klockan starta.'
echo 'Det är bäst att köra med infällda paneler och med lämplig font-storlek'
echo 'för att få bäst resultat'
```

---

### Post by sisco311 on 2011-10-01
Olle Wiklund, I hope you don't mind some suggestions. :)

First of all, you should double quote every expansion and anything that could possibly contain a special character ("$var", "$@", "$(command)"...):
```
cat "$dkd"
```

There is no need to check if a directory exist if you want to create it, you can do something like:
```
mkdir -p "$dir" || { echo "cannot create directory"; exit 1; } 1>&2
```

Invoked with the -p option mkdir won't complain if the directory exist.

**cat file | command** is wrong, don't use it, unless you want to win the [Useless Use of cat Award]("http://partmaps.org/era/unix/award.html"). :)

Most commands, like grep, sed, awk and so on, accept a filename as an argument: **grep PATTERN filename** or **sed OPTIONS SCRIPT filename**

If they don't, like in case of tr, then you can use redirection: **tr SET1 SET2 < filename**.

---

### Post by WasMeHere on 2011-10-01
Thanks for the feedback *sisco311*,

All of your tips except one are relevant and valuable for me :-)

But this one [FONT="Courier New"]sed s/'$USER'/"$USER"/ ...[/FONT] with single quote and double quote is on purpose, in order to make the current user's name to be called by the talking clock ;-)

Best regards
Olle

---

### Post by hotshot247 on 2011-10-03
> **prodigy_ said:**
> If you mean Gnome session, the launchers are in ~/.config/autostart folder. Examine existing ones and mimic them. :)

P.S. Not sure if it's still true for Unity but probably it is.

hey, i tried what you said and it worked and i use unity also. thanks for the help

---

### Post by pretty_whistle on 2011-10-03
> **prodigy_ said:**
> If you mean Gnome session, the launchers are in ~/.config/autostart folder. Examine existing ones and mimic them. :)

P.S. Not sure if it's still true for Unity but probably it is.

I'd like to do this too but I can't find the folder you mention here.  What is the full file path to it?  Where is ~/

???

---

### Post by hotshot247 on 2011-10-03
> **pretty_whistle said:**
> I'd like to do this too but I can't find the folder you mention here.  What is the full file path to it?  Where is ~/

???

go to nautllus, the file manager and in your home directory, press ctrl + h to show hidden folders and look for .config, you'll see it. anything with a dot in front of it is hidden so you have to press ctrl + h on anything like that.

---

### Post by pretty_whistle on 2011-10-03
> **hotshot247 said:**
> go to nautllus, the file manager and in your home directory, press ctrl + h to show hidden folders and look for .config, you'll see it. anything with a dot in front of it is hidden so you have to press ctrl + h on anything like that.

Thanx, that worked. :P I was just able to place 2 programs in there and have them autostart. :)

---

### Post by hotshot247 on 2011-10-03
> **pretty_whistle said:**
> Thanx, that worked. :P I was just able to place 2 programs in there and have them autostart. :)

no problem. i'm glad to help.

---

