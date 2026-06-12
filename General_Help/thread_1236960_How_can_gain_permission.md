---
title: "How can gain permission?"
date: 2009-08-10
forum: General Help
---

### Post by NMWindows on 2009-08-10
Hey All, 


I was trying to edit the permissions in the /etc/apache2/, everytime I use sudo, I get a message ending with *permission denied*, 

How get I edit root folders, what command can I use to make myself an admin?

---

### Post by michy99 on 2009-08-10
Give an example of a command you entered and the error message.

---

### Post by Iowan on 2009-08-10
**sudo** *should* work... if your user is in the admin(?) group. Is that the user you created when the machine was first set up?

---

### Post by NMWindows on 2009-08-11
> **michy99 said:**
> Give an example of a command you entered and the error message.

Sorry for the wait time. 
I tried to use gksudo nautilus, I read in Beginners Talk that it would help, but now it gives this message when I use sudo:

*sudo: /etc/sudoers is mode 0660, should be 0440*


> **Iowan said:**
> **sudo** *should* work... if your user is in the admin(?) group. Is that the user you created when the machine was first set up?

no, I am not.

---

### Post by michy99 on 2009-08-11
First, what is the output of```
ls -l /etc/sudoers
```Second, have you edited the sudoers file? If so, did you use visudo to do it?

---

### Post by NMWindows on 2009-08-11
I used this code:

ln -s /etc/apache2/sites-available/mysite.com

I tried to do a symbolic link on with the apache2 folder

---

### Post by 3rdalbum on 2009-08-11
> **NMWindows said:**
> Sorry for the wait time. 
I tried to use gksudo nautilus, I read in Beginners Talk that it would help, but now it gives this message when I use sudo:

*sudo: /etc/sudoers is mode 0660, should be 0440*

1. The Sudo command says "run the rest of this command as root". So basically, if you type:

```
sudo /etc/sudoers
```

Then you're saying "Run /etc/sudoers as root". This is wrong - you don't RUN text files, you open them in a text editor.

2. Don't modify the /etc/sudoers file in a text editor; use the Visudo command instead; it checks that your modifications are acceptable and stops your system from breaking:

```
sudo visudo
```

3. I've got a feeling that what you're trying to do with the sudoers file might be a perversion of Ubuntu's security system. If you explain what you ACTUALLY want to accomplish with your "sudoers" editing, we can suggest the best way to do it.

---

### Post by 3rdalbum on 2009-08-11
> **NMWindows said:**
> I used this code:

ln -s /etc/apache2/sites-available/mysite.com

I tried to do a symbolic link on with the apache2 folder

1. Anything outside /tmp or your home directory must be performed as root; put "sudo" in front of that command to run it as root.

2. It seems that you're a bit hazy on what a symbolic link is and what it does. You need to give a target AND a location to put the link, in that order. When you navigate or read from the link, it actually navigates to or reads from the target.

---

### Post by NMWindows on 2009-08-11
First of all, 

I thank all of you for your relpies. 

What I want to do is add a directory to the /etc/ and edit the default.conf file so I can put the information of my site in, but it says that i don't have the right permissions for it, so I can use visudo for it?

---

### Post by 3rdalbum on 2009-08-11
> **NMWindows said:**
> First of all, 

I thank all of you for your relpies. 

What I want to do is add a directory to the /etc/ and edit the default.conf file so I can put the information of my site in, but it says that i don't have the right permissions for it, so I can use visudo for it?

Okay, then you've got two choices. You can open a file browser as root:

```
gksudo nautilus
```

(or install the "nautilus-gksu" package in order to get it as a right-click menu option)

Then create folders and modify files as you please, within that file browser.

Or make your folder and edit the text file on the terminal:

```
sudo mkdir /etc/whatever_you_want_to_call_it
sudo nano /etc/apache2/default.conf
```

("nano" is a text editor)

You need to use Sudo, because only root can modify files and folders that are outside your home directory. You don't use Visudo. Visudo just helps you edit the /etc/sudoers file, nothing else. I've been using Ubuntu for three and a half years and I've never needed to edit /etc/sudoers, so you might as well forget about visudo.

---

### Post by NMWindows on 2009-08-11
Thanks!:)

I did the second option and all is well with the world....for now, could I just download the "nautilus-gksu" to give me the rights to edit any file I chose or do I make myself an admin?
If I had to make myself an admin, what would I do?

---

### Post by michy99 on 2009-08-11
You should already be a member of the admin group. To see what groups you belong to, enter this in a terminal:```
groups
```

---

### Post by NMWindows on 2009-08-11
Thanks, 

I am an admin, what do i need to do some I can just edit directories w/o using terminal commands?

---

### Post by fluffman86 on 2009-08-12
press alt+f2, then type 
```
gksu nautilus
```
or install nautilus-gksu from synaptic.  Although, I just did the latter and it's not working right now...maybe I need to logout/log back in first...hmm...well, at leat I know the alt+f2 method works.

---

