---
title: "Dual boot."
date: 2006-03-10
forum: General Help
---

### Post by godvict on 2006-03-10
I have dualboot for Ubuntu and WinXP and everything is working fine. Here is what i want to do. Right now it boots to Ubuntu unless i choose WinXP, I want it to boot to WinXP unless i choose ubuntu. How do i set it to boot WinXP when i start the computer?

---

### Post by astyanax on 2006-03-10
You have to change the boot order.  If you are using Grub, it's located here:
/boot/grub/menu.lst

You might want to back it up before you shuffle around the order, just in case something gets screwed up.

---

### Post by aysiu on 2006-03-10
Detailed instructions are here:
[https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS](https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS)

---

### Post by godvict on 2006-03-10
Sorry i have no idea what u mean. Can some1 help me step by step?

---

### Post by godvict on 2006-03-10
It said.
* Find this line in the document that was just opened

... default 0 ...        

I dont see that. I see
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.

---

### Post by godvict on 2006-03-10
This is how my startup looks like.

Ubuntu, Kernel 2.6.12-10-386
Ubuntu, Kernel 2.6.12-10-386 (recovery mode)
Ubuntu, Kernel 2.6.12-9-386
Ubuntu, Kernel 2.6.12-9-386 (recovery mode)
Ubuntu, Memtest86+

Other Operating Systems
WinXp
....... So what should i type in...
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
.... This is what i typed and didnt work.
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 6 is the default if the command is not used.
?

---

### Post by tyspot on 2006-03-10
ok,ok here we go. Drink at least 3 ounces of whatever you need for refreshment . Done that? OK now lets look at the same area you were editing. In your menu.lst file. did the changes you mention you made stay in the file? yes? Good. now lets look a little bit lower than that area for a line that shows
default           0
Note that it doesnt have any tic tac toes in front of it. this is because it is a part of the file that gets used to process information. everything behind(to the right of) the pound sign(#) is for comments.
now after you edit your change in and then close the file re-open it again and make sure that your change stuck. and that there are no extra things going on where you were working.
your line for default should look like 
default           5

hope this hits the spot for ya.

---

