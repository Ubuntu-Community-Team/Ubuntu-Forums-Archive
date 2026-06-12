---
title: "can't paste email content in terminal"
date: 2011-09-26
forum: General Help
---

### Post by sfzombie13 on 2011-09-26
good morning all, i am brand new to these forums, and like so many others, i have a problem.  i searched the forums and have become convinced that the answer lies in the minds of some of you, so i have come asking for a bit of assistance.
  
i installed ubuntu 11.04 on vmware on my toshiba satellite to get used to it before i do an install on my system.  i am thinking about helping with the project, so i decided to sign the code of conduct, and that was where my troubles started.  i created my pgp key, uploaded it to the keyserver listed in the instructions, and received a confirmation email.  when i tried to paste the encrypted contents into a terminal for authentication, it tried to process the list as commands, giving about 10 error messages.  i thought that the html from the email was to blame, so i opened the source to get the text by itself and had the same problem.

are there any tricks to pasting long content into the terminal?

any help would be appreciated.

---

### Post by matt_symes on 2011-09-26
Hi

To paste into the terminal press shift-ctrl-v. To copy from the terminal press shift-ctrl+c. Or you can right click.

Kind regards

---

### Post by collisionystm on 2011-09-26
You can create a file to run it out of.

nano key.key
*Paste information*
CTRL+X to exit, Y to save.

chmod +x key.key
./key.key

---

### Post by sfzombie13 on 2011-09-26
thanx for the quick response.  i used control + c to copy and control + v to paste, but what happened when i did that was the terminal tried to execute a command for each line pasted.  i read the reply under yours and decided that was a bit complicated for the short description, i couldn't figure out what to save it in, where to save it, where to put the chmod at to make it work, etc.  
i did ask my linux instructor and he said to put quotes around the text first, then paste it and that should work.  i'm gonna try it now.

---

