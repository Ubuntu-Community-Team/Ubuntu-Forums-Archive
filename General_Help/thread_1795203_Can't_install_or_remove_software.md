---
title: "Can't install or remove software"
date: 2011-07-02
forum: General Help
---

### Post by jamesbuhls on 2011-07-02
Please help - I don't know what's happening with my computer! A few weeks ago I began having trouble with the Ubuntu Software Centre - the software portal opens just fine, but the "Install" and "Remove" buttons don't do anything. If I see a program that I want and click "Install," nothing happens. If I see a program I don't want anymore and click "Remove," nothing happens. What's going on? Please help!

---

### Post by Gryllida on 2011-07-02
Please check that your account type is `Administrator` in System -> Administration -> Users and Groups.

More details: [https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

---

### Post by jamesbuhls on 2011-07-02
I'm the only user on my computer and I've always been the administrator. When I opened the Users Settings, I'm not able to add any new users, change my account type (listed as Custom), or open the advanced settings for this account.

---

### Post by birkopf on 2011-07-02
> **jamesbuhls said:**
> I'm the only user on my computer and I've always been the administrator. When I opened the Users Settings, I'm not able to add any new users, change my account type (listed as Custom), or open the advanced settings for this account.

Then probably like Gryllida mentioned you have a problem with your user account = lack of permissions. But it's strange. Try starting Synaptic. It should ask you for root password and once you give it, you should be able to install/remove programs. 

PS - Run on terminal 
```
whoami
```
or
```
id
```

This will show which user you are logged in as

---

### Post by jamesbuhls on 2011-07-02
Using the id code in the terminal this is what I get back:

uid=1000(james) gid=1000(james) groups=4(adm),20(dialout),24(cdrom),46(plugdev),105(lpadmin),119(admin),122(sambashare),1000(james)

I opened Synaptic and logged in but I still can't install or remove software.

(If it matters, the Update Manager is still working just fine.)

---

### Post by birkopf on 2011-07-02
> **jamesbuhls said:**
> Using the id code in the terminal this is what I get back:
uid=1000(james) gid=1000(james) groups=4(adm),20(dialout),24(cdrom),46(plugdev),105(lpadmin),119(admin),122(sambashare),1000(james)
I opened Synaptic and logged in but I still can't install or remove software.
(If it matters, the Update Manager is still working just fine.)

No idea. I would personally google and read all I can about user rights, account types etc. 

You can always create new user with full admin rights and move your files to new user but this will carry lots of changes and big chance something will go wrong along the way. 

Hopefully someone advanced will see this thread and advice you. 

PS this is my id like which differs a bit. Most important are fist ones. Have a look:

uid=1000(rich) gid=1000(rich) groups=1000(rich),

4(adm),20(dialout),24(cdrom),46(plugdev),112(lpadmin),120(admin),122(sambashare)

---

### Post by jamesbuhls on 2011-07-02
Yeah, I hope I can figure out what's happening because I'm pretty well stuck: like I said above, I can't add new user profiles. Thanks for the help.

---

### Post by birkopf on 2011-07-02
> **jamesbuhls said:**
> Yeah, I hope I can figure out what's happening because I'm pretty well stuck: like I said above, I can't add new user profiles. Thanks for the help.

Did you consider backing up your data and reinstalling system ?

---

### Post by Linux_junkie on 2011-07-02
What did you do to your system the since the last time you were able to install / remove apps?

---

### Post by nerdy_kid on 2011-07-02
have you tried rebooting your computer?  it sounds like perhaps the authentication helper might be frozen (forgot what it is called).  Open a terminal and type
```

sudo whoami

```

That should say "root".  If if doesn't, then you have permission issues, if it does, then the helper is frozen as I said above and rebooting should fix it.

---

### Post by nerdy_kid on 2011-07-02
also, while your at it, do
```

sudo apt-get install fcrackzip

```
and post the output.

{edit}
you should not have to reinstall the system.

---

### Post by wildmanne39 on 2011-07-02
> **jamesbuhls said:**
> I'm the only user on my computer and I've always been the administrator. When I opened the Users Settings, I'm not able to add any new users, change my account type (listed as Custom), or open the advanced settings for this account.Hi, have a look at this link I think your sudoer file is messed up.
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by jamesbuhls on 2011-07-02
(shaking head) I can't believe I didn't think of it before: all I needed to do was log out and reboot the computer. That fixed it. Thanks Nerdy and others for the help and suggestions.

---

### Post by wildmanne39 on 2011-07-02
> **jamesbuhls said:**
> (shaking head) I can't believe I didn't think of it before: all I needed to do was log out and reboot the computer. That fixed it. Thanks Nerdy and others for the help and suggestions.Hi, your welcome if your problem or question is resolved, would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by birkopf on 2011-07-04
> **nerdy_kid said:**
> also, while your at it, do
```

sudo apt-get install fcrackzip

```
and post the output.
{edit}
you should not have to reinstall the system.

Why did you ask him to install fcrackzip? And to post an output of what ? Sorry - don't get this answer.

---

### Post by nerdy_kid on 2011-07-04
> **birkopf said:**
> Why did you ask him to install fcrackzip? And to post an output of what ? Sorry - don't get this answer.

I wanted to see whether the issue was actually a issue with his permissions (i.e. whether he could use sudo or not) or if it was an issue with the pam authentication process.  I had him install fcrackzip simply because

1.  He said he couldn't install packages, I wanted to see if he could, and if he couldn't, I wanted to have the error message.
2. I chose fcrackzip because it is small, and because it doesn't depend on a lot of libraries -- i.e. it would be fast to install.  It was also one of the first programs I thought of.

The output I mentioned was the output of the apt-get command, see #1.

---

### Post by birkopf on 2011-07-05
> **nerdy_kid said:**
> I wanted to see whether the issue was actually a issue with his permissions (i.e. whether he could use sudo or not) or if it was an issue with the pam authentication process.  I had him install fcrackzip simply because

Now it makes sense. From your answer I thought you may ask him to use fcrackzip to break user passwords or something :)

Now problem is solved. 

PS - jamesbuhls - When did you last time before that rebooted your machine ? :lolflag:

---

### Post by Imping on 2011-07-05
i have the same problem i am unable to install or remove the anything form the ubuntu operating systems.Please tell me how i can install or remove the thing from the systesm
[http://www.impingesolutions.com/index.php/iphone-application-development](http://www.impingesolutions.com/index.php/iphone-application-development)

---

### Post by wildmanne39 on 2011-07-05
> **Imping said:**
> i have the same problem i am unable to install or remove the anything form the ubuntu operating systems.Please tell me how i can install or remove the thing from the systesm
[http://www.impingesolutions.com/index.php/iphone-application-development](http://www.impingesolutions.com/index.php/iphone-application-development)Hi, we need the complete error message you get when you try to install from software center or synaptic.

---

### Post by birkopf on 2011-07-05
> **wildmanne39 said:**
> Hi, we need the complete error message you get when you try to install from software center or synaptic.
And reproduction of all your steps during install/uninstall as well please :)

---

### Post by nerdy_kid on 2011-07-05
> **birkopf said:**
> Now it makes sense. From your answer I thought you may ask him to use fcrackzip to break user passwords or something :)

Now problem is solved. 

PS - jamesbuhls - When did you last time before that rebooted your machine ? :lolflag:

lol na :D

---

