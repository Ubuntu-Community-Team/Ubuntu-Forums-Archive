---
title: "HELP: Locked out"
date: 2010-02-11
forum: General Help
---

### Post by AmadeusOK on 2010-02-11
After playing with my shinny new laptop, I restated the computer. But I've found myself locked out. Every time I enter my password there is a sound and I'm prompted again to the login screen. Of course my password is correct because I don't get any Authentication Failure message. Why did this happen? How can I get access to the system? How can I prevent this from happening again?

---

### Post by rnerwein on 2010-02-11
hi
may be that's a silly question. what's about "shift lock" ?
ciao

---

### Post by timgood on 2010-02-11
Also, on some laptops Num Lock operates a 'virtual' numeric keypad on the normal (letter) keys. So without noticing, if numlock is on, you may not be putting in the correct password. Worth checking out!

---

### Post by AmadeusOK on 2010-02-11
I tried to log in turning Num Lck on and off but nothing have changed. I'm still locked out of Ububtu. But I know that the password is correct because I don't get any error messages.

---

### Post by SecretCode on 2010-02-11
Can you log in with 'failsafe GNOME'? (Option at the bottom of the login screen.)

Can you log in to console mode? (Ctrl-Alt-F1/F2/...)

---

### Post by 3Miro on 2010-02-11
I constantly forget to switch the keyboard layout, if you are using a different language it might be the reason why the password is not accepted.

You can try Ctr + Alt + F1, it will take you to console mode. Then enter username and password and you can log in that way (to make sure you did not mess up the password or something). If you can log in from console, then the problem is in Gnome (the graphical environment).

---

### Post by AmadeusOK on 2010-02-11
Before all of this happened I modified the file /etc/environment and apparently I screwed it up. Using CTR+ALT+F1, I was able to log in and verified that there was no mistake in the password. But instead what I'm getting is the following message:

```

Command 'sed' is available in '/bin/sed/'
The command could not be located because '/bin' is not included in the PATH environment variable.
sed: command not found

```

How can I change PATH to its default value: "/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"? BTW, the command 'sudo' is not available either.

---

### Post by Richard1979 on 2010-02-11
> **AmadeusOK said:**
> Before all of this happened I modified the file /etc/environment and apparently I screwed it up. Using CTR+ALT+F1, I was able to log in and verified that there was no mistake in the password. But instead what I'm getting is the following message:

```

Command 'sed' is available in '/bin/sed/'
The command could not be located because '/bin' is not included in the PATH environment variable.
sed: command not found

```How can I change PATH to its default value: "/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"? BTW, the command 'sudo' is not available either.

You'll find most commands in /usr/bin so sudo will be:

$ /usr/bin/sudo <your command>

Also try /usr/sbin/ if you can't find one.

---

### Post by AmadeusOK on 2010-02-11
Thank you guys for all your help. Everything happened because I had added to the /etc/environment file additional paths. With your help I was able to enter console mode with CTR+ALT+F1. Once there I used /usr/bin/sudo and edited the environment file with nano. And all I did was to add "export PATH" at the end of the file. 

Thanks again everyone!!!

---

### Post by Richard1979 on 2010-02-11
Good stuff.

---

