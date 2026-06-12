---
title: "Custom Bash Prompt Line Wrap Issue"
date: 2009-10-07
forum: General Help
---

### Post by trumpeteersman on 2009-10-07
I have made this useful bash script that I can't seem to fix.  It actually has the same problem as other custom prompts I have made over the years: Bad Line Wrapping.  I have searched around for years and none of the proposed fixes seem to apply to my situation.

This is in my .bashrc
```


shopt -s checkwinsize

#Defining Colors Used
RED='\e[0;31m'
REDWARNING='\e[4;31m'
GREEN='\e[0;32m'
YELLOW='\e[1;33m'
ORANGE='\e[0;33m'
BLUE='\e[0;34m'
MAGENTA='\e[0;35m'
WHITE='\e[0m'
GREY='\e[1;30m'

myprompt()
{
#VARS
REM=`awk '/remaining capacity/ { print $3 }' /proc/acpi/battery/BAT0/state`
LAST=`awk '/last full/ { print $4}' /proc/acpi/battery/BAT0/info`
CHARGESTATE=`awk '/charging state/ { print $3 }' /proc/acpi/battery/BAT0/state`
SPACE=`df -h | awk 'NR==2{ print $4 }'`
MEMTOT=`free -m | awk 'NR==2{print $2}'`
MEMUSED=`free -m | awk 'NR==3{print $3}'`

CHARGEPERCENT=`echo $REM $LAST | awk '{printf "%d", ($1/$2)*100'}`


case "${CHARGESTATE}" in
   'charged')
   CHARGECOLOR="$GREEN+"
   ;;
   'charging')
   CHARGECOLOR="$YELLOW+"
   ;;
   'discharging')
   if [ "$CHARGEPERCENT" -le "30" ] ; then
     CHARGECOLOR="$REDWARNING-"
   else
     CHARGECOLOR="$YELLOW-"
   fi
   ;;
esac

MEMPERCENT=`echo $MEMTOT $MEMUSED | awk '{printf "%d", ($2/$1)*100'}`

if [ $MEMPERCENT -ge "90" ] ; then
   MEMCOLOR=$RED
else
   MEMCOLOR=$MAGENTA
fi

echo -e "$GREY|${CHARGECOLOR}${CHARGEPERCENT}%$GREY|$ORANGE${SPACE}$GREY|${MEMCOLOR}${MEMPERCENT}%$GREY|"

}

PS1="${debian_chroot:+($debian_chroot)}\$(myprompt)$BLUE\w$WHITE\$ "



```

[IMG]http://img12.imageshack.us/img12/6674/69590688.png[/IMG]

The custom prompt works very well except for the line-wrap-overlap issue.  The CHARGEPERCENT changes color depending on charge and also has a +\- depending on if plugged in to AC.  The prompt also gives available space and memory used.

But it overlaps like this:
[IMG]http://img223.imageshack.us/img223/6007/36960483.png[/IMG]
to this:
[IMG]http://img29.imageshack.us/img29/8701/77868496.png[/IMG]

Another Example:
[IMG]http://img28.imageshack.us/img28/4233/36617003.png[/IMG]
to this:
[IMG]http://img28.imageshack.us/img28/8007/13838669.png[/IMG]
to this:
[http://img243.imageshack.us/img243/6948/91092830.png]("http://img243.imageshack.us/img243/6948/91092830.png")
to this when I go to the beginning and start typing:
[http://img243.imageshack.us/img243/420/62101361.png]("http://img243.imageshack.us/img243/420/62101361.png")

Because of that overlap, all of the text gets jumbled and I cannot see long commands to edit them.

Does anyone understand enough bash to fix this script?

---

### Post by trumpeteersman on 2010-03-07
Anybody?

There has to be a better way to have nice prompts than the current bash mess.

---

### Post by asmoore82 on 2010-03-07
W0W that is a really impressive prompt.

I'm on the case :KS ...

---

### Post by asmoore82 on 2010-03-07
There seems to be some unresolved issues with a "live" prompt command that issues
terminal control signals. You could use the PROMPT_COMMAND to work around this.

Also, non-printing characters within a prompt should be enclosed in \[ and \].

Replace your PS1 line with these 2:
```
PROMPT_COMMAND='myprompt'
PS1="\[$BLUE\]\w\[$WHITE\]\$ "
```
^you also have to change the `echo -e` line to `echo -ne` to complete the illusion.

The only glitches I've seen out of this method so far are
control+L clearing and control+R searching.

---

### Post by asmoore82 on 2010-03-07
You could change the `df` command to this: ```
df -h . | ...
```
So that it will always show the free space on the partition of the PWD.
Great if you have /home on a separate partition :D.

---

### Post by dcstar on 2010-03-08
> **trumpeteersman said:**
> I have made this useful bash script that I can't seem to fix.  It actually has the same problem as other custom prompts I have made over the years: Bad Line Wrapping.  I have searched around for years and none of the proposed fixes seem to apply to my situation.

This is in my .bashrc
```

.....
echo -e "$GREY|${CHARGECOLOR}${CHARGEPERCENT}%$GREY|$ORANGE${SPACE}$GREY|${MEMCOLOR}${MEMPERCENT}%$GREY|"

}

PS1="${debian_chroot:+($debian_chroot)}\$(myprompt)$BLUE\w$WHITE\$ "



```
......
Because of that overlap, all of the text gets jumbled and I cannot see long commands to edit them.

Does anyone understand enough bash to fix this script?
What happens with:

```
echo -**n**e "$GREY|${CHARGECOLOR}${CHARGEPERCENT}%$GREY|$ORANGE${SPACE}$GREY|${MEMCOLOR}${MEMPERCENT}%$GREY|"

```

---

### Post by trumpeteersman on 2010-03-08
> **asmoore82 said:**
> There seems to be some unresolved issues with a "live" prompt command that issues
terminal control signals. You could use the PROMPT_COMMAND to work around this.

Also, non-printing characters within a prompt should be enclosed in \[ and \].

Replace your PS1 line with these 2:
```
PROMPT_COMMAND='myprompt'
PS1="\[$BLUE\]\w\[$WHITE\]\$ "
```
^you also have to change the `echo -e` line to `echo -ne` to complete the illusion.

The only glitches I've seen out of this method so far are
control+L clearing and control+R searching.

THANK YOU!!  That fixes it!
I don't think I knew about the PROMPT_COMMAND.  This actually allows me to enclose the non-printing characters without disabling the prompt.

The glitches are fine with me.  I use 'clear' instead of crtl-l anyway. ;) And it only disables the prompt until a new command is entered, so it is still usable.

I am glad that the fix was simple, I was worried that I suck more at scripting than I thought. :P

And the 'df -h .' for PWD is an brilliant addition.  I was almost thinking of adding a 'du -hcs' for PWDs, but I like a small prompt.

Thank you again.

Thank you for the help!

---

