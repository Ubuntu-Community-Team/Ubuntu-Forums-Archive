---
title: "Empathy sip: Worst sip phone ever!"
date: 2009-11-05
forum: General Help
---

### Post by Isaacgallegos on 2009-11-05
Here's my routine, if I want to receive calls: 
1. Go into my accounts and DISABLE my SIP account. (xxxx@proxy01.sipphone.com)
2. Then enable it. 
3. [-o< pray to the Gizmo/Empathy/Ubuntu gods that it's now connected.
4. If I'm not convinced it worked disable and enable again. 

The audio is clear and I like that. But common! Do I really have to reconnect EVERY... DAMN... TIME!? :mad::mad::mad::mad::mad::mad:

I've even tried entering in the STUN address manually and it's the same thing. 

TO THE PROGRAMMERS: JUST MAKE IT RECONNECT AFTER EVERY CALL. OMG! EASY FIX. ):P

---

### Post by hanzj on 2010-05-18
do you still have this problem (if you are) in Ubuntu 10.04?

---

### Post by gu'an on 2010-05-24
I have been doing this since ubuntu switched to empathy in its previous version and I continue to do it with 10.04 LTS too!
And for the last few days, it is even worse - only like 1 out of 10 such routines end in a successful connection!

(BTW, I am using sip.justvoip.com)

---

### Post by Isaacgallegos on 2010-05-28
Sorry for leaving this post unanswered. 

10.04 rocks!!! It kicks butt. My mini10v runs like a supercomputer and puts my friends big Win7 rigs to shame. So why the heck did they include the worst, most incomplete, chat application ever invented? What were they thinking? You STILL CAN'T BLOCK USERS in AIM chat or any other chat platform! It's not even clear how to add plug-ins to this turd. Did they pay Ubuntu to include them? It's the most terrible thing you could add to such a great distro. It's a smudge on, what I consider, the Ferrari of Ubunutu  distros. And, it's not easy to remove; they went out of their way to make it harder to remove /rant

Pidgin for chat. (You can block users... and there's a clear way to use plug-ins)  

I gathered the cash and got skype for internet calls. It really isn't too expensive if you pay for a whole year in advance...  

I hope Google voice comes out with their desktop app soon. I hear they're already testing the desktop voice app internally, which will eliminate my need to pay for Skype. When my skype subscription runs out, I will just stick with something free until google voice's desktop app makes it's release. :guitar:

---

### Post by marshmallow1304 on 2010-05-28
> **Isaacgallegos said:**
> And, it's not easy to remove; they went out of their way to make it harder to remove

:confused::confused::confused:
```
sudo apt-get --purge remove empathy empathy-common && sudo apt-get --purge autoremove
```

---

### Post by Isaacgallegos on 2010-05-29
> **marshmallow1304 said:**
> :confused::confused::confused:
```
sudo apt-get --purge remove empathy empathy-common && sudo apt-get --purge autoremove
```

So, I run this code in the terminal and it turns out I had missed parts of Empathy. Wow. This means you can't even use the software center to remove all of this terrible program. You must resort to the terminal. 

It's funny, when I first tried to remove Empathy (the unfinished chat program) it was somehow still logging on in the background. "How the f....!?!" So, I dug around further in the software center looking for other parts to remove, but couldn't find any. I ended up having to change passwords to defeat Empathy and keep it from logging on. 

The writers of empathy must find it hilarious to watch Linux noobs struggle with stuff like this. I consider it, almost, a borderline malicious act on their part.

---

### Post by gu'an on 2010-06-06
I agree - this empathy is really annoying to the core! (esp with sip)

---

