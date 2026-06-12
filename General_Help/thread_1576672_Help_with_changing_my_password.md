---
title: "Help with changing my password"
date: 2010-09-17
forum: General Help
---

### Post by calucifer on 2010-09-17
Hi, I'm running 10.0.4 and I'm having problems changing my user password

If I change it either using passwd or user admin, the next time I log in I get an .ICEauthority error followed by a nautilis error. followed by a failure to load any panels or anything else
I know this is caused in some way by gnome-keyring, but I cant fix it

This is what I have tried
Created a new user, rebooted logged in as this user and tried resetting passwd, followed by rebooting again, log in as my self - same error
Tried same procedure again, but this time used unix passwd instead of "Users and Groups"

Tried removing ~/.gnome2/keyrings/login.keyring & rebooting, and same procedure as above having first removed the keyring.

Tried all the above, but this time while standing on one leg humming Frank Sinatra songs :D

How can I reset my passwd?

My System
Ubuntu 10.0.4 32bit (latest patch level)
Default (gnome) desktop

---

### Post by hayashi on 2010-09-17
> **calucifer said:**
> Hi, I'm running 10.0.4 and I'm having problems changing my user password

If I change it either using passwd or user admin, the next time I log in I get an .ICEauthority error followed by a nautilis error. followed by a failure to load any panels or anything else
I know this is caused in some way by gnome-keyring, but I cant fix it

This is what I have tried
Created a new user, rebooted logged in as this user and tried resetting passwd, followed by rebooting again, log in as my self - same error
Tried same procedure again, but this time used unix passwd instead of "Users and Groups"

Tried removing ~/.gnome2/keyrings/login.keyring & rebooting, and same procedure as above having first removed the keyring.

Tried all the above, but this time while standing on one leg humming Frank Sinatra songs :D

How can I reset my passwd?

My System
Ubuntu 10.0.4 32bit (latest patch level)
Default (gnome) desktop
Hello. You might find [ this]("http://www.psychocats.net/ubuntu/resetpassword") of use, although I'm not sure whether it will apply to your situation.

---

### Post by calucifer on 2010-09-17
> **hayashi said:**
> Hello. You might find [ this]("http://www.psychocats.net/ubuntu/resetpassword") of use, although I'm not sure whether it will apply to your situation.

I know my passwd, I can log in, I am logged in, I just cant change it!

I refuse to use emergency disk methods to reset the root passwd, to reset my passwd, when I already know it!!!!! :->

But thanks anyway

---

### Post by hayashi on 2010-09-17
> **calucifer said:**
> I know my passwd, I can log in, I am logged in, I just cant change it!

I refuse to use emergency disk methods to reset the root passwd, to reset my passwd, when I already know it!!!!! :->

But thanks anyway
No problem, I get that too.

Well, I hope you find your solution soon! :)

---

### Post by calucifer on 2010-09-18
I fixed it ,Damn I'm good :->
First, what the problem actually was
I would change my password, log out and back in , get 3 errors, first problem accessing .ICEauthority, then a nautilis error then some other error, followed by nada, nothing, my desktop would never load.
When I tried a console login, it told me it couldn't mount my encrypted home directory, which was a more useful error message. So I had to change that password as well. 
For good measure since I was there, I also changed my gnome-keyring password.

Ok, 3 step process
First change your gnome-keyring password 
Applications->Accessories->Passwords and Encryption Keys
On the Passwords tab you should see Passwords: login
Right click this and choose change password, change it to the new one

Second Step
Change your password
Command prompt -> tye passwd -> enter your current and a new one twice

Third step (this is the secret one that was causing all my .ICEauthority errors)
ecryptfs-rewrap-passphrase ~/.ecryptfs/wrapped-passphrase
It will prompt for your current and a new password (only once, so no typos allowed)
That's it job done.

I should note you should be able to use System->Preferences->About me to change your password and all the others should change as well, but it would hang for me and fail to change the password.

My Sources and thanks go to
For the gnome-keyring - [Dave Hay]("http://planetlotus.org/profiles/dave-hay_57473")
For the ecryptfs-rewrap-passphrase - [Bodhi's blog]("http://bodhizazen.net/Tutorials/Ecryptfs/")

My Many thanks to both of them:guitar:

---

