---
title: "Completly unable to boot into ubuntu HELP"
date: 2010-04-20
forum: General Help
---

### Post by valhemmer on 2010-04-20
I've been dual booting ubuntu and xp for about 2 months now. i booted this morning and all i get is this grub menu. i saw the grub vs. grub2 page but have no idea even where to start. if anybody could help it would be greatly appreciated. thanks

---

### Post by drs305 on 2010-04-20
Start by telling us which version of grub and which Ubuntu version you are using. If you see an actual Grub menu, the version number will be at the top.

Are you seeing a complete Grub menu and selecting something doesn't work, or are you only seeing a grub prompt?

If you see a grub prompt, and you are using Grub 2, there are instructions on this site which can help boot from the Grub2 command line: [https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot]("https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot")

If none of this makes sense, the best option might be to boot the LiveCd and run meierfra's boot info script, which will give us information to help us help you.
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by valhemmer on 2010-04-20
ok it says verbatum
gnu grub v 1.97~beta 4
min bash-like line editing...
sh:grub>

i'm dual booting so i have to restart every time i try and check something out, so slow going basicaly

---

### Post by drs305 on 2010-04-20
Try using the instructions in the link I provided to boot from the grub command line. If you have questions, just ask here.

---

### Post by valhemmer on 2010-04-20
ok didnt work, followed the directions and got to the linux/vmlinuz part, it kept saying it didnt recognize linux/vmlinuz and i couldnt continue to directions. i tried different setroot= entrys but on all it said it couldnt recognise linux/vmlinuz

---

### Post by valhemmer on 2010-04-20
finaly. this was a* wonderful *adventure into the bowels of my comp. i succesfully booted onto ubuntu. and ill admit this was a good learning experience. i got it done following this guide [Grub vs. Grub2]("https://help.ubuntu.com/community/Grub2") and the help of drs305. the problem, well i dont know what it was but the solution was to first find out where ubuntu was hiding on my partitions and then telling grub where exactly that was. all of which was explained in the guide.

---

