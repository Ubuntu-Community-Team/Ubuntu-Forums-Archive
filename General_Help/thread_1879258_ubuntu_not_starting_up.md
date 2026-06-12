---
title: "ubuntu not starting up"
date: 2011-11-11
forum: General Help
---

### Post by shealtiel on 2011-11-11
I am a complete newbie. About a week ago I installed ubuntu as an alternative alongside Windows XP Pro. I thought I was beginning to get to grips with it but since yesterday I haven't been able to get it to load. Instead get this message:
 
**GNU GRUB version 1.99-12ubuntu5**
**Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.**
 
**grub>**
 
All of which is complete gobbledy-gook to me. I am tempted to try reinstalling but thought I'd ask first what it means.

---

### Post by Rubi1200 on 2011-11-11
> **shealtiel said:**
> I am a complete newbie. About a week ago I installed ubuntu as an alternative alongside Windows XP Pro. I thought I was beginning to get to grips with it but since yesterday I haven't been able to get it to load. Instead get this message:
 
**GNU GRUB version 1.99-12ubuntu5**
**Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.**
 
**grub>**
 
All of which is complete gobbledy-gook to me. I am tempted to try reinstalling but thought I'd ask first what it means.
Hi and welcome to the forums :)

To help us diagnose the problem, please post the results of the boot info script.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by shealtiel on 2011-11-12
> **Rubi1200 said:**
> Hi and welcome to the forums :)

To help us diagnose the problem, please post the results of the boot info script.

There is a link at the bottom of my post with instructions.

Thanks.
That's no help at all - like telling me to enter a locked room where the key is on the inside of the door. The whole point is, the message I quoted is what I see as soon as I click **ubuntu** in the startup menu and I can't get any further than that, i.e., I can't boot into Linux so I'm not able to download and run the *boot info script*.

I don't understand most of the other stuff and all I can say that may be of some help is that I did use *wubi* when I did the install.

By the way it looks as though my question has been hijacked.

---

### Post by drs305 on 2011-11-12
> **shealtiel said:**
> That's no help at all - like telling me to enter a locked room where the key is on the inside of the door. The whole point is, the message I quoted is what I see as soon as I click **ubuntu** in the startup menu and I can't get any further than that, i.e., I can't boot into Linux so I'm not able to download and run the *boot info script*.

I don't understand most of the other stuff and all I can say that may be of some help is that I did use *wubi* when I did the install.

By the way it looks as though my question has been hijacked.

The boot info script can be run from the LiveCD. Until we got more information our ability to help you is really limited to guessing. Being told you are running a wubi installation is something we would have learned from the boot info script, and trying to give advice without knowing that piece of information would not have been productive.

Being at a 'grub' prompt, vs a 'grub rescue' prompt, most likely means that Grub is having problems with your Grub menu file. Either it can't find it or can't use it for some reason.

*Rubi1200* does a lot of great work troubleshooting Wubi problems. He has a Wubi megathread which may be helpful if you don't want to wait for answers:
[http://ubuntuforums.org/showthread.php?t=1639198]("http://ubuntuforums.org/showthread.php?t=1639198")

As far as the hijacking issue, *Mathivh* is new to our forums and has been advised. Since he had already posted, a solution was given. No more support will be provided for his issue within your thread.

---

### Post by Rubi1200 on 2011-11-12
Here is the download link with instructions to create and use a LiveCD:
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

As drs305 already pointed out, we need this essential piece of information that the boot script will hopefully provide so we can assist you further.

Thanks.

---

### Post by bcbc on 2011-11-12
> **shealtiel said:**
> That's no help at all - like telling me to enter a locked room where the key is on the inside of the door. The whole point is, the message I quoted is what I see as soon as I click **ubuntu** in the startup menu and I can't get any further than that, i.e., I can't boot into Linux so I'm not able to download and run the *boot info script*.

I don't understand most of the other stuff and all I can say that may be of some help is that I did use *wubi* when I did the install.

By the way it looks as though my question has been hijacked.
This is usually the cause: [http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html)

---

### Post by shealtiel on 2011-11-17
> **Rubi1200 said:**
> Here is the download link with instructions to create and use a LiveCD:
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

As drs305 already pointed out, we need this essential piece of information that the boot script will hopefully provide so we can assist you further.

Thanks.
Thanks for your help. I did the download but unfortunately, for reasons not connected with ubuntu I was unable to burn a disk so I ended up with a complete removal and re-installation and everything is working OK now.

---

### Post by nothingspecial on 2011-11-17
A new thread would be better because this thread title won't give any indication of your new question.

---

### Post by shealtiel on 2011-11-17
Thanks for nothing special ;) I figured that out and you must have been answering just at the time I edited the question out. 

I've since found out about Wine :p

---

