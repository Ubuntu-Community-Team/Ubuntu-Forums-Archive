---
title: "Update ATI Drivers"
date: 2005-01-27
forum: General Help
---

### Post by peter_barb on 2005-01-27
I am having some difficulty installing the latest ATI Drivers onto Ubuntu Linux. Check this out.... [[http://peterbarbosa.com/Screenshot.png]](http://peterbarbosa.com/Screenshot.png])

If anyone can help this would be great.

Thanks,
Peter Barbosa

---

### Post by albersag on 2005-01-27
If you are using warty, i have not seen nobody having it working. I f you decide move to hoary, developpers released a version .deb on hoary repositories.And it works. Search function on forum will give you more info.

---

### Post by peter_barb on 2005-01-27
[QUOTE=albersag]If you are using warty, i have not seen nobody having it working. I f you decide move to hoary, developpers released a version .deb on hoary repositories.And it works. Search function on forum will give you more info.[/QUOTE]
 Damn it, alright... I am new to Linux so don't mind me :P

---

### Post by jensyt on 2005-01-27
[QUOTE=peter_barb]Damn it, alright... I am new to Linux so don't mind me :P[/QUOTE]
To stop that error, you could overwrite the file. I've done it and never had problems, but **this may not work for you**.
```
alien /home/eric/ati.rpm
dpkg --force-overwrite -i /home/eric/{whatever alien outputs}
```
This will force it to overwrite libGL...

---

### Post by peter_barb on 2005-01-27
[QUOTE=jensyt]To stop that error, you could overwrite the file. I've done it and never had problems, but **this may not work for you**.
```
alien /home/eric/ati.rpm
dpkg --force-overwrite -i /home/eric/{whatever alien outputs}
```
This will force it to overwrite libGL...[/QUOTE]
 Okay.... umm call me stupid, but for some reason my root password isn't working...

---

### Post by albersag on 2005-01-27
type sudo before the comand dpkg. 

Your user account (first created on installation) is the "root" sudo account.

---

### Post by peter_barb on 2005-01-27
[QUOTE=albersag]type sudo before the comand dpkg. 

Your user account (first created on installation) is the "root" sudo account.[/QUOTE]
 Thats the thing, it prompts me for a password, I typed in the password, and now the password isn't working.. I might have typed it in wrong when I first entered it.. it is weird why it isn't working.

---

### Post by peter_barb on 2005-01-27
[QUOTE=peter_barb]Thats the thing, it prompts me for a password, I typed in the password, and now the password isn't working.. I might have typed it in wrong when I first entered it.. it is weird why it isn't working.[/QUOTE]
 Is their anyway to retrive this back? Or do I need to do a clean install?

---

### Post by albersag on 2005-01-27
Read here how.

[http://ubuntuguide.org/](http://ubuntuguide.org/)

You can enter in ubuntu with root rights.

Root password must not be forgotten :)

---

### Post by peter_barb on 2005-01-27
[QUOTE=albersag]Read here how.

[http://ubuntuguide.org/](http://ubuntuguide.org/)

You can enter in ubuntu with root rights.

Root password must not be forgotten :)[/QUOTE]
 What im trying to know is if there is a way to retrieve my password?

---

### Post by peter_barb on 2005-01-27
[QUOTE=jensyt]To stop that error, you could overwrite the file. I've done it and never had problems, but **this may not work for you**.
```
alien /home/eric/ati.rpm
dpkg --force-overwrite -i /home/eric/{whatever alien outputs}
```
This will force it to overwrite libGL...[/QUOTE]
 Okay, I did that.... Now it says this... [http://peterbarbosa.com/Screenshot.png](http://peterbarbosa.com/Screenshot.png)

Any help now?

---

### Post by Ste on 2005-01-27
[QUOTE=peter_barb]Okay, I did that.... Now it says this... [http://peterbarbosa.com/Screenshot.png](http://peterbarbosa.com/Screenshot.png)

Any help now?[/QUOTE]
 You're not typing sudo before dpkg and most of the commands have typos.
The last one failed because you didn't leave a space after --force-overwrite -i.
Best to just copy and paste the command into the terminal.

---

### Post by bunty on 2005-01-28
reboot to single user mode and use passwd command to reset root password.

(from memory append single to the kernel line in you boot menu)

HTH 8)

---

