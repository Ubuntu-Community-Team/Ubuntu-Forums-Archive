---
title: "General Linux Commands (suggestions)"
date: 2009-11-04
forum: General Help
---

### Post by Xog on 2009-11-04
Hi all. I played around with ubuntu last year and had some fun with it. I had it dual booted with Windows XP Media Center Edition on my laptop, and eventually wound up corrupting the Ubuntu boot, so I uninstalled it after about 2 or 3 months. I liked it but I was too used to WinXP.

So, now that 9.10 is out, and Lynx on the way, I decided to install KK. Had a couple problems (had to download twice, and wasted 4 disks to burn it correctly without any corrupted files). It was a complete clean install, bye bye WinXP. I got it to install completely and it's 100% clean. Nothing bad to report as of yet (except video card, but I just saw a thread to fix that, i'll do that when I get home).

I never really got the hang of the terminal lingo, so if it's possible, I'd like some advice on how to get used to all of this jazz. Like for instance, sudo. If/when I have a problem, I'm told to run a command. Lots of times, I'm told to use "sudo xx xx xx xx etc" and as that's all nice and dandy, what is "sudo" ? what does it mean?

These are the things I'd like to know. I know there's guides out there and what not, but I'm not looking for an extensive list. There's got to be a way to LEARN the commands, learning WHY this command is needed, instead of just reading them online.

sudo is just one example. So is it possible someone can give me a SMALL crash course on the GENERAL commands and grammar and what they do?

like, say I want to shut down the computer using the terminal, i'd use

shutdown -h now

Okay, I get "shutdown" but what does "-h" mean? Home? Why is there an "-" before it? What does that mean? Just simple stuff like this.

Thanks! :)

---

### Post by howefield on 2009-11-04
Go to youtube and search for linux terminal commands, you'll get loads of hits, watching a video might be more entertaining for you and less dry than reading online.

---

### Post by phillw on 2009-11-04
> **Xog said:**
> Hi all. I played around with ubuntu last year and had some fun with it. I had it dual booted with Windows XP Media Center Edition on my laptop, and eventually wound up corrupting the Ubuntu boot, so I uninstalled it after about 2 or 3 months. I liked it but I was too used to WinXP.

So, now that 9.10 is out, and Lynx on the way, I decided to install KK. Had a couple problems (had to download twice, and wasted 4 disks to burn it correctly without any corrupted files). It was a complete clean install, bye bye WinXP. I got it to install completely and it's 100% clean. Nothing bad to report as of yet (except video card, but I just saw a thread to fix that, i'll do that when I get home).

I never really got the hang of the terminal lingo, so if it's possible, I'd like some advice on how to get used to all of this jazz. Like for instance, sudo. If/when I have a problem, I'm told to run a command. Lots of times, I'm told to use "sudo xx xx xx xx etc" and as that's all nice and dandy, what is "sudo" ? what does it mean?

These are the things I'd like to know. I know there's guides out there and what not, but I'm not looking for an extensive list. There's got to be a way to LEARN the commands, learning WHY this command is needed, instead of just reading them online.

sudo is just one example. So is it possible someone can give me a SMALL crash course on the GENERAL commands and grammar and what they do?

like, say I want to shut down the computer using the terminal, i'd use

shutdown -h now

Okay, I get "shutdown" but what does "-h" mean? Home? Why is there an "-" before it? What does that mean? Just simple stuff like this.

Thanks! :)


hi, if you follow my info link - it'll take you to a sticky called resources under linux (ubuntu) ... plenty there to help you :p

Regards,

Phill.

---

### Post by DeMus on 2009-11-04
Just have a look here and study hard:
[_Learning the Shell_]("http://www.linuxcommand.org/learning_the_shell.php")

It will give you a lot of info about the commands and the way how to use them.
Have fun.

---

### Post by Xog on 2009-11-04
> **DeMus said:**
> Just have a look here and study hard:
[_Learning the Shell_]("http://www.linuxcommand.org/learning_the_shell.php")

It will give you a lot of info about the commands and the way how to use them.
Have fun.

That list looks promising! I'll study when I get home from work. That's the type of list I was looking for.

What I wasn't looking for (as an example I'm going to give a WINE howto link: [http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ)

If you notice, it's extremely complicated to "study" and is more useful for 1-time use, like a "how do I uninstall wine" google search would come up with this list, and with a simple click you're able to learn how. But to study that is just too complicated!

Thanks for the link :)

---

### Post by jnew93 on 2009-11-04
Quick response to your post question about sudo. It stands for "**S**uper **U**ser **DO**", and what it basically does is run the command with root privileges, so that you do not get permissions errors when you try to modify system policy, change system files, install packages, add repositories, etc, etc...

Hope that helped a little! :D

---

