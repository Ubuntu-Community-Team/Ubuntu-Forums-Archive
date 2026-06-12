---
title: "Auto-login still prompting Keyring password"
date: 2010-05-26
forum: General Help
---

### Post by kyleabaker on 2010-05-26
I've been using Ubuntu 10.04 since Alpha 2 and have since then continued to be prompted on auto-login to enter my Keyring password.

I've tried what few suggested solutions that I could, but have had no success in suppressing this prompt.

The prompt is triggered (I think) from auto-starting Gwibber.

I tried digging through all of the admin options and preferences that I could find that were remotely related and still have no solution.

Has anyone seen or know of a fix for this that works? It's only a minor annoyance, but I would love to figure out how to eliminate it.

Thanks in advanced.

---

### Post by mhgsys on 2010-05-26
I guess it's network-manager asking for your password;

right click the wifi/network applet-> edit connections

Select the connection you want to use.

Click Edit;

and select available to all users.

---

### Post by kyleabaker on 2010-05-26
> **mhgsys said:**
> I guess it's network-manager asking for your password;

right click the wifi/network applet-> edit connections

Select the connection you want to use.

Click Edit;

and select available to all users.
I tried that already with no luck. Is there any way for me to find out when the prompt is visible what it is unlocking?

I thought it was for Gwibber and my accounts, but I could be mistaken.

---

### Post by PRC09 on 2010-05-26
Look under applications > Accessories > Passwords and Encryption Keys.It should open another screen, highlight passwords,right click and select select change password.Enter your current password and leave the new one blank and agree for unsafe storage. That should solve the problem....

---

### Post by kyleabaker on 2010-05-26
> **PRC09 said:**
> Look under applications > Accessories > Passwords and Encryption Keys.It should open another screen, highlight passwords,right click and select select change password.Enter your current password and leave the new one blank and agree for unsafe storage. That should solve the problem....
Thanks, that seems to have solved the problem. Too bad there isn't a more secure way to solve this, but that will do just fine for now. :D

---

### Post by bodhi.zazen on 2010-05-26
> **kyleabaker said:**
> Thanks, that seems to have solved the problem. Too bad there isn't a more secure way to solve this, but that will do just fine for now. :D

Honestly , I LOL when I read this. You have just finished disabling a security feature and you want a more secure way to "solve this" ?

---

### Post by kyleabaker on 2010-05-26
> **bodhi.zazen said:**
> Honestly , I LOL when I read this. You have just finished disabling a security feature and you want a more secure way to "solve this" ?
Auto-login shouldn't prompt like this, otherwise its a step backward. I don't want to completely disarm the keyring, but there should be a way to get it to sign into gwibber on auto-login without extra steps. Would you not agree with that?

I don't have to go out of my way in Mac or Windows XP/Vista/7 to have messengers and such auto-start without prompting me for a password everytime. ;)

---

### Post by bodhi.zazen on 2010-05-26
> **kyleabaker said:**
> Auto-login shouldn't prompt like this, otherwise its a step backward. I don't want to completely disarm the keyring, but there should be a way to get it to sign into gwibber on auto-login without extra steps. Would you not agree with that?

No, I am more paranoid then that. 

To start I would never enable automatic log in.

Second, I almost never do a default installation of Ubuntu (or any distro really), I do a minimal install and build up. I do not typically install seahorse or any of these keyring applications.

If I did use a keyring, the data it stored would be way too sensitive to automatically unlock.

> I don't have to go out of my way in Mac or Windows XP/Vista/7 to have messengers and such auto-start without prompting me for a password everytime. ;)Did you ever stop to consider, perhaps this is part of the reason Mac and Windows are more readily cracked then Ubuntu ?

[http://www.theregister.co.uk/2008/03/29/ubuntu_left_standing/](http://www.theregister.co.uk/2008/03/29/ubuntu_left_standing/)

Security is a trade off with ease of use.

Personally it does not bother me in the least to have to enter a password.

I am worse on a mobile device (netbook or laptop) - password protect Gurb, full encryption, encrypted home

You get the idea, but understand I feel I have data to protect, certainly not everyone needs the same level of security.

You can not have your cake and eat it too, there is not a secure way to disable security features and your behavior leaves you more vulnerable. Now that may be your choice, but, no I would not do want to emulate your behaviors.

---

### Post by kyleabaker on 2010-05-26
> **bodhi.zazen said:**
> No, I am more paranoid then that. 

To start I would never enable automatic log in.

Second, I almost never do a default installation of Ubuntu (or any distro really), I do a minimal install and build up. I do not typically install seahorse or any of these keyring applications.

If I did use a keyring, the data it stored would be way too sensitive to automatically unlock.

Did you ever stop to consider, perhaps this is part of the reason Mac and Windows are more readily cracked then Ubuntu ?

[http://www.theregister.co.uk/2008/03/29/ubuntu_left_standing/](http://www.theregister.co.uk/2008/03/29/ubuntu_left_standing/)

Security is a trade off with ease of use.

Personally it does not bother me in the least to have to enter a password.

I am worse on a mobile device (netbook or laptop) - password protect Gurb, full encryption, encrypted home

You get the idea, but understand I feel I have data to protect, certainly not everyone needs the same level of security.

You can not have your cake and eat it too, there is not a secure way to disable security features and your behavior leaves you more vulnerable. Now that may be your choice, but, no I would not do want to emulate your behaviors.

I think you miss my point, but since this is not a topic of debate and was intended rather to solve a problem I was having then I'll give you the ending arguement so this pointless debate can come to a close. ):P

---

