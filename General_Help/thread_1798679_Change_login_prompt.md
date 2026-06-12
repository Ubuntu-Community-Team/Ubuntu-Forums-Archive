---
title: "Change login prompt"
date: 2011-07-06
forum: General Help
---

### Post by Sickpuppy87 on 2011-07-06
Hello,

This might be simple but i am unable to find an answer anyplace online.  

How do you change the terminal login prompt on a Ubuntu server?

Right now when you go to log into the server it displays:

<old_servername> login:

I would like it to just display login without the server name or the new server name. I am not sure how that info go in the login prompt to begin 

Might sound silly but it bothers me  :p

ubuntu 10.04

---

### Post by WorMzy on 2011-07-06
I believe that editing /etc/issue will accomplish this. Just remove the \n.

\n = hostname
\l = tty identifier (e.g. tty1)

---

### Post by Sickpuppy87 on 2011-07-06
I tried taking all switches out of this file and it still appears on the same line before login. :( 

It did however remove the tty1 after the ubuntu version.

---

### Post by WorMzy on 2011-07-06
Yes, sorry, I didn't read your question carefully enough. What you're describing isn't controlled by /etc/issue, but by the login command. I'm not sure that you can modify it without recompiling it.

However, if it's displaying <old_hostname>, that suggests that you haven't properly updated your hostname. Make sure you've got the correct hostname in /etc/hosts as well as /etc/hostname

---

### Post by Gyokuro on 2011-07-06
You have to change this in .bashrc and append stuff like this:

PS1='\[\e[0;31m\]\u\[\e[m\] \[\e[1;34m\]\w\[\e[m\] \[\e[0;31m\]\$ \[\e[m\]\[\e[0;32m\]'

look in the net for something like color bash prompt; you will get a lot of crazy bash prompt ideas - have fun :)

---

### Post by Sickpuppy87 on 2011-07-06
Wormzy
Thats a good question. The name was changed by doing a hostname Newservername.  I will check the two files you listed and let you know

gyokuro
i thought that PS1 only changed the prompt after logged in correct ?

---

### Post by WorMzy on 2011-07-06
That's correct. I think Gyokuro didn't read the first post properly either. ;)

btw, here's the offending code, if you choose to compile your own version.

```
		/* Make the login prompt look like we want it */
		if (gethostname (hostn, sizeof (hostn)) == 0) {
			snprintf (loginprompt,
			          sizeof (loginprompt),
			          _("%s login: "), hostn);
		} else {
			strncpy (loginprompt, _("login: "),
			         sizeof (loginprompt));
		}

```

Line 744-752 of login.c, from shadow (svn://anonscm.debian.org/pkg-shadow/upstream/trunk)

---

### Post by Gyokuro on 2011-07-06
@Sickpuppy87 + WorMzy: you're both correct - must learn to read properly ;-)

---

### Post by Sickpuppy87 on 2011-07-06
Wow I feel dumb! As you said wormzy the hostname did not update correctly it was changed hostname but not hosts.  Updated that rebooted all is well in life.  Thanks for the help.

---

