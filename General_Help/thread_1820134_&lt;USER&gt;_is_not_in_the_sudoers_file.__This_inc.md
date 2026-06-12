---
title: "&lt;USER&gt; is not in the sudoers file.  This incident will be reported."
date: 2011-08-07
forum: General Help
---

### Post by Azuruez on 2011-08-07
Stupid mistake.... I have been using Ubuntu 11.04 X86 for about 4 days now after moving on from Mint and I got very irritated when the machine kept asking me for my password. So I then searched the net for a code that would disable this feature...

The code I found was:
```
sudo visudo
```Then find the line that says:
```
%admin ALL=(ALL) ALL
```And replace it with:
```
%admin ALL=(ALL) NOPASSWD: ALL
```Now every time i try to access a 'sudo' code this is displayed:
```
ethan@Ethanje:~$ sudo ./genie_compiz
[sudo] password for ethan: 
ethan is not in the sudoers file.  This incident will be reported.

```There are no other users on my machine but me. What I want to know is, is there any way to fix this, or will I have to re-install Ubuntu and start ALL over again?

---

### Post by whatthefunk on 2011-08-07
Can you re-edit the sudoers file with visudo or do you get the same error message there too?

---

### Post by Azuruez on 2011-08-07
Yeah, I get the same error :confused:

---

### Post by mendhak on 2011-08-07
Have you given your root user a password?  If you already have, then you can go 

su

And that should ask you for your root password.  You can then use that to edit the sudoers file.  You could also try adding your user to the admin group via root.

---

### Post by WorMzy on 2011-08-07
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by Topsiho on 2011-08-07
I hope you realize why Ubuntu has this "irritating" sudo feature?

The idea is that you are only root for executing one command that needs the rights of a super user. And after that you are an ordinary user again. This prevents you to be su all the time, and forget that you are, and enables you to destruct your system (un)voluntarily.

To prevent too much irritation however, if you give commands needing su rights, when you sudo again within a certain number of minutes (15?), you need not give your password again.

The sudo feature, when you get used to it, is the main strong point of Ubuntu. It also makes that if you are the only user of the system, you only need one password, not that of yours as a normal user, ánd that for the root.

Topsiho

---

### Post by Serpher on 2011-08-07
> **mendhak said:**
> Have you given your root user a password?  If you already have, then you can go 

su

And that should ask you for your root password.  You can then use that to edit the sudoers file.  You could also try adding your user to the admin group via root.

Do not do what this user is suggesting. In Ubuntu the root account is disabled for security reasons, and is not meant to be activated. Sudo does not require you to use an actual root password for anything.

---

### Post by bodhi.zazen on 2011-08-07
post the output of 

```
id ethan
```

---

### Post by mendhak on 2011-08-08
(double post)

---

### Post by mendhak on 2011-08-08
> **Serpher said:**
> Do not do what this user is suggesting. In Ubuntu the root account is disabled for security reasons, and is not meant to be activated. Sudo does not require you to use an actual root password for anything.


I was suggesting it in order to rescue the sudoers file, which he can't get to with a normal sudo.

---

### Post by yetiman64 on 2011-08-08
> **mendhak said:**
> I was suggesting it in order to rescue the sudoers file, which he can't get to with a normal sudo.
To set the root password requires the use of sudo, which in this case has been broken. The best bet for the OP is to look into the link in WorMzy's post or post back the output for bodhi.zazen.

Use of the root account is not supported here (Canonical have it locked as default). Posting instructions for unlocking it is against forum policy (lucky you didn't do that ;-)). Hence the response to your post suggesting the use of the root account and su (which normally won't work in Ubuntu for root). Hope this helps explain the reaction/response earlier.

---

### Post by haqking on 2011-08-08
Edit: In retrospect i should of posted this in the resolution Centre.

sorry chaps ;-)

---

### Post by CharlesA on 2011-08-08
You can drop to recovery mode to get to a root prompt - that will allow you to fix the sudoers file. :)

---

### Post by 3rdalbum on 2011-08-08
> **CharlesA said:**
> You can drop to recovery mode to get to a root prompt - that will allow you to fix the sudoers file. :)

To explain: On a dual-boot system, the GRUB menu appears on startup. On a single-boot system, you hold down the Shift key while starting up and it brings up the GRUB menu.

You'll see a list of installed kernels. Basically, you choose the second one in the list - it'll have "Recovery Mode" in its name. Then you can just run:

```
visudo
```

and change back whatever you changed.

You've learnt the hard way: It's not a good idea to mess with the security system. You're just setting up your system at the moment which is why you get a fair few authentication dialogs and why they seem annoying at first. Once you've set up your system, you'll rarely get them anyway.

Making the modification you described doesn't remove all authentication dialogs anyway. It just stops the 'gksudo' ones from appearing. Any related to Policykit, such as Software Center or Gnome authentication dialogs, will continue to appear. Can't be stopped either as far as I know; you really don't want to because things will probably break, or you'll loosen your computer's security to the point where a script kiddie will 0wn your computer. If you're going to make your computer insecure, you might as well do it the quick way and install Windows XP.

---

### Post by Azuruez on 2011-08-08
Thanks for all of the help guys, problem solved :)

---

### Post by sbergman27 on 2012-01-08
Hey, I switched my desktop from Ubuntu back to CentOS 6. But it'll be a while before I break the sudo habit. Network Manager complains if I add myself to sudo, refusing to connect to the network for "security reasons". So that was not a simple option.

I got so annoyed at that whiny "I'm gonna report you!" message, that I went in with a binary editor and changed it to a less annoying "The incident will be concealed." (Yes, it's really hard-coded into the sudo binary.)

Re-establishing the "su" habit is now much less irritating.

-Steve

---

