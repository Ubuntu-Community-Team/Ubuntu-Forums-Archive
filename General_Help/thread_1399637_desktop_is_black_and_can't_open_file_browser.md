---
title: "desktop is black and can't open file browser"
date: 2010-02-05
forum: General Help
---

### Post by dr_ahmed_tarek on 2010-02-05
hi,
first of all sory for my bad english,
i installed ubuntu i have an 80 gb hard disk so i partitioned it 2 gb swap,11 gb root and 8 gb home and the rest was an ntfs partition that i dont want to format because it has important files in itthen i mounted it as \windows it worked perfect in the biggining but after three or four days the background vanished and i got a black one instead and i cant access the background changer because there's no more the right click menu and i cant access computer neither when i open it the task apears as starting computer then nothing,
please help me because i was attracted by ubuntu for knowing that it does not fall like windows so what can i do or what sudo codes i have to use???
regards and thanks in advance,
sory again for my bad english

---

### Post by Andreas1 on 2010-02-06
it seems like nautilus (the file browser) is not running, it is responsible for the desktop as well. try <alt>+<F2> and run "nautilus". although i have no idea why it is not started when you attempt to open "computer".

also: please do change the thread title to something descriptive like "desktop is black and can't open file browser" instead of "please help".

---

### Post by dr_ahmed_tarek on 2010-02-06
i changed the thread title.....
thank you for helping but i tried to run nautilus but nothing changed its all the same,same black desktop and file browser doesnt open....

---

### Post by Solethara on 2010-02-06
A wild guess but you can try:

sudo /etc/init.d/gdm start

---

### Post by warfacegod on 2010-02-06
Try hitting Alt+F2 and type: update-manager

Install all updates and reboot.

---

