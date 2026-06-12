---
title: "I've messed up big time!!!! Need help ASAP"
date: 2011-02-24
forum: General Help
---

### Post by legend_gibby on 2011-02-24
Right here goes.

I changed the settings for my urs file so I could change and add new ones to the files!
I did this thru "gksudo nautilus" program!
I then saved the settings then exited that program! Then all of my programes wouldn't work such as the vlc and appearance settings! So on and so forth!

I then switched the comp off and then back on and now I can't get onto the desktop at all! Think it is to do with me changing the files access From root!

So I need to change the usr file back to root! How can I do that so my comp will load up the desktop!?

I was told to login and then load up terminal!  But I can't even get to this part of ubuntu! There must be away for me to do this without loosing all my files and stuff on my comp!

This is what I get when I start up my comp. I get alist of:-
Ubuntu, with Linux 2.6.35-25-gereric
Ubuntu, with Linux 2.6.35-25-generic (recovery mode)


So I picked the first one then I get a list of commands
Pretty much all of them have permission denied at the end of them!
And then just stops! So I have to sworn I off again!

Then if I pick the second one, same thing again but this time
The last command says:- root@James-A0751h:~#
now I don't know what to do after that!

Need help fast!

---

### Post by wiggly81 on 2011-02-24
never had to do anything like this myself yet but maybe this will help you

in recovery mode
sudo nano /path/to/file/that/you/edited

---

### Post by neu5eeCh on 2011-02-24
If it were me (and I'm not a hacker) the first thing I would do is to boot up a live CD, then mount the hard drive. From there, I would copy my home folder (or the important files therein) to a USB Key or whatever. 

Secure your files first.

Then, still using the live CD, you should be able to make any changes (if you know what those changes need to be) to your filesystem. On the other hand, once you've backed up your files, it might be quicker just to reinstall Ubuntu. I've done that any number of times.

P.S. Oh, did I mention? You reap what you tweak.

---

### Post by legend_gibby on 2011-02-24
> **wiggly81 said:**
> never had to do anything like this myself yet but maybe this will help you

in recovery mode
sudo nano /path/to/file/that/you/edited

Ok it was the usr file that I edited but I don't know if there is any other files in front of that! Aaaaaahhhhh I really don't want to reboot the OS again!

I was told to do this:- chown -R root:root /usr

What will this do?

---

### Post by legend_gibby on 2011-02-24
> **VTPoet said:**
> If it were me (and I'm not a hacker) the first thing I would do is to boot up a live CD, then mount the hard drive. From there, I would copy my home folder (or the important files therein) to a USB Key or whatever. 

Secure your files first.

Then, still using the live CD, you should be able to make any changes (if you know what those changes need to be) to your filesystem. On the other hand, once you've backed up your files, it might be quicker just to reinstall Ubuntu. I've done that any number of times.

But the thing is I can't even get onto the desktop! And I loaded the ubuntu softwear with a USB stick! All I'm needing to do is change the folder i changed back to what it was!
It was the usr folder which is in the cdrive!

It just won't let me access the desktop at all!

---

### Post by neu5eeCh on 2011-02-24
OK, now I'm confused. I thought you made the changes on your hard drive? 

If you load a LiveCD, what you did to your HD install is irrelevant. You will get a desktop (a GUI environment) and from there, or so was my thinking, you can mount your HD and make the necessary changes? 

If it's the folder in the CD Drive, how did you change it? Is it a CD-RW?

[Edit:] I was just trying to get you back into a GUI environment, which is what you seemed most comfortable with (which is what I also prefer).

---

### Post by legend_gibby on 2011-02-24
> **VTPoet said:**
> OK, now I'm confused. I thought you made the changes on your hard drive? 

If you load a LiveCD, what you did to your HD install is irrelevant. You will get a desktop (a GUI environment) and from there, or so was my thinking, you can mount your HD and make the necessary changes? 

If it's the folder in the CD Drive, how did you change it? Is it a CD-RW?

[Edit:] I was just trying to get you back into a GUI environment, which is what you seemed most comfortable with (which is what I also prefer).

I forgot to mention I'm runing ubuntu on a netbook!

Can someone please tell me the folder that lead up to the usr folder in the hard drive?

---

### Post by wiggly81 on 2011-02-24
usr folder is located simply at /usr/

---

### Post by azmyth on 2011-02-24
I'd reboot in recovery mode. This is an option you'll see in Grub as you've already seen per your other post. It'll prompt you on what you want to do select root no networking. You'll be taken to a command prompt which will look like this # You won't get a gui.

simply enter the command "chown -R root:root /usr" without the quotes and then hit enter this will change all the files in the usr and sub-dir to the user group root. Reboot

---

### Post by legend_gibby on 2011-02-24
> **azmyth said:**
> I'd reboot in recovery mode. This is an option you'll see in Grub as you've already seen per your other post. It'll prompt you on what you want to do select root no networking. You'll be taken to a command prompt which will look like this # You won't get a gui.

simply enter the command "chown -R root:root /usr" without the quotes and then hit enter this will change all the files in the usr and sub-dir to the user group root. Reboot

Ok..... I re booted in recovery and got this : root@James-A0751h:~#

 So I entered what ya said and nothing happened! Just the same quote again!

Now what!

---

### Post by legend_gibby on 2011-02-24
Ok so I ran the root ya told me to do!
And when I run it it says at the end of every line operation not permitted!

Think I have totally messed up my netbook! Aaaaaahhhhh
Re instailling the OS might be the only way!?
Can anyone else help me out before I do this?

---

### Post by SeijiSensei on 2011-02-24
Did you run chmod with sudo or at the # prompt in recovery mode?  (I suggest the latter.) You can't chmod /usr as a normal user, only as root.

The only places you can/should touch as an ordinary user are /home/user and /tmp.  Everything else (other than things like USB drives mounted in /media) is off-limits.  If you try to save a file, and you get a "permission denied" error, save it somewhere you have permissions like your home directory.

---

### Post by legend_gibby on 2011-02-24
> **SeijiSensei said:**
> Did you run chmod with sudo or at the # prompt in recovery mode?  (I suggest the latter.) You can't chmod /usr as a normal user, only as root.

The only places you can/should touch as an ordinary user are /home/user and /tmp.  Everything else (other than things like USB drives mounted in /media) is off-limits.  If you try to save a file, and you get a "permission denied" error, save it somewhere you have permissions like your home directory.

Don't quite understand what ya mean by the first question!
Chmod? Not too sure how to! Was in the mode if ya press ctrl alt f1(but I didn't press this) so if I'm right in saying I have to run chmod? How do I do this!

Ur second statement is true and I now know not to touch this! Hahaha
So how do I run as root! Even tho I changed the file name! I can't change it back to root coz I don't have permission since I changed it!
I can't run sudo either!

---

### Post by neu5eeCh on 2011-02-24
//Did you run chmod with sudo or at the # prompt in recovery mode?  (I  suggest the latter.) You can't chmod /usr as a normal user, only as  root.//

> **legend_gibby said:**
> Don't quite understand what ya mean by the first question!
Chmod? Not too sure how to! Was in the mode if ya press ctrl alt f1(but I didn't press this) so if I'm right in saying I have to run chmod? How do I do this!

This is why I was trying to get you into a GUI environment with a live CD. What he means is that if you're logged in as root, you will see # at the command prompt. 

In my case, I would see something like this: vtpoet@traveller:~# instead of vtpoet@traveller:~$.

So... if you run the command chmod and your prompt is a $, the Terminal should tell you that you don't have the rights to change whatever file you're trying to change.

In that case, you either have to preface the command with Sudo or log in as root (and the latter will change the prompt from a $ to a #.

How are you communicating on this forum? You must be using a different computer. Google the command chmod if you're not in Linux.

---

