---
title: "Is it possible to bind a script to a key shortcut?"
date: 2009-10-10
forum: General Help
---

### Post by kajman on 2009-10-10
For e.g. combinations like Ctrl+Shift+LETTER or Ctrl+Alt+End (or some other functional character) and possibly the FnKey+F1-F12 (functional key on laptop computers)?

I'd be very happy to be able to do so :) thanks in advance for all the answers.

---

### Post by delcypher on 2009-10-10
OOPS really sorry just noticed you're using kubuntu, so you're using KDE... I'll leave these instructions here anyway.
In principle it should be similar to the way I described below.

Have a look at this, it may help you [http://hygen.net/blog/?p=519]("http://hygen.net/blog/?p=519")


Yes it is possible.

Once you've made your script (in these examples the script is located at /home/ben/myscript.sh) and made it executable (using chmod)
NOTE: I'm assuming you wrote a bash script, if you used something like python or perl then replace bash with the appropriate program.

GNOME:
1. Go to System > Preferences > Keyboard Shortcuts
2. Click the Add button
3. Choose a Name for your shortcut (can be just about anything)
4. Type "bash" followed by the absolute path to your script.
```
bash /home/ben/myscript.sh
```
If you want to be able to see your script running.
5. If you scroll to the bottom of the list you will see a section marked "Custom Shortcuts"
6. Click on it and press your key combination

If you want to see your script running when you press the shortcut key then
1. run gnome-terminal
2. Edit > Profile Preferences
3. choose "Title and command " tab
4. Set "When command exits" to "Hold the terminal open"
5. Now set your keyboard shortcut command to
```
gnome-terminal --command /home/ben/myscript.sh
```

and you're done!

---

### Post by kajman on 2009-10-10
Thank you very much!
It worked fine and was very easy to do (a pity I didn't do it myself).

Thanks again :)

---

