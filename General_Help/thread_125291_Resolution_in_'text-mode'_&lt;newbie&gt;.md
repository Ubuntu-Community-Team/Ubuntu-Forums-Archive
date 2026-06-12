---
title: "Resolution in 'text-mode'?? &lt;newbie&gt;"
date: 2006-02-03
forum: General Help
---

### Post by riwa on 2006-02-03
When I go in to text-mode I have way to many 'lines-per-page' and can never see the bottom of the screen. This is annoying since i need to clear the screen every tenth command or so and is impossible in vi. How can i turn it down? 

And also how can I make the 'text-mode' default when login in?

Regards
Richard

ps. By text-mode I mean pressing *ctrl-alt-F1*

---

### Post by ranf on 2006-02-03
```
stty -a
```

tells you the current settings. 
You can temporarily change that with
```
stty rows 25
```

I just removed "splash" from the kernel's parameters in /boot/grub/menu.lst.

---

### Post by riwa on 2006-02-06
Oh! Thats great. Problem solved. How can I make that permanent. 

Also, how can I make text mode default when I start the computer??

Thanks man!

---

### Post by engla on 2006-02-06
[QUOTE=riwa]Oh! Thats great. Problem solved. How can I make that permanent. 

Also, how can I make text mode default when I start the computer??

Thanks man![/QUOTE]
The ["Speed up your boot" thread]("http://ubuntuforums.org/showthread.php?t=89491") talks about disabling services. Use the methods described there to turn off the gdm service, that's the one that starts the login window

---

