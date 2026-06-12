---
title: "Logoff script"
date: 2010-06-25
forum: General Help
---

### Post by J V on 2010-06-25
I hear ~/.bash_logout doesn't run in X...

I've heard a lot of different potential options for this, but all of them have flaws: I need this script to run on logoff, shutdown and reboot (Poweroffs can be ignored)

Anyone know how to do this?

I understand ~/.profile does run every time a user logs in yes?

---

### Post by gzarkadas on 2010-06-25
[B]User Logout
[/B]Modify /etc/gdm/PostSession/Default (or just place a script in the directory /etc/gdm/PostSession; didn't try that one)

References (see especially the later):
[URL="http://ubuntuforums.org/showthread.php?t=45184"]http://ubuntuforums.org/showthread.php?t=45184
[/URL][http://www.linuxquestions.org/questions/linux-desktop-74/gnome-run-script-on-logout-724453/](http://www.linuxquestions.org/questions/linux-desktop-74/gnome-run-script-on-logout-724453/)

[B]Shutdown, Reboot
[/B]Make a startup script in /etc/init.d (use one of the installed there as a template) and then use from a terminal the `update-rc.d' command to install the appropriate start-stop links at the /etc/rcX.d/ directories.

The easiest setup would be IMO to make one script in /etc/init.d and just call it from within /etc/gdm/PostSession/Default.

---

### Post by J V on 2010-06-26
I assume that I should use .profile for login?

Edit: Gnome says X will already be closed by the time PostSession runs, this sounds more like what runs when the entire system is shut down...

Theres got to be a more lower down way to do this...

---

### Post by gzarkadas on 2010-06-26
> **J V said:**
> I assume that I should use .profile for login?
Yes, you can, it is sourced by /etc/gdm/Xsession.

> **J V said:**
> Edit: Gnome says X will already be closed by the time PostSession runs, **this sounds more like what runs when the entire system is shut down**...
No it is not, X closes and then the graphical login screen is displayed. I confirmed (by writing a file) that the post session script is indeed get called.

If you want to find where exactly the script is get called, make it contain a
```

ps -A > /<postsession-log-file>

```Do inside a terminal window:
```

ps -A > /<insession-log-file>

```and logout. Then login again and diff the two logfiles. In particular see if X is still there. You could also put extra information such as the caller, etc.

> **J V said:**
> Theres got to be a more lower down way to do this...
If it is it will be inside X; check the /etc/X11/Xsession script; it may give a clue.

---

### Post by J V on 2010-06-26
So basically, put some code in .profile and some more in PostSession/Default with an if statement checking the which user...

Ok, not as clean as .bash_logout could have been, but it works I guess... Don't suppose .bash_logout works eh? You'd think canonical would fix that...

---

### Post by gzarkadas on 2010-06-26
Well, as stated [here]("http://www.linuxfromscratch.org/blfs/view/cvs/postlfs/profile.html"):
> The file ~/.bash_logout is not used for         an invocation of the shell. It is read and executed when a user exits         from an interactive login shell.The point is that /etc/gdm/Xsession is not run by an interactive login shell, but instead it is executed as a script (see the last paragraph at the header comments, inside it). This is why .bash_logout is not executed.

Now what I don't know is if it *can* be made to execute this way (through /etc/gdm/PostSession/Default):

1. find the user
2. source his/her ~/.bash_logout

The thing to consider is whether there is a reason that this wasn't fixed (for example it is called from elsewhere) or not. A test that can be made is the following:

1. Put some commands in .bash_logout to output a message to a file. 
2. Check if during a graphical login/logout this message gets output (just re-login and open the file).
2a. If yes, .bash_logout is invoked from somewhere else
2b. If no, .bash_logout is not invoked
3. Check if during shutdown this message gets output (just re-boot). I don't expect it to happen but should be checked to be sure.
3a. If yes, .bash_logout is invoked from somewhere else (this would be strange)
3b. If no, .bash_logout is not invoked
4. If the answer of 2 and 3 is no, then it is safe to invoke .bash_logout from /etc/gdm/PostSession/Default (in the sense that it is not called twice).

---

### Post by J V on 2010-06-26
```
# Runs .bash_logout on GDM logout
sudo -u $USER sh ~/.bash_logout
```This works... turns out .bash_logout only works when logging out from a shell (Aka, tty 1 through 6)

This will run a users .bash_logout script...

One problem: PostSession only runs on logout, not on shutdown or restart... And .profile only runs on GDM login... Not text based... Someone really needs to standardize around .bash_logout and .profile: This is a pain...

---

### Post by gzarkadas on 2010-06-26
If PostSession is not run on shutdown/restart then the setup I can think to make things work as expected is the following:

1. A start-up script in /etc/init.d is created to inspect a given file, writable by root only (say /var/lib/<script-name>/logged-users). Clear its contents on start, read them on stop. Add to it a custom logout parameter.

2. In each users .profile set a command to append the userid in that file. Do this through a script that can do error checking (for example verify that the user is indeed logged in; a user may forge this command since it is in its home folder) and also avoid duplicates. The easiest path is to have a parameter-less command; this will ease sudo config on step #3. 

3. Put the script #2 in root-land (outside /home) and give only read-exec perms to users. In order not to make it setuid, prepend writes to file #1 above with sudo and give users permission to execute the script without password through /etc/sudoers. There is a nice howto on this; see the howto of the month sticky on the Tutorials and Tips forum to locate it.

4. In /etc/gdm/PostSession/Default run the startup script with logout parameter

5. Now the script algorithm:
start: clean the file (the users will update it as they login).
logout: locate the logging-out user entry, delete it from file and run his/her .bash_logout.
stop: run the .bash_logout for all entries of the file; optionally clean the file just to be sure.

---

### Post by J V on 2010-06-26
Well, that's an over complicated method of doing things, and seeing as one of these accounts is publicly accessible, it really needs to run every logoff before someone else gets there...

Is there a way to stop people having permissions to shutdown/use other TTYs?

---

### Post by J V on 2010-06-27
I guess this will work... but someone with decent skills might shutdown rather than logoff, then login from a diff TTY, and get access to the data of whoever was there last...

---

### Post by gzarkadas on 2010-06-27
I must admit that I lost you here :). What is the specific task that you want to accomplish through those scripts? 

In any case, I think (at first consideration - without knowing the exact target application) the setup I have sketched is not vulnerable to that kind of manipulation. Users just call a "system" routine to register their login so that an exit script (logout/shutdown) is run when the event happens.

---

### Post by J V on 2010-06-28
Theres this old computer that will be publicly accessible: To protect user data it should delete the ~ (Except for the scripts of course) and copy the default one over every login.

At the moment they are using winXP no SP, no AV, no firewall, so they probably couldn't care less...

But still, it would be nice to plug the tiny hole... And I have no idea/experience/intention to use rc.d scripts... xD

---

### Post by gzarkadas on 2010-06-28
You 'll have to define in more detail the usage scenario (how is this public computer will be accessed, by whom, will users be left unattended for a long time, how much they are trusted, etc.) to close the big holes first, such as the ability to restart in single user (root) mode, etc.

Regarding the user home issue, if you want a secure setup for highly untrusted users, then you must abandon the .profile, .bash_logout scripts and in general everything inside the user home folder because even a mildly competent user can overwrite them; all your script magic must reside in root-land ie in /etc , /usr/local and maybe /var.

If you don't want to fiddle with rc.d scripts, just put: 

[LIST]
[*]in /etc/gdm/Init/Default a command to clear everything and copy the defaults (this is done before the login screen even appears).
[*]in /etc/gdm/PostLogin/Default a command to create a brand new home for the user.
[*]in /etc/gdm/PostSession/Default a command to delete the home for the user.
[/LIST]
and make all home directories unreachable to other users (set permissions as per:
```
chmod -R g-rwx,o-rwx /home/<user>
``` for each user's home folder and also set ```
umask 077
``` inside /etc/profile).

See for reference:

[LIST]
[*] Securing Debian: [http://www.debian.org/doc/manuals/securing-debian-howto/index.en.html](http://www.debian.org/doc/manuals/securing-debian-howto/index.en.html), in particular section 4.
[*]GDM Manual: [http://library.gnome.org/admin/gdm/2.30/gdm.html](http://library.gnome.org/admin/gdm/2.30/gdm.html)
[/LIST]

---

### Post by J V on 2010-06-28
First, of course I'm going to set ownership and write to root only on .profile and .bash_logout...

Second: There will be only one account (I'd use something like the internet cafe stuff but from the looks of it they all need a server machine to run) for the guests to use...

Most of the users are naive, and those who aren't don't know squat about linux...

---

### Post by gzarkadas on 2010-06-28
> **J V said:**
> Most of the users are naive, and those who aren't don't know squat about linux...But they can learn, can't they? ;)

Having just one guest user account makes things easier; you know what to delete everytime :p. So, here what I propose:

1. Create your user (lets call him `johndoe').
2. Customise your user's home directory to the point you are satisfied.
3. Copy the entire johndoe directory to another folder and give ownership to root
```

sudo cp -a /home/johndoe/ /home/johndoe-template/
sudo chown -R root:root /home/johndoe-template

```4. Modify /etc/gdm/Init/Default to contain these lines:
```

rm -Rf /home/johndoe
cp -a /home/johndoe-template/ /home/johndoe/
chown -R johndoe:johndoe /home/johndoe

```5. Do the same modification to /etc/gdm/PostSession/Default.
6. Secure the startup sequence of the computer by applying the instructions set out in "Securing Debian", sections 4.3-4.6 (link is in my previous post).
7. Test: Enter as guest an try to crack the scheme by any means you can think of; if you can't then you are done.

---

### Post by J V on 2010-06-28
Nah, not worth the effort... besides duplicating effort whenever the admin logs in, Debian 4.3-4.6 still allows for a malicious user to log into TTY1 and get access to files that may have belonged to a user who shutdown rather than logged off...

I'll just leave the hole there, it's not like it will be a big problem, and even then it will only effect the last user on the system, not everyone... And then theres the old maxim of "If someone has physical access to your computer, you're doomed"

---

