---
title: "Can't log-in after update"
date: 2011-09-22
forum: General Help
---

### Post by frenchian on 2011-09-22
I'm using Kubuntu 11.04, with all the recommended daily updates. Just now, I did my daily update - among other packages was a new kernel (38-11). Now, I can't get into Kubuntu.

During the upgrade, there was a message along the lines of "your plasma profile needs replaced, choose another", or something similar. Now, I get to the log-in screen, where it asks for my id and password (didn't used to....) and it doesn't recognise my password.

I **can** get to a console, though.

*EDIT: I can log-in at a console with my ID and password, but if I, eg, try and restart KDM, it takes me to the log-in screen. When I enter the valid ID and password, it loops back to the log-in screen. ??*

(Please forgive the vagueness, I'm trying to remember what happened)

Everything is backed up, so this may be a chance to test my recovery strategy. But, I'd rather not if I can avoid it.

Any help will be appreciated.

Thanks

---

### Post by frenchian on 2011-09-22
> **frenchian said:**
> I'm using Kubuntu 11.04, with all the recommended daily updates. Just now, I did my daily update - among other packages was a new kernel (38-11). Now, I can't get into Kubuntu.

During the upgrade, there was a message along the lines of "your plasma profile needs replaced, choose another", or something similar. Now, I get to the log-in screen, where it asks for my id and password (didn't used to....) and it doesn't recognise my password.

I **can** get to a console, though.

*EDIT: I can log-in at a console with my ID and password, but if I, eg, try and restart KDM, it takes me to the log-in screen. When I enter the valid ID and password, it loops back to the log-in screen. ??*

(Please forgive the vagueness, I'm trying to remember what happened)

Everything is backed up, so this may be a chance to test my recovery strategy. But, I'd rather not if I can avoid it.

Any help will be appreciated.

Thanks

Well, I created a new user ("temp") at the console, and tried to log-in with it. I got two error messages

"/home/temp/.kde/share/config/kdedrc not writable"
"/home/temp/.kde/share/config/konsolerc not writable"

Looks like I'm going to be testing my recovery strategy sooner than I expected.......

Cheers

---

### Post by raja.genupula on 2011-09-22
hey man use reset password for your issue 
follow this link to get it 
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by frenchian on 2011-09-22
> **raja.genupula said:**
> hey man use reset password for your issue 
follow this link to get it 
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Thanks for the response, raja, but I'm not sure it's the password that's wrong.

I can get into the console using my ID and PW - it's only when I try to log via the GUI screen that I have a problem. Nothing starts - it just loops back to the GUI screen. The same thing happens when I use another (new and working) set of ID and PW.

Whatever is supposed to happen after I log-in isn't happening...

Cheers

---

### Post by raja.genupula on 2011-09-22
oh ok man. 

then after login from the console press Ctrl + alt+f7 to get GUI interface and let me know what you got.


all the best.

---

### Post by Duncan Williams on 2011-09-22
kernel updates can break things like `video drivers' and lock you out of your system in the process.

---

### Post by raja.genupula on 2011-09-22
> **Duncan Williams said:**
> kernel updates can break things like `video drivers' and lock you out of your system in the process.

+1 
yeah we have a possibility of this

---

### Post by frenchian on 2011-09-22
[QUOTE=raja.genupula;11274908]oh ok man. 

then after login from the console press Ctrl + alt+f7 to get GUI interface and let me know what you got.


all the best.[/QUOTE

When I log in at the console, I get the "console prompt" (option to enter commands). Trying Ctl-AltF7 doesn't get me a GUI  it gives me a "~" character (tilde?)at the prompt.

Tx

---

### Post by raja.genupula on 2011-09-22
hey man 
just now i re-confirmed .keep hold ctrl key and alt key and then press F7 key .

---

### Post by frenchian on 2011-09-22
> **raja.genupula said:**
> hey man 
just now i re-confirmed .keep hold ctrl key and alt key and then press F7 key .
OK, raja, a small advancement.

When I press Ctl-Alt-F7, while in console mode, I get half a static screen of messages about starting and stopping daemons etc. These are the same messages that roll up the screen quickly if I start the system as usual. In that situation, they end with the log-in screen (the one with the Kubuntu wallpaper in the background, and a log-in box in the foreground.

This box asks me for an ID and a PW. The problem is that when I press "enter", the system doesn't start - it doesn't start, eg, wifi, or present me with my desktop. All that happens is that it goes back to the log-in screen

Thanks

---

### Post by raja.genupula on 2011-09-22
Do you have any old kernels in your grub menu ? if so boot from them

---

### Post by frenchian on 2011-09-22
Tried that, with the same result - I get to the log-in screen, but no further.

---

### Post by raja.genupula on 2011-09-22
Hey man, I am really trying to help you , but i dont know upto what extent i can make this .

give a try to this 
 
boot from fail safex mode which is in recovery mode and then re install your video drivers and restart your system  check once again .

let me know what you got 

all the best

---

### Post by frenchian on 2011-09-22
Sorry, raja, that's difficult for me. I guess they're on the Kubuntu live CD, but i don't know where.

Is thee a simple command I can enter at the command line to start the lan connection? I was thinking that if I had that, I could run apt-get update/upgrade again?

I'm clutching at straws here, just postponing the moment when I have to start the complete recovery process

cheers

---

### Post by raja.genupula on 2011-09-22
```
ifconfig
```
will shows the connections to you 
```
ifup connection
```
will enable your connection 

hey man , give a try to this. I am not sure about this but give a try 
```
sudo apt-get install --reinstall kubuntu-desktop
``` 

all the best man .

---

### Post by frenchian on 2011-09-22
> **raja.genupula said:**
> ```
ifconfig
```
will shows the connections to you 
```
ifup connection
```
will enable your connection 

hey man , give a try to this. I am not sure about this but give a try 
```
sudo apt-get install --reinstall kubuntu-desktop
``` 

all the best man .

Sorry, raja, I was too impatient. I got the LAN connection working, so tried apt-get update/upgrade. No improvement, though - same problem as before.

So, I re-installed /root and /home from two Clonezilla images. This worked perfectly - I'm now back up and running. I haven't tried reinstalling this morning's update, though. May leave it till tomorrow, in case there was a bug.

It would have been nice if we could have solved this problem, without having to recover but that's life. At least I got to test my master plan.

Many thanks for all your help.

Cheers

---

### Post by raja.genupula on 2011-09-22
hey man, have you tried that last command i have given to you ?
its gonna make all the things to its defaults . please try it.

---

