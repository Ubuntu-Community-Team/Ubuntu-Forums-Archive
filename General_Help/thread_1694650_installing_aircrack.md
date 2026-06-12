---
title: "installing aircrack"
date: 2011-02-24
forum: General Help
---

### Post by maelstrom.1k on 2011-02-24
to whom it may concern:
 
 
this post, is in regards to a plea for help, in my trying to request any, & all assistance anyone here can give to me, (or may be willing to), on step by step instructions, regarding my installing aircrack on my laptop.... although i have the software for setting up & using aircrack, {on my Hewlett/Packard G71 340us} I am very, very confused as to how to install it: as it is unlike any software you install, requiring you to take a great deal of steps to install it... and i do not have the expertise nor know how to set it up.... {obviously, this program was written for & by techies & hackers, who know what they are doing & can install it} i ask, if anyone on here would be willing to have mercy on me, to email me, step by step instructions on how to set it up, {on my laptop} & what other software i would need to get it running..... I conclude here, & await for any & all of your replies to me regarding this matter.... and thank you for all of your time & attention...

---

### Post by oldos2er on 2011-02-24
```
sudo apt-get update && sudo apt-get install aircrack-ng
```

---

### Post by maelstrom.1k on 2011-02-25
Dear Sir:


I don't know if this message is an attempt at humor, of if your giving me some actual instructions.... If it is indeed the latter: Could you please clarify for me, _just what this information is_, & what
purpose, should I utilize it for?... Thank you....


]> **oldos2er said:**
> ```
sudo apt-get update && sudo apt-get install aircrack-ng
```

---

### Post by oldos2er on 2011-02-25
Please don't call me "sir."

The command I gave you is meant to be copied and pasted into a terminal, which you can find via the menus Applications, Accessories, Terminal.

---

### Post by WorMzy on 2011-02-25
oldos2er's advice is, as always, spot on.

However, if you, for whatever reason, wish to install from source. You need to make sure that you have all the required dependencies (lorcon version 1 and the python wrapper -- pylorcon), then run "make" from the folder containing the source code you downloaded, and then, assuming that you get no errors, run "sudo make install" (or "sudo checkinstall")

---

### Post by maelstrom.1k on 2011-02-26
dear Ms.:
No disrespect was intended....


> **oldos2er said:**
> please don't call me "sir."

the command i gave you is meant to be copied and pasted into a terminal, which you can find via the menus applications, accessories, terminal.

---

### Post by maelstrom.1k on 2011-02-26
being the {really} big dummy here, & all of you, being the  echelon of experts, I have no right, to challenge, nor question anything as to what you're all posting to me... i believe you all, implicitly.... but if i am {ever} going to install this program, i need all of the links you're all willing to post, {if you would be willing to} for the additional software & "cogs", i will need to run this program.... if any of you would be willing to help..... i have aircrack1.1, as a tag file, from [www.fullandfree.info](www.fullandfree.info), but you will have to let me know if this is indeed the most current version for me to install.... if your all willing to reply, then i will await for your wise replies to me... thank you....


> **WorMzy said:**
> oldos2er's advice is, as always, spot on.

However, if you, for whatever reason, wish to install from source. You need to make sure that you have all the required dependencies (lorcon version 1 and the python wrapper -- pylorcon), then run "make" from the folder containing the source code you downloaded, and then, assuming that you get no errors, run "sudo make install" (or "sudo checkinstall")

---

### Post by wiggly81 on 2011-02-26
you would be much easier to open a terminal window as discribed previously and typing ```
sudo apt-get install aircrack-ng
``` or even going to System > Administration > Synaptic Package Manager and searching "aircrack-ng" in the box that comes up

---

### Post by mhgsys on 2011-02-26
^ + 

inb4 the lock.. 

next thing your gonna ask is how to use it to crack a network

):P

---

### Post by oldos2er on 2011-02-27
The version in the repositories is 1.1-1. I looked at the website you posted, all I could find was a Windows version of aircrack. Windows programs do not run natively on Linux.

---

### Post by lisati on 2011-02-27
> **maelstrom.1k said:**
> Dear Sir:

> **oldos2er said:**
> Please don't call me "sir."

> **maelstrom.1k said:**
> dear Ms.:

A friendly, off-topic aside here: although we appreciate people being polite, salutations such as "Dear Sir" are a little bit more formal than we're accustomed to here.

---

### Post by maelstrom.1k on 2011-02-27
[CENTER]I do not know how to do that... would you {PLEASE} explain as to how I can perform this function?..... by the way: {as I have posted} I have a Hewlett/Packard G71-340us: so you will have to let me know what feature I will have to go to, in order to initiate this command...[/CENTER]
 
 
 
> **wiggly81 said:**
> you would be much easier to open a terminal window as discribed previously and typing ```
sudo apt-get install aircrack-ng
``` or even going to System > Administration > Synaptic Package Manager and searching "aircrack-ng" in the box that comes up

---

### Post by maelstrom.1k on 2011-02-27
[CENTER]Dear ma'am:


cAN YOU PLEASE ME THEN, WHAT VERSION SHOULD I BE RUNNING?..... AS I CAN'T USE THE MAC VERSION, AS MY LAPTOP IS NOT MAC.... {IT'S A HEWLETT PACKARD G71-340US} PLEASE TELL ME WHAT VERSION I SHOULD HAVE, & WOULD PLEASE BE SO KIND TO EMAIL ALL OF THE STEP TO FOLLOW TO INSTALL THIS PROGRAM?..... I WOULD APPRECIATE YOUR HELP....[/CENTER]
 
 
 
 
 
> **oldos2er said:**
> The version in the repositories is 1.1-1. I looked at the website you posted, all I could find was a Windows version of aircrack. Windows programs do not run natively on Linux.

---

### Post by Slave2Metal on 2011-02-27
May I make a friendly suggestion...You really need to understand linux and the command line in general before you go auditing wireless all willy nilly.  Please visit the aircrack forums and wiki.
> **maelstrom.1k said:**
> [CENTER]I do not know how to do that... would you {PLEASE} explain as to how I can perform this function?..... by the way: {as I have posted} I have a Hewlett/Packard G71-340us: so you will have to let me know what feature I will have to go to, in order to initiate this command...[/CENTER]


---

### Post by spiky001 on 2011-02-27
Go to top left cornor click system goto Administration click go down to SYNAPTIC PACKAGE MANAGER, select it when it opens top right type in search box aircrack thhen select Aircrack-ng then apply it will install it

---

### Post by uRock on 2011-02-27
Please install Aircrack via your menus. Go to **Applications> Ubuntu Software Center**, then in the search box enter aircrack, then click the button to install the software.

[SIZE=4]Please use the default fonts.[/SIZE]

---

### Post by maelstrom.1k on 2011-02-28
[COLOR=blue][SIZE=3]****[/SIZE][/COLOR]hello lisa!:
Decency & respect, don't cost a thing, to  give to good people on here, who have been so nice to reply to me..... It's the least i can do as you all have been so good to reply to me..... You all deserve that much.......



> **lisati said:**
> a friendly, off-topic aside here: Although we appreciate people being polite, salutations such as "dear sir" are a little bit more formal than we're accustomed to here.

---

### Post by maelstrom.1k on 2011-02-28
dear ma'am:
Can you please tell me then, what version should i be running?..... As i can't use the mac version, as my laptop is not mac.... {it's a hewlett packard g71-340us} please tell me what version i should have?....  Would you please be so kind to email all of the step to follow to install this program?..... I would appreciate your help....

---

### Post by uRock on 2011-02-28
Use the version in the repos.

---

### Post by maelstrom.1k on 2011-02-28
[COLOR=red][SIZE=3]****[/SIZE][/COLOR]dear sir;
can such be found on here?...... Can you post a link for me to direct download it?...... I will try to download it from my cell phone...... (which i am posting from now).....

> **urock said:**
> use the version in the repos.

---

### Post by maelstrom.1k on 2011-02-28
***[SIZE=3] [/SIZE]***i have a wep &wap cracking program called 'airsnort' saved too......... From what i understand, this program is no longer supported, so therefore it can no longer be used for "cracking"..... Does any on here know if this is true?..... Should i delete the program, seeing it no longer has any use?.... If i can use it, how can i install it?......

---

### Post by uRock on 2011-03-01
> **maelstrom.1k said:**
> dear sir;
can such be found on here?...... Can you post a link for me to direct  download it?...... I will try to download it from my cell phone......  (which i am posting from now).....> **oldos2er said:**
> ```
sudo apt-get update && sudo apt-get install aircrack-ng
```

> **wiggly81 said:**
> you would be much easier to open a terminal window as discribed previously and typing ```
sudo apt-get install aircrack-ng
``` or even going to System > Administration > Synaptic Package Manager and searching "aircrack-ng" in the box that comes up
> **uRock said:**
> Please install Aircrack via your menus. Go to **Applications> Ubuntu Software Center**, then in the search box enter aircrack, then click the button to install the software.

[SIZE=4]Please use the default fonts.[/SIZE]

**[COLOR=Red]*****[/COLOR]You were given many methods here that will install Aircrack NG. Please select one and do it. Any one of these methods will install the newest version of Aircrack NG on your system.[COLOR=Red]*****[/COLOR]**[B]

Once you give one of these methods a try, please let us know how it went.

Cheers,
uRock[/B]

---

### Post by cariboo on 2011-03-01
From the looks of it the op isn't using Ubuntu, so we can't be of any help to him, this thread is closed.

---

