---
title: "Big problem need help"
date: 2010-05-15
forum: General Help
---

### Post by Jiminy555 on 2010-05-15
Ok so... I messed up my ubuntu some how and now Nautilus won't work on my account and my password won't let me install packages, go root etc.  I want to copy the home folder of my account before I reinstall but when I go to the account that nautilus works on I can't copy some folders because I don't have permission.  How can I copy those folders?  Thanks

---

### Post by Phrea on 2010-05-15
First thing that comes to mind is running a live cd session, to get to your files and back them up somewhere.

---

### Post by mjitkop on 2010-05-15
The Live CD would be my suggestion too.

---

### Post by Jiminy555 on 2010-05-15
> **mjitkop said:**
> The Live CD would be my suggestion too.
live CD still says I don't have permission and same with even a fedora one!

---

### Post by mjitkop on 2010-05-15
If you are having problems with Nautilus, how about trying to use the terminal? Have you given it a try already?

---

### Post by Phrea on 2010-05-15
Have you tried a rescue cd?
Something like [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

### Post by Jiminy555 on 2010-05-15
> **mjitkop said:**
> If you are having problems with Nautilus, how about trying to use the terminal? Have you given it a try already?
do i need a password for that cause mine doesn't work with anything

and I'm reading the rescue disk thing right now

---

### Post by Jiminy555 on 2010-05-15
it doesn't work, is there any way I can just get Nautilus working or reinstall it without admin password?

---

### Post by gadolinio on 2010-05-15
What caused this? I mean, how did you mess ubuntu? It might be something related with permissions, and that can be fixed from the terminal without reinstalling anything.
Do you know how to use the chmod command, if the problem is with permissions?

---

### Post by Jiminy555 on 2010-05-15
> **gadolinio said:**
> What caused this? I mean, how did you mess ubuntu? It might be something related with permissions, and that can be fixed from the terminal without reinstalling anything.
Do you know how to use the chmod command, if the problem is with permissions?
ya i follwed directions to change my username but this happened.  How do i fix it in terminal?

---

### Post by gadolinio on 2010-05-15
> **Jiminy555 said:**
> ya i follwed directions to change my username but this happened.  How do i fix it in terminal?

( ! ) FIRST OF ALL:
I'm not 100% sure, so consider waiting for another opinion and doing more research.

So, once you've read the previous line several times, go on ;) And then remember about that line again.

Maybe the command chown is the way out. Take a look at [http://manpages.ubuntu.com/manpages/karmic/man1/chown.1.html](http://manpages.ubuntu.com/manpages/karmic/man1/chown.1.html). Using chown (with sudo) you can make your user folder be yours again, if that's the problem -- I mean, make the folder you used to have as yours belong to the "new you". It would be something like "sudo chown YOUR_NEW_USER_NAME /home/THE_FOLDER_YOU_WANT_TO_OWN". You might also have to turn that folder into the newly-named-user's home folder, if there's trouble with that. How did you change your username?
If you can't use sudo from that account because your password isn't recognized, try the command from a liveCD session.

---

### Post by nothingspecial on 2010-05-15
> **Jiminy555 said:**
> ya i follwed directions to change my username but this happened.  How do i fix it in terminal?

Reboot. Hold down shift. Boot into recovery mode. You want a root recovery shell. (I`m not sure what they call it nowadays).

When you get there type - 

```
adduser *[COLOR="Red"]username[/COLOR]* admin
```

Change *[COLOR="Red"]username[/COLOR]* to your new username

Type ```
exit
```

Log in normally and all should be well, if I have understood your problem correctly.

---

### Post by gadolinio on 2010-05-15
> **nothingspecial said:**
> Reboot. Hold down shift. Boot into recovery mode. You want a root recovery shell. (I`m not sure what they call it nowadays).

When you get there type - 

```
adduser *[COLOR=Red]username[/COLOR]* admin
```Change *[COLOR=Red]username[/COLOR]* to your new username

Type ```
exit
```Log in normally and all should be well, if I have understood your problem correctly.

From a new user, you can use chmod to have all permissions and thus backup your files. Suppose you create the user "newaccount", and the folder you want to back up is "/home/firstuser". Once you log in with newaccount, open a terminal and type
```

sudo chmod 777 -R /home/firstuser

```

When asked for a password, give newaccount's, which should be working ok. Then you can backup the folder as its permissions are granted for everyone. Hope that helps...

---

### Post by alcohol52 on 2010-05-15
Here is the trick.

Use  **Puppy** Linux live Cd /Usb. The current version is 4.3.1 and it is only 90 to 110 mb (depends upon which iso you download). Burn iso or create live usb with Unetbootin/lili live linux creator.

Puppy Linux is one of the few distributions that ***doesn't use a root password**;**** it doesn't make **any distinction between normal user and root user***. This makes the system easier to use, and grants complete control of the hard drives to the user. (*Wikipedia*)

That is as far as theory goes. 

As for practical,I was able to access any file in my Ubuntu partition with live Puppy linux Usb. Give it a try.

---

### Post by Jiminy555 on 2010-05-15
Thanks guys! I made myself admin and am now using GNOME Commander.  If anyone knows how to make Nautilus working again it would be appreciated.  Thanks again!

---

### Post by ryan858 on 2010-05-15
Reinstall Nautilus? I thought you were going along those lines to begin with (in your first post)?

if you've made a new user and gotten the old home folder copied over, then all you need to do is uninstall nautilus and reinstall it again using either Software Center, or apt-get.

to use apt-get open a terminal and:

[B]$ sudo apt-get remove nautilus
$ sudo apt-get update && sudo apt-get install nautilus[/B]

---

### Post by Jiminy555 on 2010-05-15
> **ryan858 said:**
> Reinstall Nautilus? I thought you were going along those lines to begin with (in your first post)?

if you've made a new user and gotten the old home folder copied over, then all you need to do is uninstall nautilus and reinstall it again using either Software Center, or apt-get.

to use apt-get open a terminal and:

[B]$ sudo apt-get remove nautilus
$ sudo apt-get update && sudo apt-get install nautilus[/B]
I did what you said exactly and now I can't login to any account! WTF man! it just goes back to login screen when i press login!

---

### Post by Jiminy555 on 2010-05-15
anyone know what to do? I tried the dkpg thing and reinstalling nautilus again but it won't work!

---

