---
title: "Update Crash"
date: 2011-11-28
forum: General Help
---

### Post by Kaspar44 on 2011-11-28
Im trying to get in to my ubuntu after an update it now says It cant find my graphics settings and I cant restore it to default. 

I really need to get in to it as I have important files in there.

I need help to either recover the files or restore ubuntu.

Any ideas.

---

### Post by ventrical on 2011-11-28
Go to terminal and enter  <Ctrl+alt+F1> and enter:
lspci

and the command prompt and tell us what type of graphics adapter you have.

  You can also try this at the terminal prompt:

sudo dpkg -i --configue -a
 then
sudo apt-get update
sudo apt-get upgrade

---

### Post by Kaspar44 on 2011-11-28
ok I tryed what you said now when I restart it it ha come up with a terminal screen with stopping anac(h)ronistic cron as the last line?? Is there any way I can  jsut extract this 1 file and then wipe the rest?

---

### Post by BC59 on 2011-11-28
First of all.

Boot with a Live CD (burn Ubuntu on a CD, or USB, boot and choose try instead of install).

Then when Ubuntu is working from the CD, backup the files you need.

After that follow the instructions to restore your system.

---

### Post by Kaspar44 on 2011-11-29
ok Ive got a back up disk and it loads fine do you know how I can gain permissions to get my files out?

---

