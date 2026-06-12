---
title: "New User"
date: 2010-02-27
forum: General Help
---

### Post by ncdigger1 on 2010-02-27
I'm new to ubuntu. Should I install all the updates that came down?

And do I need a antivirus, or anything like that?

Thanks for your help.

---

### Post by steveneddy on 2010-02-27
Yes - update regularly.

No anti-virus is necessary.

Enjoy!

---

### Post by Arkitekt on 2010-02-27
antivirus? whats that? 

and its up to you what to install, generally sercurity updates are a good thing to install. Some people like to stay on the bleeding edge, others like to keep things where they know they work.

---

### Post by ncdigger1 on 2010-02-27
Got no sound, but I think I downloaded the right driver. AC97 for ubuntu?
But I not 100% sure.

Or how to even install it.

I have a HP Pavilion M7300e 
Athlon AMD 64 4000+
X86 32bit.

Also I have a PNY 8800GT video card.

And thanks for the quick reply.

---

### Post by Lunx on 2010-02-27
> **ncdigger1 said:**
> I'm new to ubuntu. Should I install all the updates that came down?

And do I need a antivirus, or anything like that?

Thanks for your help.

I install all updates as they become available. Being a new user, you may not be aware that you can change the location of where you download your software packages, select a mirror nearer to where you are (**System > Administration > Software Sources**), or you can change it from within Synaptic. Here in Australia, my ISP doesn't count my Linux updates/downloads against my quota (a big factor in this country, since we pay way more than what most other comparable countries offer, the words "rip" and "off" spring to mind).

And like a previous poster said, enjoy :)

---

### Post by Sef on 2010-02-27
>  And do I need a antivirus, or anything like that?

The only time you need an anti-virus is if you have an email client, so you do not infect your friends running Windows.  The virus will not infect your Linux system, but it can ride on top and go out with your emails.

---

### Post by ncdigger1 on 2010-02-27
I got my stuff installed, it was pretty easy. This seems to be an awsome o.s. I have a recovery disk set, windows xp mediacenter 2005, that came with my pc. But there was not many free programs avaible that had the features I needed.

I just got a new camera a panasonic lumix fz35, and needed a better video editor, and I saw nixipixi on youtube talking about kdenlive, and desided to just install ubuntu. :) I bet nixiepixi is loafing around here somewhere. :)

Thanks guys for the help.

---

### Post by ncdigger1 on 2010-02-27
I want to get the Slickness black theme into my Apperance, so I can install it. On youtube Nixiepixi, uses the terminal to move it from the desktop to the apperance folder/location what have you.

When I open the terminal up, it says outback@outback-desktop:~$

Nixie's does not say desktop in it. 

When I try to make it work, it says something password.

Gosh this is getting confusing.

---

### Post by JackRock on 2010-02-27
> **ncdigger1 said:**
> I want to get the Slickness black theme into my Apperance, so I can install it. On youtube Nixiepixi, uses the terminal to move it from the desktop to the apperance folder/location what have you.

When I open the terminal up, it says outback@outback-desktop:~$

Nixie's does not say desktop in it. 

When I try to make it work, it says something password.

Gosh this is getting confusing.


It's a bit of a learning curve, but if you think back to your first experience with Windows, I bet it was a similar feeling.

The "Desktop" notation is fine.  Nixi's just got a slightly different name for his than you do.

What is the EXACT (including casing) command you are typing in?

---

### Post by Red Penguin on 2010-02-27
The stuff you see when you open the terminal is 

[Username]@[Computername]:[location in file system]$

So you are Outback, logged onto Outback-desktop, and you are 'in' your home folder (~ is a shortcut for home)

When you do stuff with the terminal, you must nearly always do it with admin rights, which means you have to type a password to confirm you have those rights. Type in the password for your username and it'll do what you tell it to.

---

### Post by ncdigger1 on 2010-02-27
Nixie's was like this except it did not say desktop in the code.

outback@outback-desktop:~$ sudo cp -r $HOME/Desktop/SlicknesS-black /usr/share/themes 
outback@outback-desktop:~$ sudo chmod 755 /usr/share/themes/SlicknesS-black/Slickness-black.jpeg outback@outback:~$


It keeps saying command not found. 
I'll type a line, then hit enter to start the next line, and it says command not found.

---

### Post by Red Penguin on 2010-02-27
You should only be typing

sudo cp -r $HOME/Desktop/SlicknesS-black /usr/share/themes

and

sudo chmod 755 /usr/share/themes/SlicknesS-black/Slickness-black.jpeg

if you type 'outback@outback-desktop:~$' before 'sudo' it will return command not found.

---

### Post by ncdigger1 on 2010-02-27
Edit: it did work, but now it says it want look right becasue the required icon theme pack is not installed?

---

### Post by luftadler on 2010-02-27
> **ncdigger1 said:**
> I'm new to ubuntu. Should I install all the updates that came down?

And do I need a antivirus, or anything like that?

Thanks for your help.
You need a antiwindos application.... :)

---

### Post by ncdigger1 on 2010-02-27
> **luftadler said:**
> You need a antiwindos application.... :)

LOL, Yeah I think thats what it's called.

Anyone have an idea about the icon pack, in my post before this one?

---

