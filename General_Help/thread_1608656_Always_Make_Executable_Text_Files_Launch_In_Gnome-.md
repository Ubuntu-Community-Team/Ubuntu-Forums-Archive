---
title: "Always Make Executable Text Files Launch In Gnome-terminal"
date: 2010-10-29
forum: General Help
---

### Post by johnathanamber on 2010-10-29
Hey everyone,

So I have a bunch of executable text files that allow us to connect to various VPN sites via vpnc.

What I want is for each of these files to automatically launch in the gnome-terminal instead of asking whether this should be run in the terminal, display the file or run it.

I have already tried to set the default behavior to run the executable text file... but it does not run in the terminal.

I've also tried to use the following to make it work:
> gnome-terminal -e echo "* Connecting to site via VPN...";sudo vpnc site; sleep 10

Any ideas?

Thank you very much,
Johnathan

---

### Post by ms4py on 2010-12-02
What about creating a launcher with "application in terminal"?

---

