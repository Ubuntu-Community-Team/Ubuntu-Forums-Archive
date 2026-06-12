---
title: "How to run a terminal command at startup"
date: 2010-11-09
forum: General Help
---

### Post by Bitech on 2010-11-09
I've searched everywhere, but they all talk about BOOTING into the terminal instead of ubuntu. But here all I want is for ubuntu to automatically run a certain command when I boot into ubuntu. 

This is related to the screen brightness change problem that's still much of an unsolved mystery for ubuntu and I have mostly solved this 
I'm able to change the brightness with sudo setpci -s 00:02.0 F4.B=xx, xx being from 00 to FF, but it doesnt seem to stay when I log out and log back in. 

Is there any possible way to put a terminal command in the startup applications or something or a possible solution to the brightness problem that I havent discovered yet?

My graphics card/chipset is an Intel Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)

---

### Post by sgage on 2010-11-09
You can put your command in /etc/init.d/rc.local, and it will execute upon boot.

---

### Post by Bitech on 2010-11-09
I really dont know how to follow this guide:

[https://help.ubuntu.com/community/RcLocalHowto](https://help.ubuntu.com/community/RcLocalHowto)
Making the file in terminal all I see are dashed line to the side and wierd things happen when I try to type something in or go backspace or down a line, etc. Can someone thoroughly explain this guide to me, because I'm not an ubuntu expert and I just wanna follow step-by-step directions to making this file and exexcuting a command at startup. 

Honestly what am I supposed to do after step one just leave my terminal there and execute step 2 on a new terminal? Because there's a no file such file or directory error comes up. Thanks

---

### Post by TSJason on 2010-11-10
Hi,

You probably don't want to use "vi" unless you're familiar with it. Instead, why don't you try:

```
sudo gedit /etc/init.d/rc.local
```

"gedit" will give you a graphical editor.

If you're looking for a command-line editor that works similar to the old dos editor, you can try "nano" in place of gedit or vi.

---

### Post by Hippytaff on 2010-11-10
vi takes some learning, I settled on nano too :-)

---

### Post by Bitech on 2010-11-10
guess ill just stick with simple gedit. 

to add my command script to start up is there a specific line on rc.local where i should add the command?

and how should i add the command if it requires the password to be typed in?

---

### Post by SeijiSensei on 2010-11-10
> **Bitech said:**
> guess ill just stick with simple gedit. 

to add my command script to start up is there a specific line on rc.local where i should add the command?

and how should i add the command if it requires the password to be typed in?

All init scripts like rc.local run with root privileges, so you don't need to use sudo or enter a password.  Just add the command to rc.local like this:

```
setpci -s 00:02.0 F4.B=xx
```

Make sure it comes before the "exit 0" line.

---

### Post by yetiman64 on 2010-11-10
> **Bitech said:**
> guess ill just stick with simple gedit. 

to add my command script to start up is there a specific line on rc.local where i should add the command?

and how should i add the command if it requires the password to be typed in?
When editing the file with gedit, please use **gksudo** as gedit is a graphical application, Link #4 in my sig (RootSudo) "Graphical Sudo" section explains why this is.

You can edit that file and add your command without sudo as rc.local runs as root when starting up.

I would suggest you try the command with the file /etc/rc.local to see if it works, as you are less likely to accidentally alter the scripting in /etc/init.d/rc.local and /etc/rc.local is run on startup and should activate  your command.

Just stick your command
> setpci -s 00:02.0 F4.B=xxafter the line (in a new line of its own)
> # By default this script does nothing.and before the line
> exit 0(this must be left)

---

### Post by Bitech on 2010-11-10
wait whats the difference between the rc.local files in etc and init.d?

Edit: the guide seems to have pointed me to the one in init.d, which doesnt have the exit 0 line but the one in etc does and doesnt have all the clutter lines in it, and adding the command in that solves my problem, thanks a lot guys!

---

### Post by TSJason on 2010-11-11
Actually, you want to use the one in /etc. The one in init.d actually executes the one in /etc at startup.

---

