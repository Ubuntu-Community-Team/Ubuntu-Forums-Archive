---
title: "stuck in command mode"
date: 2006-04-19
forum: General Help
---

### Post by talos452 on 2006-04-19
someone help me.. im stuck in the command prompt... and cant find a text editer... help... i need a list of one or a list of one to install

---

### Post by mztriz on 2006-04-19
[QUOTE=talos452]someone help me.. im stuck in the command prompt... and cant find a text editer... help... i need a list of one or a list of one to install[/QUOTE]

what do you mean by stuck in command prompt? As in you booted your computer and it was in command line? If that is the case type in 'startx'.

---

### Post by talos452 on 2006-04-19
[QUOTE=mztriz]what do you mean by stuck in command prompt? As in you booted your computer and it was in command line? If that is the case type in 'startx'.[/QUOTE]
it gives me configuration problem.. so i wanna edit the file it mentions.... but i dont know what a good editor is for text

cant install emacs from this... and no others load.. have a list?

---

### Post by Nequeo on 2006-04-19
[QUOTE=talos452]someone help me.. im stuck in the command prompt... and cant find a text editer... help... i need a list of one or a list of one to install[/QUOTE]

Try 'nano' or 'pico'. I forgot which one comes with Ubuntu. They are baby editors, though. Real Hackers use 'vim'. Type 'vimtutor' from the command line for a quick tutorial on how to use Vim. 

If you're a real masochist, try 'ed'. :twisted:

---

### Post by talos452 on 2006-04-19
[QUOTE=Nequeo]Try 'nano' or 'pico'. I forgot which one comes with Ubuntu. They are baby editors, though. Real Hackers use 'vim'. Type 'vimtutor' from the command line for a quick tutorial on how to use Vim. 

If you're a real masochist, try 'ed'. :twisted:[/QUOTE]
thank you, that worked....  but i still couldn't get in... had to do a re-install...  i was using full new hardware on an existing install
lol

---

### Post by az on 2006-04-20
[QUOTE=talos452]  i was using full new hardware on an existing install
lol[/QUOTE]

There is not that much to do for that:

Change your fstab and grub menu.list if your hard drive is in a different place and reconfigure X.  You're done

Boot into recovery mode (you already changed ftsba and grub or you would not be able to boot) and run
dpkg-reconfugre -phigh xserver-xorg
and then
init 2

---

