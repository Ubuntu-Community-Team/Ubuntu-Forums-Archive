---
title: "SSH Password"
date: 2011-07-22
forum: General Help
---

### Post by PinguyOS on 2011-07-22
Hello
I am using ubuntu 10.10. I want to use SSH to connect to a server that has open-suse.
I know the server's ip. I used angry ip scanner for ubuntu to scan the ip. It said that it is alive. I right-clicked it from the list and i chosed open SSH. A terminal windows blew up and prompted me for password.
What password should i enter? Is it the login password?
I apreciate your help

---

### Post by e79 on 2011-07-22
It should be the password of the user you are trying to connect with (root or else).

---

### Post by kaspar_silas on 2011-07-22
yes it's the login password. However by default it uses the username you are currently on as (I think). If that does not match your login on the other computer open a terminal and type:

$ ssh [username]@[ip]

for example to connect as bob to 192.168.1.23

$ ssh bob@192.168.1.23

then when prompted enter bob's password.

---

### Post by haqking on 2011-07-22
> **PinguyOS said:**
> Hello
I am using ubuntu 10.10. I want to use SSH to connect to a server that has open-suse.
I know the server's ip. I used angry ip scanner for ubuntu to scan the ip. It said that it is alive. I right-clicked it from the list and i chosed open SSH. A terminal windows blew up and prompted me for password.
What password should i enter? Is it the login password?
I apreciate your help


well you are trying to login, it is asking for a password, so the login password would be a good assumption ;-)

whatever account is setup for you to login with is the one you use

---

### Post by PinguyOS on 2011-07-22
Thank you very much!
My new problem is that i don't know any username of password for the server i want to connect.

---

### Post by haqking on 2011-07-22
> **PinguyOS said:**
> Thank you very much!
My new problem is that i don't know any username of password for the server i want to connect.


LOL then ask the admin, it appears you are trying to connect to something you are not authorised to connect to.

if you are not authorised then guess what...

---

### Post by PinguyOS on 2011-07-22
I can't ask the admin. Is there any way to bypass the password?
It doesn't let me to try passwords more than 5 times, so brute-force will not work.

---

### Post by e79 on 2011-07-22
> **PinguyOS said:**
> I can't ask the admin. Is there any way to bypass the password?
It doesn't let me to try passwords more than 5 times, so brute-force will not work.

:confused: Why do you want to connect to a server that you don't have the password :confused:

And no, connecting through SSH without a password is not feasible. By mentionning brute-force and stating that you 'cannot' ask the admin, are you plainly telling us that you are trying to hack that server or try to get access while you are not intitle of..? Because it do sounds like it... imho this thread should be closed.

---

### Post by PinguyOS on 2011-07-22
Yes i need to get access to that server. I know the person that owns the server but i can't ask it for password. What should i use to get access to the server without password. Ithought that ssh is the best way.

---

### Post by haqking on 2011-07-22
> **PinguyOS said:**
> I can't ask the admin. Is there any way to bypass the password?
It doesn't let me to try passwords more than 5 times, so brute-force will not work.


await the thread to be closed ;-)

---

### Post by haqking on 2011-07-22
> **PinguyOS said:**
> Yes i need to get access to that server. I know the person that owns the server but i can't ask it for password. What should i use to get access to the server if not SSH.

you wont get any informed responses here.

This forum does not support circumventing security mechanisms without authority or condone cracking or script kiddie activity in any ways.

I am not a forum admin but im pretty sure you shouldnt be asking such questions ;-)

---

### Post by e79 on 2011-07-22
> **PinguyOS said:**
> Yes i need to get access to that server. I know the person that owns the server but i can't ask it for password. What should i use to get access to the server without password. Ithought that ssh is the best way.

LOL....just plain old LOL.... lets count to see how much time this thread will stay alive....

1....

---

### Post by uRock on 2011-07-22
If your aren't the admin, then you have to contact the admin. UF is not here to assist with illegal activities.

Thread Closed.

---

