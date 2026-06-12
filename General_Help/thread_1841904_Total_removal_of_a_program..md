---
title: "Total removal of a program."
date: 2011-09-10
forum: General Help
---

### Post by noahdiehl on 2011-09-10
Hello,

I have just set up a dual boot system and use GRUB to pick the OS to boot to. I wanted to jazz up GRUB a bit and installed "super-boot-manager"... when I opened it I was a little too excited and accidentally picked French as a language... I must have been craving a croissant or something... so I uninstalled and reinstalled... but it now skips the part when I pick an language and goes right into French... ah non. I am guessing when I uninstall some little parts of the program must be left that are keeping the French language setting. Any idea on how I can totally kill this install so it might prompt me for a language setting again?

I just want to easily add a background image (found how to do that I think) and change the colors... messing with code in the Terminal is kind of a last resort... I could do it but it's would just be a lot of copy and pasting as I try different colors and looking up hex codes for colors.... so figured "super-boot-manager" would be a good tool.

Thanks for an help you folks can give.

---

### Post by aeronutt on 2011-09-10
Configuration files for programs are typically stored somewhere in your home directory. Usually in a ".applicationname" sort of file, many times in the .config directory (but certainly not always).

Try ```
ls -R ~/.* | grep super
```

Where the word 'super' is trying to find files related to the application super-boot-manager.

Once you find the associated directory and/or files, just delete them. (But confirm they are for super-boot-manager.

---

### Post by claracc on 2011-09-10
To remove a program including configuration files:

You open a xterm and write: sudo apt-get purge name_of_the_program, then enter your password when it is required by command line.

---

### Post by philinux on 2011-09-10
> **claracc said:**
> To remove a program including configuration files:

You open a xterm and write: sudo apt-get purge name_of_the_program, then enter your password when it is required by command line.

Unfortunately, or maybe it is the correct way, but purging does not remove the .app config files in a users home directory.

---

### Post by noahdiehl on 2011-09-10
"ls -R ~/.* | grep super" did not seem to actually do anything in the Terminal. I tried purging and when I reinstalled, still had French by default.... blah!... I ended up using Grub Customizer, but I would like to figure out how to do this in case I need to in the future and anyone would like me to try something else.

Thanks for your help!

---

### Post by aeronutt on 2011-09-10
Try

```
ls -R ~/.* | grep -i boot
```
and

```
ls -R ~/.* | grep -i manager
```
and

```
ls -R ~/.* | grep -i super
```

Although if these show files, be careful that they are associated with super-boot-manager before you delete them. All this is doing is looking for files of a specific name in the tree of your home directory.

---

### Post by Enigmapond on 2011-09-10
If all the above doesn't help...Learn French..:lolflag:.....sorry I was compelled.:-\"

---

### Post by claracc on 2011-09-11
> Unfortunately, or maybe it is the correct way, but purging does not remove the .app config files in a users home directory. 

Thanks, I didn't know.

---

### Post by agillator on 2011-09-11
It sounds like it is time for the bigger hammer approach. I know nothing about the actual program you are having trouble with, but the procedure is the same. Find the filename of the program from the command you use to run it, from a menu, or somewhere. Or guess at part of it (super?). Then use the find command, for example sudo find / -name "super*.*". Be patient. You might also try searching for hidden files (sudo find / -name ".super*.*") and other variations. As a result of the various finds you now have the information to REALLY screw up your machine. Go through the results carefully and see if you can find a configuration file or some other file that looks suspicious. You might try reading the file if you think you may have found one; configuration files in Linux are normally text files. Remember you probably have enough information to totally destroy your system, so proceed with extreme care! If you find something, try changing the name and see what happens. If something unpleasant happens you can boot with a live CD (you have one, right?) and change it back, but be very careful. Don't change things willy nilly or you will be reinstalling.

---

### Post by aeronutt on 2011-09-11
It looks like super-boot-manager may go by the acronym "sbm" or "buc". (See here, and notice 'buc' in the title window: [http://www.unixmen.com/linux-tutorials/1735-super-boot-manager-great-tool-to-manage-burg-grub2-and-plymouth-in-ubuntu](http://www.unixmen.com/linux-tutorials/1735-super-boot-manager-great-tool-to-manage-burg-grub2-and-plymouth-in-ubuntu)) 
You might retry all the above search commands with sbm and buc as the key word.

I also found this at [http://www.unixmen.com/software/1072-burg-manager-install-and-configure-burg-the-easy-way](http://www.unixmen.com/software/1072-burg-manager-install-and-configure-burg-the-easy-way) under 'known issues'. Note the .burg-manager files that need to be removed to purge:


[B]If you have already installed any previous version of burg-manager and now you have installed version 1.0.5, if burg-manager doesn&#8217;t start, purge it executing:

1- remove previous version :

sudo apt-get purge burg-manager

sudo rm -rf ~/.burg-manager

sudo rm -rf /root/.burg-manager[/B][/I][/I]

---

