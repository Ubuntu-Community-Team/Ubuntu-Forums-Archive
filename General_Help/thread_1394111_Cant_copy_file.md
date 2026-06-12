---
title: "Cant copy file"
date: 2010-01-30
forum: General Help
---

### Post by hephaestus69 on 2010-01-30
I just got utorrent working and i need to place the file from my desktop to /usr/local/bin/ but when i do it says permission denied. So i tried sudo cp /home/username/Desktop/uTorrent /usr/local/bin/ but when i do that the terminal just shows > and just sits their and no commands work after that. Can someone tell me a alternative way or tell me why the terminal is doing this?

---

### Post by lykeion on 2010-01-30
Well, it shouldn't be a problem to copy a file to /usr/local/bin
Maybe you made some typo?
```
sudo cp ~/Desktop/uTorrent /usr/local/bin
<enter your password>
```
A tip: I would dish uTorrent and use Transmission instead. It's a superior bittorrent-client for Ubuntu.

---

### Post by pbrane on 2010-01-30
Are you sure that ~/Desktop/uTorrent is the complete path to the file name? If you are trying to copy a directory you should either move ( mv ) or cp -R the directory. The '>' after you hit enter indicates that the command is not complete. That is a command continuation prompt.

Also CTRL+C will cancel a command so you can get your terminal prompt back.

---

### Post by hephaestus69 on 2010-01-30
thanks pbrane you were right it was the wrong directory. LOL

---

