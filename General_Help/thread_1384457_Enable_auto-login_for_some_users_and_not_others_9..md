---
title: "Enable auto-login for some users and not others? 9.10"
date: 2010-01-18
forum: General Help
---

### Post by Buttons840 on 2010-01-18
I have Ubuntu on a family computer.  Other members of my family don't like entering the password to login.  I am using Ubuntu 9.10.

First, I would like to enable auto-login on boot for the family (non-administer) account.  Meaning when I turn on the computer, it automatically logs into the family account; and they never need to enter any passwords.

Second, under System -> Administration -> Users and Groups (users-admin from terminal) there is a "Don't ask for password on login" option (toggle) which is desirable for this family account.  However, I have never seen this option enabled, but always grayed out.  Is there any way to enable this option?

In short, I want:
1) For the family account never to require a password on login.
2) Automatically log into the family account on boot.

It seems like a common question, but I couldn't find any posts to help me.

Thanks.

---

### Post by Scunnered on 2010-01-18
If you try System > Administration > Login Screen you will be offered in the login screen settings the facility to automatically login.

I found that whilst this worked perfectly well it caused me to have to then provide my password to access my wireless connection every time.  As you can appreciate it was a pain.  If you need to login into your ISP if you right click on your network connection icon and select edit connection.  Highlight your connection and this should display editing auto and in the bottom left corner you will find the tick box against available to all users. Tick the box and then click apply and this will let you not only access your login but your wireless connection automatically.

Hope you find this of use.

---

### Post by LordHawke on 2010-02-06
This option seems to be disabled because of some features which require passwords for administrative tasks will not function properly if the user does not have a password. Some things such as sudo. Hopefully the execution bugs of such apps will be fixed in the future as this is a widely and greatly desired option.

There is a way to enable auto-authentication at the login screen. The user will still have a password and will require it for such apps the would prompt for one, but the login screen will skip the password prompt. Clicking on the user will login automatically. The steps are:

1.) Add the following line to **/etc/pam.d/gdm** just before the line [FONT="Courier New"]@include common-auth[/FONT]:

[FONT="Courier New"]auth sufficient pam_listfile.so item=user sense=allow file=/usr/local/etc/nopassusers onerr=fail[/FONT]

You need to either be root or run a text editor as root to do this. Since you're using Ubuntu, you'd probably use the command [FONT="Courier New"]sudo gedit /etc/pam.d/gdm[/FONT] to open **/etc/pam.d/gdm** with gedit.



2.) Create a file called **nopassusers** in **/usr/local/etc/**.

Again, you need to be root, so use [FONT="Courier New"]sudo gedit /usr/local/etc/nopassusers[/FONT].



3.) Type the names of the users who will not need a password to login, one to a line, and save. That should do the trick.



REMEMBER!! This only works for the GNOME Login Screen. Anything else that prompts for a pass, including login screens other than the default on tty7, will not accept blank passwords. You will the the actual password.

Hope this helped, or at least made things easier until the option to do so is enabled in an update.

---

