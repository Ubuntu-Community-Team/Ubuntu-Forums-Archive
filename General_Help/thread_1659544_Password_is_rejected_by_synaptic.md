---
title: "Password is rejected by synaptic"
date: 2011-01-04
forum: General Help
---

### Post by Scunnered on 2011-01-04
I have come up with a problem when attempting to use synaptic or Ubuntu software centre.  No matter what I try neither will accept my password.

I recently changed the password via sudo and everything worked well and I am able to login to the system but nothing else.  As my system is used for the majority of the time at home I have my login set to automatically login.  As this is the only password in use what can I do to be able to download software.

As the password is set to automatically work is there the ability to have synaptic and the software centre to similarly auto register?

I took the care to make a mental note on a piece of paper of my password so I know that what I am entering is correct. I am well confused at it not being accepted.

Your kind assistance will be appreciated

---

### Post by ridgeland on 2011-01-04
Did you try Menu -> System -> Administration -> User&Groups.
There you could try to set the password again.  I don't know about using sudo to set the password.  Sounds like you may have set root's password rather than your user password.  Does the old password work still?

---

### Post by Scunnered on 2011-01-05
Thanks for your reply.

Had a look at your suggestion and found that when I attempted to change it rejected the current password.  Old password does not work.

Looks very much like I will have to do a fresh install unless someone comes up with an another way of rectifying the problem.

Again thanks

---

### Post by ridgeland on 2011-01-05
I just tried this on my sandbox partition.
$ sudo gedit /etc/passwd
delete the x in
my_user_id:x:.....
whoops I see that mr smilie steps on my code :(
that was supposed to be : followed by x followed by :
The x is the password.  This leaves my_user_id with no password.  Then log out.  Log in again and it doesn't ask for a password.  Go to the terminal
$ passwd
and it asks for your new password (no request for old password first)

Now the obvious question of how to use sudo gedit when you cannot use sudo.  That's why I always have a copy of [SystemRescueCD]("http://www.sysresccd.org/Main_Page").  It's a liveCD that will let you use root to change /etc/passwd on your hard drive.

---

### Post by MooPi on 2011-01-05
I've had this happen to me but instead of reinstalling try this first. From terminal ```
gksudo synaptic
``` You'll be asked for your password and hopefully the GUI for apt will pop up. This is definitely a bug as I've run into it a couple of times and heard 
others grumble about it. None of my current machines is exhibiting this bug though.
If your going to change your password the best and only way I've ever done it is at boot. Hit the shift key just after the bois flash disappears. This should give you the grub menu. Choose Recovery mode and then scroll down to root. From the root prompt type ```
passwd username_here
``` With username_here replaced with your actual user name. You'll be prompted to enter a new UNIX password then a confirmation. Reboot and password should be changed.

---

### Post by Scunnered on 2011-01-06
Many thanks for your replies.

I attempted to follow your details but kept falling by the wayside.

I suspect that as I have autologin for my password and wireless that either I am not quick enough or Lucid has taken over the world.

Ended up with a fresh install and am now able to download software.

Again my thanks for all your assistance

---

### Post by DukeBoxer on 2011-03-19
I'm having the same problems that seem to happen each time I have installed just a base system first and then a desktop (ubuntu-desktop in my case) I can also run synaptic starting it through the terminal but clicking on it from the System>Administration menu never accepts my password. The only way to fix it without reinstalling that I have read is by creating a new user with administrator privileges and switching to that user...oh well

---

### Post by jmszr on 2011-03-19
DukeBoxer,

You might want to try this: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) , first.

Edit: Doh! Same as post #5.

---

