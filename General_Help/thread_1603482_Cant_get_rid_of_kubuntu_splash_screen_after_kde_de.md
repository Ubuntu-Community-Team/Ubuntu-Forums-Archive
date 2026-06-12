---
title: "Cant get rid of kubuntu splash screen after kde desktop install."
date: 2010-10-22
forum: General Help
---

### Post by 1984dc on 2010-10-22
Hello all.
 
I installed the kde desktop about 6 months ago and since then after choosing my boot option from grub i am stuck with the kubuntu splash screen instead of the ubuntu one.

does anyone know if there is a way i can go back to the good ol' ubuntu style splash screen (btw the splash screen manager does not seem to make any changes to my splash screen  when  i try to select another image for my splash screen, this has never worked not even before the installation of kde desktop).

many thanks in advance 

dc

---

### Post by 1984dc on 2010-10-29
Bump

---

### Post by Hippytaff on 2010-10-29
I had the same problem...I think this worked, if my memory serve me correctly

```

sudo dpkg-reconfigure gdm

```
but it was a while ago

---

### Post by 1984dc on 2010-10-29
Thanks Hippytaff
 
I will try that when i get home :)

---

### Post by Hippytaff on 2010-10-29
I also ran into a problem which you might come accross if you decided to get rid of all the KDE stuff you got when you installed with the desktop...so just incase heres the thread that solved it for me :-)

[http://ubuntuforums.org/showthread.php?t=1583246&highlight=gnome+hippytaff](http://ubuntuforums.org/showthread.php?t=1583246&highlight=gnome+hippytaff)

---

### Post by 1984dc on 2010-11-02
I tried 

sudo dpkg-reconfigure gdm

But no luck the splash screenstill shows the kubuntu splash (though weirdly enough the shutdown screen seems to display ubuntu). 

I really don't want to remove the kde desktop completely as i have various desktops and i like to use them all for different purposes. I just want to restore the old ubuntu splash screen.

Sorry for the time period between posts i had allot of family *stuff* to sort out over the last couple of days.

many thanks 

dc

---

### Post by Hippytaff on 2010-11-02
have a read of this, I haven't read it thoroughly (I have small children and one of them needs me to do something right now...right now) but it might help

[B][http://embraceubuntu.com/2006/02/20/restoring-the-ubuntu-usplash-after-a-kubuntu-install/](http://embraceubuntu.com/2006/02/20/restoring-the-ubuntu-usplash-after-a-kubuntu-install/)

[/B]

---

### Post by matt_symes on 2010-11-02
Hi

Does this help in any way.

[http://www.ubuntugeek.com/how-do-you-change-the-boot-splash-screen-image-for-10-04-lucid-lynx.html](http://www.ubuntugeek.com/how-do-you-change-the-boot-splash-screen-image-for-10-04-lucid-lynx.html)

EDIT: Actually just tried it so no.

Kind regards

---

### Post by matt_symes on 2010-11-02
Hi

Go to synaptic package manager and see if you have 

plymouth-theme-kubuntu-logo 

installed. If you have uninstall it then install

plymouth-theme-ubuntu-logo

See if that works.

Kind regards.

---

### Post by Hippytaff on 2010-11-02
out of interest, what is the result of
```
[FONT=monospace]
[/FONT]cat /etc/X11/default-display-manager

```

---

### Post by 1984dc on 2010-11-03
I tried to uninstall the plymouth-theme-kubuntu-logo and re-install the plymouth-theme-ubuntu-logo as, but i'm still getting the same kubuntu splash screen on boot up. 


The result of  

```
cat /etc/X11/default-display-manager
```

is /usr/sbin/gdm so that seems to be right??#-o 

To be honest i am getting tempted just to leave it as it is, bearing in mind it is purely an aesthetic problem (though an annoying one!!)

Once again many thanks.

dc

---

### Post by Hippytaff on 2010-11-03
I got so annoyed I removed all Windows managers and reinstalled GDM. But that is a bit extreme (I am quite fussy though) :-)

---

### Post by matt_symes on 2010-11-03
Hi 

Sounds like you should have the correct theme installed. Now type in a terminal
sudo update-alternatives --config default.plymouth

This should give a list of configured plymouth themes you have installed. 
One should be ubuntu (ubuntu-logo.plymouth). Select it.
After that type
sudo update-initramfs -u


to update. Then reboot.


Kind regards

---

### Post by 1984dc on 2010-11-05
This project is going to have to go on the backburner for the time being as my hole gnome architecture (along with all of my other window managers seems to have crashed leaving nme in a *login of death *scenario (where ebvery ime i try to login it asks me for my password again and again ad infinitum). 
 
For the time being i'm just backing up my data using windows (as i dual boot) and i suppose i'll reinstall ubuntu maybe formating the drive again, but this will all go in a new post once i've recovered all my data.
 
Many thanks for all your thoughts on the problem with the splash screen though.
 
All the best.
 
Dc.

---

### Post by Hippytaff on 2010-11-05
might be worth having a look at this [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
and if the link doesn't solve it for you, check out the site,because there's probably a fix there somewhere for you

---

### Post by 1984dc on 2010-11-23
Ubuntu back up and running again :guitar:

I tried; 

```
sudo update-alternatives --config default.plymouth
sudo update-initramfs -u
```

But the Kubuntu splash still remains after choosing the ubuntu gnome plymouth theme.

I don't really want to completely remove Kubuntu desktop as i do like to use it along side Gnome which i use as my main desktop.

Many thanks 

Dc

---

### Post by 1984dc on 2010-12-01
bump

---

### Post by xxodd on 2010-12-06
See [http://tuxtweaks.com/2010/04/how-to-select-the-splash-screen-in-ubuntu-lucid/](http://tuxtweaks.com/2010/04/how-to-select-the-splash-screen-in-ubuntu-lucid/)

This helped me with the same issue.

---

### Post by pauljwells on 2010-12-06
matt_symes already gave you the right answer:

sudo update-alternatives --config default.plymouth

---

### Post by 1984dc on 2010-12-08
Thanks pauljwells but that's a pretty unnecessary post, this may well be the solution in most cases, but on my box (and don't ask me why) this does not solve the incorrect splash screen error. 
I always try the code at least twice before posting a response on here to allow for any human error on my behalf, so I *know*that this code does not work for this particular problem, but thank you for your post.

xxod I had a look @ the link, but unfortunately once again the problem still persists, but many thanks for your post neway :)

please keep posting ideas though & hopefully we&#314;l crack it :D


Once again many thanks 


Dc

---

### Post by matt_symes on 2010-12-08
Hi

Still  no joy? I am running out of ideas.

What the the output of the following command?

ls -l /etc/alternatives/default*

Post back here. Lets follow your symlinks.

Kind regards

---

### Post by 1984dc on 2010-12-14
The output of 
ls -l /etc/alternatives/default*
Is ; 
lrwxrwxrwx 1 root root 53 2010-12-08 20:08 /etc/alternatives/default.plymouth -> /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth

Thanks 

Dc

---

### Post by matt_symes on 2010-12-14
Hi

> **1984dc said:**
> The output of
ls -l /etc/alternatives/default*
Is ;
lrwxrwxrwx 1 root root 53 2010-12-08 20:08 /etc/alternatives/default.plymouth -> /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth


That looks alright. What is the output of...

cat /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth

Post the result back.

BTW: I am currently setting up a VM with a fresh copy of Ubuntu 10.10 installed in it. I am going to try to recreate your current situation.

Kind regards

---

### Post by matt_symes on 2010-12-14
Hi

Well, I just installed Ubuntu 10.10 in a VM.

I then installed KDE

```
sudo apt-get install kubuntu-desktop
```

and had the KDE boot splash. In your posts you have said you wanted to keep KDE but just remove the KDE splash screen, so this is what i did.

I uninstalled

plymouth-theme-kubuntu-logo
plymouth-theme-kubuntu-text

using synaptic.

I then checked the ubuntu plymouth theme was still installed using synaptic.

plymouth-theme-ubuntu-logo
plymouth-theme-ubuntu-text

It was. I then typed

```
sudo update-alternatives --config default.plymouth
```

and this was the response (as was expected)

matthew@ubuntu:~$ sudo update-alternatives --config default.plymouth
[sudo] password for matthew: 
There is only one alternative in link group default.plymouth: /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth
Nothing to configure.
matthew@ubuntu:~$ 

I then typed...

```
sudo update-initramfs -u
```

It recreated initramfs and after a reboot i only had the Ubuntu Plymouth splash, but still had the ability to select Gnome or KDE from the log on screen. 

Is this what you did?

Kind regards

---

### Post by 1984dc on 2010-12-16
Okay thats done it!

It was the plymouth-theme-kubuntu-text file that I needed to uninstall to recover the original splash screen.

Many thanks once again :D

DC

---

### Post by matt_symes on 2010-12-16
Hi

My pleasure. Could you mark the thread as solved please. It helps others searching for a solution.

Kind regards.

---

### Post by 1984dc on 2010-12-17
Whoops i forgot!

Now marked as [SOLVED]. Thanks for all your help.

All the best 

Dc

---

### Post by tbhatia4 on 2012-03-09
> **matt_symes said:**
> Hi

Well, I just installed Ubuntu 10.10 in a VM.

I then installed KDE

```
sudo apt-get install kubuntu-desktop
```

and had the KDE boot splash. In your posts you have said you wanted to keep KDE but just remove the KDE splash screen, so this is what i did.

I uninstalled

plymouth-theme-kubuntu-logo
plymouth-theme-kubuntu-text

using synaptic.

I then checked the ubuntu plymouth theme was still installed using synaptic.

plymouth-theme-ubuntu-logo
plymouth-theme-ubuntu-text

It was. I then typed

```
sudo update-alternatives --config default.plymouth
```

and this was the response (as was expected)

matthew@ubuntu:~$ sudo update-alternatives --config default.plymouth
[sudo] password for matthew: 
There is only one alternative in link group default.plymouth: /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth
Nothing to configure.
matthew@ubuntu:~$ 

I then typed...

```
sudo update-initramfs -u
```

It recreated initramfs and after a reboot i only had the Ubuntu Plymouth splash, but still had the ability to select Gnome or KDE from the log on screen. 

Is this what you did?

Kind regards

i did the same you sugessted going to reboot fingers crossed

---

### Post by oldos2er on 2012-03-09
Closed, necromancy.

---

