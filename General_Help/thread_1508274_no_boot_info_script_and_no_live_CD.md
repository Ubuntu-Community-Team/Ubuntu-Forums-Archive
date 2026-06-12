---
title: "no boot info script and no live CD"
date: 2010-06-12
forum: General Help
---

### Post by RusitoQbano on 2010-06-12
Trying to solve a grub problem which I solved, I encountered that the boot info script doesn't run on my Jaunty. Output:
Here the output when running boot info script:

```
andy@andy-laptop:~$ cd Desktop
andy@andy-laptop:~/Desktop$ sudo bash boot_info_script055.sh
[sudo] password for andy: 
: command not found.sh: line 52: 
: command not found.sh: line 53: 
'oot_info_script055.sh: line 63: syntax error near unexpected token `
'oot_info_script055.sh: line 63: `fi 
andy@andy-laptop:~/Desktop$ 

```
I also found out that ubuntu isn't booting from the live CD but just freezes with a blank screen. Could it be because I used a workaround in xorg.conf to enhance performance of my Intel video card? If that's a reason, then why is the live CD which supposedly works well when you have no OS on your PC affected by the configuration of the installed system?

---

### Post by prodigy_ on 2010-06-12
Installed OS configuration can't affect Live CD. Something else is wrong - maybe your CD drive is dying?

As for the script... are you sure that the file is intact? What did you use to d/l it?

---

### Post by RusitoQbano on 2010-06-12
My drive is ok and it reads the CD. Jus when I select the option try ubuntu without affecting your system I get the problem described earlier.
Also when I mistakenly installed a ATI driver that overrode my settings booting from CD was affected.
I downloaded the boot infoscript at work from a sourceforge site I think. Basically it opened in a little window and I copied it to a txt file.

---

### Post by wilee-nilee on 2010-06-12
Youve left out part of the script to get it to work you have this.
```
sudo bash boot_info_script055.sh
```

And it should this.
```
sudo bash ~/Desktop/boot_info_script*.sh
``` 

Where desktop is= where the downloaded script is. The easiest way to do this is download the script put it on the desk top then run this.
```
sudo bash ~/Desktop/boot_info_script*.sh
```

Then paste the readout produced to a reply, and put it in code tags.
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I have to ask here as well is this some sort of joke, or you really having problems the line for running the script you posted looks suspicious to me. Or your trying to run the script from root with sudo.

---

### Post by RusitoQbano on 2010-06-12
No, it's no joke.
And I ran the script from the Desktop directory, so this doesn't help me. It isn't that the file isn't found. It's that bash doesn't like something about the syntax.

---

### Post by RusitoQbano on 2010-06-12
Now it worked. Maybe it was again a linebreak error cause I imported the txt file from windows.

---

### Post by wilee-nilee on 2010-06-12
> **RusitoQbano said:**
> Now it worked. Maybe it was again a linebreak error cause I imported the txt file from windows.

Cool, post it in code tags.[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

I only asked the question as a couple people have done just that, and a low bean count with a strange looking terminal read now throws up a red flag for me.

---

### Post by prodigy_ on 2010-06-13
> **RusitoQbano said:**
> and I copied it to a txt file.

This explains much. ;-) Did you use a Windows PC to do d/l it? Because if it was Windows PC and you saved the file with Notepad, you've got file format (Windows uses CR/LF as line break, Unix systems use LF).

And shell scripts don't work if they're saved in Windows format.

---

