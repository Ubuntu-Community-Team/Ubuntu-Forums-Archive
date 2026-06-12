---
title: "New installation 10.10 narcoleptic !"
date: 2011-01-30
forum: General Help
---

### Post by grey1beard on 2011-01-30
Newly installed 10.10 on Toshiba Satellite laptop.

In creating a dual boot with xp originally installed, I had problems getting the laptop to run the live cd which I successfully used to install the os onto my wife's laptop three weeks ago.
("couldn't find a utility driver" ? - not sure if that was the exact wording).

Started over, and for the second attempt, I tried without the wireless link connected, and didn't accept the 3rd party software. 
This time it started well, but during the installation I noticed that the "program loading icon"(the little round wheel thingy) would occasionally stop until I moved the mouse. Then all would be well for some time, then it would stop again, and moving the mouse once more would get it going.

I then connected to the web, and ran the update manager, and again had problems with it dozing off till I moved the mouse.
Made for a very slow installation !

It seemed to finish OK, but starting again this am, it froze completely.
I rebooted, and it did it again, so I rebooted into "recovery mode" and got the following -

[26.081755] AC'97 1 access is not valid [0xffffffff], removing mixer.
[26.081814] Unable to initiate codec #1.

I then chose to reboot, and at the end of a cl screen, logged in, typed startx, and got here.

I don't know if this is part of the same problem, but I should be grateful for some guidance.

Please don't assume by the above that I have anything more than newbie skills. I'm flying by the seat of my pants here.

John

---

### Post by grey1beard on 2011-01-30
Additional info -
When the screen refuses to respond to the mouse movement, it does respond to shortcut key strokes.
I'd just hovered over the "File" on the toolbar, dropped the menu, and it froze. However, typing "Shift+T" gave me a new tab, and off we went again !
Taking the mouse back a second time didn't produce the problem.
John

---

### Post by grey1beard on 2011-01-30
The laptop has now frozen, and a poke with the big stick was the only way I could regain control.

It occurred to me that I should check it in xp, and at the moment it's been running for about 20 mins with no sign of the problem there.
So it does look as though it's a software issue, rather than a problem with the hardware.

New live cd ?
](*,)
John

---

### Post by grey1beard on 2011-01-30
I've now tried a new live cd, and when I ran it preparatory to reinstalling, I got the same sudden lack of response from the mouse(actually the tracker pad on the laptop) when I went to the advanced page to reformat the partitions, but still response from the keyboard.
Near to giving up.
john

---

### Post by grey1beard on 2011-01-31
I've just tried the alternate iso. Checked the m5sum etc, but trying to install it, it froze when the keyboard type query came up.
I started again, trying the "check the cd" instead of install, and again it froze after a couple of windows.
I'll try an earlier version(10.04 alternate) next and see if that will go in.

---

### Post by grey1beard on 2011-01-31
"If you firstly don't succeed..."
Well, I didn't, so I used the "noapci" option in the help menu on the first install page.
Currently installing, though remembering what the dhcp details were was more by luck than judgement.
So I'll see how it goes....
John

---

### Post by grey1beard on 2011-01-31
Installed, and it reaches the Ubuntu splash screen. 
This instantly disappears and leaves me with a blank screen and no sign of life.

Can anyone suggest that there is a point in continuing, and if so in what direction ?

Alternatively, how do I delete the whole ubuntu partition before trying something else ?

So far the only way seems to be to use my Toshiba recovery disc to reinstall xp.
This effectively erases the ubuntu, and as I have nothing yet on the xp one, it's only another few hours of my life wasted:rolleyes:

John

---

### Post by grey1beard on 2011-01-31
I've just tried to use my alternate live cd to see if the "repair installation" would help, but, you've guessed it, it froze at line [3.186625]

Ho hum

---

### Post by Kirboosy on 2011-01-31
You said earlier that your mouse would freeze but the keyboard worked. Have you tried plugging in a USB mouse?

I have found in my experience of installing Ubuntu that the update and 3rd party software install breaks Ubuntu. I always install my updates once I'm done installing Ubuntu.

---

### Post by grey1beard on 2011-01-31
No usb mouse unfortunately, to try it. Also no mouse serial(?)port, which is a pain !
But thanks for the thought.
John

---

### Post by grey1beard on 2011-01-31
I am able to run 8.04 from a live cd successfully, so far !!

Do I take that as a sign that I should try installing it, and do I need to remove anything (ie previous "broken" installations) first, or what ?
What a mess. Very tired brain going round in circles.

---

### Post by Kirboosy on 2011-01-31
You could get the PS/2 to USB converter.

Try installing it. Was 10.10 crashing during Live CD as well?

---

### Post by grey1beard on 2011-01-31
Shopping tomorrow !
No, if you don't count the broken bits of the last couple of days !!
PS ignore that line, I misread your question.
Yes it's been crashing at every opportunity.
John

---

### Post by grey1beard on 2011-01-31
Now installing 8.04 allongside the mess.
If it works, I'll sort it all out on Wednesday - hospital tomorrow.
John

---

### Post by Kirboosy on 2011-01-31
What is the exact Laptop Model and all that jazz. Maybe I can find something about the hardware that will prove useful to you.

---

### Post by grey1beard on 2011-01-31
At the moment it's running 8.04, and in the process of updating.
All is going smoothly, but when it finishes I'll get all the data that might be useful.
John

---

