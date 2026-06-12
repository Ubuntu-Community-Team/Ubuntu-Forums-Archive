---
title: "Can't typed the password ---&gt; to login"
date: 2011-08-05
forum: General Help
---

### Post by iMaster on 2011-08-05
Hi, all!
I have installed linux 10.04 server and after the installation I can't login. There stands:

Ubuntu 10.04.04 LTS xNAMEx tty1

xNAMEx login: 

------> after entering there comes a new line with...

Password:

And there I can't type anything. What I must do?

Thanks!

---

### Post by haqking on 2011-08-05
> **iMaster said:**
> Hi, all!
I have installed linux 10.04 server and after the installation I can't login. There stands:

Ubuntu 10.04.04 LTS xNAMEx tty1

xNAMEx login: 

------> after entering there comes a new line with...

Password:

And there I can't type anything. What I must do?

Thanks!


just type the password and press enter, it will not echo to the screen so it will not show any characters or masks

---

### Post by Basher101 on 2011-08-05
Did you try to type it completeley, or does it simply not display the output? when i type my password in the Terminal, i cant see what im typing, but it does reveive the input. Can you confirm this? Or does it not receive the input?

---

### Post by iMaster on 2011-08-05
? - I mean,
     If I type nothing and press just enter, then it comes a new line with "Password".
     So, there I can't type anything.

---

### Post by raja.genupula on 2011-08-05
> **Basher101 said:**
> Did you try to type it completeley, or does it simply not display the output? when i type my password in the Terminal, i cant see what im typing, but it does reveive the input. Can you confirm this? Or does it not receive the input?
  i agree with  haqking .

---

### Post by haqking on 2011-08-05
> **iMaster said:**
> ? - I mean,
     If I type nothing and press just enter, then it comes a new line with "Password".
     So, there I can't type anything.


why would you type nothing when it is asking for a password ?

i am confused i think.

why are you not typing your password when it asks for one ?

---

### Post by WorMzy on 2011-08-05
Here's a short guide on how to log in:
[LIST=1]
[*]Type your username.
[*]Press enter.
[*]Type your password.
[*]Press enter.
[/LIST]

---

### Post by iMaster on 2011-08-05
I can't enter anything in this line.(Password line)

 If I type in the "xNAME<  login"-line it comes the password line. So, if I press enter it jumps in  the next line(it's emty). 5 Seconds later it comes the same.

---

### Post by haqking on 2011-08-05
> **iMaster said:**
> I can't enter anything in this line.(Password line)

 If I type in the "xNAME<  login"-line it comes the password line. So, if I press enter it jumps in  the next line(it's emty). 5 Seconds later it comes the same.

so it asks for password ?

type your password (it wont show anything on the screen, the cursor wont move and nothing you type will be shown)

soif passowrd is bob then at password prompt type "bob" then press enter, but bob or *** wont be shown, nothing will move. then press enter.

or are we not understanding you ? you mean when you enter your password it still jumps to password prompt again ?

---

### Post by iMaster on 2011-08-05
Maybe you understand me not....

First there is a line. It looks so.
xNAMEx login:_

So, if I type my name or username there coms a new line. It looks so.
Password:_

The cursor there doesn't move, if I press a key.
So, I can't type my password there. If I press enter, it comes a new line (it's empty).
~ 5 Seconds later, the same comes there. But now there stands at the first....

Login incorrect

---

### Post by zealibib slaughter on 2011-08-05
At the password prompt the cursor does not move just type in your password.  Nothing will be displayed but it will take your password.

---

### Post by fdrake on 2011-08-05
look at this vid at 1:00 and you'll se that when he enters the password the cursor does not move

[http://www.youtube.com/watch?v=vpXrimawCOQ](http://www.youtube.com/watch?v=vpXrimawCOQ)

---

### Post by iMaster on 2011-08-05
Hmm, ok I try it.

No. It says "Login incorrect"
What I must enter by xNAMEx login: ?

---

### Post by zealibib slaughter on 2011-08-05
Your user name.

---

### Post by iMaster on 2011-08-05
Done, but it doesn't login

---

### Post by zealibib slaughter on 2011-08-05
just wondering but why are you trying to log into tty1 instead of using a terminal in the GUI? 
 
NEVERMIND ignore the above, just went back and seen that it is SERVER.
 
Make sure you are using the right username and you type everything in the right case.

---

### Post by iMaster on 2011-08-05
I don't know this. I'm a beginner in linux

---

### Post by haqking on 2011-08-05
> **iMaster said:**
> Maybe you understand me not....

First there is a line. It looks so.
xNAMEx login:_

So, if I type my name or username there coms a new line. It looks so.
Password:_

The cursor there doesn't move, if I press a key.
So, I can't type my password there. If I press enter, it comes a new line (it's empty).
~ 5 Seconds later, the same comes there. But now there stands at the first....

Login incorrect

like i said in my first post and thereafter, it wont show you anything the cursor will not move.

at login type in your username for logging in.
at password type the password associated with that username (nothing will show on the screen.

if it says incorrect login or bad password then you typed wrong credentials

---

### Post by haqking on 2011-08-05
> **iMaster said:**
> I don't know this. I'm a beginner in linux


do you know your username ?

is it your computer ?

did you install it ?

use your username supplied and password supplied during install.

THE PASSWORD PROMPT WILL NOT SHOW ANYTHING WHEN YOU TYPE IT !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by fdrake on 2011-08-05
> **zealibib slaughter said:**
> just wondering but why are you trying to log into tty1 instead of using a terminal in the GUI?

```
linux 10.04 server
```
i think his server install does not have a guy.


maybe you need to change the user's password (since it looks like you forgot it)

see link on how to change your pass
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by iMaster on 2011-08-05
End---

I reinstall linux. I hope, it will work. 

Thank you, to all!

---

### Post by zealibib slaughter on 2011-08-05
> **fdrake said:**
> ```
linux 10.04 server
```
i think his server install does not have a guy.
 
 
maybe you need to change the user's password (since it looks like you forgot it)
 
see link on how to change your pass
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
 
Yeah after I posted this I went back and seen its a server setup.  My bad.

---

### Post by haqking on 2011-08-05
> **iMaster said:**
> End---

I reinstall linux. I hope, it will work. 

Thank you, to all!


if you reinstall it will still be the same, it wont show you a password at the prompt as you type it.

a link was provided above to allow you to change it if you have forgotten it.

If you are not understanding the prompt wont show you feedback then you will have same situation when you re-install.

chane your password if you cant remember it using the link and save yourself time

---

### Post by iMaster on 2011-08-05
It works. Thanks!

---

### Post by Basher101 on 2011-08-05
Please mark your thread as [SOLVED] if you got all your questions answered :idea:

---

### Post by iMaster on 2011-08-05
Oh...I have one question.
How i start the desktop?

---

### Post by fdrake on 2011-08-05
> **iMaster said:**
> Oh...I have one question.
How i start the desktop?

:confused::confused:alright.......hmmmm.. ithink we have a problem here.....
how can i put this.......  You just installed a server edition.... therefore  ..... there is **_NO DESKTOP_** just a shy command line :(
--------------------------------------------------------------------------
jokes aside you can install gnome and the gui follwing the commands from this link
[http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html](http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html)

---

### Post by zealibib slaughter on 2011-08-05
on a server there is no desktop by default.  But you can install a desktop by typing
```
sudo apt-get install ubuntu-desktop
```
follow the how to here for more help: [http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html](http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html)

---

### Post by iMaster on 2011-08-05
You're really friendly to a linux beginner <.<"

---

### Post by haqking on 2011-08-05
> **iMaster said:**
> You're really friendly to a linux beginner <.<"


no problem.

though i am wandering if you actually want the server edition ?

are you running it as a server and providing server services on a network ?

as oppose to the desktop edition

---

### Post by iMaster on 2011-08-05
I would run a server. I used Windows for that, but it doesn't work. So I take linux. I use XAMPP and Pythoon and MySql...^^

---

### Post by haqking on 2011-08-05
> **iMaster said:**
> I would run a server. I used Windows for that, but it doesn't work. So I take linux. I use XAMPP and Pythoon and MySql...^^


ok well you might want to have a good read here

[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

it is 8.04 but most of it is applicable.

Seeing as you had problems simply logging in then a good bit of research might be worth it before you setup your LAMP etc.

best of luck

---

### Post by RonCam on 2012-08-07
Preface:  this is obviously not for the original poster, but for those who come across this thread through a search, looking for a solution.  Second, my compliments to the members here for their considerate tone in helping a newbie!

There is yet another reason the no one has mentioned, why *iMaster* could have been typing his correct password but still repeatedly refused entry: at least on my setup, *there is no keyboard debounce active at this prompt.*

Since you are typing blind, you will never know if you are typing a corrupted password.  So, go back to being a one-finger typist and hit each key quickly and sharply, with one finger.  

It worked for me ... after months of wondering why my correct username and password wouldn't work.  It's better to try this, instead of reinstalling the OS ...

---

