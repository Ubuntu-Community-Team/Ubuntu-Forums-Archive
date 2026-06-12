---
title: "¿How do I recover Ubuntu after a crash?"
date: 2009-09-02
forum: General Help
---

### Post by ZequeZ on 2009-09-02
Well, in Win. i used to use Crtl+Alt+Supr and mostly crashes resolved, but today Ubuntu have crashed 2 times because of IEs4Linux (I'm a web developer) and I had to reset the computer :S.

I have a Hotkey to the System Monitor, but it crash totally, the cursor start to move really snatchy and I can't click anywhere :S.

There is a way for "unchrash"? :S

Thanks.
And sorry for my English =/.

---

### Post by fluffman86 on 2009-09-02
Killing/Restarting the X server usually helps.
```
sudo apt-get install dontzap
sudo dontzap -d
```
Once you do that, anytime you're having trouble you can press ctrl + alt + backspace to log out and back in really quick.

Also, pressing ctrl + alt + f2 will take you to a terminal, and you can kill unresponsive processes from there.  I don't remember what the process name for ies4linux was, but let's say it's iexplore.exe.  So if ies4linux is giving you trouble, then press ctrl + alt + f2 to get to a terminal, log in with your normal username/password, and type:
```
sudo killall -9 iexplore.exe
```
If you don't know the name of the process, you can type "top" to see what's running, then press "q" to exit top and run the above command.

---

### Post by nothingspecial on 2009-09-03
Press Alt+SysRq and while holding those down RESUIB.

---

### Post by P4man on 2009-09-03
fluffman86 gave some good advice, but IE shouldnt be able to bring down ubuntu entirely when it crashes. 

Try this: right click the gnome panel, add to panel, select "force quit". Next time IE crashes, click the force quit applet, then select the IE window to force it to quit.

That said, you should be able to quit most hung programs by just clicking the close button. A prompt will ask for confirmation.

If none of this is working, then Im guessing you're having a different issue. Its all too tempting and convenient to blame IE for crashing your machine, but if it really freezes up to the point where nothing works, I dont think it would be IE.

---

### Post by brian3 on 2009-09-03
i've been useing ubuntu for 4 years if it crashes reinstall it it saves a lot searching and asking questions
brian3

---

### Post by ZequeZ on 2009-09-03
> **fluffman86 said:**
> Killing/Restarting the X server usually helps.
```
sudo apt-get install dontzap
sudo dontzap -d
```Once you do that, anytime you're having trouble you can press ctrl + alt + backspace to log out and back in really quick.

Also, pressing ctrl + alt + f2 will take you to a terminal, and you can kill unresponsive processes from there.  I don't remember what the process name for ies4linux was, but let's say it's iexplore.exe.  So if ies4linux is giving you trouble, then press ctrl + alt + f2 to get to a terminal, log in with your normal username/password, and type:
```
sudo killall -9 iexplore.exe
```If you don't know the name of the process, you can type "top" to see what's running, then press "q" to exit top and run the above command.

After install Dontzap the key combination you say doesn't work for me :S
O knew the terminal hotkey, but I never use it because I don't know how to go out of it xDDD. How do I go back to the graphic interface? xD

PD: nothingspecial: Where are those keys? In my keyboard aren't :S xD (Sysrq and RESUIB I mean)

---

### Post by nothingspecial on 2009-09-03
SysRq is sometimes on the same key as Print Scrn up the top somewhere.

RESUIB is just those letter keys in that order.

---

### Post by nothingspecial on 2009-09-03
Actually its Raising Skinny Elephants Is Never Utterly Boring

RSEINUB

---

### Post by ZequeZ on 2009-09-03
> **nothingspecial said:**
> SysRq is sometimes on the same key as Print Scrn up the top somewhere.

RESUIB is just those letter keys in that order.

I do that... But, appear a screen to save a screenshot xD. Why I would want to save a screenshot of my freezing Ubuntu? xDD.

PD: I Googled RSEIUB and I know what it means, but it doesn't work in my computr :S.

---

### Post by P4man on 2009-09-04
if a screenhot window appears, then your system isn't all that frozen, is it ? Try the things I posted above.

PS: you have to hold the printscreen down while typing those letters, but really, if a printscreen appears, its not necessary!

---

### Post by humaneasy on 2009-09-08
> **ZequeZ said:**
> I do that... But, appear a screen to save a screenshot xD. Why I would want to save a screenshot of my freezing Ubuntu? xDD.

PD: I Googled RSEIUB and I know what it means, but it doesn't work in my computr :S.

As I understood you meant an computer froze under Ubuntu and not a crash. Am I right?

I don't use the above sequence for cleanly rebooting the system.
I use, when everything completely forzes (rarely), to shutdown correctly the computer:

[LIST=1]
[*]Press simultaneously  "Ctrl" + "SysRq"
[*]Keeping those two pressed, press the following letters one after the other R,  E, I, S, U, B.
[/LIST]

It will reboot.

---

