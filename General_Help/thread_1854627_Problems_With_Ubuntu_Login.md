---
title: "Problems With Ubuntu Login"
date: 2011-10-04
forum: General Help
---

### Post by hockeystar711 on 2011-10-04
Hello,

Two days ago, I dual installed Ubuntu Natty with my windows 7 laptop.  After a while, I got it to actually start, and then I was absolutely in love with it.  Then, while I was looking at all of the cool settings and options like I always do, I found one about "Automatic Login."  I was like sure, what the heck, idk what that means but we'll go with that.

Now, I kept going and customizing things and forgot about it, until i rebooted.  Then, when it booted up to the log-in screen, it said "Jayden" and so I clicked on it and it went "permission denied."  The same happened for all of the options, including underneath it "Automatic Log-in" and "Other." 

I have since then been doing constant google searches to find an answer, and have not found a single person with this exact problem...but I have tried to implement several methods that I hoped would work.  I have added two separate accounts, moved them between "groups" like admin and nopasswdlogin...same result.

Also, I cannot for the life of me log into the tty terminal, I have to run these by booting into "recovery mode" and starting a root shell.  anything i try with a password turns up something along the lines of "Permission denied; Password will remain unchanged."  One of the more recent attempts it said something about Password expiry something has changed...

Anyways,  thank you to anyone who reads this novel of a post.  I hardly ever actually post with  questions, as I usually find answers, but this is truly evading my every attempt at finding a solution.   My last resort is to re-install...or go back to Windows 7...yuck.

Thanks again,
Jayden

---

### Post by grahammechanical on 2011-10-04
What I think is strange about this saga is that you checked Automatic log-in and Ubuntu did not do it. Automatically log you in, that is. It should not have given you a log-in screen. It should have just booted into the desktop.

Did you set up more than one user? If so were you logged in as another user at the time that you were experimenting?

Regards.

P.S. It occurs to be that you may have give yourself a new user name and password or change your password and give yourself administrator privileges. There are commands to do this from recovery mode. I have seen them in other posts.

---

### Post by hockeystar711 on 2011-10-04
grahammechanical,

Yes, although I didn't know exactly what it would do, I agree that it is strange...I only had one user at the time of experimenting.  However, in my many different attempts to somehow get into ubuntu, I created 2 more accounts.  

One time, I did eventually get into a sort of "desktop" and I believe the user was "root" when I browsed some files.  There was no launcher, just a blank desktop, my mouse, and I made a shortcut or two.  Very strange.  I've tried several different things, and what mostly concerns me is that while I'm at the log-in screen I get no option to type a password.  For any of the accounts.

Any suggestions as to how to continue are appreciated, I would love to get back into Ubuntu.

Thanks.

---

### Post by hockeystar711 on 2011-10-05
So, I have now deleted the /etc/gdm/custom.conf file entirely...

My main concern is this: At the log-in screen, I get no option to enter any passwords on any account.  There is no error, it just doesn't do it.  And if i click it enough times in a row, I can see it flash "permission denied" while it comes down, and then zooms back out.

I cannot edit any sort of password, other than group passwords apparently (found that one today, not helpful as of yet), I always get the permission denied.  Still trying to fix this without re-installing.

Thanks again.

---

