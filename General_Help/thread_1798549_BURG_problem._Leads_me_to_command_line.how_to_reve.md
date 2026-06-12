---
title: "BURG problem. Leads me to command line.how to revert ?"
date: 2011-07-06
forum: General Help
---

### Post by Ronalddig on 2011-07-06
Hi

I installed BURG and when i rebooted , instead of fancy booting , I got almost similar booting menu as GRUB and I could see BURG written on top. 

[B]Never mind, I thought may be I had to apply theme after installing it but when i chose Ubuntu option to boot , It lead me see some command line for some second.

Main problem is i get command prompt after that . i pressed ctrl+alt+f7 yet a command prompt.[/B]

I just want to go back to what was before and get GRUB only. how do i do that ?

---

### Post by wojox on 2011-07-06
Have you tried reinstalling [Grub from a Live-CD]("https://help.ubuntu.com/community/Grub2#Copy%20LiveCD%20Files")?

---

### Post by Ronalddig on 2011-07-06
Oh no , i messed up ...

i read tonnes of posts . i installed grub somehow ( i thought that it was installed )

so i removed BURG

now when i reboot , i get nothing :
it shows this :

>  [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub>


HELP ME PLEASE.

i cannot install grub from booting by USB .

---

### Post by wojox on 2011-07-06
Sounds like your config file is corrupted. Read through this [Command Line and Rescue Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode")

---

### Post by Ronalddig on 2011-07-07
I tried as you said but it gives error on this command  :

**linux /vmlinuz root=/dev/sdXY  ro**


[B]Isnt there a simple way to reinstall GRUB from Live CD ( or USB which i use to boot ) ?
[/B]

---

### Post by Ronalddig on 2011-07-07
Also, i booted from USB :

when i opened terminal and typed:

**sudo grub **

it gave me : command not found 

???

so, how do i restore grub now

---

### Post by decoherence on 2011-07-07
> 
I tried as you said but it gives error on this command :

linux /vmlinuz root=/dev/sdXY ro

Is that the line you put in? If so, you need to change the XY to whatever is appropriate for your system. Hopefully the instructions you have tell you how to do this, but if not you can always guess. Start with

linux /vmlinuz root=/dev/sda1 ro

if that's not it (it probably won't be) then reboot and try

linux /vmlinuz root=/dev/sda2 ro
linux /vmlinuz root=/dev/sda3 ro
etc. etc until you find your root partition. If you start getting past 6 or 7, replace the 'a' with a 'b' and do it again (unless you have a windows dual boot.... then the number could conceivably be higher)

linux /vmlinuz root=/dev/sdb1 ro
linux /vmlinuz root=/dev/sdb2 ro
linux /vmlinuz root=/dev/sdb3 ro
etc. etc. Eventually you'll hit your root partition.

good luck,

---

### Post by Ronalddig on 2011-07-07
yes, i did put my sda6 ( and even 4,3,2, all ) but nothing worked :(

after beating my head for 2 days , I re-installed grub using website [http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html](http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html)

( thank you so much other for clear instructions :) )

---

