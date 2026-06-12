---
title: "How do I setup windows games on ubuntu from .iso files?"
date: 2011-05-02
forum: General Help
---

### Post by projectfox on 2011-05-02
Please don't send me links to tutorials i've been going through them for days now, and please don't send to to other threads, i've read them all. Thank you.

---

### Post by edm1 on 2011-05-02
What game is it? Your best bet is to use PlayOnLinux or buy Cross-over linux or something equivalent. Then you'll either have to burn the iso to a DVD or mount the iso (google 'ubuntu mount iso').

Here is a list of games supported by PlayOnLinux: [http://www.playonlinux.com/repository/?cat=1](http://www.playonlinux.com/repository/?cat=1)

---

### Post by x C0MMAND0 x on 2011-05-02
This will not be possible with all games.  What games in particular are you trying to set up?  If you have an .iso of the games, do you have the original disc as well?

---

### Post by nerdy_kid on 2011-05-02
do this:

```

mkdir ~/drive
sudo mount -o loop PATHTOISO ~/drive
nautilus ~/drive/

```

and then, to unmount the iso:

```

sudo umount ~/

```

---

### Post by projectfox on 2011-05-02
Thanks this is my third day with linux. It's starcraft, I have the original CD, its just scratched beyond use but I backed up all my CD's a few years ago and I just copied the .iso to my desktop, if you could help me with terminal commands to access it and what each of the specific commands do that would be awesome: like how to mount it and what to do from there.

---

### Post by edm1 on 2011-05-02
Starcraft has only 3/5 stars with PlayOnLinux, which uses the WINE windows emulator with custom scripts for whatever program you are trying to install, so i cant guarantee it will run perfectly. Go to the software centre and search for and install 'playonlinux'. Open play on linux and click install then select starcraft from the menu and click apply. You will have to either mount the iso as nerdy_kid said (which will mount it to a folder called 'drive' in your home folder). Then select use playonlinux to select the setup file from the 'drive' folder. The rest should be self explanatory. If it doesnt work, i would recommend burning the iso to a dvd (using Brasero) and trying again.

Just to expand on what nerdy_kid said. in the terminal you will have to be in the folder that your iso is in. You do this with the cd (change directory) command. You will start in you home folder (called '~') so for example if you want to move to your Downloads folder type 'cd Downloads'. Type 'ls' to see what files are in the folder. To go back a folder type 'cd ..' A useful tip is that you can partially type the directory name or file name and press tab to complete it, speeds things up a bit.

---

### Post by x C0MMAND0 x on 2011-05-02
I would install PlayOnLinux from the software center and install it that way.  Much easier.

---

