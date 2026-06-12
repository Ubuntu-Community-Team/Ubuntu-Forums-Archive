---
title: "Thunar Custom Action to Change folder View Style?"
date: 2012-10-09
forum: General Help
---

### Post by holadebob on 2012-10-09
On Thunar if I change a view to icons, it is a global change. Can anyone suggest a method to write a custom action to fix the view in just the one folder and make it stay that way for just the one folder.

As we go back and forth switching views between folders that need a list view (large files) or ones that we would like icons, it gets a bit old. Doable, but old. :)

Maybe it's not possible, because I see nothing in Ubuntu forum history and Google. 

Thought one of you programmer types out there would crack it with a Custom Action.

Thank you

---

### Post by holadebob on 2012-10-10
No answer? Is the solution too complex for the result?

---

### Post by Merrattic on 2012-10-10
This might have some mileage, although is still two clicks to get there.

Install xdotool, then setup a custom action just for directories with this command:

for IconView:

```
xdotool key CTRL+1 %d
``` (and set appearance conditions to directories only)

Now when you right click on a directory you will be offered IconView and it changes to that. You can also right click in blank space to change the view. It's still global, but with a bit more scripting, and if only specific directories require a specific view, it should be possible to improve on this.

For example, you could use this code in the custom action so that only Pictures will change to IconView. 
```
if [ %n = Pictures ]; then xdotool key CTRL+1 %d;fi
```It's still global though :(

CTRL+2 gives DetailsView and CTRL+3 give CompactView so you could write additional custom actions for these as well

Separate windows of thunar will use different views

Alternatively, you could setup a shortcut on your desktop to open thunar at a particular directory you want in a particular view, and write a scipt that changes the contents of ~/.config/Thunar.thunarrc "LastView" before opening a thunar window. Just as an example:

```
#!/bin/bash
#opens thunar to a directory in IconView


if (grep -Fxq "DefaultView=void" ~/.config/Thunar/thunarrc); then

sed -ie 's/DefaultView=ThunarDetailsView/DefaultView=ThunarIconView/g' /home/user/.config/Thunar/thunarrc

fi


if (grep -Fxq "DefaultView=ThunarDetailsView" ~/.config/Thunar/thunarrc); then

sed -ie 's/DefaultView=ThunarDetailsView/DefaultView=ThunarIconView/g' /home/user/.config/Thunar/thunarrc

fi


if (grep -Fxq "DefaultView=ThunarCompactView" ~/.config/Thunar/thunarrc); then

sed -ie 's/DefaultView=ThunarDetailsView/DefaultView=ThunarIconView/g' /home/user/.config/Thunar/thunarrc

fi

thunar ~/Pictures

```

---

### Post by holadebob on 2012-10-10
I'll play around with that tonight, thanks for the ideas!

---

