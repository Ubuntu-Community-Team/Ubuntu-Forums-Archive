---
title: "Terminal asks for password and then crashes"
date: 2011-09-18
forum: General Help
---

### Post by niuri_cigarete on 2011-09-18
Hi everyone,

I've encountered this problem here and I don't really remember doing anything to the terminal... After opening it asks for my password and after I type it in and hit enter the whole window crashes. I tried opening synaptics and it gives me this error:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

All I can do then is to close it. But since I cannot use the terminal then I can't fix this. Can anyone help? I'm using Ubuntu 11.04.

---

### Post by wildmanne39 on 2011-09-18
Hi, it looks like you are having a problem with your source list. Try this please and post any errors here:
```
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```
run these commands one at a time.

I hope you can run these commands
Thank you

---

### Post by oldos2er on 2011-09-18
When you say "crashes" do you mean the window closes? Disappears? If you're using gnome-terminal, try xterm instead.

---

### Post by sikander3786 on 2011-09-18
Welcome to the forums ;)

Press Ctrl + Alt + F1 and log in to the tty1 (Terminal type console) using your username and password. Now execute these commands one-by-one:

```
sudo dpkg --configure -a | tee ~/dpkg.log
sudo apt-get install -f | tee ~/dependency.log
sudo apt-get update | tee ~/update.log
sudo apt-get upgrade | tee ~/upgrade.log
```

After the commands complete, press Ctrl + Alt + F7 to get back to the GUI.

If Terminal starts working, you are good to go otherwise open you home directory and attach the files named dpkg.log, dependency.log, update.log and upgrade.log to let us take a look.

---

### Post by niuri_cigarete on 2011-09-18
I can't run any commands in terminal and yes, the window just disappears after I hit 'enter'. And about using tty1: do I have to type in my username normally? Because it says it's incorrect and I'm sure I typed it right...

EDIT: I've tried using gnome-terminal and it does the thing I described, but the xterm runs normally. I did what wildmanne39 said and it didn't work.

EDIT #2: The synaptic actually worked and it showed me a broken package which was Sun-java6-jre. I upgraded it and everything seem to be fine now here. The terminal still doesn't work though.

---

### Post by wildmanne39 on 2011-09-18
Hi, in tty you type your username then your password.
Thank you

---

### Post by TeoBigusGeekus on 2011-09-18
What about pressing Alt+F2 (I don't know if this works on unity)?
If you get a prompt, type
```
xterm
```
If nothing happens, it means that xterm is not installed, so press Alt+F2, give 
```
sudo apt-get install xterm
```
and try again.

---

### Post by sikander3786 on 2011-09-18
> **niuri_cigarete said:**
> I can't run any commands in terminal and yes, the window just disappears after I hit 'enter'. And about using tty1: do I have to type in my username normally? Because it says it's incorrect and I'm sure I typed it right...
Yeah, you need to type your username (not full name). Try running this command in a Terminal to find you username, hopefully it wouldn't crash this time:

```
ls /home
```

Otherwise, open up your home directory and press the 'Up' button from toolbar. What is the name of your home directory, the same is the username.

---

### Post by niuri_cigarete on 2011-09-18
In tty1 it doesn't recognize my username for some reason... I'm sure it is correct but it still states that I'm wrong. That's why I asked about typing it...

---

### Post by sikander3786 on 2011-09-18
Hmmm. Then reboot your PC. From Bios screen, press and hold down <Shift> key until you see the Grub menu. Choose the second option on the menu i.e. Recovery Mode and then choose Drop to root shell.

Now try these commands:

```
dhclient eth0
```

Where eth0 is your network interface.

```
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by niuri_cigarete on 2011-09-18
Silly me, for my password I was using the side number pad instead of the ones above qwerty... ](*,)

Anyway, I got to use tty and I got some more errors, in the end of update/upgrade:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (var/lib/dpkg/), is another process using it?

EDIT: Oh, and that some index files failed to download. But that's about that Sun-java6-jre I told about before.

---

### Post by TeoBigusGeekus on 2011-09-18
Do you by any chance have software centre of synaptic open?

---

### Post by adit on 2011-09-18
> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
Simply restarting the computer will solve the problem

---

### Post by niuri_cigarete on 2011-09-18
> **TeoBigusGeekus said:**
> Do you by any chance have software centre of synaptic open?

No, it was closed. And a reboot fixed this.

But as I said that terminal problem still persists.

---

### Post by TeoBigusGeekus on 2011-09-18
Have you run the previously mentioned commands?
ie.
```
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by niuri_cigarete on 2011-09-18
> **TeoBigusGeekus said:**
> Have you run the previously mentioned commands?
ie.
```
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
```

Yes, that's exactly what I did and everything went fine except for update/upgrade. It can't download sun-java6-jre. I've just removed it but the terminal thing still persists as I said.

---

### Post by adit on 2011-09-18
See post#1
> After opening it asks for my password and after I type it in and hit enter the whole window crashes
1) Are you sure you are using gnome-terminal?  Does the window close only during password input or whenever you press 'Enter' key?

---

### Post by sikander3786 on 2011-09-19
> **niuri_cigarete said:**
> Yes, that's exactly what I did and everything went fine except for update/upgrade. It can't download sun-java6-jre. I've just removed it but the terminal thing still persists as I said.
We needed to see the complete outputs of the commands as mentioned back in post # 4 to diagnose your problems.

---

### Post by niuri_cigarete on 2011-09-19
> **adit said:**
> See post#1

1) Are you sure you are using gnome-terminal?  Does the window close only during password input or whenever you press 'Enter' key?

Yes, I'm sure. It closes when I enter the correct password and press 'Enter'. If I'm wrong then it tells me to try again and doesn't close.

EDIT: I can't upload files here for some reason so I'll attach links:
[dpkg.log](http://dl.dropbox.com/u/32128676/dpkg.log)
[dependency.log](http://dl.dropbox.com/u/32128676/dependency.log)
[update.log](http://dl.dropbox.com/u/32128676/update.log)
[upgrade.log](http://dl.dropbox.com/u/32128676/upgrade.log)

---

### Post by niuri_cigarete on 2011-09-19
Thank you all for answers but I decided to switch to older version of Ubuntu and reinstalled everything. I'm having less problems with my work :) (with my weather forecasting model to be exact, it was the cause for me switching to Linux for a short period of time). Thank you again!

---

