---
title: "Root On Gnome &amp; Bash"
date: 2009-08-15
forum: General Help
---

### Post by Deicider on 2009-08-15
How do i gain permanent access to root admn rights?

---

### Post by bchurchill on 2009-08-15
> **Deicider said:**
> How do i gain permanent access to root admn rights?

You really don't want to.  Assuming you have the root password you can use 'sudo' to go into root as needed.  Being in root all the time is very insecure, and even trivial mistakes can ruin your system.

---

### Post by Bradj47 on 2009-08-15
> **Deicider said:**
> How do i gain permanent access to root admn rights?

I'm not sure if you can. I try 'su root' on the command line and it asks for a password when I never specified a root password. I try my current password and the two previous ones I had. But none works. 
```

brad@rockstar:~$ su root
Password: 
su: Authentication failure
brad@rockstar:~$ su root
Password: 
su: Authentication failure
brad@rockstar:~$ su root
Password: 
su: Authentication failure
brad@rockstar:~$ 

```
I'm not sure what's goes on with root but whenever I want to run something as root i just use 'sudo' and type my password and it works. It even remembers your password for a certain amount of time so you don't have to type it over and over.

---

### Post by louieb on 2009-08-15
You Google it - its forum policy - no how tos here on logging into  X as root.

[forum policy on log-in-as-root tutorials - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=716201") 

Don't need it  sudo will meet all your needs
to get a root shell
```
sudo -i

```to launch a command line application
```
sudo <app name>
```to launch a graphical application 
```
gksudo <app name>
```[RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Deicider on 2009-08-15
i see, then -/ The real reason am asking this cause my other HD's  want root access (cause i accidentally done somthing..dunno) and its time consuming for me to do things must open console....so how i return the HD's access rights in normal?

---

### Post by Mardoct909 on 2009-08-15
run chown USERNAME /path/to/HD

or chmod 777 /path/to/HD

I'd go for the top one, though.

---

### Post by Deicider on 2009-08-15
it will be ON after reboot right?
Just tried it...well, what i meant is that i wanted to have access to my HD's in graphic mode

---

### Post by bchurchill on 2009-08-15
What Mardoct909 suggested should work immediately.  If you're actually applying this to the mounted folder though, you'll need to add the -R option to the command, so it's

```
chown -R USERNAME /path/to/mounted/drive
```this recursively (-R) sets everything in /path/to/mounted/drive to be owned by USERNAME, so USERNAME has control over them (depending on other permissions).

If this doesn't work, please post the contents of ```
ls -l /path/to/mounted/drive
```

And after this it shouldn't matter if you're accessing it graphically or via the terminal.

---

### Post by Deicider on 2009-08-16
ye, bchurchill , it worked tnks ;D

---

