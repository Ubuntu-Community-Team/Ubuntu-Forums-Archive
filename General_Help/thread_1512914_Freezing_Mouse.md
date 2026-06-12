---
title: "Freezing Mouse"
date: 2010-06-18
forum: General Help
---

### Post by Gael33 on 2010-06-18
For the last couple of weeks my PS2 mouse has been freezing up. It doesn't seize up completely ... just a few seconds at a time. It's proving very frustrating when working on a program that requires much use of the mouse. Is there any way I can fix this?
I am using Ubuntu 10.04 LTS.

Gael.

---

### Post by jonobr on 2010-06-18
If this is happening frequently you could try the following... it may show something

Open a terminal,
type xev

place the pointer in the blank square.
move it around and you should see the thing receiving input from the device.

keep moving until you get a pause.
the question would be during the pause, do you see input ?
is there still activity in the log while moving the mouse, but the mouse is not moving on the screen?
no input would point more towards the device, receiving input and it not doing anything may require a deeper look at your system and at dmesg output to see if anything is going on.

---

