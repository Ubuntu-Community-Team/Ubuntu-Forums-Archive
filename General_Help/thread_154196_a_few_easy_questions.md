---
title: "a few easy questions"
date: 2006-04-02
forum: General Help
---

### Post by nighttime on 2006-04-02
I have an old PC running the ubuntu base system (no GUI) and I was just wondering if there's a way to turn it off without having to

```
sudo poweroff
```

It's really annoying having to type the password every time. I figure there must be a script or a binary file somewhere in the system to 'just shut it down' since you can do this from gnome by just clicking a button.

Oh and, does anyone know what "<<" means? as in

```
cat > filename << "EOF"
```

I know it does something like, end input to filename when EOF is typed alone in a line or something, but I'm looking for a more general explenation (just in case that's not all it does). I tried to google it but It didn't accept the "<<", not even quoted.

Anyway, thanks in advance.

---

### Post by mlalkaka on 2006-04-02
> **nighttime]
I have an old PC running the ubuntu base system (no GUI) and I was just wondering if there's a way to turn it off without having to

```
sudo poweroff
```

It's really annoying having to type the password every time. I figure there must be a script or a binary file somewhere in the system to 'just shut it down' since you can do this from gnome by just clicking a button.
[/QUOTE]
I don't know the answer to this question, but I think it is probably possible said:**
> 
Oh and, does anyone know what "<<" means? as in

```
cat > filename << "EOF"
```

I know, I know!
Basically, running
```
some-command <<**word**
```
Will collect all data that is entered until a line that only contains **word** (excluding **word**). It will send that data to the program (some-command, in the above example) as standard input.
For more detailed information, run the all-knowing 'man' command:
```
man bash
```
(Redirection is a feature provided by command shells, and the default command shell in GNU/Linux is bash). Search the man page for "Here Documents". I recommend that you read it.

---

### Post by nanotube on 2006-04-02
to be able to poweroff without having to enter a password, you have to edit your sudoers file. to do this, run 
```
sudo visudo
```
from commandline, and at the end of the file add the following line:
```
username ALL = (ALL) NOPASSWD: /sbin/poweroff
```
replace "username" with your own username, of course.
now, you should be able to run "sudo poweroff" without having to enter a password.

---

### Post by nighttime on 2006-04-04
Cool! Thanks guys!

---

