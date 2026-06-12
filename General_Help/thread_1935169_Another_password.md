---
title: "Another password"
date: 2012-03-03
forum: General Help
---

### Post by thebigbry on 2012-03-03
OK so I admit. I am a windows dummy.  

 I have been using Ubuntu 11.10 dual boot on my laptop for a while now and love it. But I am so sick of having to type a password, every time I click anything and everything. I finally went in and set password to none. Finally I can open my laptop and it just starts instead of having to log in.  (I tried just changing the password to 1. but it kept telling me too short) because I need my computer telling me what kind of security I need. 
Any way. Now I try to install something and it again asks me for password!  well I have tried leaving it blank, I tried my old password, I even tried 1 just in case it did take. Nothing. It doesn't even tell you it's wrong, it just does NOTHING!

 I rebooted and occasionally it will popup and tell me "keyring did not get my main unlock password please enter it" I entered my old password and it goes away. But still can't install anything, keeps asking for a non existent password.

 Help an idiot out please.

---

### Post by sffvba[e0rt on 2012-03-03
Use this [tutorial]("http://www.psychocats.net/ubuntu/resetpassword") (or any other of a dozen or so on-line) and create yourself a new password.


404

---

### Post by snowpine on 2012-03-03
My recommendation is to use a strong password and enter it when prompted. :)

---

### Post by thebigbry on 2012-03-03
> **snowpine said:**
> My recommendation is to use a strong password and enter it when prompted. :)


 Yep! that is the one thing that makes this program so great. Nothing like being made to use a password and being told what your own private security should be. It's almost like government. Nothing like moving into a new house and having some one insist you install and use 3 deadbolt lock an every door in your house.

---

### Post by sffvba[e0rt on 2012-03-03
> **thebigbry said:**
> Yep! that is the one thing that makes this program so great. Nothing like being made to use a password and being told what your own private security should be. It's almost like government. Nothing like moving into a new house and having some one insist you install and use 3 deadbolt lock an every door in your house.

Plenty of other operating systems out there to choose from.


404

---

### Post by thebigbry on 2012-03-03
> **not found said:**
> Use this [tutorial]("http://www.psychocats.net/ubuntu/resetpassword") (or any other of a dozen or so on-line) and create yourself a new password.


404
  

 Thanks. Didn't realize creating new password was the problem as I never lost my password to begin with.    I simply told it not to use one. I guess that meant not to use one during log in but just make up it's own for every thing else??  which may be why I didn't find the dozen or so other on-line solutions.  Besides I figured I would get betetr more accurate help from a forum  specializing in this rather than just Google searching.
I am not trying to be ungrateful just making sure that this is correct. As i say I have not lost of forgotten anything.

---

### Post by Karlchen on 2012-03-03
> **thebigbry said:**
> But I am so sick of having to type a password, every time I click anything and everything. This statement makes me wonder what your main activities on Ubuntu might be? Ubuntu will only ask you to enter your password during logon and every time you are about to perform an action which needs to be run with root privileges. So this is comparable to the situations where Windows will present the UAC dialogue.

So unless you install and uninstall software permanently and unless you (re)configure systemwide settings all the time, Ubuntu is unlikely to keep bothering your with password prompts _all the time_. So the phrase "every time I click anything and everything" is likely to be largely exaggerated.

Karl

---

### Post by snowpine on 2012-03-03
> **thebigbry said:**
> Yep! that is the one thing that makes this program so great. Nothing like being made to use a password and being told what your own private security should be. It's almost like government. Nothing like moving into a new house and having some one insist you install and use 3 deadbolt lock an every door in your house.

This is the official Ubuntu support forum. If you go to the official Toyota support forum, they will not help you disable your brakes and airbag. :)

---

### Post by sffvba[e0rt on 2012-03-03
Fact is I am not sure how you went about changing your password to "nothing" as I am pretty sure it would have complained that your password was too short.

If you use the tutorial in the link you will be able to change your password to "something", and then you will be able to use your system as normal.


404

---

### Post by Karlchen on 2012-03-03
> **thebigbry said:**
> As i say I have not lost of forgotten anything. In your initial post you stated that you changed your password to be empty. An empty password is no password at all. 
Privilege elevation to root which works via sudo in Ubuntu, via UAC dialogue in Windows, does not permit an empty password by default.
As you have set your password to be empty and as you have not managed to create a new password so far, the idea of sending you to psychocat's tutorial was to help you create a new valid password for your own account which will allow you to run sudo again and hence will give back full control over your system. I fail to see what might be wrong with this approach.

Karl

---

### Post by thebigbry on 2012-03-03
> **not found said:**
> Fact is I am not sure how you went about changing your password to "nothing" as I am pretty sure it would have complained that your password was too short.

If you use the tutorial in the link you will be able to change your password to "something", and then you will be able to use your system as normal.


404

 Did not work. I followed instructions and reset password. logged back in and still the exact same.

---

### Post by thebigbry on 2012-03-03
> **Karlchen said:**
> This statement makes me wonder what your main activities on Ubuntu might be? Ubuntu will only ask you to enter your password during logon and every time you are about to perform an action which needs to be run with root privileges. So this is comparable to the situations where Windows will present the UAC dialogue.

So unless you install and uninstall software permanently and unless you (re)configure systemwide settings all the time, Ubuntu is unlikely to keep bothering your with password prompts _all the time_. So the phrase "every time I click anything and everything" is likely to be largely exaggerated.

Karl

 Yes exaggerated to make the point that it is every time. It is a fresh install there for requiring various add ons how ever every time I try to add something it asks for it again. want to install a new add on. enter password, want to remove an add on type password.

---

### Post by sffvba[e0rt on 2012-03-03
> **thebigbry said:**
> Did not work. I followed instructions and reset password. logged back in and still the exact same.

OK, so just for clarity:  

You have changed your password via the tutorial (and didn't leave the password blank).

When you reboot your system you are automatically logged in without you having to enter a user name and/or password.

When ever you try and do anything that requires elevated privileges you enter your newly created password and authentication fails.

Correct?


404

---

### Post by thebigbry on 2012-03-03
> **snowpine said:**
> This is the official Ubuntu support forum. If you go to the official Toyota support forum, they will not help you disable your brakes and airbag. :)

 No, but they would tell you how to set your glove box, windows, center console and radio so it does not need a key every time you need to open or use it.

---

### Post by thebigbry on 2012-03-03
> **not found said:**
> OK, so just for clarity:  

You have changed your password via the tutorial (and didn't leave the password blank).

When you reboot your system you are automatically logged in without you having to enter a user name and/or password.

When ever you try and do anything that requires elevated privileges you enter your newly created password and authentication fails.

Correct?


404

Correct. I log in, it does not have the log in screen. It DOES pop up and say keyring did not authenticate or something like that. I enter the password, it goes away. I try to intall an addon. It asks for password and does not wok

---

### Post by snowpine on 2012-03-03
You're entitled to your opinion, of course. A strong password is basic Security 101, in **my** opinion. :)

---

### Post by thebigbry on 2012-03-03
> **thebigbry said:**
> Correct. I log in, it does not have the log in screen. It DOES pop up and say keyring did not authenticate or something like that. I enter the password, it goes away. I try to intall an addon. It asks for password and does not wok

 Here is where I set password to "none" Now I can not unlock it to change anything. I have tried and empty password, I have tried my new password and as mentioned even 1

 Well, I tried pasting a screen shot. it pasted and then disappeared when posted.

---

### Post by snowpine on 2012-03-03
> **thebigbry said:**
> Correct. I log in, it does not have the log in screen. It DOES pop up and say keyring did not authenticate or something like that. I enter the password, it goes away. I try to intall an addon. It asks for password and does not wok

gnome-keying is a separate password, it may (or may not) be the same as your login password.

---

### Post by winh8r on 2012-03-03
Could you please open a terminal and enter 

```
sudo -l
```

and post the result?

---

### Post by thebigbry on 2012-03-03
[Screenshot at 2012-03-03 17:00:16.jpg]("http://ubuntuforums.org/attachment.php?attachmentid=213650&stc=1&d=1330815984")


OK try this

---

### Post by thebigbry on 2012-03-03
> **winh8r said:**
> Could you please open a terminal and enter 

```
sudo -l
```and post the result?


thebigbry@thebigbry:~$ sudo -i
[sudo] password for thebigbry: 
Sorry, try again.
[sudo] password for thebigbry: 
Sorry, try again.
[sudo] password for thebigbry: 
Sorry, try again.
sudo: 3 incorrect password attempts


Great!! yeah i tried the password that I used in the tutorial along with blank and 1   
Now am I even more hosed?

---

### Post by thebigbry on 2012-03-03
> **snowpine said:**
> You're entitled to your opinion, of course. A strong password is basic Security 101, in **my** opinion. :)

 And I would agree, if I where ina work place, or an area with lots of traffic. how ever on my home laptop where I or my direct family are the only ones with access to it. I am either using it, or it is off. Not a desk top that just sits on and connected waiting to be hacked.

---

### Post by winh8r on 2012-03-03
the command was 

```
**sudo -l**
```

that is a lower-case L

---

### Post by Mcron on 2012-03-03
> **snowpine said:**
> This is the official Ubuntu support forum. If  you go to the official Toyota support forum, they will not help you  disable your brakes and airbag. :smile:

I have to ask...   why would would you want to disable your airbag and brakes :)

---

### Post by thebigbry on 2012-03-03
> **winh8r said:**
> the command was 

```
**sudo -l**
```that is a lower-case L

   DOH! Ok I tried again with l Same result. Only I didn'te try 3 times this time.  Thank you for continuing the help guys. I appriciate it. I have to go do some running for a few but will check back shortly.   Thanks again.

---

### Post by thebigbry on 2012-03-03
> **Mcron said:**
> I have to ask...   why would would you want to disable your airbag and brakes :)


 you aint never been married Have you.
:p

---

### Post by HavarN on 2012-03-03
The keyring will ask you for a password after login if your login password does not match your keyring password or if you have enabled automatic login. You can change your keyring password from the *seahorse* program. (Right click on the Password: login entry).

Hint: Setting suid root for key programs, will make them run as root no matter which user initiated the program, in which case it will not prompt for password. However it is really not wise to remove your password, and setting suid root on any program introduces a new severe security risk. So proceed with great caution.

---

### Post by thebigbry on 2012-03-05
Well I never found the problem so i finally just re-installed and started over..

---

