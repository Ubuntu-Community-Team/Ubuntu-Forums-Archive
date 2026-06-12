---
title: "How do I change my display manager?"
date: 2012-03-19
forum: General Help
---

### Post by coldjeanz on 2012-03-19
I am running 11.10 Unity and I installed SLiM (simple login manager) but I don't know how to run it. I don't want to delete the default one (lightDM?) I just want to use the new one I installed.

---

### Post by coldjeanz on 2012-03-19
Lol ok I really messed things up 

I typed this into terminal

"sudo dpkg-reconfigure slim"

and it brought me to a little thing that let me switch my default login manager to Slim so i figured everything went alright. I restarted my computer to test it out and now it just sits on the Ubuntu loading screen, unable to go to any login screen. I thought I had Slim installed correctly since it let me switch to it but I'm guessing something went wrong. Now I can't log in and I can't switch my display manager back to whatever it was before. I know there must be a way :confused:

---

### Post by pr3zident on 2012-03-20
> **coldjeanz said:**
> Lol ok I really messed things up 

I typed this into terminal

"sudo dpkg-reconfigure slim"

and it brought me to a little thing that let me switch my default login manager to Slim so i figured everything went alright. I restarted my computer to test it out and now it just sits on the Ubuntu loading screen, unable to go to any login screen. I thought I had Slim installed correctly since it let me switch to it but I'm guessing something went wrong. Now I can't log in and I can't switch my display manager back to whatever it was before. I know there must be a way :confused:

Are you unable to access the terminal using crtl + alt + f1 and login as root and uninstall slim ? if not try ...

---

### Post by coldjeanz on 2012-03-20
Ok I managed to do that, I entered in my name and then pw but all itdid was just produce a few lines of text that said welcome to ubuntu and some other stuff. It didn't actually log me in to my physical desktop

---

### Post by pr3zident on 2012-03-20
> **coldjeanz said:**
> Ok I managed to do that, I entered in my name and then pw but all itdid was just produce a few lines of text that said welcome to ubuntu and some other stuff. It didn't actually log me in to my physical desktop

i know that, you can use the terminal to uninstall slim and fix your settings for the login screen...

---

### Post by coldjeanz on 2012-03-20
yeah ok i got it. removed slim and then had to reconfigure default back to lightdm. 
 
guess i'll try to get slim working when i have time then.

---

### Post by pr3zident on 2012-03-20
> **coldjeanz said:**
> yeah ok i got it. removed slim and then had to reconfigure default back to lightdm. 
 
guess i'll try to get slim working when i have time then.

cool

---

