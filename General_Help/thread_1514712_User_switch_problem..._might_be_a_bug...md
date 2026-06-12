---
title: "User switch problem... might be a bug.."
date: 2010-06-21
forum: General Help
---

### Post by rahilm on 2010-06-21
There are two issues I have been facing:
1)
So I have created two accounts on my ubuntu desktop. One for me and one generic guest type. I was busy surfing the web and was waiting for a video to load, then my brother comes and says he has some data to transfer to his pen drive. 
I decided to check the new account and how this thing works. I select the account from the 'fast user switcher' applet. It loads fine, everything is done. After his work is done, i logged out from the same menu. It logged out, but a little differently. The screen went blank and I saw some lines written as programs were loading (these things occur if i kill X).
So i patiently waited for the login screen to appear. To my surprise, it showed i hadn't logged in and I had to login again. Everything was gone and i had to  do everything all over again.
But after some time I realised the sound wasn't working. I tried increasing volume but the volume applet had greyed out and I had to restart the computer to make it work.
Apparently, X gets killed if i switch user. And sound driver also shuts off.

Is it a bug? because it can't be a driver issue. I use intel graphics which work out-of-the-box.

I am really confused, should I delete the other account? Else, there is no meaning to it.. Previously, everyone used windows to do these kind of stuff, where i had to restart the machine. I made the account so i can fast switch...


2)
I have been facing this problem since a long time. I had posted something about it but they moved it to community cafe. What happens is, when I am downloading something, i usually lock the screen and go out. My little brother comes and finds the screen locked. Theoretically, he can't do anything (that's what i thought). He restarted the machine. When I asked how he did it. He said there was an option there. I figure out where that option is in about 2 minutes. 
When the screen is locked, you click "Switch User". Then it goes to the login screen with the restart option at the bottom, which surprisingly doesn't ask for a password and reboots.

Is it meant to be that way? Is there a way to prevent it? Is my understanding of the term "Lock Screen" incorrect?

Any help is appreciated.

---

### Post by Pollox on 2010-06-21
As to your second question, even if locking the screen prevented someone from restarting the computer, they could still shut it down by pulling the power or holding down the power button.  If someone has physical access to the computer, you can't prevent this.  The one problem with this is that restarting vs shutting down allows you to not have to enter the poweron password (if you have that option enabled in your BIOS), but you could put a password on grub.  In short, you can't stop someone who can touch your computer from shutting it down, only from using it.

Also, note that Ubuntu comes with a built-in option for someone to log in as a Guest without needing to create an explicit guest account.

---

### Post by rahilm on 2010-06-22
> **Pollox said:**
> 
Also, note that Ubuntu comes with a built-in option for someone to log in as a Guest without needing to create an explicit guest account.

That behaves in the same manner too. In fact, I used that before I created a new account because it wasn't working while switching back.

---

### Post by rahilm on 2010-06-24
So I have done some testing and ended up on the following observations regarding problem 1...(problem 2 can be ignored...i don't care now)

Apparently, I was wrong.
If I 'switch user' instead of logging out of the new account, only my account gets logged out automatically, sort of crashes. The new account stays logged in.
This only happens once every boot. Means that once it has happened, i can use user switcher normally without problems until next boot.

Solutions??

---

### Post by rahilm on 2010-08-01
UPDATE:
The latest kernel update solved the problem..
but now I hav a new problem..
when i log into my account.. the pointer icon does not display. although i can point and click but there is no pointer icon.
to restore normal.. i switch to virtual console and switch back.

---

### Post by rahilm on 2010-08-06
A newer kernel update restored the original problem..
:(

---

### Post by rahilm on 2010-08-07
bump..

---

