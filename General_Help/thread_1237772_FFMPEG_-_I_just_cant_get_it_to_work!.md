---
title: "FFMPEG - I just cant get it to work!"
date: 2009-08-11
forum: General Help
---

### Post by hollyswanson on 2009-08-11
For those of you that want to know how to install fmpeg/mencoder ect the easy way, check my site.
**[http://www.hollyswanson.com/installing-ffmpeg-the-easy-way-ubuntu-8-10-or-higher/](http://www.hollyswanson.com/installing-ffmpeg-the-easy-way-ubuntu-8-10-or-higher/)**

**I will help where i can and so will others!!!**

-------------------------------------------------------------------------------------
ok this is my problem, I need my website to process user videos.
However,No matter what i do i just cannot use FFMPEG.

I can get as far as installing FFMPEG by using apt-get install ffmpeg, that works fine,then i install the other codecs ect.then when i do a whereis ffmpeg, it tells me where its installed to.but none of the scripts that i have tried are working.

i have come here in the hope that someone to help me through it all step by step.I have tried virtually every single thread online even the one linked here.

So what i have done now is reinstall my server.
**Its now running ubuntu 8.10 intrepid...**

Intel core 2 duo 2.0GHZ 
4GIG RAM
2 x 250GB SATA IIs

Please Please Please help me,its a fresh install, I cant go sleep until this is installed.

**Holly Swanson**
:confused::confused::confused::confused::confused:

---

### Post by Johnny B on 2009-08-11
can you post error messages please?
and also, what scripts are you using?

---

### Post by hollyswanson on 2009-08-11
> **Johnny B said:**
> can you post error messages please?
and also, what scripts are you using?

I cant post errors messages now because i have reinstalled the server.
I have just added the repo lists found here **[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)**  and just waiting for some to help me now  :-)

i tried phpmotion,vidiscript and a few others.My friend even tried his clipshare script quickly then yook it off and that didnt work.he has shared hosting and it works on his.

Any ideas.My Server is now blank so my site is down and its a fresh install.

Just awaiting commands  :-)

---

### Post by credobyte on 2009-08-11
You can't use ffmpeg without installing appropriate* plugins* ..
```
sudo apt-get install php5-ffmpeg && sudo /etc/init.d/apache2 restart

```

---

### Post by hollyswanson on 2009-08-11
> **credobyte said:**
> You can't use ffmpeg without installing appropriate* plugins* ..
```
sudo apt-get install php5-ffmpeg && sudo /etc/init.d/apache2 restart

```


tried all that before.Still couldn't get it to work with any of the scripts.

another thing,I think my server comes with minimal install,so i did a repo update,then sudo apt-get update, it went through the process. Now when i want to install something or compile something i get lots of errors about dependencies such a GCC ect.

I havnt used ubuntu for a while now because i have been so busy but i know there was a command that enabled me to install all dependencies and build tools.it came to around 255MB or something like that.???

any idea?

---

### Post by hollyswanson on 2009-08-11
these are the kind of errors i am getting?
[IMG]http://hollyswanson.com/error001.jpg[/IMG]

---

### Post by credobyte on 2009-08-11
Dev tools ( compilers, libraries .. ):
```
sudo apt-get install build-essential
```

---

### Post by hollyswanson on 2009-08-11
> **credobyte said:**
> Dev tools ( compilers, libraries .. ):
```
sudo apt-get install build-essential
```

yay thats the one!!!
Lemme do that now.

---

### Post by hollyswanson on 2009-08-11
i know get this

[IMG]http://www.hollyswanson.com/error002.jpg[/IMG]

---

### Post by hollyswanson on 2009-08-11
ok i fixed my abouve problem by 
sudo aptitude install g++

EDIT:  Now i was able to 
sudo apt-get install build-essential

---

### Post by hollyswanson on 2009-08-11
ok i think i have got it, just rebooting now  =)

---

### Post by hollyswanson on 2009-08-11
Nope,still not working. I Fail.

I put a phpinfo file in the root of0 my site.its [www.hollyswanson.com](www.hollyswanson.com) 

please read and see where i am going wrong!

Please reply if you can, i cant go sleep until i know this is working its soooo important!!!

its 2AM here in the uk london time  :-(
13 coffees later and i still fail   =(

---

### Post by hollyswanson on 2009-08-11
ill do anything you guys tell me to do so i can get this server to process videos and thumbnails automatically!

plzzzz help me  :frown:

---

### Post by hollyswanson on 2009-08-11
gonna install the gnome GUI and see if i can do stuff from there because this is getting me nowhere  =/

---

### Post by hollyswanson on 2009-08-11
ok well that was a fail, reinstalling ubuntu 8.10 again

is there anyone on this forum that knows anything about ubuntu that can help me at all???

Holly

---

### Post by credobyte on 2009-08-11
> **hollyswanson said:**
> ok well that was a fail, reinstalling ubuntu 8.10 again

is there anyone on this forum that knows anything about ubuntu that can help me at all???

Holly

Answer to all these questions and you might get some help ..


[LIST=1]
[*]How did you installed ffmpeg ?
[*]How are you trying to use it ( PHP, bash, etc. ) ?
[*]What exactly does not work ( any errors ? ) ?
[/LIST]

---

