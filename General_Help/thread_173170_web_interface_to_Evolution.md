---
title: "web interface to Evolution"
date: 2006-05-09
forum: General Help
---

### Post by kaplanmyrth on 2006-05-09
I'm an ubuntu user with a single machine on the internet, but I often work from other locations (office, school, library, etc.). I am trying to figure out how I can  manage mail and calendar while I am away from my desk.

My computer is set up as a web server already. Is there any program that will give me basically a web interface to Evolution?

It feels like it would be overkill to run a groupware server like zimbra, but that's the sort of program that has the features I'm looking for -- but for a single user.

I know what you're thinking, and no, I don't want a pony too. I've looked at phpiCalendar, which lets me *see* my calendar and tasklist, which is a good start. But I haven't seen anything similar for email. Also, I'm surprised there isn't anything more AJAXified out there.

Any tips?

---

### Post by Aphorism on 2006-05-09
OK, I'll bite.  How about simple?  ssh -X and launch it?

Or do you mean from a Winblows / SackOSX box?

---

### Post by kaplanmyrth on 2006-05-09
[QUOTE=Aphorism]How about simple?  ssh -X and launch it?

Or do you mean from a Winblows / SackOSX box?[/QUOTE]

Yes, I use Ubuntu at home where Evolution is running, but I use Windows at work, Mac at school, usually Windows when travelling, etc. Without entering into a debate about the relative merits of the various OS's, let's just say I'd like to use the web browser to avoid those compatibility problems.

btw, I prefer Firefox :-)

---

### Post by rvergara on 2006-05-09
I do this on a daily basis using Freenx. It has excellent performance over remote connections.

Ramiro

---

### Post by kaplanmyrth on 2006-05-10
I use vino, which is okay, but remote desktop apps don't serve the same purposes as putting it on the web. I can't use freenx because I don't always have admin access at the other end, and I haven't found a freenx client that doesn't need to be installed. I use TightVNC instead.

---

### Post by z_diver on 2006-05-10
As far as I know, this is not a feature of Evolution and I don't know of a project that attempts to provide a web interface for Evo.  It's a good idea though.  

I've accomplished some of these requirements by using imap and publishing web pages of my calendar.   For a long time now I've meant to put my addresses in an LDAP directory but so far haven't gotten around to it.

---

