---
title: "Locked out Ubuntu"
date: 2011-05-09
forum: General Help
---

### Post by gmolivier on 2011-05-09
Frustrated with ubuntu v11, i re-installed v10.
At first my old authetication password worked.  Then it stopped working and i can't make any changes because i don't know what word the blasted system wants.  Am i locked out forever?  Should i re-re-install v10 and everything else?

or

Can anyone tell me how i can change my authentication password without knowing what the computer wants?

I'm a novice, please be clear with your answers.

---

### Post by WorMzy on 2011-05-09
Have you forgotten *your* password, or is the pop-up authentication window not accepting it? There is no separate authentication password (unless you set one).

If the pop-up is rejecting your password, then you may have it set to su mode instead of sudo. Press Alt+F2 and run
```
gksu-properties
```
and make sure that "Authentication mode" is set to "sudo".

Also, the current version of Ubuntu is version 14, not 11. The name "11.04" just means that it was released in April (04) of 20_11_.

---

### Post by gmolivier on 2011-05-09
> **WorMzy said:**
> Have you forgotten *your* password, or is the pop-up authentication window not accepting it? There is no separate authentication password (unless you set one).

If the pop-up is rejecting your password, then you may have it set to su mode instead of sudo. Press Alt+F2 and run
```
gksu-properties
```
and make sure that "Authentication mode" is set to "sudo".

Also, the current version of Ubuntu is version 14, not 11. The name "11.04" just means that it was released in April (04) of 20_11_.
Thanks, i'll try that.
I have to re-boot to get ubuntu started again.  
Re: versions....so confusing. I thought it was "v11" and i re-installed "v10"...don't like the newest version... not at all good.

I kept my password from earlier installations and it seemed to work at first.   I'm the only one who uses this computer and don't want a hassel getting in.

I just did as you said above.  My old password still doesn't work.  Do i need to re-set it?  How?

---

### Post by WorMzy on 2011-05-09
How do you log in, is it automatic?

Can you use sudo at all? Open a terminal (Applications -> Accessories -> Terminal) and run

```
sudo echo "I can use sudo"
```
then enter your password when prompted. Does it accept your password then?

---

### Post by gmolivier on 2011-05-09
> **WorMzy said:**
> How do you log in, is it automatic?

Can you use sudo at all? Open a terminal (Applications -> Accessories -> Terminal) and run

```
sudo echo "I can use sudo"
```
then enter your password when prompted. Does it accept your password then?
Sorry, not working.

The terminal window has the following:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

gmo@gmo-desktop:-$ sudo echo "I can use sudo"

((gmo is me))

[sudo] password for gmo:

((but it still doesn't accept my password.  Is there any way i can simply change the password that the computer will accept?

I appreciate your time and effort)))

---

### Post by ajgreeny on 2011-05-09
If it is just your user password that does not work try this:  [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

If that does not work, and I assume recovery mode does still work, can we see your /etc/sudoers file, from recovery mode please with command ```
cat /etc/sudoers
```as it may be that you have been locked out of using sudo.

If an edit of your current file is needed you can do it using ```
visudo
```from recovery mode, but let's see it first.

---

### Post by gmolivier on 2011-05-09
Typing your first line in terminal, i get: 

cat: /etc/sudoers: No such file or directory

Typing visudo, i get:

visudo: /etc/sudoers: Permission denied

Btw: ubuntu is running right now, i can check email and surf Firefox....but, it suddenly just dims black  and wants a password to do any thing else.  As bad as the last version of Ubuntu is, this is somewhat worse.

---

### Post by WorMzy on 2011-05-09
That.. can't be right. sudo would through a right wobbler if /etc/sudoers didn't exist. It wouldn't even ask you for your password, it'd just sit there and sulk about not being able to find it.

Did you boot into recovery mode first? You shouldn't get a permission denied error from recovery mode.

---

### Post by ajgreeny on 2011-05-09
> **gmolivier said:**
> Typing your first line in terminal, i get: 

cat: /etc/sudoers: No such file or directory

Typing visudo, i get:

visudo: /etc/sudoers: Permission denied

Btw: ubuntu is running right now, i can check email and surf Firefox....but, it suddenly just dims black  and wants a password to do any thing else.  As bad as the last version of Ubuntu is, this is somewhat worse.
Is this from recovery mode?

If you are doing it from your user you will normally need to use sudo, but as your problem is not being able to use sudo, I suggested you go into recovery mode to run the code.

---

### Post by gmolivier on 2011-05-09
Thanks for your help, i'm going to re-install v10 (if that's what it is)...it worked fine before i upgraded to v14.

gmo

---

