---
title: "Password and Log In"
date: 2012-08-07
forum: General Help
---

### Post by JackH15911 on 2012-08-07
Hello all - first post. I've used Linux before but am not anywhere near being a guru.

I installed Kubuntu 12.04 on a fifteen-year-old Pentium II (384 MB RAM) and it seems to run well enough, once I moved over to the Gnome desktop - the default had the system constantly working and chattering.

On install, I checked the "no password required" box. On that same screen, however, I did enter a password. (This box will be a web browser box only, for relatives who don't do  anything else with a computer - I'm tired of cleaning viruses off  their Win XP machine).

Now Kubuntu requires that password for log on, and, what's worse, uses that password as su, so I'm now in the bad position of having to give my relatives as password to remember that will allow them (or other visitors) to mess with the system.

So, if possible, I'd like one of two things:

1 - Allow no password log on and keep the current password as su, or

2 - (not quite as good) two separate log ons, one for the user and the second for the su.

I'd appreciate whatever help you can offer. Please forgive me in advance if I follow your suggestion with, "How do I do that?"

---

### Post by ranger1021994 on 2012-08-07
1 - Enable Automatic Logon from System settings>User
  - Open terminal and type
   > sudo passwd
It will ask your sudo command password ie. login password
Now enter your NEW UNIX password ie. your su password

2 - You can create user accounts but su account is already present,it is the ROOT account.


See if this helps :)

---

### Post by houseworkshy on 2012-08-07
I haven't used Kubuntu for a while but am using KDE on mepris.  This is differant as it is closely based on debian in which one has two passwords, the su and user.  
As far as I recall Kubuntu shouldn't be using a su at all unless you have specifically told it to.  It should only be sudo in day to day use.  A look in "users" would be informative.  On Gnome it'd be in Administration tools.  
I've just looked in my own machine in order to confirm how it is done but I have a "mepris user assistant" instead.
Some manual pages you could look at via the terminal would be "man sudo",  "man su" "man passwd" and "man sudoers". The last of those may be the command you need to use in order to work out what is going on.

Why not set up password less accounts for the people you want ( if they utterly refuse to use passwords, terrible idea but I've known some like that so can empathise ) and configure permissions for all the things you choose to allow them to do.  AND set up your own password admin account.  

You could, from that admin account, set the machine up to update itself in your absense.  You would still have to visit the machine every time one of the none admin users wanted to install anything but at least it should remain unbroken and updated.

I've never checked the no password login button so these are only ideas and a bump rather than informed help.

---

### Post by JackH15911 on 2012-08-07
Thanks - may I have a bit more detail, please?

Konsole
sudo passwd
- then I enter my root password, as normal for su use, I suppose (I've used "su," but not "sudo".)

How/when do I enter my New root password? Is there another prompt?

---

### Post by houseworkshy on 2012-08-07
If the you are sure that the su account has been enabled documentation is in the same area as here but look at this first 
[https://help.ubuntu.com/12.04/ubuntu-help/user-accounts.html](https://help.ubuntu.com/12.04/ubuntu-help/user-accounts.html)

I searched via the term kubuntu just in case I was wrong but still landed here anyway.  Ubuntu and Kubuntu are essentially the same underneath which is why I suppose.

---

### Post by steeldriver on 2012-08-07
I think there's some confusion here

Whether you choose passwordless login or not, the password that you supply during install is the password for the primary named user - NOT the super user (root) password. Ubuntu doesn't normally set a root password, instead it relies on elevated privileges defined via the 'sudo' mechanism:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Even with passwordless session login, you will be asked for this password in order to perform any actions that require elevated (sudo) privileges.

In order to do what you want, you can create a new user account and make that a member of group 'sudo' - this will then become your primary admin account. Then you can remove the original user from group 'sudo' making it a 'regular' user.

---

### Post by JackH15911 on 2012-08-07
There's no question in my mind as to there being confusion - I defne the state.  Steeldriver is correct. I am not able to use "su" in this install.

 My use of "su" was in different distros leading up to this one and I assumed...  I suppose I also assumed that because I installed it I was automatically root. Assumed again... 

Thanks for the root/sudo link; it explains why my gui package management worked with the user account that I assumed was root.  Assumed once more...  At least now I know to precede a command with "sudo" in Konsole.

Okay, then perhaps all I need is another user account not sudo capable that preferably doesn't require a password. I presume at logon then there will be two choices if I do it that way. If this is correct how will I start?

---

### Post by JackH15911 on 2012-08-07
Thanks, all - I have it figured out.

houseworkshy's link didn't look exactly right, but a reboot fixed that. I added a new user account and finally figured out the button had to be set to "off," rather than "on" to allow password-less logons. Then I figured out that might not be a good idea for someone who's still searching for the ideal desktop, as it automatically logs me on to the last one. Finally, I figured out that I never had had a problem at all, given that the main account isn't a su/root account, anyway, so anyone on the basic account would have to know the password in order to make any changes.

So, this problem is completed - thanks again.

---

