---
title: "Missing/invisible power button icon in Natty"
date: 2011-05-16
forum: General Help
---

### Post by insert_name_here on 2011-05-16
My power button icon on the toolbar in Unity is invisible -- that is, it occupies the far right-most column of pixels and displays no icon. (See attached screenshot -- the power button menu only comes up with the mouse all the way to the far right (where you can't really see it in the screencap.)).

Any idea how to get it back? It's not a big deal, but it'd be nice to avoid being made fun of by my OS X/Wind0ze-using friends for having an invisible power button... :)

I have Natty installed, but using the same /home (and thus the same config files) from previous installs. Might that be the problem?

---

### Post by Lex Luthor on 2011-05-31
Have you tried to change the system theme ?

I also have a problem with this button, but mine is inexistent. I cannot even open the menu. I've tried to remove all .gnome*, .local, .config from my home to reset the interface but it does not shows.... what can I do ?

Thanks....

---

### Post by nzjethro on 2011-05-31
To restore your panels to default (which will likely bring back the power button, but will lose other launchers on your panel), use:```
sudo debconf gnome-panel
```
Then you can re-add the launchers you want. Kindof a messy fix, but try it as a last resort.

---

### Post by Lex Luthor on 2011-05-31
But this is not gnome-panel, it is unity... 

Typing this command gives me gnome panel active, over the unity panel...

I also realized that a lot of programs that are running does not shows on notitfication area (that apeared when I typed this command), like fusion icon, googlesystray, etc...

Here are both of them. Notice the gnome-panel has much more icons on notification, from the programs on memory...

Unity-panel:
[IMG]http://img18.imageshack.us/img18/4075/unitypanel.png[/IMG]

Gnome-panel (After typing debconf gnome-panel):
[IMG]http://img62.imageshack.us/img62/6630/gnomepanel.png[/IMG]

---

### Post by Frogs Hair on 2011-05-31
Mistake , I will check for the proper package name

---

### Post by Frogs Hair on 2011-05-31
Try reinstalling the indicator-session  for the synaptic package manager and restart.

---

### Post by Lex Luthor on 2011-05-31
Thankyou !!!! It worked. I was trying to search for this package and didn't find.
In my case, it was not installed ! just reinstalled and it was there.


About the notification area, I found the solution:
```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
```

This make the magic...

Thanks again !

---

### Post by insert_name_here on 2011-07-01
No luck for me. Setting systray.whitelist to ['all'] just showed a bunch of superfluous icons, but not the power icon. Oh well.

---

### Post by 192709 on 2011-07-27
for met it worked perfectly:

sudo apt-get remove indicator-session 
sudo apt-get install  indicator-session 
sudo init 6

and I found a power menu as it should be ...

Thank you!
192709

---

