---
title: "run command in gnome-terminal without it exiting"
date: 2010-05-04
forum: General Help
---

### Post by Kodpoet on 2010-05-04
I'd like to make a launcher that starts irssi in gnome-terminal with just one click.

I guess something like:

gnome-terminal -execute "irssi"

but without it closing down as soon as irssi is run :P

Ideas? ^^

---

### Post by gzarkadas on 2010-05-04
Put the call to irssi inside a script (say ~/bin/my-irssi) and append a `read -p "Press <Enter> to close window." ' line to it. For example:
```

irssi
read -p "Press <Enter> to close window."

```Make the script executable (with `chmod u+x ~/bin/my-irssi') and use it as the argument of the --command option to your gnome-terminal.

---

### Post by dcstar on 2010-05-05
> **Kodpoet said:**
> I'd like to make a launcher that starts irssi in gnome-terminal with just one click.

I guess something like:

gnome-terminal -execute "irssi"

but without it closing down as soon as irssi is run :P

Ideas? ^^

You can create a new Gnome Terminal profile with the option to leave the terminal open after the command runs, and then use that profile name in the launcher options.

---

### Post by 8Kuula on 2010-05-05
gnome-terminal --title=irssi --command "irssi"

---

### Post by Kodpoet on 2010-05-05
> **8Kuula said:**
> gnome-terminal --title=irssi --command "irssi"

Thank you all for the help, though 8kuula's version was by far the easiest :)


Thanks again! :KS

---

