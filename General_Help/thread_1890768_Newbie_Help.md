---
title: "Newbie Help"
date: 2011-12-04
forum: General Help
---

### Post by gman3000000 on 2011-12-04
Hi I'm new to Linux making the move from win7 as just getting on my nerves, I need some help.

Trying to install fire starter, and i need to change the log settings in the confg file but I can save it as I don't have permissions how can I correct this?

Also Im trying to install ms fonts but this not working either??

Running Ubuntu 11.10

Thanks

---

### Post by MG&amp;TL on 2011-12-04
MS fonts-

Open a terminal, and type:

```
sudo apt-get install ubuntu-restricted-extras
```

Then press RETURN and enter your password. (you won't be able to see it)

Then wait for the text to stop scrolling.

---

### Post by gman3000000 on 2011-12-04
Thanks for reply, how will i know if this has worked?

---

### Post by carranty on 2011-12-04
> **gman3000000 said:**
> 
Trying to install fire starter, and i need to change the log settings in the confg file but I can save it as I don't have permissions 

You shouldn't need to change anything in the config file to install firesterter, simply open a terminal and type

```
sudo apt-get install firestarter
```

and then run it by typing

```
gksudo firestarter
```

As to how you know if installing the fonts worked, just check to see if the font you want is now available....

---

### Post by gman3000000 on 2011-12-04
When I try to run firestart there is an error to do with the log file, I googled it and found that I need to change some setting in config file.

Cant get ms fonts to show done as mentioned gone to libre office nothing there??

---

### Post by carranty on 2011-12-04
Try

```
sudo apt-get install msttcorefonts
```

---

### Post by carranty on 2011-12-04
> **gman3000000 said:**
> When I try to run firestart there is an error to do with the log file, I googled it and found that I need to change some setting in config file.

Please type 

```
gksudo firestarter
```

into a terminal and paste the output to this thread

---

### Post by gman3000000 on 2011-12-04
> **carranty said:**
> Please type 

```
gksudo firestarter
```

into a terminal and paste the output to this thread
Failed to open the system log

---

### Post by gman3000000 on 2011-12-04
> **carranty said:**
> Try

```
sudo apt-get install msttcorefonts
```
Have tired no luck?? whats going on??

---

### Post by carranty on 2011-12-04
> **gman3000000 said:**
> Failed to open the system log

Ok, so post #2 in this link
  
[https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/776361](https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/776361)

should sort you out.  To edit the file, you'll need superuser privileges, 

```
gksudo gedit *file*
```I'm not sure why libreoffice can't see the fonts.  Is there a specific font you are after?

---

### Post by gman3000000 on 2011-12-04
> **carranty said:**
> Ok, so post #2 in this link
  
[https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/776361](https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/776361)

should sort you out.  To edit the file, you'll need superuser privileges, 

```
gksudo gedit *file*
```I'm not sure why libreoffice can't see the fonts.  Is there a specific font you are after?
How do i get superuser privileges,?

Arial font

---

### Post by MG&amp;TL on 2011-12-04
Superuser privlieges:

-Anything with sudo, gksu, or gksudo, will all raise you to superuser. So you don't have to worry.

---

### Post by gman3000000 on 2011-12-04
> **MG&TL said:**
> Superuser privlieges:

-Anything with sudo, gksu, or gksudo, will all raise you to superuser. So you don't have to worry.
Sorry for all question I'm trying to edit the file by navigating via home folder, so how do I gain permmisons can you explain please.

Thanks

---

### Post by MG&amp;TL on 2011-12-04
Open a terminal and run:

```
gksu nautilus
```

You will then have a filebrowser with root privileges. :)

Breakdown:

gksu-raises you to root graphically

nautilus-ubuntu's default file browser.

---

### Post by BC59 on 2011-12-04
I don't know if you understood that you have to run the commands on a terminal as explained above.

The terminal is a command line which is opened usually by pressing ALT+CTRL+T, then you copy the commands the mentioned and paste them inside, with right click paste or SHIFT+CTRL+V.

---

### Post by gman3000000 on 2011-12-04
> **MG&TL said:**
> Open a terminal and run:

```
gksu nautilus
```

You will then have a filebrowser with root privileges. :)

Breakdown:

gksu-raises you to root graphically

nautilus-ubuntu's default file browser.
Are  root privilege set all the time now? and if so how do I close it again?

---

### Post by MG&amp;TL on 2011-12-04
Nope, ubuntu uses sudo (superuser do (this)) which means that as soon as you close whatever you are doing (the command exits, basically), sudo is unset.

See here:  [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by oldos2er on 2011-12-04
> **gman3000000 said:**
> Trying to install fire starter,

Why?

Firestarter is no longer being developed, it really should be removed from the repositories. UFW and its GUI version GUFW are the best iptables front-ends to use now, but if you're not running any services, you most likely don't need to use it. See [http://ubuntuforums.org/showthread.php?t=1871177](http://ubuntuforums.org/showthread.php?t=1871177) and [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Oh, and if you decide to use UFW, it only needs one command ```
sudo ufw enable
```

---

### Post by gman3000000 on 2011-12-04
> **oldos2er said:**
> Why?

Firestarter is no longer being developed, it really should be removed from the repositories. UFW and its GUI version GUFW are the best iptables front-ends to use now, but if you're not running any services, you most likely don't need to use it. See [http://ubuntuforums.org/showthread.php?t=1871177](http://ubuntuforums.org/showthread.php?t=1871177) and [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Oh, and if you decide to use UFW, it only needs one command ```
sudo ufw enable
```
Is it worth installing a n anti virus if so which one?

---

### Post by gman3000000 on 2011-12-04
Thanks for all help so far.
I have installed dream weaver in wine but it doesn't show my partition with my backups on?

---

### Post by MG&amp;TL on 2011-12-04
> **gman3000000 said:**
> Thanks for all help so far.
I have installed dream weaver in wine but it doesn't show my partition with my backups on?


I'm not entirely sure what you mean by this. Could you clarify a little?

Antivirus depends on your level of paranoia. It might be a good idea. Search for 'antivirus' in the ubuntu software center. Although there have been very few viruses written for linux. And even fewer active currently.

---

### Post by gman3000000 on 2011-12-04
I want to set my resolution to 1024x768 like on my windows but when i do the whole screen is no longer fill, is this possible to change because when i open dreamweaver it all to small to read.

---

### Post by MG&amp;TL on 2011-12-04
What graphics card are you using?

---

### Post by gman3000000 on 2011-12-04
dont know sorry

---

### Post by oldtimer7777 on 2011-12-04
> **gman3000000 said:**
> dont know sorry

Try moving your backups to a local folder in your home directory in Ubuntu OS. Don't work from the windows partition in Ubuntu if you can help it. Move your stuff first to work on it, that way you won't suffer any possible data loss either.  Just saying.

---

### Post by oldos2er on 2011-12-04
> **gman3000000 said:**
> Is it worth installing a n anti virus if so which one?

In my opinion, no. If you read the links I gave it will help answer your questions.

---

