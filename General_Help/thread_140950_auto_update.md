---
title: "auto update"
date: 2006-03-07
forum: General Help
---

### Post by steever on 2006-03-07
Is there any way to keep a lab of ubuntu pcs automatically patched and updated, without logging onto each one?  I had a look at [m23 ]("http://m23.sf.net")but it didn't work so well for me.

---

### Post by dcstar on 2006-03-07
[QUOTE=steever]Is there any way to keep a lab of ubuntu pcs automatically patched and updated, without logging onto each one?  I had a look at [m23 ]("http://m23.sf.net")but it didn't work so well for me.[/QUOTE]
Create cron jobs to do it.

---

### Post by bnj on 2006-03-27
Hello,
I'd like to create a cron-job to do the fully automatic update but for that, I would need a few informations:

1. What is the command-line to do an update? I know how to do it graphically, using the small icon, but not through the terminal. I would really like to know how to do that because I am more often logging on my PC from a remote machine than via the keyboard.

2. How do you go around the root-password problem? I do not have a root user on my PC, so the cron-job would have to be run by my user. Thus, I will certainly be prompted for a password, will I not?

Thank you in advance for all your answers,

Benjamin

---

### Post by kdevil on 2006-03-27
To do an update from the command line, do apt-get update && apt-get upgrade.

---

### Post by Video Toaster on 2006-03-27
[QUOTE=kdevil]To do an update from the command line, do apt-get update && apt-get upgrade.[/QUOTE]
Doesn't apt wait for user input before upgrading packages, though?

---

### Post by bnj on 2006-03-28
thank you for your answers.
I noticed that one answer to my second question is given [post=746296]here[/post].

---

### Post by yoink23 on 2006-03-29
looks like apt-get -qf update && apt-get -qf upgrade should do it, saying yes to the questions, and doing so quietly.  Anyone know if this works like it seems it should?

---

### Post by bnj on 2006-03-30
[QUOTE=yoink23]looks like apt-get -qf update && apt-get -qf upgrade should do it, saying yes to the questions, and doing so quietly.[/QUOTE]

I guess you mean apt-get -q**y** update && apt-get -q**y** upgrade.
According to this text from the man page of apt-get:
```
       -y, --yes, --assume-yes
              Automatic  yes to prompts; assume "yes" as answer to all prompts
              and run non-interactively. If an undesirable situation, such  as
              changing  a  held  package,  trying to install a unauthenticated
              package or removing an essential  package  occurs  then  apt-get
              will abort. Configuration Item: APT::Get::Assume-Yes.
```

---

