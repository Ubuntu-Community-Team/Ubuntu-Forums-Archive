---
title: "Terminal Password Issues"
date: 2011-03-13
forum: General Help
---

### Post by Muzic Lopez on 2011-03-13
This is an issue I've been tracking for hours but couldn't find a solution.

The problem is: I am trying to install Avast anti virus. I followed the instructions from here, [http://www.ubuntugeek.com/avast-antivirus-for-ubuntu-desktop.html](http://www.ubuntugeek.com/avast-antivirus-for-ubuntu-desktop.html)

I got as far as to the executing the sudo dpkg -i avast4workstation_1.0.6-2_i386.deb command in the terminal. The command was recognised but then it has for my password. I typed in the root password thats used to log in as the user and to grant permission for all sorts of things. However, terminal kept telling me to try again. When I try to type in the password manually, terminal stops me before I can finish and ask me to try again. So every time I have to paste the password, but terminal still doesn't accept it.

I found a post here on the forums that said something about my root password and another password associated with sudo, but I didn't understand what they were talking about. : [http://ubuntuforums.org/showthread.php?t=1563623&highlight=root+password](http://ubuntuforums.org/showthread.php?t=1563623&highlight=root+password)

I installed Ubuntu 10 today, and I am running on a 64 bit HP PC laptop, I've gotten these password failures before when I tried to use PC Linux OS. All in all, I've picked up how Ubuntu works pretty well and other than understanding installations and this password issue, I've had no problems.

Thank you readers for taking the time to read this and an extra thank you to those who post responses.

---

### Post by oldos2er on 2011-03-14
Do you have your Caps Lock on by any chance? Linux is case-sensitive.

---

### Post by Muzic Lopez on 2011-03-14
Caps lock was not on.

And I copy & pasted the PW.

---

### Post by antaios256 on 2011-03-14
the only thing i can think of is that the sudo password has not been set 

try  sudo passwd

then set a new sudo password

---

### Post by evilsoup on 2011-03-14
> **Muzic Lopez said:**
> This is an issue I've been tracking for hours but couldn't find a solution.

The problem is: I am trying to install Avast anti virus. I followed the instructions from here, [http://www.ubuntugeek.com/avast-antivirus-for-ubuntu-desktop.html](http://www.ubuntugeek.com/avast-antivirus-for-ubuntu-desktop.html)

First, I'd like to point out that Ubuntu is safe from viruses, so you should only bother installing an anti-virus if you need to scan a Windows computer.

> I got as far as to the executing the sudo dpkg -i avast4workstation_1.0.6-2_i386.deb command in the terminal. The command was recognised but then it has for my password. I typed in the root password thats used to log in as the user and to grant permission for all sorts of things. However, terminal kept telling me to try again. When I try to type in the password manually, terminal stops me before I can finish and ask me to try again. So every time I have to paste the password, but terminal still doesn't accept it.I know this sounds silly, but when you enter your password manually, are you sure that you're not accidentally hitting the enter key? Also, about pasting into the terminal: you have to use CTRL+SHIFT+V - are you doing this?

If you can't get it to work in the terminal, you can always use the graphical route (that is, double-click on the .deb, when the software centre comes up click 'install').

---

### Post by Muzic Lopez on 2011-03-14
> **evilsoup said:**
> First, I'd like to point out that Ubuntu is safe from viruses, so you should only bother installing an anti-virus if you need to scan a Windows computer.

I know this sounds silly, but when you enter your password manually, are you sure that you're not accidentally hitting the enter key? Also, about pasting into the terminal: you have to use CTRL+SHIFT+V - are you doing this?

If you can't get it to work in the terminal, you can always use the graphical route (that is, double-click on the .deb, when the software centre comes up click 'install').

Yea using it cause I still have Windows.

I am doing the ctrl shift v command. the password successfully gets typed into the terminal.

And the software center wont let me install. I get this error msg: Wrong architecture '1386'

when the request for a password occurs, i hit enter so i can type. If i dont hit enter, nothing gets typed into terminal.

[sudo] password for ****: 
*******Sorry, try again.

Note: The **** are the spots where my username and password was typed out in terminal.

---

### Post by Muzic Lopez on 2011-03-14
> **antaios256 said:**
> the only thing i can think of is that the sudo password has not been set 

try  sudo passwd

then set a new sudo password

I myself have not manually set a sudo password. So that probably is the problem and according to the other post I read on, it seemed that was the problem.

I typed sudo password into the terminal but then it asked for my password again(It didnt state if it asked for my sudo or root password). but my root password was rejected as well. So I dont know how terminal expects me to make a sudo password if it asks for a sudo password.

There another method to make a sudo password?

---

### Post by wojox on 2011-03-14
[Fix Broken Sudo]("http://www.psychocats.net/ubuntu/fixsudo")

---

