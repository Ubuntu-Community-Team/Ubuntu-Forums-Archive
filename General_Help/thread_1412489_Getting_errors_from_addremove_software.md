---
title: "Getting errors from add/remove software"
date: 2010-02-21
forum: General Help
---

### Post by And1945 on 2010-02-21
I am having some trouble installing from both the now legacy "add/remove applications" and the ubuntu software center.

The add/remove applications gives me an error,
The ubuntu software center, does not. It just stalls, and takes forever at doing, what I can imagine, nothing. It does however most of the times install what i am asking it to do.

What might cause this? I am having some trouble sometimes at connecting to repositories.

EDIT:
Oh yeah, ubuntu software center, just does not let me click install...

---

### Post by Swagman on 2010-02-21
sounds like an internet connection problem

---

### Post by And1945 on 2010-02-21
I would think so to, but my internet is fine.

Might want to reboot my router.

---

### Post by mcduck on 2010-02-21
try running "sudo apt-get update" in a terminal to see if you can get any connection to the repositories.

---

### Post by nos09 on 2010-02-21
did you tried adding application from synaptic ??

---

### Post by And1945 on 2010-02-21
I did all that. Could it be because I am connected to my internet from both cabled and wireless? Hard to memorize since my nm-applet keep disappearing.

---

### Post by mcduck on 2010-02-21
> **And1945 said:**
> I did all that. Could it be because I am connected to my internet from both cabled and wireless? Hard to memorize since my nm-applet keep disappearing.

wel, if you did the "sudo apt-get update", did it work, or if it didn't what errors you got?

(and no, switching between wired and wireless connection shouldn't be a problem, I do that all the time..)

---

### Post by Swagman on 2010-02-21
If you have synaptic and software centre open at the same time it'll b0rk

---

### Post by And1945 on 2010-02-21
> **mcduck said:**
> wel, if you did the "sudo apt-get update", did it work, or if it didn't what errors you got?

(and no, switching between wired and wireless connection shouldn't be a problem, I do that all the time..)

I am not switching. Well... sudo apt-get update works. I just tested it again. It gives me the following tags: Ign, Hit, Get.

> **Swagman said:**
> If you have synaptic and software centre open at the same time it'll b0rk

I know that. If synaptic is open nothing else requiring apt doesnt work.

---

### Post by nos09 on 2010-02-21
and what happens when you use synaptic ?
any error --
give details or try to post images. if you can. that'll help mere.

---

### Post by And1945 on 2010-02-21
> **nos09 said:**
> and what happens when you use synaptic ?
any error --
give details or try to post images. if you can. that'll help mere.

Ubuntu software center, does not work. Wont let me press the install button.
Add/remove apllication, does not work. Gives me an error. I have posted the screenshot at the start of this thread.
Terminal sudo apt-get works.
Synaptic works.

---

### Post by nos09 on 2010-02-21
> **And1945 said:**
> Ubuntu software center, does not work. Wont let me press the install button.
Add/remove apllication, does not work. Gives me an error. I have posted the screenshot at the start of this thread.
Terminal sudo apt-get works.
Synaptic works.

ok here is the thing ,

what i meant by posting image was image of synaptic and image you posted was SC. nevermind.

 you are luck that synaptic is running. 

remove the ubuntu software center from synaptic and then reinstall it.

see if that works..

---

### Post by And1945 on 2010-02-21
> **nos09 said:**
> 
remove the ubuntu software center from synaptic and then reinstall it.

see if that works..

It does not.

---

### Post by nos09 on 2010-02-21
> **And1945 said:**
> It does not.

what did you do ?
did u removed SC ?

---

### Post by And1945 on 2010-02-21
> **nos09 said:**
> what did you do ?
did u removed SC ?

I clicked "Completely remove" and then install. On ubuntu software center. aka software-center in the synaptic.

EDIT:

I tried "show screenshot" from the synaptic. That stalled completely. Could there be a link?

---

### Post by nos09 on 2010-02-21
> **And1945 said:**
> I clicked "Completely remove" and then install. On ubuntu software center. aka software-center in the synaptic.


i googled out for replacement of SC but no luck.
ok looks like your having big problem. report the bug. and wait till they fix it.
and mean while you can use synaptic. and apt-get to install software.

---

### Post by And1945 on 2010-02-21
> **nos09 said:**
> i googled out for replacement of SC but no luck.
ok looks like your having big problem. report the bug. and wait till they fix it.
and mean while you can use synaptic. and apt-get to install software.
I will, thank you for your efforts.

---

### Post by nos09 on 2010-02-21
> **And1945 said:**
> I will, thank you for your efforts.

its ok thats why we are here.
remember to report the bug. it can help somany other people too who are facing similar problem. and keep posting new threads..:)

---

### Post by And1945 on 2010-02-21
> **nos09 said:**
> its ok thats why we are here.
remember to report the bug. it can help somany other people too who are facing similar problem. and keep posting new threads..:)

It had a bug that applied to my problem. So I just clicked "affects me".

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/489519](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/489519)

---

