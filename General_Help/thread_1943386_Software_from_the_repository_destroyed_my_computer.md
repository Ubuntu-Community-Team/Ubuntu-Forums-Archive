---
title: "Software from the repository destroyed my computer, HELP!"
date: 2012-03-19
forum: General Help
---

### Post by helpvv on 2012-03-19
I wanted to change the startup background. I searched and found lightdm Display Manager.

I went to change the background and it didn't work. I went to uninstall it. 

I didn't do anything else.

I rebooted a few minutes later.

I came back and my computer wouldn't start. 

It said 
loading fallback graphic something.. FAIL
loading light DM something            .. FAIL

I can't get to the login screen 

I have a lot of important data which I need to get to. 

I really have no idea what's wrong because I didn't even use sudo app-get this was all done in the software center

I'm using 11.10

---

### Post by snowpine on 2012-03-19
Welcome to the forums!

Do you get as far as a text-mode prompt where you can enter your username and password?

If the answer is Yes then log in and:

```
sudo apt-get install ubuntu-desktop
```

This should re-install the stuff you removed. :)

If you can't get to the username prompt, then try rebooting into Rescue mode (see the GRUB screen that appears when you first boot).

ps Your data is probably not lost. If your system ever has trouble booting, you can boot with an Ubuntu Live CD and copy the data. :)

---

### Post by helpvv on 2012-03-19
Ok thanks for the fast reply, I'm on a live CD so booting back and forth. I'll try this! Will tell you if it worked!

Edit: I can't get to the log in screen, it doesn't even load. I'll try this from recovery mode. 

Could you tell me how to copy the dta from a live CD? just in case?

---

### Post by snowpine on 2012-03-19
> **helpvv said:**
> Edit: I can't get to the log in screen, it doesn't even load. I'll try this from recovery mode. 

Not a good sign... but try pressing Ctrl+Alt+F1 simultaneously; does that take you to a login prompt?

> **helpvv said:**
> Could you tell me how to copy the dta from a live CD? just in case?

When you are booted to Ubuntu from the Live CD, you should see a Places option somewhere (sorry I am not too familiar with the new interface) where you can browse to your hard drive and copy files to an external hard drive/thumb drive.

---

### Post by TBABill on 2012-03-19
You shouldn't need a liveCD if you are able to boot into rescue mode. Just boot and get to a terminal, then install the Ubuntu desktop (Unity) again so it will pull in a display manager. You basically dumped your display manager so Ubuntu didn't know how to respond after you removed it. LightDM because your display manager by request when you installed it so you have to be very careful what you remove in the future so you don't create an unusable system. Removing a kernel, grub and other things will also render your machine broken.

---

### Post by helpvv on 2012-03-19
Ok, problem my home file is encrypted so I couldn't do sudo apt-get install ubuntu.. 

Could you tell me how to do this? 

I found the readme and it said exec is /usr/bin/"something with encryptfs-mount"

but I couldn't execute it although I tried

---

### Post by snowpine on 2012-03-19
I am not very knowledgable about encryption, sorry. I am sure another forum member will be able to assist you. :)

---

### Post by helpvv on 2012-03-19
I figured out how to execute it.. but it said it's not set up properly... 

Is there anything I can do?

---

### Post by donkyhotay on 2012-03-19
The easiest way past the encryption is to log in normally. First of all remove the liveCD, when the computer gives you the error message you've been getting try pressing ctrl-alt-F2 on the keyboard all at the same time. This should get you to a command prompt. If you get that far sign in with your username/password. Be aware that while typing in password here you won't see the echo (those asterisks that usually tell you you're typing in a password) but that's normal. Once you've logged in then run the command
```

sudo apt-get install ubuntu-desktop

```
that was suggested earlier.

---

### Post by ajgreeny on 2012-03-19
Depending on what was removed when you messed around with lightdm, you may be able to get to the normal desktop with the command **startx** after you have logged in to the cli.  You can then use your normal means of installing whatever packages were removed.

---

