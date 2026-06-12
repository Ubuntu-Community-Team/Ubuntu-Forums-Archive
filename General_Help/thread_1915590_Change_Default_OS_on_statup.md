---
title: "Change Default OS on statup"
date: 2012-01-26
forum: General Help
---

### Post by Skyline911 on 2012-01-26
Hello.

Please can someone help me to change the default operating system my latop selects on startup (Ubuntu/Windows 7).

At the moment it defaults to Ubuntu unless I manually select something else wthin the time limit. I would like it to default to Windows 7 instead. I have already searched elsewhere for a solution and I tried a couple of options I found - neither of which were successful :(

Please can anyone assist me?

Many thanks.

---

### Post by muteXe on 2012-01-26
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Take a look at "Grub 2 files and options" section.

Change the number for GRUB_DEFAULT in /etc/default/grub to whatever entry you want. Then run that update-grub command as sudo.

---

### Post by Skyline911 on 2012-01-26
Thank you very much for your kind response.  However, as with a lot of things in Ubuntu I am a little unsure as to what I should be typing in the terminal screen in order to achieve the desired results. :(  I think I will just resort to making sure I am there to select the OS I require every time.  I only wanted to change it for convenience really. Never mind, not to worry.

Thanks again.

---

### Post by guestolo on 2012-01-26
You can simply install Startup-Manager
In terminal, you can type, or copy/paste the below command

[B][COLOR=Blue]sudo apt-get install startupmanager

[/COLOR][/B]It will require your password at the prompt
You may also get a prompt to continue after installation
Type y
Then hit Enter on your keyboard if prompted

After installation, you can find startup-manager under 
System>>Administration
If I remember correctly
Select "Windows 7' from the dropdown list

---

### Post by Skyline911 on 2012-01-27
Hello Guestolo,

Thanks for your response.  That is one of the options I had already tried but to no avail...  It still starts Ubuntu by default?  Am I doing something wrong?

---

### Post by dragonfly41 on 2012-01-27
Grub Customizer (which I have installed) appears to allow the grub order to be changed.

[EDIT] related thread here ..

[http://ubuntuforums.org/showthread.php?t=1868447](http://ubuntuforums.org/showthread.php?t=1868447)

---

### Post by Skyline911 on 2012-01-27
Briliant!!  :D

Thank you, Dragonfly41, that worked a treat.  It's clearly something to do with the grub version I have installed.......

(Thanks to others who responded as well - very much appreciated!)

:D:D:D:D:D:D:D

---

