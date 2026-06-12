---
title: "i cant install ubuntu 5.10"
date: 2006-04-09
forum: General Help
---

### Post by mihrel4 on 2006-04-09
error Meassage

Failed to start the x server (your graphical interface). it is likely that is not set up correctly. would you like to view the x server output to diagnose the problem?



i have a amd 462 sochet processor
256 ddram
14 inches monitor
elitegroup L7VMM3 motherboard

---

### Post by trent dillman on 2006-04-09
Log in to the command line, and run 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Also, post your /var/log/Xorg.0.log....

It's either a driver issue, or you've got the wrong BusID in /etc/X11/xorg.conf

---

### Post by mihrel4 on 2006-04-09
where do i go to log in in command line?

---

### Post by trent dillman on 2006-04-09
When it errors, look at the output for the error message. You should be able to hit enter (or is it space?) when you're done, and it'll ask another question. Say no to that one. It will then dump you to a login screen.

Of course, you could also reboot, hit esc at Grub to get a selection menu (if it isn't already shown), and use recovery mode. If you do this, once you're finished you can just 'init 2'.

---

### Post by mihrel4 on 2006-04-09
same thing it dsnt work i tpye the 
root@ubuntu sudo dpkg-reconfigure -phigh xserver-xorg
but itt dnst change?

---

### Post by trent dillman on 2006-04-09
When you get the error, say yes to view detailed output, use the down arrow and scroll through the text and find the error message. You could also post the following file here for us to see:

/var/log/Xorg.0.log

Note the 'zero', not capital o....

---

### Post by mihrel4 on 2006-04-09
when i type the 


root@ubuntu /var/log/Xorg.0.log
No such file or diretory

Meassage

---

### Post by mihrel4 on 2006-04-09
[QUOTE=mihrel4]when i type the 


root@ubuntu /var/log/Xorg.0.log
No such file or diretory

Meassage[/QUOTE]
error no screen found

---

### Post by mihrel4 on 2006-04-09
error Fatal server error
no screen found

---

### Post by mihrel4 on 2006-04-09
error Fatal server error
no screen found

---

### Post by mihrel4 on 2006-04-09
error Fatal server error
no screen found

---

