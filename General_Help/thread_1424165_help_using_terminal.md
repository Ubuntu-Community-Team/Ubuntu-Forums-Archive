---
title: "help using terminal"
date: 2010-03-07
forum: General Help
---

### Post by hellsing56 on 2010-03-07
I recently installed Unbuntu because I am sick of my windows crashing every 3 months (yes, literally EVERY 3 months) I know nothing about source code or programming...

I am trying to install the repository for Cinelerra using the terminal. I did exactly as the cinelerra website said and entered the following code:

```
echo deb http://akirad.cinelerra.org akirad-karmic main | sudo tee /etc/apt/sources.list.d/akirad.list && wget -q http://akirad.cinelerra.org/dists/akirad.key -O- | sudo apt-key add - && sudo apt-get update
```However, the terminal then says "[sudo] password for cody: " but no matter what I do, I cannot enter my password. It just will not type past this point... what do I do to enter my password?


And it seems to do this anytime I try using terminal for anything.

---

### Post by dakoellis on 2010-03-07
> **hellsing56 said:**
> I recently installed Unbuntu because I am sick of my windows crashing every 3 months (yes, literally EVERY 3 months) I know nothing about source code or programming...

I am trying to install the repository for Cinelerra using the terminal. I did exactly as the cinelerra website said and entered the following code:

```
echo deb http://akirad.cinelerra.org akirad-karmic main | sudo tee /etc/apt/sources.list.d/akirad.list && wget -q http://akirad.cinelerra.org/dists/akirad.key -O- | sudo apt-key add - && sudo apt-get update
```However, the terminal then says "[sudo] password for cody: " but no matter what I do, I cannot enter my password. It just will not type past this point... what do I do to enter my password?


And it seems to do this anytime I try using terminal for anything.

the cursor does not move when you type passwords into terminal to help hide keystrokes.  just type the password and press enter and it will work

---

### Post by hellsing56 on 2010-03-07
thanks. it worked.

---

