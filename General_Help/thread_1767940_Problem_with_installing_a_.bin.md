---
title: "Problem with installing a .bin"
date: 2011-05-26
forum: General Help
---

### Post by Angelus Yukito on 2011-05-26
I'll start by saying I'm an absolute newbie to Linux and have to start managing my own server in the next few months at work so I'm hoping that the legendary support of the Linux community will help me get there.

I'm trying to install a copy of Postgres using the .bin(I want pg Admin III as well which is why I'm not using apt-get).

It's sitting in downloads so I did the following:

$ cd /home/ryan/Downloads
$ sudo chmod +x postgresql-9.0.4-1-linux.bin
$ ./postgresql-9.0.4-1-linux.bin

but I keep getting:
-bash: ./postgresql-9.0.4-1-linux.bin: No such file or directory

I did -ls and the file is there and I can't figure out how to get this installed. Thanks for the help in advance.

---

### Post by satanselbow on 2011-05-26
**

I really should learn to read :D post removed as talking $%&%

**

---

### Post by ruffEdgz on 2011-05-26
Wanted to know more about the file that you downloaded. If you did the commands:
```

ls -l ./postgresql-9.0.4-1-linux.bin
file ./postgresql-9.0.4-1-linux.bin

```
What is the output from the above commands?

---

### Post by Angelus Yukito on 2011-05-26
Yes, I'm trying to install the newest stable version and pgAdmin III and then eventually PostGIS.

running those commands I get:
-rwxr-xr-x 1 ryan ryan 45148406 2011-05-26 10:56 ./postgresql-9.0.4-1-linux.bin
and
./postgresql-9.0.4-1-linux.bin: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.2.5, stripped

---

### Post by gandaran on 2011-05-26
> **Angelus Yukito said:**
> I'll start by saying I'm an absolute newbie to Linux and have to start managing my own server in the next few months at work so I'm hoping that the legendary support of the Linux community will help me get there.

I'm trying to install a copy of Postgres using the .bin(I want pg Admin III as well which is why I'm not using apt-get).

It's sitting in downloads so I did the following:

$ cd /home/ryan/Downloads
$ sudo chmod +x postgresql-9.0.4-1-linux.bin
$ ./postgresql-9.0.4-1-linux.bin

but I keep getting:
-bash: ./postgresql-9.0.4-1-linux.bin: No such file or directory

I did -ls and the file is there and I can't figure out how to get this installed. Thanks for the help in advance.
this is an annoying error you usually get even if cd is correct, to get around it cd to the downloads folder then drag the .bin file to terminal with mouse after typing ./, it wont fail!
if you use **sh** instead ./ you don't need to chmod the file and use **sudo sh** or **sudo ./** to install the .bin file
if you don't have a gui on the server then just type the full bin file path even having cd the terminal, it should work with full path.

---

### Post by Angelus Yukito on 2011-05-26
Tried sudo sh and dragged the flie to console.

~/Downloads$ sudo sh '/home/ryan/Downloads/postgresql-9.0.4-1-linux.bin'
/home/ryan/Downloads/postgresql-9.0.4-1-linux.bin: 1: Syntax error: "(" unexpected

tried ./ and dragged
-bash: .//home/ryan/Downloads/postgresql-9.0.4-1-linux.bin: No such file or directory

tried sudo ./ and dragged
sudo: .//home/ryan/Downloads/postgresql-9.0.4-1-linux.bin: command not found
ryan@GeoServer:~/Downloads$

---

### Post by gandaran on 2011-05-26
> ~/Downloads$ sudo sh '/home/ryan/Downloads/postgresql-9.0.4-1-linux.bin'
/home/ryan/Downloads/postgresql-9.0.4-1-linux.bin: 1: Syntax error: "(" unexpected
only this one you have done it correctly, the others have some typing errors, was this only the error output?
look if you have the nautilus file gui on the server install this nautilus script [app runner]("http://hacktolive.org/wiki/App_Runner") then run the bin file as CLI root, if you still get any error then something is wrong with the bin file.

---

### Post by WorMzy on 2011-05-26
What does ```
arch
``` say?

---

### Post by Angelus Yukito on 2011-05-26
I'm sorry I'm so new at this. I fixed the typing errors with ./ and sudo ./ and got some same output. I don't think I have Nautilus but to be honest I don't really understand what your talking about.

---

### Post by Angelus Yukito on 2011-05-26
arch give me:

x86_64

---

### Post by jocko on 2011-05-26
> **Angelus Yukito said:**
> 
./postgresql-9.0.4-1-linux.bin: ELF **[COLOR=Red]32-bit[/COLOR]** LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.2.5, stripped

> **Angelus Yukito said:**
> arch give me:

**[COLOR=Red]x86_64[/COLOR]**
You are trying to install a 32 bit version on a 64 bit system. This is probably possible if you install all 32 bit libraries needed by postgresql, but you are probably better off installing the 64 bit version (you'll find it on the [same page]("http://www.enterprisedb.com/products-services-training/pgdownload") where you downloaded the 32 bit version).

---

### Post by Angelus Yukito on 2011-05-26
> **jocko said:**
> You are trying to install a 32 bit version on a 64 bit system. This is probably possible if you install all 32 bit libraries needed by postgresql, but you are probably better off installing the 64 bit version (you'll find it on the [same page]("http://www.enterprisedb.com/products-services-training/pgdownload") where you downloaded the 32 bit version).

Huh, I never realized I was using 64bit. All the computers at my office run 32 because they're old I didn't even notice. Thanks I'll take a look.

Doesn't fix the problem but will probably prevent future ones, thanks!

$ sudo ./postgresql-9.0.4-1-linux-x64.bin
sudo: ./postgresql-9.0.4-1-linux-x64.bin: command not found

---

### Post by Angelus Yukito on 2011-05-26
Seems to be working now. The 64x dl and dropping it on my desktop seems to have fixed it. Thanks for your help everyone, I'm sure I'll be around a lot in the weeks to come.

---

