---
title: "Compiz command/Keyboard shortcut not accepting a custom script with argument"
date: 2011-07-08
forum: General Help
---

### Post by quantdev on 2011-07-08
Hello,

I made a bash script that accepts a single argument.  I went to Compiz Command plugin and assigned a keybinding to it.  It does not work.  When I enter the command and the argument in the terminal, everything works fine.  When I modify the script so that the argument is not needed (i.e. hard-coded into the script), it works fine, too.  So it seems like the argument is not accepted properly.  I tried with default gnome keybinging (System > Keyboard Shortcuts) and that does not work either.  I am thinking I am doing something wrong.  I am attaching the script if that helps.  (The script uses xdotool to shift focus, BTW.)

```

eval $(xdotool getactivewindow getwindowgeometry --shell)
echo $1
if [ $1 == 'up' ]; then
        dX=0;
        dY=-50;
elif [ $1 == 'down' ]; then
        dX=0;
        dY=$HEIGHT+50;
elif [ $1 == 'left' ]; then
        dX=-50;
        dY=0;
elif [ $1 == 'right' ]; then
        dX=$WIDTH+50;
        dY=0;
fi
xdotool mousemove $(($X+$dX)) $(($Y+$dY)) click 1

```

Oh, as you can see, I have an echo statement in the script.  Where is the logging file that has the stdout of gnome environment?

Thanks.

---

### Post by CaptainMark on 2011-07-08
i dont think its possible to do this, its running the command in the background without arguments, i could be wrong because ive never actually used this compiz plugin but you could use the command ```
gnome-terminal -x /path/to/your/script
```attached to a keybinding and in the script use bash's read function to accept user input as a variable

---

### Post by quantdev on 2011-07-08
Thanks for your reply.  I forgot to note that arguments are accepted perfectly fine for regular xdotool command.  The following code works as attached to a keybinding.

```

xdotool getactivewindow windowmove  2048 0

```

Seems like I am doing something silly and wrong here...

---

