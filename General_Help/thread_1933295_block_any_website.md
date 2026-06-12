---
title: "block any website"
date: 2012-02-29
forum: General Help
---

### Post by ramakanta on 2012-02-29
How to block any website in my ubuntu 10.04 OS like Windows OS.
please help me.
thank you.

---

### Post by enjoijesus94 on 2012-02-29
Open ```
gksudo gedit /etc/hosts
``` as root by pasting following command in terminal.

In there you will see 

the IP
127.0.0.1 put banned website here.

paste your local ip and the website you want to ban 

hope it helped

---

### Post by ramakanta on 2012-02-29
> **enjoijesus94 said:**
> Open ```
gksudo gedit /etc/hosts
``` as root by pasting following command in terminal.

In there you will see 

the IP
127.0.0.1 put banned website here.

paste your local ip and the website you want to ban 

hope it helped
i want to block facebook website ,if possible kindly give example
with details.
thank you.

---

### Post by clausrei on 2012-02-29
> 
How to block any website in my ubuntu 10.04 OS like Windows OS.


In exactly the same way I suppose !? By blocking the website inside your browser. I found this Firefox add-on ([here]("https://addons.mozilla.org/en-US/firefox/addon/blocksite/")).

---

### Post by enjoijesus94 on 2012-02-29
> **ramakanta said:**
> i want to block facebook website ,if possible kindly give example
with details.
thank you.

No problem 

ok so i open /etc/hosts inside terminal.
go to 
Applications > Accessories > Terminal

when it opens type 

gksudo gedit /etc/hosts

When it opens go to line 5 in that script and write your Local ip.

and beside your IP write the website [www.facebook.com](www.facebook.com)

for example 

my Local Ip is 
127.0.0.1 [www.facebook.com](www.facebook.com)

and save the script and exit 

now when the person goes to the webpage it will be locked.

---

### Post by ramakanta on 2012-02-29
> **enjoijesus94 said:**
> No problem 
 
ok so i open /etc/hosts inside terminal.
go to 
Applications > Accessories > Terminal
 
when it opens type 
 
gksudo gedit /etc/hosts
 
When it opens go to line 5 in that script and write your Local ip.
 
and beside your IP write the website [www.facebook.com]("http://www.facebook.com")
 
for example 
 
my Local Ip is 
127.0.0.1 [www.facebook.com]("http://www.facebook.com")
 
and save the script and exit 
 
now when the person goes to the webpage it will be locked.
thank you friend. it works.
now i had try 0.0.0.0 it also works.
but if u have no problem , then i have one question. **gksudo** means. please .
thank you.

---

### Post by enjoijesus94 on 2012-02-29
Gksudo just pops open a dialog box for the password 
as in sudo only asks for the password in via terminal 

and glad it helped.
just ask for more help.:popcorn:

---

### Post by ramakanta on 2012-02-29
> **enjoijesus94 said:**
> Gksudo just pops open a dialog box for the password 
as in sudo only asks for the password in via terminal 

and glad it helped.
just ask for more help.:popcorn:
just i want full form of gksudo.
thank you.

---

### Post by enjoijesus94 on 2012-02-29
For More Info On Gksudo 

go to terminal and type 

```
man gksudo
```

it will give you all kinds of info on it.:guitar:

---

### Post by ramakanta on 2012-02-29
> **enjoijesus94 said:**
> For More Info On Gksudo 

go to terminal and type 

```
man gksudo
```

it will give you all kinds of info on it.:guitar:
Thaks Friend.

---

### Post by enjoijesus94 on 2012-02-29
> **ramakanta said:**
> Thaks Friend.

No problem:popcorn:

---

