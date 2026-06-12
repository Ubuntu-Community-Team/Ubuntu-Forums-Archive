---
title: "Could not update ICEauthority file..."
date: 2010-02-18
forum: General Help
---

### Post by hiakaash on 2010-02-18
I've updated my password some days back and when I restarted my machine I got error messages stating...

1. **Could not update ICEauthority file** /home/*username*/.ICEauthority
it gives me only          xClose  tab and when I click it I get another error message saying...

2. There is a problem with the configuration server.
    (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)
   xClose
and the last message which i get says that...
3. Nautilus could not create the required folder "/home/*username*/Desktop".
    Before running Nautilus, please create the following folder, or set permissions such 
    that Nautilus can create it.   

Now every time when I restart my machine I've to follow this procedure...
1. I select my username and then login using xterm.
 2. I give command ecryptfs-mount-private and give another password to mount it  (it's not taking my regular password)
3. After doing this it takes me back to the login screen and allow me to log in normally...
   I'm sick of following this procedure again & again... I'm screwed...help me...
](*,)

---

### Post by bingobingo on 2010-02-19
Gee, how nice I am not the only one in the camp that this insanity came too. I got the same thing two days ago and have not the clue what to do next. WTH!

---

### Post by XpplicitLeX on 2010-02-19
Quick story what happened to me. 

I ran klamav as sudo (big mistake) started up the next day and got C N Upd ICEauth file. Surfed through a few posts tried many chown and chmod, then got the sanity 256 error and nautilus. Then today I'm home sick and was working on my netbook to get it fixed cause I didn't want to reinstall and have to re-setup.

I tried this and it worked perfectly, I'm still a bit shocked it worked but am happy to have my computer working again.

Boot up how you normally would

CTRL-ALT-F2

Login 

sudo chmod 755 /home/(user)/


I hope it works for you.

---

### Post by mlissner on 2010-02-22
I have an encrypted home directory too, and just started getting this error. I didn't change any passwords though, so I'm pretty annoyed at whatever made this config come up.

I do have auto-login enabled though, so maybe that has something to do with it, but that's nothing new.

---

### Post by hiakaash on 2010-02-23
> **XpplicitLeX said:**
> Quick story what happened to me. 

I ran klamav as sudo (big mistake) started up the next day and got C N Upd ICEauth file. Surfed through a few posts tried many chown and chmod, then got the sanity 256 error and nautilus. Then today I'm home sick and was working on my netbook to get it fixed cause I didn't want to reinstall and have to re-setup.

I tried this and it worked perfectly, I'm still a bit shocked it worked but am happy to have my computer working again.

Boot up how you normally would

CTRL-ALT-F2

Login 

sudo chmod 755 /home/(user)/


I hope it works for you.
ahh...it didn't work...it just created a new profile for my user name and i still have to run xterm and give command ecryptfs... to mount my home folder...

---

### Post by d3v1150m471c on 2010-02-23
Have you tried fixing the broken packages in recovery mode? It seems like this happened to me once and that fixed it. I want to say this is caused by opening graphical apps with sudo instead of gksudo/kdesudo.

---

### Post by Knb15 on 2010-02-23
> **XpplicitLeX said:**
> Quick story what happened to me. 

I ran klamav as sudo (big mistake) started up the next day and got C N Upd ICEauth file. Surfed through a few posts tried many chown and chmod, then got the sanity 256 error and nautilus. Then today I'm home sick and was working on my netbook to get it fixed cause I didn't want to reinstall and have to re-setup.

I tried this and it worked perfectly, I'm still a bit shocked it worked but am happy to have my computer working again.

Boot up how you normally would

CTRL-ALT-F2

Login 

sudo chmod 755 /home/(user)/


I hope it works for you.

I had tried other things that had not worked. However, this solution worked!

Thanks!

---

### Post by pacmanic91 on 2010-02-27
:O

Oh my...

The simplest solutuion, that i don't even understand, works!!

Try XpliccitLex's solution (above)

Thanks so much!

---

### Post by marc1uk on 2010-03-10
I had this problem after trying to change my password from the user preferences menu. Something went wrong though, and next time i tried to log in, I was told the new password was incorrect, but the old one gave me these .ICEauthority errors.
Turns out the problem's to do with having chosen to encrypt my home directory. (there's a good simple explanation here; [http://ubuntuforums.org/showpost.php?p=8646710&postcount=8](http://ubuntuforums.org/showpost.php?p=8646710&postcount=8))
 
 Basically it seems your login password is used to decrypt a longer passphrase used to mount your /home/user (including .ICEauthority etc. that you need to start a gnome session). 
 While the login system didn't update, the password to decrypt my /home did, so whichever i used I couldn't login and start a gnome session.
 
 tl;dr: The fix was just to change my login password to the same password I'd tried to earlier, using "passwd user" in a root shell (accessible from booting into recovery mode -> drop to root shell prompt). 
 
 This meant my login password coincided with the password to decrypt my /home, and it's all good. :)

---

### Post by amgalitz on 2010-03-15
A simpler solution that solved the problem for me was to reboot using the last working kernel from the grub2 menu.

After applying several weeks worth of updates including taking the kernel from 2.6.31-19-generic to 2.6.31-20-generic, our computer threw errors similar to these on the first reboot. The first was the ICEAuthority file then several more which I did not record. There are two users on this machine and one has their home directory encrypted with truecrypt. The system showed only one user (the original with the encrypted /home). Upon logon, the gnome desktop was completely blank except for the default gold sand background.

Before trying any of the fixes listed above, I rebooted using the previous kernel grub2 entry, 2.6.31-19-generic, and the system booted normally, showing no errors and all users available at the usual logon screen. After this, rebooting with the new 2.6.31-20-generic kernal entry also was fine.

It seems, a normal boot even with an older kernel cleared the issue for me. I am sorry to be so vague about the error messages, but I tried this just as I was starting to work the problem and since it no longer exists, I can't reproduce it. I do have several other machines to upgrade and will save some diagnostic data if it pops up.  They are not running truecrypt (which may have nothing to do with this)

Is this working for others?
Could someone suggest the best places to look for the root cause so others don't get this and give ubuntu a bad rep?

cheers

---

### Post by Flos Headford on 2010-04-08
This worked for me:
Use a Ubuntu Live CD to boot up, and choose a command-line (shell) option.
With this, set your $HOME directory (/home/username) permissions to something appropriate (I used 755) and make sure all directories can be listed with the "ls" command. Then remove nautilus with ```
sudo apt-get remove nautilus
``` and delete the .ICEauthority entry in $HOME, and possibly in /var/lib/gdm. Then reboot with ```
sudo shutdown -r now
``` When you choose the same option on boot-up, from the command line you can use ```
sudo apt-get install nautilus
 sudo shutdown -r now
``` and retrieve the CD a bit smartish. I do hope you get a clean straight boot and login, as I did!
with thanks to all who helped me,
Phil

---

### Post by Flos Headford on 2010-04-08
This worked for me:
Use a Ubuntu Live CD to boot up, and choose a command-line (shell) option.
With this, set your $HOME directory (/home/username) permissions to something appropriate (I used 755) and make sure all directories can be listed with the "ls" command. Then remove nautilus with ```
sudo apt-get remove nautilus
``` and delete the .ICEauthority entry in $HOME, and possibly in /var/lib/gdm. Then reboot with ```
sudo shutdown -r now
``` When you choose the same option on boot-up, from the command line you can use ```
sudo apt-get install nautilus
sudo shutdown -r now
``` and retrieve the CD a bit smartish. I do hope you get a clean straight boot and login, as I did!
With thanks to all who helped me,
Phil

---

### Post by mirchichamu on 2010-08-20
I was having the same problem when I created a new account for my wife but used to get the same errors what you described. Actually I opted to sign in without password being asked. When I opted to be asked for password on log in, in users and groups then I was able to log in. I don't know why they have created this option when it is not working?

I have replied to this post because I want to benefit those who may be having the same problem.

---

