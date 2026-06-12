---
title: "Two questions"
date: 2010-12-26
forum: General Help
---

### Post by Cyber geeK on 2010-12-26
Hello guys,
I never really used linux, maybe tried it a few times. But now I'm planning to stick with it.
I have one problem with my sound. I have SteelSeries Siberia Headset, and SteelSeries usb soundcard that I got with it. I can't get it to work :/
I tried alsamixer, but had no success. 
Here's the screenshot
[img]http://i.min.us/ibt2Kq.jpg

And one more question. What's the difference of getting root access with,
sudo - (then type the password)
and 
sudo -s (I managed to login like this once, can't remember how :/ )
?
And I've posted this on another forum, that's why you see that picture.
Thanks for the answers in advance guys.

-cgeek

---

### Post by karthick87 on 2010-12-26
Welcome to ubuntuforums :)

Look at the following link, 
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Cyber geeK on 2010-12-26
Thanks for the reply.
I've already checked that link, yesterday. But when I'm in Terminal, and type
sudo su, then my password, I can login successfully.
But when I type, su -, and then my password, I can't :/
And do you have a solution for my first question ?

-cgeek

---

### Post by fatal_ERROR777 on 2010-12-26
Go to System-> Preferences -> Sound. Maybe you have your output/input device switched off?

Fatal_Error

---

### Post by Cyber geeK on 2010-12-26
That's not the problem bro :/
I've already checked that before.
Any other suggestion ?

-cgeek

---

### Post by fatal_ERROR777 on 2010-12-26
Second question: why don't you have a volume meter on your panel? That icon is very useful knowing weather the output is turned on or off. 
Second solution: Maybe you have a volume control in your headset don't you? Then, turn it on. Also, try another headset, if it doesn't work... But firstly check this.

Fatal_Error

---

### Post by fatal_ERROR777 on 2010-12-26
Some folks are saying, that it's better to replace [ALSA]("http://www.alsa-project.org/main/index.php/Main_Page") to [PulseAudio]("https://wiki.ubuntu.com/PulseAudio"). I don't know weather it's going to work. And, check for system update in update manager. Maybe this will solve your problem.

Fatal_Error

---

### Post by Cyber geeK on 2010-12-26
I've accidentally deleted it, and don't know how to get it back :/
When I right click on the panel, and then "Add to Panel", I can't find it..
Will try PulseAudio, and then post the if it works ;)

#edit
I set everything at it's max level, and still no sound :/

-cgeek

---

### Post by fatal_ERROR777 on 2010-12-26
hmm... I am getting out of arsenal ](*,) 
After googling a while, I have found a solution for the volume icon
[http://ubuntuforums.org/showthread.php?t=1595517]("http://ubuntuforums.org/showthread.php?t=1595517")
After reading that thread, I have reloaded my guns :D
Add a "Notification area" applet.
[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449") I haven't figured out, what was the person doing in the terminal, but this may fix your sound problem.
And, you better change your sound from MAX to normal (around of 50-60%) because if it will suddenly work, your ears are going to BBQued

Fatal_Error

---

### Post by WorMzy on 2010-12-26
> **Cyber geeK said:**
> Thanks for the reply.
I've already checked that link, yesterday. But when I'm in Terminal, and type
sudo su, then my password, I can login successfully.
But when I type, su -, and then my password, I can't :/
And do you have a solution for my first question ?

-cgeek

```
sudo COMMAND
```
uses *your* password
```
su
```
uses *root's* password (which is disabled by default on Ubuntu)
```
sudo su
```
works because you're using sudo (with your password) to gain root privileges, then using the root privileges to run su (which doesn't ask for a password, because it thinks that root is running it)

To avoid confusion, I avoid telling people to use su at all, you can use```
sudo -i
``` to get a root shell, instead of "sudo su".

---

### Post by Cyber geeK on 2010-12-26
Thanks for your effort man.
I've managed to get my volume slide back again. But it's not "Notification area", as it only gives me a simple separator :/
The one I've needed is "Indicator Applet".
And the tread about the sound, I don't have that problem :/
My Ubuntu can see my sound card, but it's not working..
When I type "aplay -l" in terminal I can see it. 
It's called "C-Media USB Headphone Set", as you can see on the Screenshot in attachments.

> **WorMzy said:**
> ```
sudo COMMAND
```
uses *your* password
```
su
```
uses *root's* password (which is disabled by default on Ubuntu)
```
sudo su
```
works because you're using sudo (with your password) to gain root privileges, then using the root privileges to run su (which doesn't ask for a password, because it thinks that root is running it)

To avoid confusion, I avoid telling people to use su at all, you can use```
sudo -i
``` to get a root shell, instead of "sudo su".
When I type, "su -", then my password, it won't let me log in.
But when I type, "sudo su", and then my password I log in successfully.
What's the difference between these two ?

-cgeek

---

### Post by WorMzy on 2010-12-26
Like I said, su uses *root's* password, not yours. On Ubuntu, root's password is disabled, so no matter what you enter at the su password prompt, it will be incorrect.

---

### Post by Cyber geeK on 2010-12-26
Oh..
I get it now bro :)
Thanks for the answer.
But I still have a sound problem :/

-cgeek

---

### Post by Cyber geeK on 2010-12-26
Still need help guys.
Dunno how to get my sound to work :/

-cgeek

---

