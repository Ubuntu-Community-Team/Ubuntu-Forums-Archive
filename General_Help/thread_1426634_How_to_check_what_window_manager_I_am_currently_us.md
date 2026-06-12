---
title: "How to check what window manager I am currently using (via terminal)?"
date: 2010-03-10
forum: General Help
---

### Post by drewsus on 2010-03-10
Hello all,
Just a quick question: 
[INDENT]**How can I check what window manager (compiz/metacity) I am using in the terminal?** I know how to change from one to the other or to just visually see what is currently running, but I need to know a way to check in the terminal for a script. How can I do this?[/INDENT]

Thanks in advance,
dRewsus

---

### Post by cjhabs on 2010-03-10
> **drewsus said:**
> Hello all,
Just a quick question: 
[INDENT]**How can I check what window manager (compiz/metacity) I am using in the terminal?** I know how to change from one to the other or to just visually see what is currently running, but I need to know a way to check in the terminal for a script. How can I do this?[/INDENT]

Thanks in advance,
dRewsus

I am running gnome and a bash shell.
My environmental variables include:
DESKTOP_SESSION=gnome
GDMSESSION=gnome

would these help you?
You can check with the "env" command.

---

### Post by drewsus on 2010-03-10
Hmmm, no, those and the env command don't give me what I want. 
I want to know specifically whether compiz or metacity is active. 
But thank you cjhabs, I'm sure we're getting warmer!

Anyone else!? There must be a way. 
Obviously something like compiz-switch has a way to do it, but I can't make sense of it from the source code....
Maybe I'll include it here so someone else might be able to pick through it and see what I do not?

**compiz-switch code:**
```
#!/bin/bash
# Compiz-Switch - script to switch Compiz on and off
# 
# Copyright (c) 2007 Nick Bauermeister <Forlong@gmx.de> 
#
# This program is free software. Feel free to redistribute and/or
# modify it under the terms of the GNU General Public License v3
# as published by the Free Software Foundation.
#
# This program is distributed in the hope that it will be useful
# but comes WITHOUT ANY WARRANTY; without even the implied warranty
# of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
# See the GNU General Public License for more details.

COMPIZ_WRAPPER="/usr/local/bin/compiz-wrapper"
COMPIZ_BIN=compiz

VERSION=0.4.0~source

usage()
{
  printf "\nUsage: compiz-switch [option(s)]\n\n"
  printf "%4sAvailable options:\n\n"
  printf "Informations:\n"
  printf "%4s-h  or --help\t\tList all available options (this message).\n"
  printf "%4s-v  or --version\t\tPrint version of Compiz-Switch in use.\n\n"
  printf "Compiz options:\n"
  printf "%4s-o  or --output\t\tGive output made by the Compiz start script.\n\n"
  printf "Window managers:\n"
  printf "%4s-m  or --metacity\t\tUse one of these options to specify which\n"
  printf "%4s-k  or --kwin\t\twindow manager you want to switch to, if\n"
  printf "%4s-x  or --xfwm\t\tCompiz-Switch doesn't use it by default.\n\n"
  printf "Switch Screenlets:\t\tSwitch Screenlets off and on with Compiz.\n"
  printf "%4s-s  or --screenlets\t\tKills and restores running Screenlets.\n"
  printf "%4s-sa or --screenlets-auto\tUses autostart files to rerun Screenlets.\n\n" 
  printf "Staus icon:\t\t\tChange icon according to activity of Compiz.\n"
  printf "%4s-c  or --change-icon\tWorks only in GNOME for the panel icon.\n\n"
}

mug()
{
  printf "\t\t )%3s(\n\t%5s( ( (%2s)%2s)\n\t%6s)%3s)(%2s(\n\t%5s(%2s)(%2s)%2s)\n\t%4s( )( )(%2s(%2s)\n\t .- (%2s( )%2s( ) ( -.\n\t(%3s( ) ( ) ( ) )%3s)\n\t|\`-..,_________,..-\`|\n\t|\t\t%4s|\n\t|%7s.--.%7s .--.\n\t|%6s|o_o |%6s(__%2s\\ \n\t|%6s|:_/ |%7s| )%2s)\n\t|%5s//%3s\\ \\%6s|/%2s/\n\t|%4s(|%5s| )%5s(_ /\n\t|%3s/'\\_%3s_/\`\\%5s|\n\t|%3s\\___)=(___/%5s|\n\t|\t\t%4s|\n\t \`-..,_________,..-\`\n\n"
}

# Detect desktop environment in use
if [ ! -z $GNOME_DESKTOP_SESSION_ID ]; then
  SWITCH_TO_WM=metacity
elif [ "$KDE_FULL_SESSION" = "true" ]; then
  SWITCH_TO_WM=kwin
elif xprop -root _DT_SAVE_MODE | grep ' = \"xfce4\"$' >/dev/null 2>&1 ; then
  SWITCH_TO_WM=xfwm4
fi

PIXDIR="/usr/local/share/pixmaps"
CHANGE_ICON="$HOME/.icons/compiz-switch.png"

while [ $# -gt 0 ]
do
  case $1 in
    -h | --help)
      usage
      exit 0
      ;;
    -v | --version)
      echo $VERSION
      exit 0
      ;;
    -o | --output)
      OUTPUT=yes
      shift
      ;;
    -m | --metacity)
      SWITCH_TO_WM=metacity
      shift
      ;;
    -k | --kwin)
      SWITCH_TO_WM=kwin
      shift
      ;;
    -x | --xfwm)
      SWITCH_TO_WM=xfwm4
      shift
      ;;
    -s | --screenlets)
      SCRNLTS=yes
      shift
      ;;
    -sa | --screenlets-auto)
      SCRNLTS_AUTO=yes
      shift
      ;;
    -c | --change-icon)
      mkdir -p $HOME/.icons
      cp $PIXDIR/compiz-switch.png $CHANGE_ICON
      CHANGE=yes
      shift
      ;;
    --coffee)
      mug
      exit 0
      ;;
    *)
      printf "Error, unknown option: \"$1\"\nRun 'compiz-switch --help' for details.\n"
      exit 1
      ;;
  esac
done

COMPIZ_RUNNING=$(ps -o comm= -C $COMPIZ_BIN)
WM_OPTION="--replace"

switch_wm()
{
  case $SWITCH_TO_WM in
    xfwm4)
      killall $COMPIZ_RUNNING
      while [ $(ps -o comm= -C $COMPIZ_BIN) ]
      do
        sleep 1
      done
      exec xfwm4
      ;;
    metacity | kwin)
      exec $SWITCH_TO_WM $WM_OPTION
      ;;
    *)
      printf "No window manager to switch to found, exiting.\n"
      exit 1
      ;;
  esac
}

compiz_switch_inactive_icon()
{
  if [ ! -z $CHANGE ]; then
    rm $CHANGE_ICON
    cp $PIXDIR/compiz-switch-inactive.png $CHANGE_ICON
  fi
}

compiz_switch_icon()
{
  if [ ! -z $CHANGE ]; then
    rm $CHANGE_ICON
    cp $PIXDIR/compiz-switch.png $CHANGE_ICON
  fi
}

kill_and_save_screenlets()
{
  if [ ! -z $SCRNLTS ] || [ "$SCRNLTS_AUTO" = "yes" ]; then
    SCRNLTS_RUN=$(ps -ef | grep -v grep | grep Screenlet | awk '{print $9}')
    RUN_BY_MNGR=$(ps -ef | grep -v grep | grep "\-u" | grep Screenlet | awk '{print $10}')

    if [ -e $HOME/.screenlets_killed ] && [ "$SCRNLTS_RUN" -o "$RUN_BY_MNGR" ]; then
      rm $HOME/.screenlets_killed
    fi

      for m in $SCRNLTS_RUN; do
        if [ "$m" != "-u" ]; then
          echo $m >> $HOME/.screenlets_killed
          kill -9 $(ps -ef | grep -v grep | grep $m | awk '{print $2}')
        fi
      done

      for n in $RUN_BY_MNGR; do
        echo $n >> $HOME/.screenlets_killed
        kill -9 $(ps -ef | grep -v grep | grep $n | awk '{print $2}')
      done
  fi
}

restore_screenlets()
{
  if [ ! -z $SCRNLTS ]; then
    while [ "$(ps -o comm= -C $COMPIZ_BIN)" != "$COMPIZ_BIN" ]
    do
      sleep 2
    done
    
    if [ -e $HOME/.screenlets_killed ]; then
      while read LINE
      do
        exec $LINE > /dev/null &
      done < $HOME/.screenlets_killed
    else
      printf "\nUnable to restore Screenlets, $HOME/.screenlets_killed not found.\n"
    fi
  fi
}

AUTOSTART="$HOME/.config/autostart"
USE_MNGR="Use 'screenlets-manager' to add Screenlets to your autostart."

run_screenlets_from_autostart()
{
  if [ ! -z $SCRNLTS_AUTO ]; then
    if [ ! -d $AUTOSTART ]; then
      printf "$AUTOSTART does not exist, will be created.\n${USE_MNGR}\n\n"
      mkdir $AUTOSTART
      SCRNLTS_AUTO=no
    else
      SCRNLTS_FROM_AUTO=$(ls $AUTOSTART | grep Screenlet.desktop)
    fi

    if [ ! -z $SCRNLTS_AUTO ]; then
      if [ "x$SCRNLTS_FROM_AUTO" = "x" ]; then
        printf "\nNo Screenlets found in ${AUTOSTART}.\n${USE_MNGR}\n\n"
      else
        while [ "$(ps -o comm= -C $COMPIZ_BIN)" != "$COMPIZ_BIN" ]
        do
          sleep 2
        done
        for i in $SCRNLTS_FROM_AUTO ; do
          if [ "$(grep X-GNOME-Autostart-enabled $AUTOSTART/$i | cut -d = -f 2)" != "false" ]; then
            exec `grep Exec $AUTOSTART/$i | cut -d = -f 2` > /dev/null &
          fi
        done
      fi
    fi
  fi
}

run_compiz()
{
  if [ ! -z $OUTPUT ]; then
    exec $COMPIZ_WRAPPER 2>/dev/null
  else
    exec $COMPIZ_WRAPPER > /dev/null 2>&1
  fi
}

if [ ! -z $COMPIZ_RUNNING ]; then
  compiz_switch_inactive_icon
  kill_and_save_screenlets
  switch_wm
  compiz_switch_inactive_icon
else
  compiz_switch_icon
  run_screenlets_from_autostart &
  restore_screenlets &
  run_compiz
  compiz_switch_icon
fi

```

---

### Post by cjhabs on 2010-03-10
As you can see, I don;t know to much about this :-(

How about:
ps -elf | grep metacity
and likewise for compiz

---

### Post by sisco311 on 2010-03-10
try something like:
```
if [ $(pidof metacity) ]; do
  echo metacity
else
...
fi

```
or
```
[ $(pidof compiz) ] && echo "enabled" || echo "disabled" 
```

---

### Post by drewsus on 2010-03-10
ahhhh, thanks guys. Your musing put me on the right track.

this will give me what I want:
```
if [ $(pgrep -c metacity) -gt 0 ]; then
  echo "metacity is running"
elif [ $(pgrep -c compiz) -gt 0 ]; then
  echo "compiz is running"
fi
```

"pgrep -c" -> suppress normal output; instead print a count of matching processes.

The above works! 
Thanks for the help guys!
dRewsus

---

### Post by stinkeye on 2010-03-10
Could also use```
wmctrl -m | grep "Name" | cut -c7-
```
May need to install wmctrl.

---

### Post by drewsus on 2010-03-10
Ah yes, thats very nice too!

```
if [ $(wmctrl -m | grep "Name" | cut -c7-) == "Metacity" ]; then
	echo "Metacity is running"
	compiz-switch&
	docky&
elif [ $(wmctrl -m | grep "Name" | cut -c7-) == "compiz" ]; then
	echo "Compiz is running"
	killall docky
	compiz-switch&
fi
```

---

