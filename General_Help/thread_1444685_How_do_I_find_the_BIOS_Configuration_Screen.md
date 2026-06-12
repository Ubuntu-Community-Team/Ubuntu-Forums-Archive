---
title: "How do I find the BIOS Configuration Screen?"
date: 2010-04-01
forum: General Help
---

### Post by TDHicks on 2010-04-01
I'm having epic problems with my sound card and upon going through the Sound Troubleshooting, It says to activate my sound card through the BIOS Configuration Screen.  How on earth do I find that?

---

### Post by Pikestaff on 2010-04-01
That's one of those things you do before you boot up the OS.  Usually by pressing Esc or Del when you turn the computer on (it should tell you).

---

### Post by TDHicks on 2010-04-01
I forgot to mention I'm running 9.10 if that makes a difference

---

### Post by mocoloco on 2010-04-01
Sometimes it's F2 as well.

---

### Post by wbee on 2010-04-01
Hello,

First,get your owner's manual,or failing that,get online and go to the manufacuter's website and ask them for specifics.

That said,when you log on your computer,you will be given the opportunity to access the bios,usually by hitting the F2 key on the top line of the keyboard.

Once there,before you do anything else,read everything carefully. 

What you are looking for is getting to the listing for sound. 

In my instance,my motherboard(what is controlled by the bios) had on board sound,but I added a separate sound card. For it to work,I had to "disable" the on board sound.

**Let me say again,check your owner's manual or your manufacturer's web site. If it is still under warranty(the whole computer or just the motherboard),ask them to walk you through it.

Good luck.

---

### Post by Vaphell on 2010-04-01
> I forgot to mention I'm running 9.10 if that makes a difference

it doesn't, you access bios before the operating system even starts to boot up. Look for any info how to get to BIOS in the very first screen after power on. Regular motherboards for PC usually use some standard BIOS which shows hotkey combination on screen. Laptops often have that info obfuscated, but google knows the answer if you provide the model name.
Manual should contain that info too.

---

### Post by TDHicks on 2010-04-01
Do I press whatever button on the log on screen or when it says "GRUB Loading"
I'm a noob at this kind of stuff

---

### Post by TDHicks on 2010-04-01
I'll have a look for it.
This laptop is so old I'd be lucky to find valuable information on it, but I'll look

---

### Post by Jeffster999 on 2010-04-01
Turn your computer off 
Turn it back on and when the splash screen shows press F2 or F12 or Del or Esc 

you will see a messsageon the bottom of the screen that says 
"press "...." to enter bios

---

### Post by Pikestaff on 2010-04-01
> **TDHicks said:**
> Do I press whatever button on the log on screen or when it says "GRUB Loading"
I'm a noob at this kind of stuff

You'll want to press it before it gets to GRUB.

---

### Post by TDHicks on 2010-04-01
Thanks everyone.  I'll give that a shot.

---

### Post by TDHicks on 2010-04-01
Ok, so I restarted my computer and the splah screen just read "COMPAQ"
There was no other text on the screen

---

### Post by soryu on 2010-04-01
i have a compaq too press F8 or F10. it's one of those

press it as soon as the compaq logo comes up

---

### Post by TDHicks on 2010-04-01
> **soryu said:**
> i have a compaq too press F8 or F10. it's one of those

I'll try that too.  Thanks!

---

### Post by mocoloco on 2010-04-01
If you're not doing this already, it's a good idea to be repeatedly hitting the key maybe one or two seconds apart.  Try with each of the suggested keys in this thread.  If it gets to grub or beyond it didn't work so reboot and try again.  One of them should work.

---

### Post by TDHicks on 2010-04-01
This is the last bit of information that could affect this.
This is a Compaq Presario 2700 from (what I can imagine) about 10 years ago.
If that changes anything, how?  Again, I'm a noob at this...

---

### Post by Chesamo on 2010-04-01
I have a Presario 1800T (circa 1994), you're not alone.

The default key for me was F8. Hope that helps.

---

### Post by ajgreeny on 2010-04-01
The prompt for which key to hit may not mention **BIOS** at all.  My laptop says **"Press F2 to enter setup"** so look for something like that as well, usually right at the bottom of the makers splash screen, the one that just says "compaq" in big letters.

You could also run ```
sudo lshw >hw.txt
``` and search the hw.txt file now in your home for the word BIOS; this will tell you which BIOS the laptop has and you can then easily google for the access key.

---

### Post by Chesamo on 2010-04-01
EDIT fffffffffff didn't read post my bad.

---

### Post by NCLI on 2010-04-01
If nothing else works, reboot your computer, and as soon as the screen lights up, start tapping F1 through F12, and Delete + Esc, like mad. That should get you to the BIOS.

---

### Post by TDHicks on 2010-04-01
I tried hitting some of the recommended buttons you guys suggested and on "esc" and "F8" something new happened.
On, "esc" a small page of White text came up for a split second and then the regular boot cycle repeated.
For "F8" the same thing happened, but when the Ubuntu logo popped up, some white text showed up under the logo and it seemed to be loading something.
But still nothing.
Help D:

---

### Post by NCLI on 2010-04-01
> **TDHicks said:**
> I tried hitting some of the recommended buttons you guys suggested and on "esc" and "F8" something new happened.
On, "esc" a small page of White text came up for a split second and then the regular boot cycle repeated.
For "F8" the same thing happened, but when the Ubuntu logo popped up, some white text showed up under the logo and it seemed to be loading something.
But still nothing.
Help D:

If nothing else works, reboot your computer, and as soon as the screen lights up, start tapping F1 through F12, plus Delete & Esc, like mad. That should get you to the BIOS.

---

### Post by TDHicks on 2010-04-01
I don't know how it happened, but my sound now works!  Thanks everyone!

---

