---
title: "scim on kubuntu"
date: 2006-01-26
forum: General Help
---

### Post by noeluylee on 2006-01-26
I tried installing SCIM, as per instruction press ctrl + spacebar will lunch the program., but  i didnt on my system. I tried to run it on terminal/ konsole, by type scim but it didnt run.

noel@Noel:~$ scim
Smart Common Input Method 1.0.2

Launching a SCIM daemon with Socket FrontEnd...
Launching a SCIM process with x11...
SCIM has exited abnormally.

any clue on this?

I also tried to run the SCIM input method setup on Settings, but its just trying to run the program and gone, it didnt open the actual windows or program.

If you know the fixes on this. Please help..  thanks
[B]
--- installation of scim successfull... but have problem on running it. see #4[/B]

---

### Post by GoldBuggie on 2006-01-27
While getting scim to work on all apps is possible there is still some trouble with firefox 1.5 and scim(but it works with 1.07 which is in the repositories). 

Maybe this howto will help
[http://www.ubuntuforums.org/showthread.php?t=94447](http://www.ubuntuforums.org/showthread.php?t=94447)

Getting a working perfectly working scim for dapper seems to be on the move:p[-o<

---

### Post by Psimon on 2006-01-27
If you still have trouble, try installing the Japanese version of Ubuntu which comes with scim as default. It works perfectly in absolutely everything, including Firefox 1.5 and the Kubuntu desktop once installed. The OS install is in Japanese but it's easy if you've installed Ubuntu before. Then you just have to change the default language to whatever you want. Here's the link: [http://www.ubuntulinux.jp/download/](http://www.ubuntulinux.jp/download/)

---

### Post by noeluylee on 2006-01-29
I was able to install the scim and skim using the instruction at [http://www.ubuntuforums.org/showthread.php?t=94447](http://www.ubuntuforums.org/showthread.php?t=94447) , however, when I press control + spacebar, nothing happens. but I was able to run the scim imput method setup. I tried using terminal and type scim... this is the output.

linux@linux:~$ scim
Smart Common Input Method 1.4.2

Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
Launching a SCIM process with x11...
Loading socket Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
Starting SCIM ...

--- then nothing happens..

Any clue on this?

---

### Post by noeluylee on 2006-01-31
Still cant figure out the problem. :-( any help?

---

