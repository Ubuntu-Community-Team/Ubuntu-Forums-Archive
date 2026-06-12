---
title: "Noname keyboard keys repeating randomly"
date: 2005-03-11
forum: General Help
---

### Post by rotorwash on 2005-03-11
Just installed ubuntu (Linux ubuntu 2.6.8.1-5-k7) and have a major problem with keys repeating randomly in gnome. I will be typing along and then thiiiiiiiiiiiiiiiiiis happppppensss... kind of scary when doing admin chores. I've read about setting a boot parameter to 'softrepeat=1' but this does not stop the repeating problem. If I disable key repeat in the gnome setup the problem does not occur (so far) but not having repeat when editing is a real pain. Anyone have any pointers on a solution? BTW, this is my first post. Hope it ain't a FAQ.

mwd

---

### Post by Burgundavia on 2005-03-11
Try System --> admin (i believe this is called something different in warty --> keyboard
That will control repeat rates.

Corey

---

### Post by rotorwash on 2005-03-11
[QUOTE=Burgundavia]Try System --> admin (i believe this is called something different in warty --> keyboard
That will control repeat rates.

Corey[/QUOTE]
The problem is spontaneous key repeats, that is, when I am typing, randomly one of the characters I type will start repeating until I initiate some keyboard action to stop it, like ^C. Using the keyboard panel allows me to turn off key repeats but does not fix the problem. Various keyboard repeat delays or rates do not affect the problem either.

---

### Post by meldroc on 2005-03-14
[QUOTE=rotorwash]The problem is spontaneous key repeats, that is, when I am typing, randomly one of the characters I type will start repeating until I initiate some keyboard action to stop it, like ^C. Using the keyboard panel allows me to turn off key repeats but does not fix the problem. Various keyboard repeat delays or rates do not affect the problem either.[/QUOTE]
 It could be that your keyboard is going bad - that is not normal behavior for a keyboard.

---

### Post by rotorwash on 2005-03-14
[QUOTE=meldroc]It could be that your keyboard is going bad - that is not normal behavior for a keyboard.[/QUOTE]
That is a possibility but highly unlikely since I use it for a Debian Sarge and an XP box. Neither exhibit this problem. Also, the problem does not occur in a console, only under Gnome. This leads me to think the problem is within the version of Gnome used and not the hardware. Changing the keyboard is not an option at this time.

---

### Post by Conte0 on 2005-03-15
I have the same problem...i saw that is an xfree86 bug...a big bug... i don't know how to fix it...actually i'm new in linux world...please if someone found a solution... help us

---

### Post by maurom on 2005-03-18
Same happens to me, using Ubuntu Hoary, Kernel 2.6.10-5-686, and Xorg.
Whenever I press a key, it repeats several times altough the repeat rate is low. When I deactivate key repeating, the problem is solved, but that ain't good for me.
This problem happens randomly when logged in Gnome and XFCE, but never happens in real console or in the Gnome Desktop Manager when typing the username and password.

---

### Post by rotorwash on 2005-03-18
[QUOTE=maurom]Same happens to me, using Ubuntu Hoary, Kernel 2.6.10-5-686, and Xorg.
Whenever I press a key, it repeats several times altough the repeat rate is low. When I deactivate key repeating, the problem is solved, but that ain't good for me.
This problem happens randomly when logged in Gnome and XFCE, but never happens in real console or in the Gnome Desktop Manager when typing the username and password.[/QUOTE]
 I haven't been able to find a fix. I find it dismaying that this problem exists in Xorg also. I've read that it has been around for a long time but most of the folks reporting key repeats also say that it happens when the machine is under a heavy load or they are using a laptop. Neither of these scenarios exist for me. I am the only one on this machine with nothing heavy going on and it occurs. I was doing a ^k in emacs when it happened last... needless to say that I was very unhappy at the results. Since I do not hear many people clamoring for a fix I assume the problem only occurs with a small subset of users. I also assume it has something to do with the hardware I am using. Unfortunately, I do not have the time to figure out what is going on. Time to look at other desktop solutions.

---

### Post by MAZDA on 2005-03-19
I have the same Problem with GNOME.

In my case it was happen after i have used the Hoary Live CD Preview on my Notebook last Week using the standart boot option => Gnome.

After the Start of the Application Mozilla Firefox and typing the Web Adress of the
Ubuntu Forums i have try to post a Answer to the Ubuntu Forums.

The effect was allways the Same.

After typing some Letters in the Answer Forumular of the Website, the Application begann automaticly to fill the the Screen with the Last typed Letter.

I can remember that the first thing what i have try to type was the Word Helo.
After i have try to corect the word to Hello the Aplication had began to write

Hellllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllll
lllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllo

It was happen allways to me when i have try to Change a Word.

I don't belive that this is a Hardware problem because this was the First and Only Time that this was Happen and always under Ubuntu.

I am wondering why such a good Question has to search in a X.org/Xfree86 Forum.

---

### Post by arrizaba on 2005-04-10
Hi guys!

I've had the key-bounce problem since I bought my laptop (a Toshiba M30) in both Ubuntu and Mandrake. First I thought it was specifically a Toshiba problem, then I realized it has to do with the Synaptics mouse. This might be a generic problem, due to a bug in the 2.6 kernel, though I do not know if it has been fixed. Here's a link with possible solutions:

[COLOR=Blue]http://www.marcsaric.de/m30_linux1.html[/COLOR]

These are valid for a Toshiba M30, but if the problem is generic, then the solutions could be easily exported.

---

### Post by rotorwash on 2005-04-18
I updated to Hoary and as maurom says, the problem is still there in Hoary. This is the most annoying problem I've seen and it appears that there is no fix except to change your keyboard or disable key repeat :mad:

---

### Post by maurom on 2005-04-18
I´ve tried arrizaba´s tip and that seems to work for me.

You could try too. Add...

psmouse.rate=40

to your kernel parameters (edit grub´s menu.lst),

or edit /etc/modules and add

psmouse rate=40

Try it and then post the results...

---

### Post by rotorwash on 2005-04-19
[QUOTE=maurom]I´ve tried arrizaba´s tip and that seems to work for me.

You could try too. Add...

psmouse.rate=40

to your kernel parameters (edit grub´s menu.lst),

or edit /etc/modules and add

psmouse rate=40

Try it and then post the results...[/QUOTE]
I added the parameter and I still get the random repeats.

---

### Post by Goober on 2005-04-22
I had this problem as well.  Except my KeyBoard isn't no-name, nor cheap.  Every so often, a letter that I had just typed would keep randomly repeating until I stopped it.  

The solution, for me, was to go to Computer -> Desktop Preferences -> Keyboard.  Then turn off "Repeat Keys".  This means that when you press a key, it does that action only once, and won't repeat it if you continue pressing it.  It is slightly more annoying for using the arrow keys, and Backspace, but it is much more annoying to have the bloody letters repeating.

Hope that helps :)

---

### Post by Revan on 2005-04-22
Hi guys, I have the same exact problem.. but I suppose it's related to my usb wireless card.

Sometimes when I load the OS my wifi connection stop responding after some seconds... and as I open the terminal and try to see what's wrong, it starts repeating some of the letters typed.

But when I disconnect the USB wireless card, everything gets fine. Then I have to reboot the OS and the wifi card usually works fine.

 ](*,)

---

### Post by Michele Moglia on 2005-05-18
If could be of any help I also have the same problem, everything was fine with Warty then I upgraded to Hoary and now I have the problem of random keys repeat.
I cannot remember when it starts but now there is no way to stop it.

I hope that someone will find a solution.

Michele

---

### Post by ExemplarUbuntu on 2005-05-20
I have the same problem in the console (bash) window and in the Gedit editor but it only seems to happen when I VNC onto the Ubuntu box.

The repeat happens randomly and can affect any key.

---

### Post by c-m on 2005-08-23
[QUOTE=ExemplarUbuntu]I have the same problem in the console (bash) window and in the Gedit editor but it only seems to happen when I VNC onto the Ubuntu box.

The repeat happens randomly and can affect any key.[/QUOTE]
 has this been fixed as it just happened to me typing an e-mail to someone? I used to get this in gentoo with a usb keyboard, i can't remember how i fixed it.

Now i have another issue where i'm typing and there is a delay in the words being shown on screen. its VERY annoying and makes this box useless for office type work. good job uni doesn't restart till late sept.

---

### Post by BoHu on 2005-09-24
This happens to me in both Gnome and KDE. I also happens in the konsole. Most annoying is when I can't unlock a screensaver because of the key repeat problem. I have to hard-reboot :-(

---

### Post by luckyaba on 2005-10-14
I just set the delay to maximum and that seemed to work for me...
under the keyboard settings.

---

### Post by sredlich on 2006-02-11
I'm seeing this as well with a new HP PS2 keyboard and PS2 mouse with Breezy.  Can't comment on whether it's cheap, but they did come with my computer (hp a1350n AMD64 X2 4200.)

I don't have the problem in Gnome Terminal.  I do see it in Firefox.  Tried this
# modprobe psmouse rate=40
based on instructions from earlier in the thread.  [http://www.marcsaric.de/m30_linux1.html](http://www.marcsaric.de/m30_linux1.html)

Now firefox doesn't see key repeats, but I get them in Gnome Terminal.

Turned off the key repeat for now.
System->Preferences->Keyboard->Repeat_Keys (off)

Thanks,
Steve

---

### Post by nandoflorestan on 2006-02-12
I had reported this bug on November 2005:
[https://launchpad.net/distros/ubuntu/+bug/25104](https://launchpad.net/distros/ubuntu/+bug/25104)

You guys can see the kernel warnings if you type:
 dmesg > dmesg.txt
...then open the dmesg.txt file in a text editor.

Whenever I have the keyboard problem, dmesg shows a few unrecognized keypresses.

Today I have edited /boot/grub/menu.lst. I have added the "noapic" parameter to the kernel line.

Hope this will finally rid me of the key repeat and mouse problem... But I won't say it definitely worked until a week has passed.

---

### Post by sredlich on 2006-02-13
[QUOTE=nandoflorestan]I had reported this bug on November 2005:
[https://launchpad.net/distros/ubuntu/+bug/25104](https://launchpad.net/distros/ubuntu/+bug/25104)

You guys can see the kernel warnings if you type:
 dmesg > dmesg.txt
...then open the dmesg.txt file in a text editor.

Whenever I have the keyboard problem, dmesg shows a few unrecognized keypresses.

Today I have edited /boot/grub/menu.lst. I have added the "noapic" parameter to the kernel line.

Hope this will finally rid me of the key repeat and mouse problem... But I won't say it definitely worked until a week has passed.[/QUOTE]

Thanks for the followup.

My system is not yet perfect.  today I seem to have trouble pasting from firefox to gnome terminal.  also my system does not seem to be keeping time that well.  I probably need the APIC chip for something.  I'm thinking of buying either a USB keyboard or mouse as my next workaround.  Other than adding on to your bug report, I don't know what to do to get this bug fixed.

Thanks,
Steve

---

### Post by monkeydust on 2006-08-13
Hello all

My install of Dapper 6.0.6LTS has just started doing this! (the random repeating key). The system freezes up for about 2 seconds repeating the same key -- like ttttttttttttttttttttthis!

Very annoying!

This bug (which is definitely not my keyboard, which was fine before and is perfect under Windows) along with the endless hardware hassles I've had, is pushing me further towards deleting my Linux partition!

Please help me -- if you have a bugfix for this I'd love to know, because I want to stick with Ubuntu, but if I can't even type I'll have to get rid! :( 

Hellppp! :-k

---

### Post by superboss on 2006-09-30
I too am interested in a fix!

---

### Post by gdlx on 2006-10-21
the problem occurs in graphic mode.   I have no problem with CLI. Login is terrible.  I have discoverd that by typing one key with a very light tap and waiting about 5 secs before pressing the next key, I can login.  
So many people have had this problem for so long, I wonder why some of the programmers can't figure out what is causing it.  Sometimes it even occurs when the key repeat is turned off.

:confused:

---

### Post by handy on 2006-10-23
I have 2 machines on Edgy RC1, the first has an old clunker IBM PS/2 keyboard, & behaves flawlessly.

The 2nd machine (spec's in my signature) normally runs a Belkin cordless keyboard & MS USB IntelliMouse Explorer; no prob's in Breezy or Dapper, keyboard prob's only, like keys that you are using are lagging & then all of a sudden catch up, giving multiple iterations of some of the keys.

I have been forced to turn off key repeat too.

Oh! yeh I am now using a brand new M$ PS/2 keyboard, with exactly the same response, or lack of...

We'll be happy when this one goes away for sure!

---

### Post by captain.kipper on 2006-10-25
Me too!

>The symptoms are lag followed by sudden catchup, which translates to >multiple interations of some letters, & some being totally left out.

(see [http://www.ubuntuforums.org/showthread.php?p=1662715#post1662715](http://www.ubuntuforums.org/showthread.php?p=1662715#post1662715))

baaaaaaaaaaaaaaaaaaaah!

---

### Post by captain.kipper on 2006-10-25
see bug report:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/39315](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/39315)

---

### Post by spaceghoti on 2006-10-30
This was happened to me in Dapper on my Compaq Evo N610c, but now that I've switched to an IBM Thinkpad T42 it's started repeating arrow or page down even when I'm not touching the keyboard.  It just started today and comes back even after the system has been shut down for a few minutes.  It started in Firefox, then started running through my active desktops at full speed.  It also happened under Opera.  The only way I can stop it is to switch to a TTY session and shut down the xserver.

I originally installed the KDE desktop.  I have now installed the XFCE desktop and only encountered the problem once.

---

