---
title: "Gnome Terminal"
date: 2011-10-19
forum: General Help
---

### Post by Chriske on 2011-10-19
Just out of interest, I wonder if anybody knows how long Gnome Terminal retains previously entered commands? I'm referring to the entries it will bring up if one presses the keyboard up arrow.

I imagined it just retained anything entered in the current session and would lose any data after closing, but now I'm not so sure and believe it retains commands for longer.

Thank you.

---

### Post by SNIFFER_dog on 2011-10-19
I'm not really sure, but you can look at the .history file located in your home directory and that lists all the terminal commands you have used in the past. I think the history is set-up to not save similar commands next to exch other.

If you want to enter one of these commands in the terminal type ! followed by the line number of the command. You may have to tick a box in your editor to see the line numbers.

For example, if your history was like this:
```
1 ls
2 cd /Public
3 ls -a

```And in the terminal your type:
```
!3
```This will resolve too 'ls-a' in the terminal.

If you look at the .bashrc file in your home directory you will be able to see how your terminal is configured once you get round all the codes in there. They are well documented online.

As for how much it remembers, I'm not really sure as it seems to depend on how many terminals you might run at once. But after a reboot, you can scroll up and get commands you have entered before and I'm sure that comes from the history file.

Typing Ctrl + r in the terminal will give you a quicker way of accessing commands you have typed before, just type the first few letters of the command and it should auto fill what you have typed before.

Hope this helps

Regards

SNIFFY

---

### Post by mcduck on 2011-10-19
It's not actually Gnome-terminal that saves the command, but Bash itself.

The default setting seems to be 1000 last commands, or alternatively max history file size of 2000. The settings are configured in your ~/.bashrc file, so if you want to change them just edit the HISTSIZE and HISTFILESIZE variables there.

edit: HISTSIZE value is the number of commands saved, and HISTFILESIZE is the maximum amount of *lines* to be saved in the file. You can see "man bash" for more details.

---

### Post by Chriske on 2011-10-19
Thank you both for those excellent replies! :P

Much appreciated, I'm off to investigate now.

---

