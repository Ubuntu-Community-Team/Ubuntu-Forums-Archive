---
title: "Num Lock"
date: 2010-10-30
forum: General Help
---

### Post by Master Ninja on 2010-10-30
Hi, I just installed Ubuntu 10.10 64 bit (WUBI).

I want Num Lock to automatically be enabled before login.

I read this but I am confused:

[URL="https://help.ubuntu.com/community/NumLock"]https://help.ubuntu.com/community/NumLock


Which option should I choose?[/URL]

---

### Post by Master Ninja on 2010-10-30
bump, help please :KS

---

### Post by jeremyswalker on 2010-10-30
Install "numlockx" using your package installation method of choice. Afterwards, press Alt + F2 on your keyboard and enter:
```
gksu gedit /etc/gdm/Init/Default
```
Enter your password at the prompt.
Find the line that reads "exit 0". It should be the last line. Just above that line, enter the following:
```
if [ -x /usr/bin/numlockx ]; then
  /usr/bin/numlockx on
fi
```
Save the file, and you're done!

---

### Post by lisati on 2010-10-30
Please be patient - we are all volunteers here. The usual "rule of thumb" here is to wait 24 hours after the last post before bumping.

If you have a "standard" Ubuntu installation, I suggest you concentrate on the GDM section of the tutorial.

---

### Post by Master Ninja on 2010-10-30
thanks jeremyswalker, but my keyboard is a bit complicated; alt + f2 doesn't work. I installed numlockx via ubuntu software centre. is Alt + f2 the terminal?

sorry [[COLOR=#d40000]**lisati**[/COLOR]]("http://ubuntuforums.org/member.php?u=327635")

---

### Post by jeremyswalker on 2010-10-30
You can enter what I said in the terminal, as well.

---

### Post by Master Ninja on 2010-10-30
thanks a million, it worked :KS

---

