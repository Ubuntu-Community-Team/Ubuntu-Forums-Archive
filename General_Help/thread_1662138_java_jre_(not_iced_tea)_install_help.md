---
title: "java jre (not iced tea) install help"
date: 2011-01-07
forum: General Help
---

### Post by dbowlin17 on 2011-01-07
I am trying to install the full java, not the open java, because iced tea keeps crashing. i followed [http://ubuntuforums.org/showthread.php?t=774956]("http://ubuntuforums.org/showthread.php?t=774956") and went to the java website, downloaded the jre and followed the instructions it gave to install, but i am not sure if i am done or if there is more to do. i know the game im trying to play thats java still isn't running...

---

### Post by 23dornot23d on 2011-01-07
Do you run the game from a Terminal window  ..... are there any error messages that you can post 

Is the game online .... do you have a link to it ....... we could check it out to see if the same problems occur ..... on our systems .........

---

### Post by dbowlin17 on 2011-01-07
[http://www.runescape.com/game.ws?j=1](http://www.runescape.com/game.ws?j=1)

it says  "missing plug-in" i think i got rid of iced tea...

---

### Post by 23dornot23d on 2011-01-07
Quick reply to that is ..... its not running here neither ...... 

but I have a few systems and there is a later jre to load up .... which I am just in the
process of installing to see if that works .....

give me a few minutes ..... will see if I can get it working ......

Got as far as logging in after downloading and installing it .....

Ok it hangs when it tries to load the game up from download .....

[http://img689.imageshack.us/img689/1723/screenshot6yu.png](http://img689.imageshack.us/img689/1723/screenshot6yu.png)

will see if I can run it from a terminal window to see why its hanging ........

---

### Post by dbowlin17 on 2011-01-07
did it crash on you then? thats the problem i was having when i tried using the iced tea. not sure if it makes a difference, i am using google chrome.

---

### Post by 23dornot23d on 2011-01-07
Ok I have used Firefox 3.6.13  ..... and the download ....... msi ...... file ...... neither work yet ..... but I do not give up easily ..... will try a few more things .....am always a little wary of free games ..... do you know if it does run in windows ok ?

---

### Post by ajgreeny on 2011-01-07
I always install sun-java apps instead of the open source versions as in many cases they work better.  if you enable the partner repos in your /etc/apt/sources.list file (use System ->Administration ->Software Sources to do it) you can install sun-java* packages with the normal package manager.

---

### Post by dbowlin17 on 2011-01-07
i have actually used it in 32bit ubuntu 10.10 in google chrome without a problem. but i built a new computer today, and in building it, took the old one out of service. and since i have 8gb of ram, i ended up installing 64 bit.

---

### Post by wojox on 2011-01-07
This has always helped me [Oracle (Sun) Java JRE]("http://sites.google.com/site/easylinuxtipsproject/java")

---

### Post by dbowlin17 on 2011-01-07
I followed everything in the link wojox, and there were no error messages. however, i did not install the firefox plugin, because i am not using firefox. i use chrome.

---

### Post by 23dornot23d on 2011-01-07
I now have it running using the partner repository ...... 

but I am running 32 bit ..... 
and using the
Sun-java from the partner repository ...... and Firefox 3.6.13

and its running ok no crashes

[http://img709.imageshack.us/img709/3475/screenshot13rj.png](http://img709.imageshack.us/img709/3475/screenshot13rj.png)

so you will now need someone running 64 bit to confirm it will work ok in that ......
but everything is fine in firefox 3.6.13 .... using the Sun-java .... been playing to the point of killing
the dragon in the training section. (sound and movements are ok too ...)

[IMG]http://img46.imageshack.us/img46/3633/forweb1.jpg[/IMG]

---

### Post by dbowlin17 on 2011-01-07
I GOT IT WORKING. using the link provided by wojox, and setting up the firefox plugin and it now works no crashes in chrome! thanks again everyone. one thing i love about ubuntu is the incredible community support, thank you!!!!!!!!

---

### Post by 23dornot23d on 2011-01-07
Good one ..... mark as solved .... great work everyone .... 

I like it here too .... best Forum to be on ..... ;)

---

### Post by dbowlin17 on 2011-01-07
heh, i still don't know how to mark solved... help?

---

### Post by 23dornot23d on 2011-01-07
Thread tools - in red ... 

Near to the top of this page ..... third one in from the right hand side of the page.

There is a drop down menu ..... bottom option is .... thread solved

---

