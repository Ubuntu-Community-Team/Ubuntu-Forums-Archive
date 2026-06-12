---
title: "Winecfg not doing anything&gt;"
date: 2006-06-16
forum: General Help
---

### Post by kewldude606 on 2006-06-16
I'm trying to set up wine.  I'm reading all these guides and they say to run winecfg in the Terminal and then click on this or that tab.  Now, when I run winecfg in the terminal, this is the output:```
wine: creating configuration directory '/home/daniel/.wine'...
```(daniel is my username).  It doesn't go back so that you can type in a new command but I can type in random words and stuff.

Also, whenever I run winecfg a new file is created in my home directory.  They are named .wine-[a-zA-Z0-9]{6} for example: .wine-1hgB6z and .wine-2E5WPF .wine-EfJuW2 .wine-H1sW6j .wine-HhCFR2 .wine-K6KfeR .wine-nBvrdn .wine-pN5XFv (those are the actual folders out of my home dir).

At first I thought this was a problem with my wine install, so I uninstalled it and then reinstalled from the repositories (I followed the directions on winehq and added wine's repository).  That still didn't work so I build from source (still using apt-get) and it still didn't work.

Please help me!  I really want to run [uTorrent]("http://utorrent").

---

### Post by kewldude606 on 2006-06-17
No replies yet?  I take it this is not the expected behavior?

---

### Post by s_h_a_d_o_w_s on 2006-06-17
Maybe you should try to install it with automatix. That's how I got it and i've never had any poblems. Once automatix installs it, winecfg should works. Be sure to rebott though....


hope that has helped you, or as they say in french:
J'espere que ca t'a aide

---

### Post by kewldude606 on 2006-06-17
I hope that this helped you?  Did I translate that right?  Oh...just now I see that line above.  I'm in French 2 (and its the end of the school year).

But the same thing happened when I installed with Automatix.

---

### Post by kewldude606 on 2006-06-21
I have a solution!
Run this command:```
WINEPREFIX=~/.wine wineprefixcreate
```
Wait a little bit, then exit that terminal and open up a new terminal.  Run the command again.    Now you should be able to use winecfg.

---

