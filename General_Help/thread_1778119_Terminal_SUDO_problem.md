---
title: "Terminal SUDO problem"
date: 2011-06-08
forum: General Help
---

### Post by antoiner_roquentin on 2011-06-08
I am having a problem with authenticating when I try to use sudo privileges within my terminal. I am very new to this, so it's probably my ignorance at play. In any case, this is what is happening:

If I try to change something that requires me to borrow root powers within my GUI, it will prompt me for a password, which I provide [this is the password for my one and only account] and everything goes off without a hitch. However, when I am using the terminal and try to use any sudo command [which as I understand it is borrowing root powers just the same way that you do it within the GUI] I type in exactly the same password and it will refuse to authenticate me.

I tried to use: su root also, but it asks me for a password once again and will not authenticate.

Can someone please explain this to me?

---

### Post by collisionystm on 2011-06-08
> **antoiner_roquentin said:**
> I am having a problem with authenticating when I try to use sudo privileges within my terminal. I am very new to this, so it's probably my ignorance at play. In any case, this is what is happening:

If I try to change something that requires me to borrow root powers within my GUI, it will prompt me for a password, which I provide [this is the password for my one and only account] and everything goes off without a hitch. However, when I am using the terminal and try to use any sudo command [which as I understand it is borrowing root powers just the same way that you do it within the GUI] I type in exactly the same password and it will refuse to authenticate me.

I tried to use: su root also, but it asks me for a password once again and will not authenticate.

Can someone please explain this to me?


so for instance if you do

```
sudo nano
```

and you enter your password, what happens?

---

### Post by antoiner_roquentin on 2011-06-08
It just says:
antoine_roquentin@antoineroquentin-1005HA:~$ sudo apt-get install pavucontrol pavumeter
[sudo] password for antoine_roquentin: 
Sorry, try again.
[sudo] password for antoine_roquentin: 
Sorry, try again.
[sudo] password for antoine_roquentin: 
Sorry, try again.
sudo: 3 incorrect password attempts
antoine_roquentin@antoineroquentin-1005HA:~$ su root
Password: 
su: Authentication failure
antoine_roquentin@antoineroquentin-1005HA:~$ su root
Password: 
su: Authentication failure
antoine_roquentin@antoineroquentin-1005HA:~$ sudo apt-get install pavucontrol pavumeter
[sudo] password for antoine_roquentin: 
Sorry, try again.
[sudo] password for antoine_roquentin: 
Sorry, try again.
[sudo] password for antoine_roquentin: 

I keep entering the password, it keeps saying it's sorry. 
Hahaha!

---

### Post by coffeecat on 2011-06-08
When you type "su root" it is asking you for the root password, which doesn't exist in Ubuntu, so there's no point in trying that.

When you preface a command with "sudo" it is asking you for the password that is working for you for administrator authentication in the GUI. So it must be that you are not typing the same password. Since there is no visual feedback in the terminal it is very easy to make a typo. Or make sure you do not have caps lock on.

---

### Post by FormatSeize on 2011-06-08
Perhaps sudo on the machine in question somehow became broken, I found [this article](http://www.psychocats.net/ubuntu/fixsudo) which may shed some insight into how to get it working again.  But like *coffeecat* already mentioned, it could be that you are mistyping the password. It happened to me once on a fresh install. I had a password in mind, and somehow mistyped it twice during installation, and when I tried to do my normal setup that required a password, I ran into this problem.
 
How long have you had the installation? If this is your first time using this particular installation, or maybe if you have the system log you on automatically, there's a mistyped password somewhere. If not, then I would try the article mentioned above.

---

### Post by antoiner_roquentin on 2011-06-08
I think you might be right FormatSeize, it could be that I specified a different password than the one that works for my normal profile. I just switched from using Windows to using Linux, so this install is my first and only a few days old. What did you do when you entered a mistyped password on a fresh install?

---

### Post by dFlyer on 2011-06-08
> **antoiner_roquentin said:**
> I am having a problem with authenticating when I try to use sudo privileges within my terminal. I am very new to this, so it's probably my ignorance at play. In any case, this is what is happening:

If I try to change something that requires me to borrow root powers within my GUI, it will prompt me for a password, which I provide [this is the password for my one and only account] and everything goes off without a hitch. However, when I am using the terminal and try to use any sudo command [which as I understand it is borrowing root powers just the same way that you do it within the GUI] I type in exactly the same password and it will refuse to authenticate me.

I tried to use: su root also, but it asks me for a password once again and will not authenticate.

Can someone please explain this to me?

Has it always been this way or did it just start after the recent update to sudo?

---

### Post by antoiner_roquentin on 2011-06-08
Well, that's the thing dFlyer, I don't know because this is a very fresh installation. I was attempting to add some components to my PulseAudio application so that I could figure out a different issue and when I tried to give the commands through the terminal I realized that I do not have access through the terminal to root powers. However, in the GUI, like I said, it works just fine when I "borrow" root powers on the system.

---

### Post by antoiner_roquentin on 2011-06-08
I figured it out! What was going on was that under my user settings I was listed under a custom type of account that must not have included the ability to borrow root powers and change the system. As soon as I changed the setting to administrator I was able to execute my command in the terminal with no problem.

Here is a question though:
When I was using Windows I always had an administrator account separate from my normal user accounts because it is recommended for security reasons. If I am only using one account with Ubuntu is it safe to have that account set up with administrator privileges? 

Thanks everyone for your help on this, I really appreciate it!

---

### Post by el_koraco on 2011-06-08
> **antoiner_roquentin said:**
> 
When I was using Windows I always had an administrator account separate from my normal user accounts because it is recommended for security reasons. If I am only using one account with Ubuntu is it safe to have that account set up with administrator privileges? 


Yes, because the account is not the administrator account, it just has the authority to borrow administrative privileges.

---

### Post by dFlyer on 2011-06-08
You are safe using one account for both regular user and administrator. The reason being is that a regular user can only use his local files and run local and non system programs that do not require administrator privileges. To do any administrator work you need to sudo which will give you system wide privileges to complete the task. Once you complete the task and exit the shell, you no longer have administrator privileges. You might want to read up on sudo by entering this at a terminal:

man sudo

Have fun.

---

### Post by coffeecat on 2011-06-08
In case you haven't come across it already, a useful link about the sudo model in Ubuntu:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by grahammechanical on 2011-06-08
If you are worried about being set up as administrator then change it back to Custom and go to Advance Settings>User privileges and make sure that there is a tick mark against Administer the System. This is the set up that I have and I can authenticate in the GUI and run sudo commands in the terminal. Which is what you want to do.

Regards.

---

