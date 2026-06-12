---
title: "Disable 'W' on keyboard"
date: 2010-04-15
forum: General Help
---

### Post by naval_arch1 on 2010-04-15
First time user of ubuntu on a resurected laptop.
 
Upon boot up, I get an irritating series of beeps as if a button is being pushed down.
 
I'm guessing it's the 'W' as I'm not able to use it after I log-in.
 
Looking for simple instructions on how to disable the 'W'.
 
Many thx.

---

### Post by LurkyLou on 2010-04-15
Hi, I'm new to Ubuntu myself.  Here are a couple of links that might help, assuming you can boot and get to a terminal:
[http://www.linuxscrew.com/2008/09/15/faq-how-to-disableremap-a-keyboard-key-in-linux/](http://www.linuxscrew.com/2008/09/15/faq-how-to-disableremap-a-keyboard-key-in-linux/)
[http://ubuntuforums.org/showthread.php?t=842970](http://ubuntuforums.org/showthread.php?t=842970)

---

### Post by naval_arch1 on 2010-04-15
Excellent, I'll give that a go.
 
This will only demonstrate my "newness" to ubuntu, but when you say "get to a terminal" can you tell me what that means?

---

### Post by Bungler on 2010-04-15
Ha ha, apperently! Welcome to the community.
Go to:
Applications -> Accessories -> Terminal.

I can recommend you to read some Ubuntu tutorials/wiki's on the web. You will find yourself more comfortable to navigate around and get used to some Linux terminology.

---

### Post by LurkyLou on 2010-04-15
Applications->Accessories->Terminal:
This is your access to the command line from the GUI (The screen with the icons, etc).
Sometimes you won't be able to run commands unless you put "sudo" (without quotes) in front of them.
ie instead of 'apt-get install...' you might need to do 'sudo apt-get install....'

---

### Post by naval_arch1 on 2010-04-15
thanks very much to all!
 
i'd be receptive to a few tutorials for a newb such as myself.

---

### Post by naval_arch1 on 2010-04-16
So I went to the following website to disable the 'W' key.
 
[http://www.linuxscrew.com/2008/09/15/faq-how-to-disableremap-a-keyboard-key-in-linux/](http://www.linuxscrew.com/2008/09/15/faq-how-to-disableremap-a-keyboard-key-in-linux/)
 
Found my way to the terminal and entered xmodmap -e 'keycode 25=' at the prompt.
 
Is what I did correct?

---

### Post by naval_arch1 on 2010-04-17
Tried logging in again...still getting beeps.

Assistance would be greatly appreciated.

---

### Post by philinux on 2010-04-17
> **naval_arch1 said:**
> Tried logging in again...still getting beeps.

Assistance would be greatly appreciated.

Does it beep before the grub menu or after?

---

### Post by naval_arch1 on 2010-04-17
Before, I'm guessing, it starts Within about ten seconds of me turning the machine on.

M.

---

### Post by Bungler on 2010-04-18
Well then I think it is not useful to disable this key in Ubuntu, since Ubuntu is not loaded yet.
Perhaps you can 'physically' disable the key?

---

### Post by lisati on 2010-04-18
I'm thinking that possibly your computer's BIOS is picking up on some problem that warrants your attention but isn't serious enough to warrant halting your system. It might be possible to set your computer to display the kind of diagnostic messages that these days are hidden by the manufacturer's splash screen.

---

### Post by jondodson on 2010-04-18
Maybe you have a paperclip or staple stuck in your keyboard.  Try turning it upside down and giving it a good shake, rattle and roll.

---

