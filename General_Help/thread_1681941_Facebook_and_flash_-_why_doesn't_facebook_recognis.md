---
title: "Facebook and flash - why doesn't facebook recognise that I have flash installed?"
date: 2011-02-05
forum: General Help
---

### Post by mannyweb.ca on 2011-02-05
[IMG]http://i.imgur.com/518dy.png[/IMG]

The above is what I get everytime I try to upload multiple pictures to facebook.  Now I've tried everything I've looked all over the internet and infact all I found was somebody else with the same issue:

 [http://askubuntu.com/questions/16732/facebook-and-flash-why-doesnt-facebook-recognise-that-i-have-flash-installed](http://askubuntu.com/questions/16732/facebook-and-flash-why-doesnt-facebook-recognise-that-i-have-flash-installed)

but no solution. 

Is there anything I can do?  

I have Ubuntu 10.04 64bit and yes flash is installed and so is java.

Thanks.

---

### Post by dollzii on 2011-02-05
What browser are you using?

---

### Post by mannyweb.ca on 2011-02-05
Firefox version 3.6.13
Chrome version 9.0.597.84
Opera version 11.01

---

### Post by dcstar on 2011-02-05
> **mannyweb.ca said:**
> 
.........
I have Ubuntu 10.04 64bit and yes flash is installed and so is java.

Thanks.

Try installing the 64-bit version of Flash.

---

### Post by mannyweb.ca on 2011-02-05
^ Already installed no dice.  :(

---

### Post by steveneddy on 2011-02-05
Just use the Simple Uploader like the rest of us do and get past it.

Some things while using Linux are not going to work as intended because we live in a Windows world. We are the odd balls here and we just need to find the easiest way to accomplish our tasks, even if it means using a not so flashy and graphically attractive alternative that works just as well.

---

### Post by mannyweb.ca on 2011-02-05
> **steveneddy said:**
> Just use the Simple Uploader like the rest of us do and get past it.



For 200 Photos!  You scary dude!  Lol!

But seriously are you saying that every Ubuntu user has this issue?

---

### Post by steveneddy on 2011-02-08
> **mannyweb.ca said:**
> For 200 Photos!  You scary dude!  Lol!

But seriously are you saying that every Ubuntu user has this issue?

Sorry - poor choice of words on my part.

200 photos? What the...?

AFAIK if you use Linux, this is the case.

You could try Firefox with User Agent Switcher to see if that works.

Just a thought.

---

### Post by djeikyb on 2011-02-08
Go to [http://whatismyflash.com](http://whatismyflash.com). Does that website correctly report your flash install?

---

### Post by Frogs Hair on 2011-02-08
I updated my Win 7 flash players today , so there may be an update coming . I usually get my Ubuntu update first and that is my signal to update Win7 , but not this time.

---

### Post by mannyweb.ca on 2011-02-08
> **djeikyb said:**
> Go to [http://whatismyflash.com](http://whatismyflash.com). Does that website correctly report your flash install?

All good version 
**10.3.0**

---

### Post by djeikyb on 2011-02-09
I've had some success with the normal uploader. I'm on 10.04 32 bit Firefox/Chromium. Often I have to make my selection two or three times, but eventually it will work.

Manny, I don't know why it isn't working for you, but I know 64 bit linux and flash traditionally don't get along.

---

### Post by Frogs Hair on 2011-02-09
Received flash update this morning via update manager.

---

### Post by goldencako on 2011-02-14
The same happened to me. This is what I've done to solve it:

First, remove the 64-bit player you installed manually. I had installed it copying to /usr/lib/firefox-3.6.13/plugins/. So to uninstall it, I deleted that file.

Then I downgraded flashplugin-installer from version 10.2.152.27ubuntu0.10.10.1 to version 10.1.85.3ubuntu1 by forcing the version on Synaptic.

---

### Post by mannyweb.ca on 2011-03-06
> **goldencako said:**
> The same happened to me. This is what I've done to solve it:

First, remove the 64-bit player you installed manually. I had installed it copying to /usr/lib/firefox-3.6.13/plugins/. So to uninstall it, I deleted that file.

Then I downgraded flashplugin-installer from version 10.2.152.27ubuntu0.10.10.1 to version 10.1.85.3ubuntu1 by forcing the version on Synaptic.

Thank you so much not only did this work, but it also fixed that ******** issue occuring with Youtube lately.

Thanks again.:)

---

