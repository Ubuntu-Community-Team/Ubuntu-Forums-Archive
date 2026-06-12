---
title: "Cant you turn off passord thing??"
date: 2011-11-29
forum: General Help
---

### Post by tears of the river on 2011-11-29
I'm relatively new to Ubuntu only had it for about 3 days and before this i had windows xp any way One thing i find incredibly annoying is that it keeps asking the password for every little thing. Isn't there anyway to stop it from doing that???

---

### Post by hansdown on 2011-11-29
Welcome to ubuntu, tears of the river.

We're not allowed to give that info.

Trust me, your system is more secure, with the password system.

---

### Post by fdrake on 2011-11-29
tears of rever if your computer is fully functional there is not need for you to change these setting unless you are configuring you system. If you don't want keeping reinstall your system because of fatal mistakes everyweek i suggest you to leave the current setting and learn more about it.

---

### Post by fbelzile on 2011-11-29
Yes, you can. In the Linux world, everything is configurable, usually by editing files.
What you want to do though is highly discouraged. Let me explain why:

1) You will automatically grant root privileges (the same as an Administrator account on Windows) to any program that requests it, without even knowing. This is a risky move.
2) Important/critical system files can easily be changed by you. Not that I mean that in a bad way. But being the humans we are, accidents happen. Accidents can go as far as deleting some kernel modules, etc...
3) You will probably forget that you have done this (from not seeing any pop-ups to remind you). This leaving your system horribly vulnerable.
4) Since your a new user, this might be an inconvenience to you compared to Windows, but guess what? Your system is that much more secure. It should make you feel good, warm and comfy :)
5) Once you finish setting up your Ubunutu the way you like it, you won't have to do as many configuration changes, so you will see those pop-ups less and less.


If you want to go ahead anyways, here is how you do it:

1) Start a Terminal window
2) Run the command: sudo gedit /etc/sudoers
3) Type your password (see how secure this is :P)
4) A configuration file should come up.
5) Find the line that says:
%admin ALL=(ALL) ALL 
and replace it with this:[FONT=monospace]
[/FONT]%admin  ALL=NOPASSWD: ALL
6) Save the file.
7) Reboot so that changes can take effect.


I haven't actually tested this out. Here is the reference (on older versions, so do not attempt) :
[http://my.opera.com/Viperstryker/blog/how-to-disable-sudo-password-prompts-on-ubuntu](http://my.opera.com/Viperstryker/blog/how-to-disable-sudo-password-prompts-on-ubuntu)

---

### Post by llamabr on 2011-11-29
Also, it depends on when you're having to type your password. The above notes are all assuming it's when you run sudo or other super user application.  Under what other circumstances are you asked for your passwd?

---

### Post by bluexrider on 2011-11-29
> **hansdown said:**
> Welcome to ubuntu, tears of the river.

We're not allowed to give that info.

Trust me, your system is more secure, with the password system.

I agree with hansdown

It is un-wise to do what you are requesting but it is YOUR system and YOU are allowed to screw it up. Thats how we learn right!

---

### Post by CharlesA on 2011-11-30
> **fbelzile said:**
> Stuff

If you are going to post how to disable sudo from prompting for a password, you should have at least posted a warning about it.

Read the page here:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by duke.tim on 2011-11-30
> **CharlesA said:**
> If you are going to post how to disable sudo from prompting for a password, you should have at least posted a warning about it.

Read the page here:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

+1

I agree, This is very very very important

---

### Post by tears of the river on 2011-11-30
Thank you everyone for their help but i decided that it is not that annoying so im not going to mess it up again

---

### Post by fbelzile on 2011-12-02
> **CharlesA said:**
> If you are going to post how to disable sudo from prompting for a password, you should have at least posted a warning about it.

Read the page here:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Sorry I don't mean to bring this thread back up since its solved, I'm fairly experienced with Linux distributions and I did give a warning before my instructions... :confused:

"1) You will automatically grant root privileges (the same as an  Administrator account on Windows) to any program that requests it,  without even knowing. This is a risky move.
2) Important/critical system files can easily be changed by you. Not  that I mean that in a bad way. But being the humans we are, accidents  happen. Accidents can go as far as deleting some kernel modules, etc...
3) You will probably forget that you have done this (from not seeing any  pop-ups to remind you). This leaving your system horribly vulnerable.
4) Since your a new user, this might be an inconvenience to you compared  to Windows, but guess what? Your system is that much more secure. It  should make you feel good, warm and comfy :smile:
5) Once you finish setting up your Ubuntu the way you like it, you  won't have to do as many configuration changes, so you will see those  pop-ups less and less."


Did I miss something?
Sorry if my list of reasons (not to do this) looked like instructions. I just don't like it when people don't read my posts and criticize.

---

### Post by CharlesA on 2011-12-02
> **fbelzile said:**
> 
Did I miss something?
Sorry if my list of reasons (not to do this) looked like instructions. I just don't like it when people don't read my posts and criticize.

I don't think you missed anything. They looked a bit like instructions if you just glance at them. :)

---

### Post by duke.tim on 2011-12-03
I thought it was important to include the link to the RootSudo wiki, because it provides additional information hence the +1. There is no problem with your post in my opinion :)

---

