---
title: "Fullscreening a youtube video - What to do when it crashes?"
date: 2012-06-06
forum: General Help
---

### Post by Mycotheologist on 2012-06-06
When I'm watching a flash video (i.e. youtube, google videos etc.) and have it on fullscreen, sometimes the screen freezes. If I hold alt+tab, the window selector screen comes up but if I select another window, the frozen video screen stays on top so theres no way out of it. I can press ctrl+alt+t to get the terminal up and kill processes (blindly since I can't actually see the terminal window) but I don't know which process I have to kill or restart to get the screen back to normal. Killing firefox doesn't work, in fact sometimes what causes the screen to freeze is firefox crashing.

---

### Post by brainwash on 2012-06-06
You should be able to [switch]("https://help.ubuntu.com/12.04/ubuntu-help/shell-workspaces-switch.html") to another workspace and open a new terminal. Now you have to kill the [plugin-container]("http://support.mozilla.org/en-US/kb/What%20is%20plugin-container") process to terminate the crashed Flash Player plugin:
```
killall plugin-containe
```

---

### Post by Mycotheologist on 2012-06-06
Thanks, I'll try this next time it happens. I never tried switching workspace. I can open up a new terminal when the screens frozen, I just can't see what I'm doing. I usually just run reboot now because I didn't know any processes to kill. I'll try killing plugin-container next time.

---

### Post by Mycotheologist on 2012-06-10
It happened again just there and switching workspace (using the hotkey CTRL + ALT + RIGHT) works but plugin-containe isn't even running so killing it doesn't work. Its not really a problem since its only workspace 1 that has a frozen screen now though.

---

### Post by brainwash on 2012-06-10
The playback of HTML5 videos might have caused the freeze and you will have to kill the Firefox process. Are you sure, that you were watching a Flash video? The plugin-container process (plugin-containe) should still be present after Flash Player has frozen the screen.

---

