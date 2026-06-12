---
title: "Is There A Way Or Means To Permanently Have Ubuntu Keep The Number Lock ALWAYS ON?"
date: 2012-05-02
forum: General Help
---

### Post by montecarlo87 on 2012-05-02
[FONT=Arial][SIZE=2]Hello. I am running Linux Ubuntu v.12.04 64-bit LTS. I am having an issue with the NumLock function of the keypad section of my keyboard not working ONLY at the Ubuntu login screen.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2][COLOR=#222222]When I startup Ubuntu 64-bit, I notice each and every time regardless of the setting from the last Ubuntu session (whether a system start or restart) and when I always get into the Ubuntu Login screen, that I have to either turn ON my number lock key ("NumLock") for the numeric keypad on the right side of my desktop keyboard or use the numeric keys associated with the QWERTY side of my keyboard instead. It is always OFF when I start at the instance of starting the computer. Then following a successful login, the after the Ubuntu desktop loads is when on my keyboard the NumLock LED light is finally ON. [/COLOR][/SIZE][/FONT]
 
[FONT=Arial][SIZE=2][COLOR=#222222]Yes, if you are asking: I have my BIOS for my ASUS P5Q motherboard's "Bootup Num-Lock" set to "ON". So I have eliminated this as a possibility of issues. [/COLOR][/SIZE][/FONT]
 
[COLOR=#222222][FONT=Arial][SIZE=2]I see by following the top GUI section of the Ubuntu weblink tutorial with instructions/diagrams on "NumLock" - "Enable Numlock on Login" (website: [/SIZE][/FONT][[FONT=Arial][SIZE=2]https://help.ubuntu.com/community/NumLock);[/SIZE][/FONT]]("https://help.ubuntu.com/community/NumLock);")[FONT=Arial][SIZE=2] resolved the issue OF 'ORIGINALLY' NOT RECEIVING 'ANY' NumLock functions AT ALL, even after the Ubuntu desktop loaded. Yes, before performing this Ubuntu weblink tutorial, the NumLock functions did not work AT ALL. There was no LED lit on my keyboard for the NumLock to be ON. So I received some resolution by performing this Ubuntu weblink tutorial.[/SIZE][/FONT][/COLOR]
 
[COLOR=#222222][FONT=Arial][SIZE=2]So just to clarify, I get NumLock to function (*AFTER* my Ubuntu login screen and) *AFTER* my desktop loads up where on my keyboard the NumLock LED light finally comes ON. [/SIZE][/FONT][/COLOR]
 
[FONT=Arial][SIZE=2][COLOR=#222222]Question:[/COLOR][/SIZE][/FONT]
 
[FONT=Arial][SIZE=2][COLOR=#222222]Is there a way or means to permanently have Ubuntu keep the number lock key always ON when I first arrive at the Ubuntu login screen? Some Ubuntu setting I need to change? Some third party program installation to achieve this, etc.? Please explain.[/COLOR][/SIZE][/FONT]
 
[FONT=Arial][SIZE=2][COLOR=#222222]Please reply.[/COLOR][/SIZE][/FONT]
 
[FONT=Arial][SIZE=2][COLOR=#222222]Thank you! [/COLOR][/SIZE][/FONT]

---

### Post by Xgen on 2012-05-02
Sudo apt-get install numlockx.

Edit: Sorry, tried it and it doesn't work either.

---

### Post by stinkeye on 2012-05-02
> **Xgen said:**
> Sudo apt-get install numlockx.

Edit: Sorry, tried it and it doesn't work either.
You also need to edit **lightdm.conf**
```
gksudo gedit /etc/lightdm/lightdm.conf
```

and add the line...
```
greeter-setup-script=/usr/bin/numlockx on
```

---

### Post by montecarlo87 on 2012-05-02
@ xgen & stinkeye: 

Hello. Nice to meet you both.

Thank you both for your comments.

Yes, xgen, I had that line command and it did not work for me either. Thank you for your try!

Thank you stinkeye! It worked! Yes, after adding that command script into gedit, saving it, and rebooting/starting my Ubuntu system, the numlock key now works at the login screen!!! Thank you very much!!!

---

### Post by kwitkowski on 2012-05-14
I'm having a similar problem, I've tried the methods above and still no luck.

Running numlockx on and numlock off simply turns the led on and off, the number keys still don't work.   =(

I've tried two different keyboards in the odd chance it was a bad keyboard.
[COLOR=DarkRed]
Found my own answer in a different thread.  The key is actually in a mouse setting.  

[http://ubuntuforums.org/showthread.php?t=1971830&highlight=numlock](http://ubuntuforums.org/showthread.php?t=1971830&highlight=numlock)
[/COLOR]

---

