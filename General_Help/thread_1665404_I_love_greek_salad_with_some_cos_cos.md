---
title: "I love greek salad with some cos cos"
date: 2011-01-12
forum: General Help
---

### Post by YummyOlives on 2011-01-12
hello peeps


Might have been asked before and sincere apologies for that ! 

I am about to install Ubuntu through the windows installer (Wubi) on the same partition i have vista installed. 

What shall be the consequences for all that ! 

As some have mentioned here in the forums that the win-bootloader will be overwritten with  somthing else and it wont load anything and might give some 'file missing error' while booting the system, so my Q is , if i install EasyBCD, would i be able to choose between the two operating systems w/o any sort of troubles, even if the winloader is overwritten ?

thanks alot for the help 
 
HAPPY NEW YEAR :KS

---

### Post by Verbeck on 2011-01-12
afaik, a wubi install wont overwrite the mbr - it just adds an entry to the win bootloader (not the case with a partitioned dual-boot where the mbr would be overwritten if installing on the same harddisk)

---

### Post by t0p on 2011-01-12
Isn't that *couscous*?  Or has something just swooshed over my head?

---

### Post by nothingspecial on 2011-01-12
It could be cos lettuce in a Greek salad?????

Wubi installs ubuntu inside windows and will not overwrite the mbr.

It is an excellent way of testing Ubuntu, however you will not get the full experience unless you install it to your harddrive. Then it will use grub to boot both ubuntu and windows.

---

### Post by YummyOlives on 2011-01-12
cous cous - correction , jeopardizing my salad

thanks for the replies ! what i understand is that the mbr wont be overwritten and i would get the taste of the Mighty Ubuntu, BUT i had a little bad experience with the same sort of installation last month and i got ''bootloader missing'' error and then had to use the backup win dvd, 

would that happen again? if yes, any remedies for that ?

thanks lodsssss

---

### Post by Rubi1200 on 2011-01-12
Just to be clear, Wubi installs do not (or should not) touch the MBR. 

If you want more information about Wubi as well as issues and solutions, see here:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

What you experienced before was one of the issues Wubi installs are currently experiencing.

If you do a fresh install now, see the section about the Permanent Fix. What you need to do is lock the grub packages in Synaptic to prevent this happening.

If you have more questions, feel free to ask.

---

### Post by Rubi1200 on 2011-01-12
Just to be clear, Wubi installs do not (or should not) touch the MBR. 

If you want more information about Wubi as well as issues and solutions, see here:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

What you experienced before was one of the issues Wubi installs are currently experiencing.

If you do a fresh install now, see the section about the Permanent Fix. What you need to do is lock the grub packages in Synaptic to prevent this happening.

If you have more questions, feel free to ask.

---

### Post by YummyOlives on 2011-01-13
thanks for the replies, but in a troublesome situation again, after the window installer rebooted the system and i get to the bootloader screen , all i get to select is vista and there is no sign of ubuntu in the list , any diagnosis of that ? 
(maybe because  i have easybcd installed ? maybe not ! please guide me)
thaxxx

---

