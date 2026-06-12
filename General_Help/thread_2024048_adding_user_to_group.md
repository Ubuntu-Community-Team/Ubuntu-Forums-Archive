---
title: "adding user to group"
date: 2012-07-13
forum: General Help
---

### Post by Pedroski55 on 2012-07-13
I wanted to add myself to the group mail, so I went to system settings>user accounts.
But there is nothing there about managing groups. Please see attached screenshot.

Is there no gui for managing groups??

---

### Post by Morbius1 on 2012-07-13
2 options:

(1) Install the gnome2 version that actually does something:
```
sudo apt-get install gnome-system-tools
```Then run:
```
users-admin
```OR, Go old-school:
```
sudo gpasswd -a your-user-name mail
```Then logout and login again for the group membership to take affect.

---

### Post by Kopkins on 2012-07-13
> **Morbius1 said:**
> 
```
sudo gpasswd -a your-user-name mail
```Then logout and login again for the group membership to take affect.

I've always used this method, it's simple and fast. 

Kopkins

---

### Post by Habitual on 2012-07-13
> **Kopkins said:**
> I've always used this method, it's simple and fast. 


and it always works, everywhere. :)

---

### Post by Pedroski55 on 2012-07-13
Thanks.
So it is not my computer, but gnome3 that is causing the problem??
Will there be any nasty side effects to installing gnome2 stuff in gnome3??
I mean, adding myself to groups is not something I do often. I did it command line style. I just wondered why that could not be done under User Accounts

---

### Post by Morbius1 on 2012-07-14
> Will there be any nasty side effects to installing gnome2 stuff in gnome3??All of it's dependencies are within the repositories and designed to work withing Gnome3 and will not conflict with anything else.
> I just wondered why that could not be done under User Accounts     That I'm afraid transcends the question you asked and goes to the heart of the Gnome design philosophy. Each successive release of a Gnome application has less function than the one before it. Nautilus 3.6 will have less function that 3.4. 3.8 will have, from the preliminary view of things, far less function than 3.6. It's just the way Gnome works. In the case of this topic Gnome is pretty up front about it though. The old application can be found under: **Users and Groups**. The new one is called: **User Accounts** - doesn't say anything about groups. 

Gnome want's to be the GUI for a Tablet or a Phone or a TV ( of course they'll have to battle Ubuntu's Unity to get there ). These things are usually single user devices so eventually they will eliminate the need to add users or change groups altogether.

---

