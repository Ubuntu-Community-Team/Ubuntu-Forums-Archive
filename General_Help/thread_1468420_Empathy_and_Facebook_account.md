---
title: "Empathy and Facebook account"
date: 2010-05-01
forum: General Help
---

### Post by Thrasonic on 2010-05-01
Hi everyone.  I just did a clean install of Ubuntu 10.04.  I've never used Empathy before (I used Pidgin in Kubuntu 9.04) and I can't seem to get the Facebook account to authenticate.  I get an authentication failed message every time.  I've removed the account, recreated it, rebooted, etc. and nothing.  I am using my accounts name instead of my e-mail address, but I've tried both and neither is working.  I'm pretty much a newbie, especially in the Gnome interface, so I'm looking for some help with this.  Anything you all can offer will be greatly appreciated.

---

### Post by Thrasonic on 2010-05-01
Okay, all I needed to do I guess was log into Facebook through Firefox with my new account name instead of my e-mail address and then try connecting with the Empathy account.  That did the trick.

---

### Post by msambenny on 2010-05-01
actually in lucid lynx facebook asks you to create a badger or a username has anyone created a badger ??if so kindly tell me what that is...

---

### Post by mkrmec on 2010-05-05
It's not working for me. I've chosen the damn username and all it does is smacks me with an authentication failed thing.

Tried every variation of username besede the badger, passwords and facebook settings. I don't get it.. to me this is a bug in Empathy rather than something else.

---

### Post by nucleuskore on 2010-05-05
> **Thrasonic said:**
> Okay, all I needed to do I guess was log into Facebook through Firefox with my new account name instead of my e-mail address and then try connecting with the Empathy account.  That did the trick.

Thank you for your insight. I wish to confirm the above.
Somehow you need to maybe poke facebook and link the username to the login process.

All who have trouble logging in through empathy:
[list][*]Click on Applications->Accessories->Terminal[*]type **sudo apt-get update && sudo apt-get upgrade** and press ENTER. This will update your empathy.[*]**Logout of your desktop at the end of this process.**[*]Login to Ubuntu.[*]Open Firefox and Login to facebook website using your email address as usual.
[*]Click [*here*](http://www.facebook.com/username/) to set your "username" What does this mean? This means that you have to set a new username which is **not** the email id you use to login.
[*]Once you get this username, you should be able to access your facebook page by typing [www.facebook.com/yourusername](www.facebook.com/yourusername)
[*]**Logout of facebook**
[*]Login to facebook using your newly created username as the login name and your usual facebook password
[*]You should be able to login successfully
[*]Logout
[*]open empathy, press F4 and add a facebook chat account. In the username field, only fill out the newly created username, and in the password field fill out the usual facebook password.
[/list]

That should do it !

---

### Post by sagara on 2010-05-05
nucleuskore, thanks for the tip!
I was also struggling with this after my fresh lucid install.

It now works like a charm :D

---

### Post by jthirt on 2010-05-11
> **Thrasonic said:**
> Okay, all I needed to do I guess was log into Facebook through Firefox with my new account name instead of my e-mail address and then try connecting with the Empathy account.  That did the trick.

Thanks a lot for the tip!

Same for me. I was struggling with identification until I changed my login in the browser (Chrome in my case). So all you really need to do is Logout of Facebook in the browser, then Login again with the new account name.

Then I wasn't sure how to add contacts, but they are added automatically. I found out by displaying the disconnected contacts!    

That's cool! :)

JT

---

### Post by Mellon on 2010-05-23
thx :P

---

### Post by pavmav on 2010-05-24
Empathy still is searching and making the same error .. 
Ubuntu 10.04 64 bit is the OS 

I did that what u suggested a few times ... no effect

---

### Post by mrb260478 on 2010-08-22
Thanks

Manish B

---

### Post by tango_ninja on 2010-08-24
> **nucleuskore said:**
> Thank you for your insight. I wish to confirm the above.
Somehow you need to maybe poke facebook and link the username to the login process.

All who have trouble logging in through empathy:
[list][*]Click on Applications->Accessories->Terminal[*]type **sudo apt-get update && sudo apt-get upgrade** and press ENTER. This will update your empathy.[*]**Logout of your desktop at the end of this process.**[*]Login to Ubuntu.[*]Open Firefox and Login to facebook website using your email address as usual.
[*]Click [*here*](http://www.facebook.com/username/) to set your "username" What does this mean? This means that you have to set a new username which is **not** the email id you use to login.
[*]Once you get this username, you should be able to access your facebook page by typing [www.facebook.com/yourusername](www.facebook.com/yourusername)
[*]**Logout of facebook**
[*]Login to facebook using your newly created username as the login name and your usual facebook password
[*]You should be able to login successfully
[*]Logout
[*]open empathy, press F4 and add a facebook chat account. In the username field, only fill out the newly created username, and in the password field fill out the usual facebook password.
[/list]

That should do it !

This works for me also.... looks like the key is logging into facebook via browser with username instead of email.  This stumped me for a long time!

---

### Post by Baldrick_NZ on 2010-09-20
> **nucleuskore said:**
> Thank you for your insight. I wish to confirm the above.
Somehow you need to maybe poke facebook and link the username to the login process.

All who have trouble logging in through empathy:
[list][*]Click on Applications->Accessories->Terminal[*]type **sudo apt-get update && sudo apt-get upgrade** and press ENTER. This will update your empathy.[*]**Logout of your desktop at the end of this process.**[*]Login to Ubuntu.[*]Open Firefox and Login to facebook website using your email address as usual.
[*]Click [*here*](http://www.facebook.com/username/) to set your "username" What does this mean? This means that you have to set a new username which is **not** the email id you use to login.
[*]Once you get this username, you should be able to access your facebook page by typing [www.facebook.com/yourusername](www.facebook.com/yourusername)
[*]**Logout of facebook**
[*]Login to facebook using your newly created username as the login name and your usual facebook password
[*]You should be able to login successfully
[*]Logout
[*]open empathy, press F4 and add a facebook chat account. In the username field, only fill out the newly created username, and in the password field fill out the usual facebook password.
[/list]

That should do it !

Which is all fine and dandy up until facebook decide to f*ck around with you. I don't know how many times I have been to change my username, tried different combinations of my cellphone number (+64, etc..), only to find they don't support my provider. Then give it a number it does support in various combinations only to receive no sms activation code! 
Empathy could also live upto it's name and change their login to include either a username or email address. Sooo frustrating!! 

It's clear to me that logic doesn't necessarily apply in IT after all. Rant over.

---

### Post by xzinkx on 2010-10-06
Tried this many times word for word with no success, anyone got any other ideas?

---

### Post by ze3rax on 2010-10-06
Works great here ! Thanks, I'm new to Linux and haven't used such programs before.

xzinkx please, post me a link to your Facebook please.

---

### Post by niceguy123 on 2010-10-23
I am working with a new installation of Ubuntu 10.10 first time I've tried using Empathy. Facebook seems to be logged in. But, is not showing friends in the contact list. I do have gtalk friends on the list. Any ideas how to make the facebook friends show?

Thanks.

---

### Post by zer010 on 2010-10-29
I'm having the same problem. Did updates, logged in with my username, etc.. Still nothing. Yahoo account logs in fine. Any other ideas? Maybe FB is blocking 3rd party apps from accessing chat? Just guessing, but it sounds like something they would do....

---

### Post by solde9 on 2010-12-09
> **nucleuskore said:**
> Thank you for your insight. I wish to confirm the above.
Somehow you need to maybe poke facebook and link the username to the login process.

All who have trouble logging in through empathy:
[LIST]
[*]Click on Applications->Accessories->Terminal
[*]type **sudo apt-get update && sudo apt-get upgrade** and press ENTER. This will update your empathy.
[*]**Logout of your desktop at the end of this process.**
[*]Login to Ubuntu.
[*]Open Firefox and Login to facebook website using your email address as usual.
[*]Click [*here*]("http://www.facebook.com/username/") to set your "username" What does this mean? This means that you have to set a new username which is **not** the email id you use to login.
[*]Once you get this username, you should be able to access your facebook page by typing [www.facebook.com/yourusername]("http://www.facebook.com/yourusername")
[*]**Logout of facebook**
[*]Login to facebook using your newly created username as the login name and your usual facebook password
[*]You should be able to login successfully
[*]Logout
[*]open empathy, press F4 and add a facebook chat account. In the username field, only fill out the newly created username, and in the password field fill out the usual facebook password.
[/LIST]

That should do it !

That's work for me! I am using Fedora 14. Thank you :D

---

### Post by tango_ninja on 2011-02-09
The real key to these instructions is the log in to facebook with your username and **not your email address**.

Sometimes I log in to facebook with my email address.  Empathy then will not connect.

Sometimes I log in to facebook with my Google account (it connects automatically from a setting I chose a while back).  Empathy then will not connect.

So far the only solution I have found to these seemingly "random" (but now fully explainable) Empathy facebook blackouts is to go to [www.facebook.com](www.facebook.com), log out, log in again with your username and password and then try again in Empathy.  Works 100% of the time for me.

---

### Post by kwanylongy on 2011-10-13
This works for me! I am on Ubuntu 11.04. 
Thanks! :D

> **nucleuskore said:**
> Thank you for your insight. I wish to confirm the above.
Somehow you need to maybe poke facebook and link the username to the login process.

All who have trouble logging in through empathy:
[list][*]Click on Applications->Accessories->Terminal[*]type **sudo apt-get update && sudo apt-get upgrade** and press ENTER. This will update your empathy.[*]**Logout of your desktop at the end of this process.**[*]Login to Ubuntu.[*]Open Firefox and Login to facebook website using your email address as usual.
[*]Click [*here*](http://www.facebook.com/username/) to set your "username" What does this mean? This means that you have to set a new username which is **not** the email id you use to login.
[*]Once you get this username, you should be able to access your facebook page by typing [www.facebook.com/yourusername](www.facebook.com/yourusername)
[*]**Logout of facebook**
[*]Login to facebook using your newly created username as the login name and your usual facebook password
[*]You should be able to login successfully
[*]Logout
[*]open empathy, press F4 and add a facebook chat account. In the username field, only fill out the newly created username, and in the password field fill out the usual facebook password.
[/list]

That should do it !

---

