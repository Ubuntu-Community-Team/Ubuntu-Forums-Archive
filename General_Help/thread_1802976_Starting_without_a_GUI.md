---
title: "Starting without a GUI"
date: 2011-07-12
forum: General Help
---

### Post by Bre Ntt on 2011-07-12
I've been trying to figure out how to start Ubuntu without a GUI with grub2 (I had it figured out for legacy GRUB). Done several searches, and there are a few threads, but they all give different advice that I either don't understand or that don't work. 

I tried editing /etc/default/grub 
with 
GRUB_TERMINAL=console
then updated grub. gdm still loads automatically. 

I'm probably one of those people "The Idiot's Guide" were written for, so if anyone helps (thank you) can you tell me specifically where the configuration file is that I may have to edit, and exactly what goes on the line that I have to edit? 

And what does "editing on the fly mean?" I see that a lot in these GRUB tutorials.

---

### Post by WorMzy on 2011-07-12
Not too familiar with grub 2, but you need to add "text" to the kernel line.

Editing "on the fly" means editing grub when you boot up, rather than editing the config files and running update-grub.

---

### Post by Bre Ntt on 2011-07-12
I've seen that said in other posts. 

But I don't know what "the kernel line" is? 

If it is a line in /boot/grub/menu.lst the file has been replaced by /boot/grub/grub.cfg. But that file is not supposed to be edited, as it is the product of scripts and will be changed. 

There is the /etc/grub.d/40_custom file, which apparently is supposed to be where you put these sorts of options. But there is no "kernel line", or any lines at all, in that file.

---

### Post by WorMzy on 2011-07-12
It works for either grub legacy (menu.lst) or grub2 (/etc/default/grub, or whatever it is). Just have a poke about in the config files and look for a default line with "quiet" and "splash", or similar. That's where you need to add the "text" to, and then run update-grub. (or grub-mkconfig, or whatever it is these days)

The wiki page on Grub2 will probably tell you more, I should have included a link to it in my first post: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by sisco311 on 2011-07-12
If you are using natty (11.04), then see: [http://ubuntuforums.org/showpost.php?p=10798400&postcount=4](http://ubuntuforums.org/showpost.php?p=10798400&postcount=4)

The **text** kernel parameter should work in earlier versions: [http://ubuntuforums.org/showthread.php?p=9644518#post9644518](http://ubuntuforums.org/showthread.php?p=9644518#post9644518)

---

### Post by Bre Ntt on 2011-07-12
Ok figured it out. 

There is no more "kernel line" that is why I was getting confused. Everybody kept saying to edit it. 

Now in /etc/default/grub

there is a line that corresponds to the "kernel line" called "linux line" that in the file looks like

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 

"quiet splash" needs to be changed to "text"

Thank you for the help.

Here are the option explanations for anyone else that might come across the thread:

[https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202)

---

### Post by AlphaLexman on 2011-07-12
> **Bre Ntt said:**
> But I don't know what "the kernel line" is? 
At the grub menu screen, down at the bottom it might say something like..
```
Press 'C' for a command line
```I may not have the actual syntax correct, as I didn't reboot to get it exact.

That will give you the "on-the-fly" options, or as Wormzy called it, the "kernel line"

EDIT: Beat by the OP!!

---

### Post by ajgreeny on 2011-07-12
There is still a kernel line.  It's just not in the equivalent of the menu.lst file.

You do it "on the fly" by hitting E in the grub menu on the listed kernel you want to boot, then scroll to the kernel line, which still shows there, and ends with "quiet splash".  Simply add the word "text" there to get "quiet splash text".  Now hit ctrl+X

That edit will only take effect for the one boot and everything will revert to normal next time.

---

