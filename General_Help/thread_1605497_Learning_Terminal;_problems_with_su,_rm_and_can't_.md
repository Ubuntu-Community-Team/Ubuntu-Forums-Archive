---
title: "Learning Terminal; problems with su, rm and can't find some scripts"
date: 2010-10-25
forum: General Help
---

### Post by HitmanNumber86 on 2010-10-25
Karmic; Asus PEB 1005

Forgive me for not being HTML savvy. I apologize again if this problem is simple, but I'm trying. 


Code:
hitmannumber86@Faptop-357:~/Documents$ sudo rm -f bollox
[sudo] password for hitmannumber86: 
rm: cannot remove `bollox': Is a directory
hitmannumber86@Faptop-357:~/Documents$ su
Password: 
su: Authentication failure


rm never seems to work and even though sudo works su doesn't. What the hell am I doing wrong? 

I'm trying to learn via Linuxcommand.org. They ask me to use .bash_profile as well as .bashrc but I can't seem to find them. They told me to use ~/bin but there was none, so I made one as suggested and added the $PATH by throwing the command in bash.bashrc. 

I know it sounds stupid but I'm really trying here guys.

Thank you in advance

---

### Post by WorMzy on 2010-10-25
su doesn't work in Ubuntu, it requires the root account's password, which isn't set by default. You can set one, but this is highly discouraged since sudo can be used for everything that would require su.

You can't rm a directory without the -r flag, you can use rmdir for empty directories. For non-empty directories, use

```
rm -r <directory>
```

Prepend sudo if required. You were in your Document's folder, so this is unlikely. You only need sudo if root permissions are required.

---

### Post by nothingspecial on 2010-10-25
su means switch user.

On it`s own it defaults to root.

On ubuntu, we use sudo instead. So instead of switching to root, you put any command root needs to do with a sudo infront of it.

If you need to do a few, don`t worry you will only have to type your password once, it will remember you for a few minutes.

What command did you put in .bashrc?

I have 

```
PATH=$PATH:~/myscripts
export PATH
```

but the same would work for ~/bin

or ~/bananas if you wanted.

---

### Post by HitmanNumber86 on 2010-10-25
In bash.bashrc I put...

#Allow scripts to run from profile bin folder, as per linuxcommand.org lecture.
export PATH=$PATH:/home/hitmannumber86/bin

I know the folder could be named anything, but I'm trying to stick to the lecture. I'll be upgrading to 10.04 here soon but I expect the problems won't change. 

Does anyone know of any more updated in depth terminal lectures that are ubuntu based? I'm also very interested in learning vi but I haven't looked for anything yet. Due to limited Internet connectivity I must prioritize my time and save lectures to HTML archives when I can.

---

### Post by WorMzy on 2010-10-25
Install vim (_vi_ i_m_proved) and run vimtutor. That'll teach you the basics of using vim (and vi).

---

### Post by AlphaLexman on 2010-10-25
In ubuntu, linux, and unix, paths are relative. I have noticed that twice you referred to:
> bash.bashrc
The actual location should be:
```
~/.bashrc
```
(~) is the 'home' folder for your $USERNAME in /home.
A filename of 'bash.bashrc' will NOT be invoked by an 'interactive' shell or terminal, unless expressly called by a 'login' shell.

---

