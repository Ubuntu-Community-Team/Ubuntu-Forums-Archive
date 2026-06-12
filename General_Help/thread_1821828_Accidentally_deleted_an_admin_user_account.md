---
title: "Accidentally deleted an admin user account"
date: 2011-08-09
forum: General Help
---

### Post by AI52487963 on 2011-08-09
I had two accounts. One was an admin and I set the other as an admin as well, but left it without a password since I wanted the new user to enter it themselves. I went into the new admin account and deleted the old, passworded one. 

However, this new account doesn't have a password that I explicitly defined on it. How do I change that? The account is the only one and still 'disabled'.

---

### Post by haqking on 2011-08-09
> **AI52487963 said:**
> I had two accounts. One was an admin and I set the other as an admin as well, but left it without a password since I wanted the new user to enter it themselves. I went into the new admin account and deleted the old, passworded one. 

However, this new account doesn't have a password that I explicitly defined on it. How do I change that? The account is the only one and still 'disabled'.

perhaps i am misunderstanding you.

YOu said you deleted the account with a password on it.

Then you say you are left with an admin account that you explicitly defined a password for...and the account is disabled ?

Sorry but i dont understand ? perhaps i am being a moron

---

### Post by AI52487963 on 2011-08-09
> **haqking said:**
> perhaps i am misunderstanding you.

YOu said you deleted the account with a password on it.

Then you say you are left with an admin account that you explicitly defined a password for...and the account is disabled ?

Sorry but i dont understand ? perhaps i am being a moron


Sorry, my passworded account was the one that was deleted. I set up a non-passworded one, switched to that, deleted the other one and and now left with an account whose password is totally unknown to me.

---

### Post by haqking on 2011-08-09
> **AI52487963 said:**
> Sorry, my passworded account was the one that was deleted. I set up a non-passworded one, switched to that, deleted the other one and and now left with an account whose password is totally unknown to me.

again i am confused.

You deleted one account i understand.  But you said there is an account without a password ?

what account is the one with a password unknown to you ?

---

### Post by AI52487963 on 2011-08-09
> **haqking said:**
> again i am confused.

You deleted one account i understand.  But you said there is an account without a password ?

what account is the one with a password unknown to you ?

The one I'm left with has an unknown password.

---

### Post by ajgreeny on 2011-08-09
I think you should be able to set a password with this link
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
though it is normally used when someone forgets their password, not if one is not set in the first place.

How did you manage to do that; not set a password; I didn't realise it was possible.

---

### Post by haqking on 2011-08-09
> **ajgreeny said:**
> I think you should be able to set a password with this link
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
though it is normally used when someone forgets their password, not if one is not set in the first place.

How did you manage to do that; not set a password; I didn't realise it was possible.


i was going to supply that link but i was skeptical of activity ;-)

I still cant make sense of it to be honest but it is late

you switched to the non-passworded one to delete the other one....now you have an account with an unknown password ? im still confused

---

### Post by AI52487963 on 2011-08-09
> **haqking said:**
> i was going to supply that link but i was skeptical of activity ;-)

I still cant make sense of it to be honest but it is late

you switched to the non-passworded one to delete the other one....now you have an account with an unknown password ? im still confused


Yeah I don't really know why Ubuntu would allow me to do it, honestly. I'm prepping an old computer to be sold off and I wanted to create a new user profile for the guy who bought it. I figured I'd set it up without a password so they could just log in straight away, but I was playing around on the windows side all day and forgot that you actually use the sudo password for, like, stuff.

So I took my user account, Scott, which had admin privileges, etc, and created another one, User, for whoever's gonna buy it. I deliberately didn't set a password for User so the guy who just bought it wouldn't freak out coming to a login screen and didn't know what the password was to a computer he just bought.

I cleaned out the Scott profile from all my data, logged out, logged in as User and deleted my Scott account. The User profile has admin privileges, but no password that I know of. I can't use sudo, since it prompts for a password I'm oblivious to. 


The psychocats link worked like a charm, though, thanks guys! :o

---

### Post by haqking on 2011-08-09
> **AI52487963 said:**
> Yeah I don't really know why Ubuntu would allow me to do it, honestly. I'm prepping an old computer to be sold off and I wanted to create a new user profile for the guy who bought it. I figured I'd set it up without a password so they could just log in straight away, but I was playing around on the windows side all day and forgot that you actually use the sudo password for, like, stuff.

So I took my user account, Scott, which had admin privileges, etc, and created another one, User, for whoever's gonna buy it. I deliberately didn't set a password for User so the guy who just bought it wouldn't freak out coming to a login screen and didn't know what the password was to a computer he just bought.

I cleaned out the Scott profile from all my data, logged out, logged in as User and deleted my Scott account. The User profile has admin privileges, but no password that I know of. I can't use sudo, since it prompts for a password I'm oblivious to. 


The psychocats link worked like a charm, though, thanks guys! :o

well if the user is admin how did you create the account with a blank password ? if the user is not admin then you couldnt delete the scott account ?

when it prompts for a sudo password then if truly is blank then you just pres enter at prompt if it is blank but i still cant understand it....LOL

oh well sounds like psychocats had your answer

---

### Post by oliveroj on 2011-11-15
> **ajgreeny said:**
> I think you should be able to set a password with this link
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
though it is normally used when someone forgets their password, not if one is not set in the first place.

How did you manage to do that; not set a password; I didn't realise it was possible.
at ajgreeny or anyone that can help me!!!  I have been trying to change my password, and found the site you directed the other person to, but i don't get the window they show.  I am using a dual system with vista and ubuntu 10.11 and all I get is the windows manager prompted and then selecting ubuntu there is no option for recovery mode, so I am really stuck with not knowing what to do :(  also, I am very new (2 days) to trying ubuntu, and also didn't realize under guest, nothing is saved so i lose about 16 hours of work... and am not sure if they is anyway to recover it.

---

### Post by Cyclane on 2011-11-15
Boot to grub.
select recovery mode.
select something that's called like 'root terminal'
voila you're now root in a simple bash environment.
change the password with 
```
passwd USERNAME
```
USERNAME being the username of the admin account that is locked.


###EDIT
Oohh and if you want the next user to set a password the next time he uses is:
```
passwd -e USERNAME
```
This expires the account, forcing the user to change the password. (see man passwd)

---

### Post by Cyclane on 2011-11-15
I forgot, and as I already edited my post I didn't wanna edit it again.

Your account might be locked, use the following to unlock it (also in man pages):
```
passwd -u USERNAME
```

---

