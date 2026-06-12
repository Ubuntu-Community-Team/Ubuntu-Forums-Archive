---
title: "Changing bash command"
date: 2011-09-13
forum: General Help
---

### Post by mobius129a on 2011-09-13
Quick question: how can I protect an application - run from the terminal - with the user password without changing permissions or ownership? Put another way, how do I add ```
gksu
``` to the application's bash command? TIA.

---

### Post by SlugSlug on 2011-09-13
> **mobius129a said:**
> Quick question: how can I protect an application - run from the terminal - with the user password without changing permissions or ownership? Put another way, how do I add ```
gksu
``` to the application's bash command? TIA.


maybe via bash alias?

look in .bashrc

---

### Post by mobius129a on 2011-09-13
Sorry, scrap that. I just realised that I DON'T want to run the application with heightened privileges. So, is there any way of running the application and password-protecting it without elevating user privileges? Thanks.

---

### Post by MG&amp;TL on 2011-09-13
depends on the command. knock sudo, gksudo, gksu, off the front, generally.

---

### Post by mobius129a on 2011-09-13
Yes, but surely that would remove any password-protection. For instance, take brasero. If I wanted to run the command 'brasero' in the terminal or launch brasero from the Applications menu, how would I password-protect it without changing privileges?

---

### Post by MG&amp;TL on 2011-09-13
This is definitely not the optimum way-but I would write a program that uses a password, then calls the program. I don't know how you'd disable the initial program....move it out of /usr/bin or /bin, I guess.

But then you could only call it through the command-line.

---

### Post by mobius129a on 2011-09-13
Ok thanks but is there no simpler way? Could the keyring daemon be of any use for storing a password?

---

### Post by MG&amp;TL on 2011-09-13
```
gksu nautilus
```

browse to /usr/bin/brasero

right-click, properties, permissions. This do what you wanted it to?

---

### Post by fdrake on 2011-09-13
well that's kinda tricky since we have user permissions to run/control programs. 
what you should u is to create a program like sudoers in python or c++
what you can do is: 
```

locate program  # locate the programs source . it should be somewhere in /usr/bin or /bin

sudo chmod o-x /usr/bin/program  # change the permissions of the program so that it will be executabile only by admin users

sudo mv /usr/bin/program /usr/bin/program_0 edit the name of the program with something different

```

and then create a script with your programs name that asks you for password authentication and after positive result runs the program. The script will have a SUID sticky bit. Bash script will not work in this case

or you can just encrypt the programs source file with a password or a pass-phrase. and decypt it each time someone uses it.
```

mcrypt -a blowfish myfile
mcrypt -d myfile.nc    

```

---

### Post by MG&amp;TL on 2011-09-13
Better question: why do you want to do that?

---

### Post by mobius129a on 2011-09-13
@MG&TL: I don't want to password-protect brasero necessarily, just any application in general. For instance, I intend to password protect my mail client and certain work-specific applicaftions.

@fdrake: I'll try that and get back some time this week to see if that works for me. I did think there would be some simple, obvious way but clearly not. Cheers anyway.

---

### Post by MG&amp;TL on 2011-09-13
Okay. I know, it was just an example. I shall have a bit of a dig, but what fdrake said is probably easiest.

---

### Post by Vaphell on 2011-09-13
i guess that you share a single user account? you know, login screen is supposed to protect user data from unauthorized access ;-) running apps by other people doesn't matter when they can't mess with your sensitive data stored in your home dir.

---

