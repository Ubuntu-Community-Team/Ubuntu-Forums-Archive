---
title: "Newb in despair."
date: 2006-04-04
forum: General Help
---

### Post by TmP on 2006-04-04
Hi!

I'm a Ubuntu enthusiast. I never finished any it course at the MIT.

Ubuntu usually works for me, but from time to time i stumble into a problem that leaves me at a total loss. I lack the basics.

Where can I download a toutorial of Ubuntu or Debian that explains:

- the commands from the terminal 
I just dont get it (lspci? how was i supposed to know that??)

- what are the basic directrories used by Ubuntu linux and what do they contain (/etc?)

- how does linux work? Starting stopping deamons? (Necromancy for beginners?) Modules? Int.d ? ARRRGH

- and everything else I need to know ( how to start x when i crush my gnome)
 
Thanx

---

### Post by LucidTaZ on 2006-04-04
You could start by reading [www.linuxcommand.org](www.linuxcommand.org)
I read it yesterday and it greatly helped me. =)

---

### Post by justleen on 2006-04-04
[QUOTE=TmP]Hi!

I'm a Ubuntu enthusiast. I never finished any it course at the MIT.

Ubuntu usually works for me, but from time to time i stumble into a problem that leaves me at a total loss. I lack the basics.

Where can I download a toutorial of Ubuntu or Debian that explains:

- the commands from the terminal 
I just dont get it (lspci? how was i supposed to know that??)

- what are the basic directrories used by Ubuntu linux and what do they contain (/etc?)

- how does linux work? Starting stopping deamons? (Necromancy for beginners?) Modules? Int.d ? ARRRGH

- and everything else I need to know ( how to start x when i crush my gnome)
 
Thanx[/QUOTE]

I think [www.linuxnewbie.org](www.linuxnewbie.org) might be a good start?
Or ask some specific questions.. The list of terminal commands is quite eloborate..
you can always try "man command""  
like man cp, this will give you the manual of the cp command..

stop/start service (for most anyway) you can do by going to /etc/init.d 
then just add stop or start
for example 
sudo /etc/init.d/gdm stop will stop the gnome dekstop manager..

---

### Post by gnu2tux on 2006-04-04
Hey !

You're in luck - I just wrote a web based guide especially for people in your position! It's proving very popular, and has an Ubuntu emphasis although it's not distro dependant. 

Check it out: [http://www.linuxnewbieguide.org]("http://www.linuxnewbieguide.org")

Most of the questions you have asked below are answered on the guide, but I can't remember if there specifically is a bit that deals with starting/stopping daemons, so for a quick answer:

to start a daemon, usually:

```

$sudo bash                             (this makes you become the super user)
Password: <your pass>             (provide your normal password)
#/etc/init.d/daemonname start  (this runs 'daemonname' with argument start)

```

all daemons have their associated scripts in init.d. The /etc/ folder always holds configurations and such like.

To stop a daemon / restart a daemon:
```

#/etc/init.d/daemonname stop
#/etc/init.d/daemonname restart

```

Hope this helps. Let me know what you think of the site!

Regards,

Al.

---

### Post by TmP on 2006-04-04
Could i download the whole resource about the ubuntu system, into my palmtop? Pdf or doc will do.. Sth comprehensive?

And btw what does "grep" do? It doesn't seem to work?
And where does linux keep it's drivers?

Thanx!

---

### Post by openmind on 2006-04-04
Very well done site Al, (I did a couple of clickthroughs to help you out!) tailored towards Noobs, I'm sure it'll help out a bunch of folk!

---

### Post by justleen on 2006-04-04
[QUOTE=TmP]And btw what does "grep" do? It doesn't seem to work?
And where does linux keep it's drivers?
Thanx![/QUOTE]

Grep is a (text) filter.
It searches for regular patterns.. for example:
you have a text file : ubuntuguide.txt
you want to search for "mount"
you could then simply use cat to disply the file, and search with grep
$ cat ubuntuguide.txt | grep mount

this way you can search in any output (the | pipe send to output of the first command to the second

$sudo apt-cache search xorg | grep xserver
for example..

grep can do a whole buch more (do a google on grep examples), but i find that i mostly use it for quick 'n dirty searching like this..

---

### Post by gnu2tux on 2006-04-04
[QUOTE=openmind]Very well done site Al, (I did a couple of clickthroughs to help you out!) tailored towards Noobs, I'm sure it'll help out a bunch of folk![/QUOTE]


Thanks very  much - Im glad you like it!

---

