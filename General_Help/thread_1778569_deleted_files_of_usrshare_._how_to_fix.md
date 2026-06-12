---
title: "deleted files of /usr/share . how to fix ??"
date: 2011-06-09
forum: General Help
---

### Post by vikashiiitdm on 2011-06-09
hiii,
can you please help me with a problem? i accidentally removed  some files from my /usr/share directory and i don't know what they are !  is there any way of fixing this situation. i have a very high speed  internet connection but i don't wanna format and reinstall my os.

thank you

---

### Post by hawthornso23 on 2011-06-09
How specifically did you delete them. If you did it by typing something ill advised in a terminal then if we know the exact command you typed we might be able to figure out which files got deleted. If you haven't logged out yet then that can be discovered by looking back at your command history (use the up arrow in a terminal). 

If we know which files got deleted then you might be able to fix it by marking certain packages for reinstallation in Synaptic. 

Are we talking about a few files here or a lot? If you've wiped most of your usr/share directory using rm -r or similar then I think you may indeed have to reinstall.

---

### Post by vikashiiitdm on 2011-06-09
> **hawthornso23 said:**
> How specifically did you delete them. If you did it by typing something ill advised in a terminal then if we know the exact command you typed we might be able to figure out which files got deleted. If you haven't logged out yet then that can be discovered by looking back at your command history (use the up arrow in a terminal). 

If we know which files got deleted then you might be able to fix it by marking certain packages for reinstallation in Synaptic. 

Are we talking about a few files here or a lot? If you've wiped most of your usr/share directory using rm -r or similar then I think you may indeed have to reinstall.
actually i had been writing a program for my system, and i chose to place my files in /usr/share/mybin. when i had to update itz version i thought of removing the old files and writing new ones. so i did rm -r /usr/share but accidentally couldn't type mybin . i have run this for only 2 or 3 secs . but after that i am not able to run my gnome-panel, software center etc and i still don't know which commands got effected. 

thanks for replying.

---

### Post by hawthornso23 on 2011-06-09
You can lose a lot of files in 2-3 seconds. I suspect you will have to reinstall.

Maybe someone reading this knows a way to get synaptic to search for all installed packages that put files into /usr/share and mark just those ones for reinstallation. That might be marginally less painful than a complete reinstall. But not by much. 

Sorry - I can't help you.

---

### Post by coffeecat on 2011-06-09
> **hawthornso23 said:**
> Maybe someone reading this knows a way to get synaptic to search for all installed packages that put files into /usr/share and mark just those ones for reinstallation. That might be marginally less painful than a complete reinstall. But not by much. 

That's an intriguing and creative idea but there's a /usr/share/synaptic folder and if that's gone, then... well... :(

@vikashiiitdm, it might be worth seeing how many folders you have left in /usr/share. It will vary, of course, depending on what extra applications have been installed, but to give you an idea I have 352 folders in /usr/share in my Natty system. That doesn't help much but does give you an idea of the extent of the damage.

Just to build on hawthorneso32's interesting suggestion, you could try:

```
dpkg --get-selections
```... to get every single installed package, somehow edit that so it is a consecutive list of packages, and then run:

```
sudo apt-get install --reinstall <*enormous list*>
```But I think a re-install would be quicker.

---

### Post by vikashiiitdm on 2011-06-10
hiii, thanx for your help.......but i had adopted the new install procedure . the problem is neither pxe boot nor pendrive boot works for me for any ubuntu version. ubuntu 11.04 stuck after 
/* binfmt -- enabling additional binary formats supports */ of kind . pxe boot also stuck @ it. 

ubuntu 10.10 , ubuntu 10.04 or any other versions are also not getting installed all of them freeze at some or the other point . i just get the ubuntu purple screen for 5-10 seconds ...with the dots moving and then everything freezes except my cursor. 
 
my system specifications are :-

core 2 duo 2.1 ghz with 2.0 mb L2 cache

512 mb nvidia 8200mg graphic card

64 bit machine with 4.0 gb ram.

thanx in advance for any kind of help.

---

### Post by hawthornso23 on 2011-06-10
Sorry to hear it isn't going well for you. I feel your pain. 

I don't understand the problem you are having reinstalling, but this appears to be a problem completely unrelated to the original one. To get noticed by the people around here who specialize in helping out with installation issues I suggest you start a new thread with a heading that says you are having trouble reinstalling.

---

### Post by coffeecat on 2011-06-10
@vikashiiitdm, yes I agree with what hawthornso23 says. It's odd that you can't boot up a pendrive on a system on which you had originally installed Ubuntu. Yes, start a new thread with a title that describes the new problem so that those who can help will see it. Also, post details of which version of Ubuntu you originally installed, and how you installed it. It might help in deciding what has gone wrong now.

---

