---
title: "Can I use my wireless card without entering password first?"
date: 2009-06-29
forum: General Help
---

### Post by metalf8801 on 2009-06-29
I have auto login setup which is really nice but then I have to enter my password before I can use my wireless card is there anyway I can change it so that I can just connect to my home network without having to enter my Ubuntu password?

---

### Post by iponeverything on 2009-06-29
Go to System -> Administration -> Users and Groups

click on Unlock then go highlight your account and go to properties.

Then click on the "User Privileges" tab and check your user rights for wireless.

---

### Post by mcduck on 2009-06-29
I suppose the password you have to enter before being able to connect is for the keyring?

The keyring is unlocked automatically when you login with your password. Of course that doesn't work if you use automatic login, so you end having to enter the kerying password instead. To get rid of that, you'll have to remove the keyring password (which is less secure, but since you are using automatic login that's probably not an issue for you)

To remove keyring password go to Applications/Accessories/Passwords and Encryption Keys. On the Passwords-tab right-click the "Passwords:login"-keyring and select "Change Password". Enter your old password, and leave the fields for new password empty.

---

### Post by metalf8801 on 2009-06-29
> **iponeverything said:**
> Go to System -> Administration -> Users and Groups

click on Unlock then go highlight your account and go to properties.

Then click on the "User Privileges" tab and check your user rights for wireless.

I tried that before posting and it didn't work but I'll double check that I did it right.  
Thank you

---

### Post by iponeverything on 2009-06-29
you might try to reinstall the gnome-keyring package.

```
sudo apt-get install --reinstall gnome-keyring
```

---

### Post by Laysan_A on 2009-06-29
> Go to System -> Administration -> Users and Groups

click on Unlock then go highlight your account and go to properties.

Then click on the "User Privileges" tab and check your user rights for wireless.

Anyone know how I can do the same thing in Kubuntu?

---

### Post by abn91c on 2009-06-29
> **Laysan_A said:**
> Anyone know how I can do the same thing in Kubuntu?
in kubuntu you usually just click the connect automatically box in the network manager

---

### Post by Laysan_A on 2009-06-29
> in kubuntu you usually just click the connect automatically box in the network manager     Hmm...I've done that...It seems network manager and whatever talks to kwallet aren't talking to each other.

Something's a little hinky on my system with kwallet anyway. I've tried twice to change my password and it won't accept it.

Well, okay, if that's how it's supposed to work then you've answered my question. Whether or not it actually works the way it's supposed to is a separate issue.

Thanks!

Oh, and nice desktop, by the way. 

Can I ask, how did you attach such a large and detailed image when the attachment limits seem so low here. I remember attaching a snapshot of my desktop some time ago and having to make it smaller and smaller and less dense, until finally you could hardly tell what it was, before the uploader would accept it.

Oh, and one final question, what is that weather widget you've got called (where can I find it)? I just looked at it again and it looks like the weather widget from the repositories, but instead of an ugly white background with transparent letters, yours has a transparent background and white letters - how did you do that?

---

### Post by abn91c on 2009-06-30
> **Laysan_A said:**
> Hmm...I've done that...It seems network manager and whatever talks to kwallet aren't talking to each other.

Something's a little hinky on my system with kwallet anyway. I've tried twice to change my password and it won't accept it.

Well, okay, if that's how it's supposed to work then you've answered my question. Whether or not it actually works the way it's supposed to is a separate issue.

Thanks!

Oh, and nice desktop, by the way. 

Can I ask, how did you attach such a large and detailed image when the attachment limits seem so low here. I remember attaching a snapshot of my desktop some time ago and having to make it smaller and smaller and less dense, until finally you could hardly tell what it was, before the uploader would accept it.

Oh, and one final question, what is that weather widget you've got called (where can I find it)? I just looked at it again and it looks like the weather widget from the repositories, but instead of an ugly white background with transparent letters, yours has a transparent background and white letters - how did you do that?
that's my laptop screen, saved as a **[COLOR="Blue"]png[/COLOR]** file
the weather widget has the color scheme of the [COLOR="blue"]bare naked[/COLOR] theme, available at [http://www.kde-look.org](http://www.kde-look.org)

---

