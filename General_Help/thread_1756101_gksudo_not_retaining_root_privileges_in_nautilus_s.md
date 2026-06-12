---
title: "gksudo not retaining root privileges in nautilus script anymore..."
date: 2011-05-11
forum: General Help
---

### Post by graben3 on 2011-05-11
This nautilus script was working before I upgraded to 11.04. Why it is not working anymore? I have many script all gaining root access throught gksudo but it does not work anymore....

The part that is not working anymore is the line using gksudo to run sudo commands after it. The script does not retain root privileges gained by gksudo and ask for a password on the second line which it was not doing before.

What should I change in the script to make it work again ?

The script : 

foo=`gksudo -u root -k -m "Enter your password for root access" /bin/echo "Do you have root access?"`
sudo umount /home/graben/Projects
sudo umount /home/graben/Pictures/TL

---

### Post by wilbertvolkers on 2011-09-24
I have the same problem after installing 11.04 today, did you find a solution? I tried to modify 'sudoers' but to no avail.

---

### Post by wilbertvolkers on 2011-09-25
Ok, as a workaround you could remove the gksudo's from your script and then call the whole script with gksudo. Thats what i did.

---

### Post by dcstar on 2011-09-25
I suspect that the privileges granted to a successful gksudo do not follow over to a subsequent sudo command.

If this is the case then there is probably some sort of security reason for the change, I can imagine some situations where combined privileges could be used as a vulnerability.

---

