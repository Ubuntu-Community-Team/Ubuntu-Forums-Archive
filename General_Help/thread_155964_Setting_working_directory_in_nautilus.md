---
title: "Setting working directory in nautilus?"
date: 2006-04-06
forum: General Help
---

### Post by schilcha on 2006-04-06
Applications launched through nautilus always have the working directory set to ~ (the users home). In quite a few cases, this is pretty annoying.

Two examples:
I open a text-file in gvim via nautilus. When I save the file with a new name it is dropped into my home.
I choose to open a .dvi file with dvips. The resulting .ps file is again dropped to my home and all graphics are missing, since they cannot be found anymore.

What I could do is writing a nautilus-script for each application that needs the working directory to be set properly. This would be really annoying -- basically I wouldn't need the "open-with" function anymore but would have to wrap any application with a script.

Is there an easier way to tell nautilus to lauch the application in the directory the currently selected file (the one I want to open) is located in?

Thanks a lot in advance!

---

### Post by dcstar on 2006-04-06
[QUOTE=schilcha]
......
Is there an easier way to tell nautilus to lauch the application in the directory the currently selected file (the one I want to open) is located in?

Thanks a lot in advance![/QUOTE]
In a Nautilus script you create to launch the app, have:
```
cd $NAUTILUS_SCRIPT_CURRENT_URI
exec $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS

```
This might do what you want (I haven't tested it........)

---

### Post by schilcha on 2006-04-06
Thanks for the hint. Unfortunately, I couldn't get this to work. Here's my script:

```

NAUTILUS_SCRIPT_CURRENT_URI=`echo $NAUTILUS_SCRIPT_CURRENT_URI | sed -e "s/^file:\/\///"`
cd $NAUTILUS_SCRIPT_CURRENT_URI

exec $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS

```
I use sed to strip off the leading "file://" from _CURRENT_URI. I guess my problem is that I do not understand what you had in mind when writing the second line (exec ...). Did you mean bash's exec command or is it just a placeholder for the executable? If so, I would need to wrap each command in a script like this. Would I?

What seems to happen is that the script changes into the correct directory, but nautilus doesn't give a damn.

BTW, I tried it with and without the "#!/bin/sh" preamble in the script's first line.

Thanks

---

