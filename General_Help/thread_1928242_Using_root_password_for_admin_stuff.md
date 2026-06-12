---
title: "Using root password for admin stuff"
date: 2012-02-19
forum: General Help
---

### Post by scheibenlosen on 2012-02-19
I'm guessing it's probably been asked before, but I'm too lazy to look. :) Is there a way to set things so that root's password, rather than the user's password, is used for administrative actions?

---

### Post by Iowan on 2012-02-19
On the default Ubuntu install, there's no root password, per se.

---

### Post by wildmanne39 on 2012-02-19
Hi, the user password is the only password created. 

You just need to use sudo in the terminal with the user password and gksu if you are running a GNU program.
Thanks

---

### Post by sisco311 on 2012-02-19
Yes. By default, the root account password is locked, so you will have to set a new root password; and, for practical reasons, you will have to reset gksu to *su mode*. If memory serves, polkit will prompt you for the the root password.

EDIT:
And, of course, you could also set sudo to prompt you for the root password, if that's what you want.

---

### Post by scheibenlosen on 2012-02-20
> **Iowan said:**
> On the default Ubuntu install, there's no root password, per se.

I've been using Ubuntu since at least 5.something, so I'm aware of that. It seems to be one of the few that does things that way.

---

### Post by scheibenlosen on 2012-02-20
> **wildmanne39 said:**
> Hi, the user password is the only password created. 

You just need to use sudo in the terminal with the user password and gksu if you are running a GNU program.
Thanks

Yup. sudo, gksu or su-to-root work just fine. After setting root's password, it seems that su is the only thing I've found, so far anyway, that actually makes use of root's password.

---

### Post by scheibenlosen on 2012-02-20
> **sisco311 said:**
> Yes. By default, the root account password is locked, so you will have to set a new root password; and, for practical reasons, you will have to reset gksu to *su mode*. If memory serves, polkit will prompt you for the the root password.

EDIT:
And, of course, you could also set sudo to prompt you for the root password, if that's what you want.

Thanks for the info. Setting root's password is one of the first things I do with a new install. sudo -s followed by passwd  works for me. I've been using su-to-root to do certain things requiring root access, and it worked well. Your mention of gksu got me to do some RTFMing and, as it turns out, gksu --su-mode does exactly what I was after. I'll have to write that down so I don't forget. :)  Hopefully others are helped by this if they were wanting to do something like this.

---

### Post by Lars Noodén on 2012-02-20
If you want you could make a second account and use one only for system administration and the other for daily use.

---

### Post by scheibenlosen on 2012-02-20
> **Lars Noodén said:**
> If you want you could make a second account and use one only for system administration and the other for daily use.

I could, although for the couple or three apps that want/need admin privileges, gksu does the trick.

---

### Post by Lars Noodén on 2012-02-20
> **scheibenlosen said:**
> I could, although for the couple or three apps that want/need admin privileges, gksu does the trick.

For that I would add specific lines to [sudoers](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sudoers.5.html) to cover each app.  [sudo](http://www.sudo.ws/sudo/intro.html) is meant to give granular access, though it's frequently (ab)used to give all-or-nothing access.

---

### Post by wildmanne39 on 2012-02-20
Hi, glad you got the answer you need, please use thread tools and mark the thread solved.
Thanks

---

### Post by magodfrey on 2012-02-22
This question has be asked on an earlier post without answer, I am hoping that you can give me a way.

I have used Ubuntu since 2007, presently Ubuntu 11.10, so I have absolutely no excuse for my stupidity. I was messing about in Setup and set my own account to Standard instead of Administration, as soon as I clicked 'save' I knew that I'd been momentarily brain dead.

As mine was the only account with root priviledge I now have no way of getting back into the settings to return my account to Administration. I have no access to 'root'.

I have read for hours and hours but only find that 'root' does not have a password of its own, I well understand the reasons for this but still wonder if there is some work-around. My years with Linux has still not managed to get me into command line and any possible answer using this would need to be quite specific.

Failing a suitable answer I wonder if the Ubuntu programmers could make it impossible for the one and only administration account to switch himself off. Have a message asking, "Hi Idiot, are you REALLY sure you want to do this?"

Thanks in advance (forlorn hope)

---

### Post by scheibenlosen on 2012-02-22
> **magodfrey said:**
> This question has be asked on an earlier post without answer, I am hoping that you can give me a way.

I have used Ubuntu since 2007, presently Ubuntu 11.10, so I have absolutely no excuse for my stupidity. I was messing about in Setup and set my own account to Standard instead of Administration, as soon as I clicked 'save' I knew that I'd been momentarily brain dead.

As mine was the only account with root priviledge I now have no way of getting back into the settings to return my account to Administration. I have no access to 'root'.

I have read for hours and hours but only find that 'root' does not have a password of its own, I well understand the reasons for this but still wonder if there is some work-around. My years with Linux has still not managed to get me into command line and any possible answer using this would need to be quite specific.

Failing a suitable answer I wonder if the Ubuntu programmers could make it impossible for the one and only administration account to switch himself off. Have a message asking, &quot;Hi Idiot, are you REALLY sure you want to do this?&quot;

Thanks in advance (forlorn hope)

 What I usually do for a new Ubuntu install, although it should work no matter how long you've been running it, is to open a terminal and type "sudo -s" (no quotes). Supply your user password, and that'll get you to root's prompt. Type "passwd" (again, no quotes) and plunk in the password of choice, and then the same one again for verification. At least you'll be able to do root stuff, like editing fstab, et al, and could probably set things back to the way you had them.  Hope that helps a bit. :)

---

### Post by CatKiller on 2012-02-22
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by magodfrey on 2012-02-23
My thanks to Catkiller for the fixsudo link.

Running the Recovery Mode ended with a command line screen, the three lines were:

Couldn't find whiptail, starting root shell instead of recovery menu.
bash: groups: command not found
root@Michael:~#

I attempted the Case 1 repair with the following result:

adduser username admin              (my username)
bash: adduser: command not found

Then Case 2, the backup attempt is left out here as it had the same result as the next command:

sudo nano /etc/sudoers
bash: sudo: command not found.

I then ran the command without sudo, the file opened in read mode only. The file contained everything shown in the fixsudo description except for the final 2 lines which were missing.

#Members of the admin group may gain root privileges
%admin ALL=(ALL) All

Having Read Only it is not possible to edit the file. Is there any further advice on this?

The original query I used to add this on to is closed and I now wonder whether I should open this query in a fresh query under my own member name.

---

### Post by magodfrey on 2012-02-23
My thanks to scheibenlosen for his reply. Unfortunately, whilst this allows me to change my password, it does not give me root privileges.

---

