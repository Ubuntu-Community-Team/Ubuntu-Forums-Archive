---
title: "export TERM=xterm"
date: 2011-06-22
forum: General Help
---

### Post by collisionystm on 2011-06-22
Question...

I am using lxterminal to connect to a telnet session on another *nix box.

After I connect, I always have to enter the command
```

export TERM=xterm
```

is there anyway to automate this?

Thanks

---

### Post by TeoBigusGeekus on 2011-06-22
Add it to your ~/.bashrc

---

### Post by amauk on 2011-06-22
Just to clarify
that's the ~/.bashrc file on the server you're connecting to
(and it assumes the server's using Bash, of course)

---

### Post by collisionystm on 2011-06-22
> # .bashrc

# User specific aliases and functions
export TERM=xterm
alias rm='rm -i'
alias cp='cp -i'
alias mv='mv -i'

# Source global definitions
if [ -f /etc/bashrc ]; then
        . /etc/bashrc
fi



Is this correct? I added this on the server I am connecting to, under the directory of the user I am connecting with

---

### Post by amauk on 2011-06-22
> **collisionystm said:**
> Is this correct? I added this on the server I am connecting to, under the directory of the user I am connecting withYes

---

### Post by collisionystm on 2011-06-22
hm. Didn't seem to work.

Maybe I need to restart something?

---

### Post by nothingspecial on 2011-06-22
Well a restart will work, but after modifying your .bashrc (or .bash_aliases, or anyother file you ask your .bashrc to read) type

```
. ~/.bashrc
```

---

### Post by collisionystm on 2011-06-22
> **nothingspecial said:**
> Well a restart will work, but after modifying your .bashrc (or .bash_aliases, or anyother file you ask your .bashrc to read) type

```
. ~/.bashrc
```


BTW... This is a CentOS Box

I performed these commands in /root where the .bashrc file is located for the root account that I am trying this with.

> /root> . ~/.bashrc
-ksh: .[11]: .[36]: shopt: not found [No such file or directory]
-ksh: .[11]: .[40]: shopt: not found [No such file or directory]> /root> . .bashrc
-ksh: .[11]: .[36]: shopt: not found [No such file or directory]
-ksh: .[11]: .[40]: shopt: not found [No such file or directory]

---

### Post by nothingspecial on 2011-06-22
](*,)

You are running the korn shell, not bash.

You might have mentioned that.

I have never used ksh.

---

### Post by TeoBigusGeekus on 2011-06-22
Put the export command into .kshrc and run
```
. ~/.kshrc
```

---

### Post by WorMzy on 2011-06-22
Add it to .kshrc, or .profile, then log out and back in.

---

### Post by collisionystm on 2011-06-22
lol sorry. I had no idea.

The system is Centos 5 running Acucobol 

We telnet to it to access menu's to fill out Job Cards, PO's, etc.

The program we use to telnet is a windows program called Reflection for Unix.

I am trying to find an alternative. I can make it work by doing an SSH inside of an xterm and issuing the export TERM=xterm command. It lets me gain control of my Function Keys ( very important ) . 

So, I thought I would ask and see what was out there.

---

### Post by collisionystm on 2011-06-22
> **WorMzy said:**
> Add it to .kshrc, or .profile, then log out and back in.


I have neither.

---

### Post by TeoBigusGeekus on 2011-06-22
> **collisionystm said:**
> I have neither.

Create one.

---

### Post by collisionystm on 2011-06-22
> **TeoBigusGeekus said:**
> Create one.


My God.

Genius.

I made the .kshrc

and added

export TERM=xterm

SUCCESS!

Thanks Gents!

Cheers

---

### Post by collisionystm on 2011-06-22
oh and before we sign off of here, quick question for you. If I chose to telnet instead of doing korn or bash, what file would I edit then? The .profile ?

---

### Post by collisionystm on 2011-06-22
> **collisionystm said:**
> oh and before we sign off of here, quick question for you. If I chose to telnet instead of doing korn or bash, what file would I edit then? The .profile ?


nevermind answerd it myself. Its the same .kshrc

---

