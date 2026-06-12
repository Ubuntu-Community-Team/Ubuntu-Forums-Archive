---
title: "dzen2 Volume.sh"
date: 2011-04-05
forum: General Help
---

### Post by croatiangrn on 2011-04-05
Hi i have some problems with running this script:

# dvolbar - OSD Volume utility
#

#Customize this stuff
IF="Master"         # audio channel: Master|PCM
SECS="3"            # sleep $SECS
BG="#002206"        # background colour of window
FG="#00ff30"        # foreground colour of text/icon
BAR_FG="#00ff30"    # foreground colour of volume bar
BAR_BG="#005e12"    # background colour of volume bar
XPOS="595"          # horizontal positioning
YPOS="425"          # vertical positioning
HEIGHT="30"         # window height
WIDTH="250"         # window width
BAR_WIDTH="165"     # width of volume bar
#ICON=~/scripts/vol-hi.xbm
FONT="-*-zekton-medium-r-*-*-14-*-*-*-*-*-*-*"
#ICON_VOL=~/scripts/vol-hi.xbm
#ICON_VOL_MUTE=~/scripts/vol-mute.xbm
#ICON=$ICON_VOL

#Probably do not customize
PIPE="/tmp/dvolpipe"

err() {
  echo "$1"
  exit 1
}
VOL=$1
usage() {
  echo "usage: dvol [option] [argument]"
  echo
  echo "Options:"
  echo "     -i, --increase - increase volume by \`argument'"
  echo "     -d, --decrease - decrease volume by \`argument'"
  echo "     -t, --toggle   - toggle mute on and off"
  echo "     -h, --help     - display this"
  exit 
}   
    
#Argument Parsing
case "$1" in 
  '-i'|'--increase')
    [ -z "$2" ] && err "No argument specified for increase."
    [ -n "$(tr -d [0-9] <<<$2)" ] && err "The argument needs to be an integer."
    AMIXARG="${2}%+"
    ;;
  '-d'|'--decrease')
    [ -z "$2" ] && err "No argument specified for decrease."
    [ -n "$(tr -d [0-9] <<<$2)" ] && err "The argument needs to be an integer."
    AMIXARG="${2}%-"
    ;;
  '-t'|'--toggle')
    AMIXARG="toggle"
    ;;
  ''|'-h'|'--help')
    usage
    ;;
  *)
    err "Unrecognized option \`$1', see dvol --help"
    ;;
esac

#Actual volume changing (readability low)
AMIXOUT="$(amixer set "$IF" "$AMIXARG" | tail -n 1)"
MUTE="$(cut -d '[' -f 4 <<<"$AMIXOUT")"
VOL="$(cut -d '[' -f 2 <<<"$AMIXOUT" | sed 's/%.*//g')"
if [ "$MUTE" = "off]" ]; then
  ICON=$ICON_VOL_MUTE
else
  ICON=$ICON_VOL
fi

#Using named pipe to determine whether previous call still exists
#Also prevents multiple volume bar instances
if [ ! -e "$PIPE" ]; then
  mkfifo "$PIPE"
  (dzen2-gdbar -tw "$WIDTH" -h "$HEIGHT" -x "$XPOS" -y "$YPOS" -fn "$FONT" -bg "$BG" -fg "$FG" < "$PIPE"
   rm -f "$PIPE") &
fi

#Feed the pipe!
#(echo "$VOL" | gdbar -l "^i(${ICON})" -fg "$BAR_FG" -bg "$BAR_BG" -w "$BAR_WIDTH" -ss 1 -sw 4; sleep "$SECS") > "$PIPE"
(echo "$VOL" | dzen2-gdbar -l "$VOL% " -fg "$BAR_FG" -bg "$BAR_BG" -w "$BAR_WIDTH" -ss 1 -sw 4; sleep "$SECS") > "$PIPE"


when i type this in terminal ./volume.sh -t it says:

usage: dbar [-w <pixel>] [-h <pixel>] [-fg <color>] [-bg <color>] [-min <minvalue>] [-max <maxvalue>] [-l <string>] [-nonl] [-o]

any suggestions?? plz help :)

---

