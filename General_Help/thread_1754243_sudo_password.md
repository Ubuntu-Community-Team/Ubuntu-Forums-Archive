---
title: "sudo password"
date: 2011-05-09
forum: General Help
---

### Post by bobbytre on 2011-05-09
Hello all, I'm a totally new Linxu/Ubuntu user and terrified of command prompt/terminal.  But I'm trying to get my Keebox W150nu to work with 11.04 and following Chili's suggestion on doing so, but ran into an early problem:

robert@lawsonbox:~$ ndiswrapper -1
The program 'ndiswrapper' is currently not installed. You can install it by typing:
sudo apt-get install ndiswrapper-common
robert@lawsonbox:~$ "sudo apt-get install ndiswrapper-common"
[sudo] password for robert:

at that last line I am STUMPED.  I can't input anything, no matter what key I press nothing is showing up there.  If I knew the password I wouldn't be able to put it in!  Do I hit an F key or what at this stage?

---

### Post by ivanovnegro on 2011-05-09
Normally you have set a root password at the install process, did you?
You have to type this password, but you cannot see it, that is normal, just type it in and hit enter.

---

### Post by bobbytre on 2011-05-09
I don't recall ever setting a root password.  Would that be the same as my login password?  If so, I've tried entering that and the cursor is not moving.

---

### Post by ivanovnegro on 2011-05-09
I think so, my sudo password is also my user password, just type this password after the command when required and hit enter, thats all. What happens when you hit enter?

---

### Post by bobbytre on 2011-05-09
Haven't tried hitting 'enter' since I don't see the cursor moving when I type... but will try and let you know how I come out.

---

### Post by ivanovnegro on 2011-05-09
Thats normal, you cannot see nothing if typing the sudo password, just type it in.

---

### Post by deconstrained on 2011-05-10
Unless you explicitly configure PAM to print asterices for each key you press in a TTY, it won't show any trace of your password as you type it in. Most GNU-Linux/Unix systems are set up in this way by default.

---

### Post by kukker32 on 2011-05-10
the line recognises your typing it just dosn't show up but try put in lkike normal and hit enter..

---

### Post by bodhi.zazen on 2011-05-10
*Thread moved to **General Help**.*

---

### Post by WorMzy on 2011-05-10
Like everyone has said, just type in your password when prompted. The lack of a visible "password" character (e.g. ******) is normal, and is a security feature.

Regarding the command you were trying to run:

> **bobbytre said:**
> robert@lawsonbox:~$ ndiswrapper -1

I believe that should be a lower case L at the end there, and not a number "1".

---

### Post by Spyderkid on 2011-05-10
I don't know how many times i've said this...

Its a security feature so the guy behind you or a hacker can't see what it is. just type and press enter.

and for Ubuntu 11.10 i think they should put astericks after each letter.

---

### Post by oldos2er on 2011-05-10
> **Spyderkid said:**
> I don't know how many times i've said this...

Its a security feature so the guy behind you or a hacker can't see what it is. just type and press enter.
  

Actually it's not, it's a bug that'll never be fixed: [http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal) , follow the link there to the bug report.

---

### Post by WorMzy on 2011-05-10
It's not a bug, although I agree that it's inconsistent with the GUI (or rather, the GUI is inconsistent with the terminal).

Like I posted in Spyderkid's own thread regarding this subject, you can enable feedback if you desire; just enable the pwfeedback option in visudo.

---

