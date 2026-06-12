---
title: "Ubuntu (dual boot) login screen problem"
date: 2009-12-11
forum: General Help
---

### Post by noweis275 on 2009-12-11
I just downloaded Ubuntu. I loaded it onto my HP laptop with Windows Vista (64 bit). I downloaded Ubuntu, burnt it to a CD, loaded it, and followed to instructions to partition the hard drives automatically and install Unbutu next to Vista. I rebooted my computer and booted it up with the Ubuntu Linux option. The logo appears and then the login screen follows. The problem is the text on the login screen is flickering, so it doesn't recognize my keystrokes. I can get my username in after a few presses of each button but I can't get the password in because of the flickering. I tried to find a solution but I'm completely new to Ubuntu and dual booting a system. Any help would be great. Thanks.):P

---

### Post by noweis275 on 2009-12-11
Anyone? I'd like to start using Ubuntu, it's a new experience for me because I've always been a Windows user. Everything seemed okay until the login screen flickering. I don't know how else I can log on. Reinstalling seems a bit extreme for one seemingly small problem so I'd like to avoid that (and since I don't know how to reinstall lol).

---

### Post by ST3ALTHPSYCH0 on 2009-12-11
It sounds like what happened to me when I borked up my video driver. Do you have an Nvidia or ATI vid card? If so try these steps.
At grub select the recovery kernel.
At the next menu select drop to root shell with networking.
Install envy 
```
 apt-get install envyng-qt
```
Run envy
```
envyng -t
```
Choose the driver you need from the menu.
Reboot
See if that helps.

---

### Post by wsims2 on 2009-12-11
I would think the best option wold to boot into recovery and update the system first to see if that fixes the problem. It couldn't hurt. 

```

sudo apt-get update
apt-get upgrade

```

I didn't think people still used envy.

---

### Post by ranch hand on 2009-12-11
> **wsims2 said:**
> I would think the best option wold to boot into recovery and update the system first to see if that fixes the problem. It couldn't hurt. 

```

sudo apt-get update
apt-get upgrade

```I didn't think people still used envy.
Yes try recovery as above.  Very good advice.

---

### Post by noweis275 on 2009-12-11
was having some trouble getting things typed in. As I would type it in, it would just act like I was hitting "enter" it would  move up a line with some text after it and it would continue to let me type in a new line. Eventually I got it but it didn't seem to help anything. I suppose I'll try the envy thing.

---

### Post by ST3ALTHPSYCH0 on 2009-12-11
Now that you say that, it doesn't sound like a vid driver error at all.

---

### Post by noweis275 on 2009-12-11
Oh no lol. What do you think it might be? Do you guys think the envy thing from the first post will help? I havn't tried it yet. If that doesn't work what would you suggest, re installing?

---

### Post by noweis275 on 2009-12-11
Okay, so you're all probably sick of my problem, but it's not going well. :(
I tried the envy thing too, and it just says it failed to fetch files. 
Before that I tried the upgrade option, and it said failed to fetch files. Something along the lines of archives/ubuntu/karmic upgrade (or security or something) Sorry I don't know how to copy it for you all to see. All I wanted to do was try Ubuntu :'(   I didn't know I was going to have to devote my life to fixing it.

---

### Post by Leppie on 2009-12-11
> **noweis275 said:**
> I tried the envy thing too, and it just says it failed to fetch files. 
Before that I tried the upgrade option, and it said failed to fetch files.

Did you boot into recovery mode? You should get to a screen providing you the "netroot shell" option. This will give you root access with networking.

---

### Post by noweis275 on 2009-12-11
Yes, I booted into recovery and then into "shell with networking." Nothing works. Any other ideas? :\ This is a bad first experience with Linux >.> Hopefully someone has some sort of solution..

---

### Post by noweis275 on 2009-12-11
Well if no one has any other ideas, I can't fix it myself so.. is there any way to  remove Ubuntu from my hard disk without my windows recovery disks? (I don't have the discs but I can still boot into my Vista partition) Someone should know how to do this I assume. Thanks guys.

---

### Post by wsims2 on 2009-12-12
If you still want help, you'll need to post exactly what the errors are. 

What happens when you try and run:

```
sudo apt-get update

apt-get upgrade
```

Are you sure you have a network connection? 

What happens if you try:
```

ping www.google.com
```

---

