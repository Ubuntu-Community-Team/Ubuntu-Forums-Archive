---
title: "installed ubuntu with no password option, and now it asks for a password"
date: 2012-01-23
forum: General Help
---

### Post by squirejons on 2012-01-23
ok, I installed the latest ubuntu on my new Asus eeebox which had some crippled version of linux called expressgate on it.

i installed ubuntu via a usb flash drive. I had to hit f8 during bootup and select the flash drive as bootup source.


the installl went fine.

during installation, it asked me to create a username, and so I created a user named randy and when it asked for a password I checked the radio button that said login without a password. The password box I left blank. then I finished the install.

It worked great.

then i went to sleep and when i woke up I was presented with a password login for my user randy. I tried typing in anything and I tried hitting enter on a blank text field.

no luck

I managed to get in on a guest login.
and yes I already tried restarting.
Same thing. I get a enter password prompt

how can I get back into the randy user login???

---

### Post by Basher101 on 2012-01-23
not sure how you managed to install without any password at all, ubuntu would never let me install without entering a password on the installer. If you haven't done any changes to the system you could simply re-install it with a password..

..unless someone knows a better solution. But re-installing will be the easiest way.

regards

---

### Post by philinux on 2012-01-23
> **Basher101 said:**
> not sure how you managed to install without any password at all, ubuntu would never let me install without entering a password on the installer. If you haven't done any changes to the system you could simply re-install it with a password..

..unless someone knows a better solution. But re-installing will be the easiest way.

regards

Re-installing is always the final option. To reset password see this.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by grahammechanical on 2012-01-23
For future reference, we always need to give a new install of Ubuntu a password. After installation we can set the system to log in automatically. In other words without a password but we will still need a password to do administrative tasks. Otherwise, any idiot with access to our computers will be able to mess around with it.

Regards.

---

### Post by squirejons on 2012-01-23
> **Basher101 said:**
> not sure how you managed to install without any password at all, ubuntu would never let me install without entering a password on the installer. 

regards

why and how do you think the 'install without a password' option button got into the install software? Trust me, that option button was there for me. I did not hallucinate it. So therefore it would be there for you, too.

Software does not change for any particular person. Code is code.

---

### Post by squirejons on 2012-01-23
> **grahammechanical said:**
> For future reference, we always need to give a new install of Ubuntu a password. After installation we can set the system to log in automatically. In other words without a password but we will still need a password to do administrative tasks. Otherwise, any idiot with access to our computers will be able to mess around with it.

Regards.

i was not trying to do admin.

i was just trying to get into the os

---

### Post by ubume2 on 2012-01-23
> **philinux said:**
> Re-installing is always the final option. To reset password see this.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

This is the proper way. I don't remember, though, whether it asks for your old password.  I have had mixed success with that.

EDIT: Thanks gsgleason post 8. I didn't read all the posts thoroughly.:oops:

---

### Post by gsgleason on 2012-01-23
If root uses passwd, it will not ask for the current passwd.  Root can explicitly set other users passwords.

---

### Post by squirejons on 2012-01-23
> **gsgleason said:**
> If root uses passwd, it will not ask for the current passwd.  Root can explicitly set other users passwords.
'



what does that mean in practical terms?

---

### Post by ubume2 on 2012-01-23
> **squirejons said:**
> 'what does that mean in practical terms?

I think it means that you can now set a password. When you reboot and enter that password, you should get to the desktop.  Then you can chose to boot into Ubuntu without that password.:)

---

