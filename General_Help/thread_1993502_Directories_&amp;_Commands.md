---
title: "Directories &amp; Commands"
date: 2012-06-02
forum: General Help
---

### Post by dionysisthrax on 2012-06-02
I have been attempting to run everything on Ubuntu operating system exclusively through the command terminal. I have encountered largely two difficulties:

1. After inserting a command to execute a program like VLC or Skype, I can no longer enter commands in the same screen, as part of continuing my control over a single program.

2. I have attempted several times to launch VLC with a folder of mp3 files located in my external hard drive. This second problem has brought me to two problems. 
        2a. VLC will not launch a file from a folder in my directory marked "/media"
        2b. I cannot access any of my files from the external hard drives under the "/media" either as the root user or otherwise. I can see them listed after inserting the "ls" command but cannot access or open any of my external hard drives under the "/media" directory. 

Please help me. 
Thanks,
Dionysis

---

### Post by VCoolio on 2012-06-02
1. Append & after your command to put it to background and be able to continue using shell. If you're annoyed by output of backgrounded commands, use "command >/dev/null 2>&1 &". Or use screen, byobu or tmux to have several screens/buffers/tabs so you can switch easily while you only have one terminal.

2. That's weird. What output does "mount" give you? With what options is your device mounted? What exact command are you running and what is the output / error message?

---

### Post by Erden on 2012-06-02
1 - Ctrl+z, sends the program to the background, you could type the command fg to get the process back.

---

