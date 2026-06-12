---
title: "Please help with screen difficulties"
date: 2009-11-20
forum: General Help
---

### Post by HEN*K on 2009-11-20
I have my computer hooked up to my Sony Bravia 37'' TV and have never had any difficulties using it as the primary (and only) screen but since a while back the computer has stopped loading. I only get a quick view of the loading scenario on the screen and then nothing happens.

Since I get a peek of the loading scenario I figure it can't be the connection with the screen that's the problem but something else, what might it be?

Thankful for all help! Pretty new to Ubuntu...

//
Henke
[email]henrik_westerlund@hotmail.com[/email]

---

### Post by Sin@Sin-Sacrifice on 2009-11-20
Are you getting a blank screen after you catch that glimpse? Also have you tried ctrl+alt+F1 to get a text log in?

---

### Post by khelben1979 on 2009-11-20
What version of Ubuntu are you using? Also, it's good to know something about your hardware configuration as well, type in the following:```
lspci
``` from a text console.

---

### Post by HEN*K on 2009-11-20
I get a black screen after seeing the first two or three rows of "dos" if you know what I mean. Apart from the new Ubuntu 9.10 (?) that's just out I have the latest allthough I have'nt uppdated in a while. My laptop workws just fine ane it has the same Ubuntu but has recently been updated. I don't know how to access any setup screens and I donn't know what to do should I get there... I really need help...

//Henke

---

### Post by HEN*K on 2009-11-20
And oh yeah, since the Ubuntu loading sound does'nt appear, my conclution is that there is something wrong with the computer itself rather than just the monitor. I'm the only one I know who uses Ubuntu so I don't know where else to ask but here. Can anyone figure oout what's wrong or what I should do? Excuse me if I explain things in a difficult way but English is just a secondary language of mine sincce I'm Swedish....

//Henke

---

### Post by khelben1979 on 2009-11-21
In non graphical mode you have the choice with using the tool called: [dselect]("http://www.debian.org/doc/manuals/dselect-beginner/").

```
sudo dselect
```
and from there you can start searching for system packages.

And ```
sudo apt-get install dselect
``` if it's not installed.

A good way of learning Linux is to use the man pages and in this case you can start by learning the apt-get command:
```
man apt-get
```

---

