---
title: "sudo update-grub no longer works"
date: 2012-09-12
forum: General Help
---

### Post by Philip Gray on 2012-09-12
Good evening

I am not sure if this is the right thread to post this. My issue is that the command sudo update-grub gives an error. I added a wallpaper to '/etc/default/grub'  file (GRUB_BACKGROUND="/home/philip/Pictures/kellyhu03_1152x864.jpg"). I then ran sudo update-grub which was successful. I then added 'set color_normal=blue/black' to the same file and ran the sudo update-grub command which was successful but the colour in the grub menu did not change.

I found a web page 'https://help.ubuntu.com/community/Grub2/Displays' which advises on how to change the grub colours. I updated '/etc/grub.d/05_debian_theme' file. I ran sudo update-grub which was successfull. The colours I initially chose did not look good so I changed the '05_debian_theme' file again. However when I ran sudo update-grub I received this error message:-

philip@philip-MS-7529:~$ sudo update-grub
[sudo] password for philip: 
Generating grub.cfg ...
Found background: /home/philip/Pictures/kellyhu03_1152x864.jpg
/usr/sbin/grub-mkconfig: 280: /usr/sbin/grub-mkconfig: /etc/grub.d/05_debian_theme: not found
philip@philip-MS-7529:~$ 

I then found this command on another web site:- 'sudo grub-mkconfig -o /boot/grub/grub.cfg'. This gave me the same error:-

Generating grub.cfg ...
Found background: /home/philip/Pictures/kellyhu03_1152x864.jpg
/usr/sbin/grub-mkconfig: 280: /usr/sbin/grub-mkconfig: /etc/grub.d/05_debian_theme: not found

Does anyone have any suggestions on how I can fix this?

Regards
Philip

---

### Post by opensshd on 2012-09-12
Check file names and paths.. just looks like a typo error or something where grub is no longer finding the same file... did you perhaps alter it last edit?

---

### Post by Philip Gray on 2012-09-13
Hi opensshd

I have not edited/changed any paths. All I did was add the wallpaper and colour entries to the two files I mentioned. I did not manually edit the grub.cfg file. After I posted this query I went and had a look in the grub.cfg file and I could see my entries in there. Does the error mean that it cannot find the '05_debian_theme' file? It is still in the same location. What does the 280 stand for? Where do i need to go to check the paths?

Regards
Philip

---

### Post by IllRepute on 2012-11-10
Not sure you still have this problem, but I had a similar issue and it was a typo causing the file to not be found.

i'd left out the first / in !#/bin/sh -e

---

