---
title: "please help with cp command"
date: 2011-07-03
forum: General Help
---

### Post by meTroubled on 2011-07-03
i wish to copy one picture placed in **home** folder to **usr/backgrounds/share** to change my login screen.
how to do that...???

---

### Post by haqking on 2011-07-03
well i could tell you the command.

however i would like to encourage you to  use the man pages for a simple command like cp.

at terminal just type:

man cp

in future any command you wish to use just look it up in the man (manual) pages ;=-)

---

### Post by mutley89 on 2011-07-03
```
sudo cp ~/nameofpic /usr/backgrounds/share/    
```Are you sure it isn't /usr/share/backgrounds/ ? You need sudo because /usr is owned by root.

---

### Post by meTroubled on 2011-07-03
> **haqking said:**
> well i could tell you the command.

however i would like to encourage you to  use the man pages for a simple command like cp.

at terminal just type:

man cp

in future any command you wish to use just look it up in the man (manual) pages ;=-)


i already read it...
whenever i input command: 
```
cp home/neuron/pICS/wallpapers/Horror Gothic Scary/Horror HQ Wallpaper 47.jpg /usr/share/backgrounds/images
```i get this output:```
cp: target `/usr/share/backgrounds/images' is not a directory
```

---

### Post by meTroubled on 2011-07-03
> **mutley89 said:**
> ```
sudo cp ~/nameofpic /usr/backgrounds/share/    
```Are you sure it isn't /usr/share/backgrounds/ ? You need sudo because /usr is owned by root.
 
yeah,i missed that....but i put correct [command]("http://ubuntuforums.org/showpost.php?p=11007336&postcount=4")

---

### Post by haqking on 2011-07-03
> **meTroubled said:**
> i already read it...
whenever i input command: 
```
cp home/neuron/pICS/wallpapers/Horror Gothic Scary/Horror HQ Wallpaper 47.jpg /usr/share/backgrounds/images
```i get this output:```
cp: target `/usr/share/backgrounds/images' is not a directory
```

is there a images directory in the backgrounds directory ?

---

### Post by meTroubled on 2011-07-03
> **haqking said:**
> is there a images directory in the backgrounds directory ?

yes...

---

### Post by mikejonesey on 2011-07-03
please paste output of this command here;
```
ls -la /usr/share/backgrounds/images
```

---

### Post by meTroubled on 2011-07-03
> **mikejonesey said:**
> please paste output of this command here;
```
ls -la /usr/share/backgrounds/images
```

```
total 1344
drwxr-xr-x.  2 root root   4096 Apr 26 05:06 .
drwxr-xr-x. 10 root root   4096 Jun 16 18:48 ..
lrwxrwxrwx.  1 root root     37 Jun  4 05:39 default-16_10.png -> ../lovelock/default/wide/lovelock.png
lrwxrwxrwx.  1 root root     42 Jun  4 05:39 default-5_4.png -> ../lovelock/default/normalish/lovelock.png
lrwxrwxrwx.  1 root root     41 Jun  4 05:39 default.png -> ../lovelock/default/standard/lovelock.png
-rw-r--r--.  1 root root 555905 Sep  6  2006 earth_from_space.jpg
-rw-r--r--.  1 root root 331775 Sep  6  2006 flowers_and_leaves.jpg
-rw-r--r--.  1 root root 210576 Sep  6  2006 ladybugs.jpg
-rw-r--r--.  1 root root 187184 Sep  6  2006 stone_bird.jpg
-rw-r--r--.  1 root root  76470 Sep  6  2006 tiny_blast_of_red.jpg
```

---

### Post by meTroubled on 2011-07-03
finally i moved the path of my original image and renamed it.... 
     
 >     /home/neuron/pICS/wallpapers/image.jpg 
so i put the new string:
     
   >   cp /home/neuron/pICS/wallpapers/image.jpg /usr/share/backgrounds/images/image.jpg 
and it worked.....[IMG]http://static.linuxquestions.org/questions/images/smilies/biggrin.gif[/IMG]
why was it not working when my image was in    
     > /home/neuron/pICS/wallpapers/Horror Gothic Scary/Horror HQ Wallpapers47.JPG 
what did i miss in my previous commands...?
    
     >  cp /home/neuron/pICS/wallpapers/Horror Gothic Scary/Horror HQ Wallpapers47.JPG /usr/share/backgrounds/images/image.JPG

---

### Post by CatKiller on 2011-07-03
> **meTroubled said:**
> why was it not working?

Spaces. A command that can take several arguments can get confused by spaces. It treats the stuff after the space as a separate argument. You can tell it to treat the space as a actual space rather than as a separator for different arguments by "escaping" it with the \ character (which also works for other characters, like ?) like so:
```

cp /home/neuron/pICS/wallpapers/Horror\ Gothic\ Scary/Horror\ HQ\ Wallpapers47.JPG /usr/share/backgrounds/images/image.JPG
```

Or you can get into the habit of Tab-completion, which is very neat. You just start typing and then press Tab to have the shell complete the filename or command as much as it can. If there's more than one way to complete what you've already typed, the shell will complete the common part and then stop until you've typed in enough more to identify which one it is that you want. Pressing Tab twice in quick succession will give a list of the ways that the string can be completed. It's much quicker to do than to type out a description :)

---

### Post by SeijiSensei on 2011-07-03
> **meTroubled said:**
> what did i miss in my previous commands...?

The file you were copying had embedded spaces.  The shell treats any spaces as command delimiters.  You have two options to avoid this problem in the future:

1) Put the filename in quotes like this:

```

cp '/home/neuron/pICS/wallpapers/Horror Gothic Scary/Horror HQ Wallpapers47.JPG' /usr/share/backgrounds/images/image.JPG 

```

2) "Escape" the spaces with backslashes like this:

```

cp /home/neuron/pICS/wallpapers/Horror\ Gothic\ Scary/Horror HQ Wallpapers47.JPG /usr/share/backgrounds/images/image.JPG 

```

My advice is to avoid giving files names with embedded spaces; use hyphens or underscores as connectives.

---

### Post by meTroubled on 2011-07-03
thanks......i figured it out now...!!

---

