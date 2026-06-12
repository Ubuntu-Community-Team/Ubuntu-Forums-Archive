---
title: "cannot find location: $HOME/.gnome2/nautilus-scripts/"
date: 2011-04-04
forum: General Help
---

### Post by heikodachi on 2011-04-04
I am trying to install google-docs-fs which entails copying a file into the following location: $HOME/.gnome2/nautilus-scripts/

I cannot find/do not know how to find the location.

Any help with this would be very much appreciated.

---

### Post by matt_symes on 2011-04-04
Hi

> **heikodachi said:**
> I am trying to install google-docs-fs which entails copying a file into the following location: $HOME/.gnome2/nautilus-scripts/

I cannot find/do not know how to find the location.

Any help with this would be very much appreciated.

It's a hidden directory in your home folder.

From the menu Places->Home folder.

From the file browser menu.

View->Show hidden files.

You should then be able to see the folder.

Kind regards

---

### Post by coffeecat on 2011-04-04
$HOME is shorthand for /home/yourusername. And the .gnome2 folder is a hidden one in your home folder.

Open your home Nautilus and press ctrl-H to reveal hidden files. You'll then see the .gnome2 folder. Double-click on that and there's the nautilus-scripts folder.

---

### Post by heikodachi on 2011-04-04
Great, thanks for your help. I have copied the script into the folder.

The README says that 'I might have to give permission to this file'. Do you know how I can give permission?

Thanks again.

---

### Post by coffeecat on 2011-04-04
What exactly does the README say? "I might have to give permission to this file" doesn't quite make sense. Does it tell you to make it executable?

---

### Post by heikodachi on 2011-04-04
Yes execute permission.

'Just copy "Send To GDoc" file to $HOME/.gnome2/nautilus-scripts/
You might have to give execute permission to this file.
Restart nautilus.'

---

### Post by coffeecat on 2011-04-04
You can do it from the terminal with chmod or from the GUI. How about the GUI? :)

Right-click on the file > Properties > Permissions tab > tick the execute box.

---

### Post by heikodachi on 2011-04-04
Brilliant! Thanks for your help!

---

