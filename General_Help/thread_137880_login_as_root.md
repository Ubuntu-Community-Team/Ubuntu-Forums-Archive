---
title: "login as root?"
date: 2006-02-28
forum: General Help
---

### Post by sledge367 on 2006-02-28
While trying to solve some other problems (no other applications working like Synaptic, Update, Users, etc) I have tried to reinstall several times. When installing using the expert command it give me the option of creating a user account and pw or not. If I choose not to, when Ubuntu loads up and ends at the Ubuntu GUI login screen, how do I login as root??

If I try is says that the system administration cannot login through this screen.

Help, please.

Sledge367

---

### Post by Bachstelze on 2006-02-28
If you cannot login as root from the GDM screen, it is for a **very** good reason. Believe me, changing that is a very bad idea. If you still want to do it it is in the Login Screen Setup (System > Administration) in the Security tab.

---

### Post by shams2 on 2006-02-28
login as root is desabled in ubuntu, you should login as user and change to root with:
sudo su

---

### Post by taurus on 2006-02-28
If it asks you to create a user account, why wouldn't you?  If you don't create an account, how in the world would you log in to your system!!!

---

### Post by aysiu on 2006-03-01
Don't use the expert install unless you're an expert.

Do a normal install and then read these two links:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://www.psychocats.net/linux/permissions](http://www.psychocats.net/linux/permissions)

---

### Post by sledge367 on 2006-03-01
Ok first off, you install in the expert mode so as to create a dual-boot instead of erasing everything!
2nd, there is not security tab in my System -> Administration section
3rd, I'm only looking to do this because I can't get ANYTHING but the currently installed programs to run - I cna't get Synaptic, Updates, Add an application, Users, ANYHTING to open up beyond asking for a password and then nada

When I try and use the terminal the same things happens

Any ideas?

---

### Post by Bachstelze on 2006-03-01
> If you still want to do it it is in the **Login Screen Setup** (System > Administration) in the Security tab.

...

---

### Post by sledge367 on 2006-03-01
Sorry Hymnforlife, you ARE correct - sorry! But, when I go there it asks for a pw and then nothing happens. No new screen, nothing. Just a normal desktop

---

### Post by gibson on 2006-03-01
[QUOTE=sledge367]Ok first off, you install in the expert mode so as to create a dual-boot instead of erasing everything![/QUOTE]

I have done several "dual-boot" installations for people and never used the expert mode.

---

### Post by Bachstelze on 2006-03-01
@sledge > the password you need to type when prompted is your user password, not any root password you have set.

---

### Post by sledge367 on 2006-03-01
I do use my user pw (I just have also tried the root pw just in case I was missing something stupid - which is how I feel at the moment)

Still can't get anything to work

---

### Post by Zalbor on 2006-03-01
If I understand correctly, none of the programs in Sysem>Administration work, right? Try opening a terminal (Applications>Accessories>Terminal) and running one of them from there (for example, "sudo synaptic"). It might have some output that can explain why they don't work.

---

### Post by sledge367 on 2006-03-01
If I use the terminal I type in what others suggest like "sudo synaptic" and if this is the first command of the OS loading up then it asks for a password and then nothing - no error messages, no other text at all other than a typical prompt.
If I have already attempted to give it a pw for anything then the terminal window doesn't ask for a pw and just gives me another typical prompt

---

