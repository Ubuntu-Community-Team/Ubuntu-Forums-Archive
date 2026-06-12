---
title: "Forgot password"
date: 2011-07-11
forum: General Help
---

### Post by euclid17 on 2011-07-11
In my ubuntu system, it states I have new updates to download. Trying to download them it states that i dont have enough memory and to delete some stuff to make room. I hit the link to do so and it asks my password. I swear I know my password, but its saying "invalid password". (no it's not the shift key on) I looked up ways to try to set/change password and I find answers that say get to "root" by holding shift key or hit "esc" while booting, etc. That doesnt seem to get me to where they say it should take me. I do see hit 2 for setup and 0 for boot menu while rebooting. All the things I just mentioned get me to a prompt of: "MBR"
 
No matter what key I hit after that, it just continues a regular boot. (and I try all over again)
 
One more thing, to clean off data it says to use "sudo apt-get clean"  No clue what that means or how to use it.
 
FRUSTRATED!!!!!!
 
HELP!!!!!

---

### Post by macaholic on 2011-07-11
Have you tried [this]("http://www.psychocats.net/ubuntu/resetpassword") guide?

---

### Post by euclid17 on 2011-07-11
Yes, as I stated in my post I tried the "shift" ket method as the link states.  
 
Regardless, I believe i screwed things up worse.  I finally was able to get into the setup pages and saw some spots where is said passwords were not enterred.
 
 
 
Now I get a prompt Enter Password when booting up.  Upon enterring it, I get a prompt for Enter HDD Password, I enter it.  Then.....
 
MBR comes up for 1 sec, then I get this (quote):
 
"[Minimal BASH-like line editing is supported.  For the first word, TAB lists possible command completions.  Anywhere else TAB lists the possible completions of a device/filename.]"
 
And then a prompt,
 
grub>
 
Nothing I do at this point brings my system up.  Am I totally hosed now?
 
I did try and go back into the boot setup, but it seems I cannot undo what I did.

---

### Post by macaholic on 2011-07-14
You can try to fix GRUB using something like [this.]("http://ubuntuforums.org/showpost.php?p=10871917&postcount=1")

---

### Post by oldos2er on 2011-07-14
> **euclid17 said:**
> Now I get a prompt Enter Password when booting up.  Upon enterring it, I get a prompt for Enter HDD Password, I enter it.  Then.....
 
MBR comes up for 1 sec, then I get this (quote):
 
"[Minimal BASH-like line editing is supported.  For the first word, TAB lists possible command completions.  Anywhere else TAB lists the possible completions of a device/filename.]"
 
And then a prompt,
 
grub>

Sounds like BIOS passwords are your problem, since no OS has loaded yet if you're seeing the grub> prompt.

Try googling your motherboard and BIOS manufacturer on how to reset its password.

---

