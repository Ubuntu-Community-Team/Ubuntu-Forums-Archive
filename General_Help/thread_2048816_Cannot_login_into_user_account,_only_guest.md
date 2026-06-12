---
title: "Cannot login into user account, only guest"
date: 2012-08-27
forum: General Help
---

### Post by cashmank on 2012-08-27
Hi all,

I'm running 12.04 and usually use Lubuntu, but have some other environments installed. My installation is encrypted and on a SSD, if it matters.

I had a weird problem recently when booting up. I get to lightdm and am able to log into the guest account but when I try my user account, it boots me back to lightdm. 

The output before sending me back to lightdm:

*Starting NTP server ntpd
saned disabled; edit /etc/default/saned
*Checking battery state...

*Stopping System V runlevel compatibility

I tried updating everything using the command line from lightdm and now it says only "Checking battery state...". After that, it was also able to load the custom background for lightdm that I have, but still won't login to the user account.

Any ideas on how to troubleshoot this?

Thanks!

---

### Post by cashmank on 2012-08-28
Now it's back to:

*Starting NTP server ntpd
saned disabled; edit /etc/default/saned
*Checking battery state...

---

### Post by Toz on 2012-08-28
From a command prompt (Ctrl+Alt+F1), check the ownership of the .Xauthority and .ICEauthority files in your home directory. If you are not the owner, then either change ownership or delete the files.

---

### Post by cashmank on 2012-08-31
> **Toz said:**
> From a command prompt (Ctrl+Alt+F1), check the ownership of the .Xauthority and .ICEauthority files in your home directory. If you are not the owner, then either change ownership or delete the files.
I tried to check ownership on those files in the Home directory. 

When trying to I thought the home directory was home/<username>, but when trying to list files it says it didn't exist. echo $HOME displays just /. Am I doing something wrong/is there a better way to check ownership?

I've already entered my password at boot and my user password in the terminal, so I don't think it's the encryption that's messing with things.

---

### Post by bogan on 2012-08-31
Hi!, **cashmank,**

If your terminal prompt shows as: "user@user -Computername:~$", or similar, and if you enter:```
[COLOR=Blue]cd /home/<user>[/COLOR]
``` and the Prompt stays the same, then you are already in 'HOME'.

Entering:```
 ls  -l  .*authority # will list permissions and ownership
```In your Post you wrote:>   I thought the home directory was [COLOR=Red]home/<username[/COLOR]>```
cd  home/<username>
bash: cd: home/<username>: No such file or directory
``` IE. you left of the first 'slash' symbol.

Chao!,** bogan**.

---

### Post by cashmank on 2012-09-04
Entering

```
cd /home/username
``` yields ```
-bash: cd: /home/username: No such file or directory
```Entering ```
ls  -l  .*authority #
``` yields ```
ls: cannot access .*authority: No such file or directory
```I'm not sure exactly what's going on here...

---

### Post by bogan on 2012-09-04
> **cashmank said:**
> Entering

```
cd /home/username
``` yields ```
-bash: cd: /home/username: No such file or directory
```Entering ```
ls  -l  .*authority #
``` yields ```
ls: cannot access .*authority: No such file or directory
```I'm not sure exactly what's going on here... "cd /home/<user>" means substitute  for "<user>" in the command, the/your user name, that you log-in with.

Have another go, Chao! bogan.

---

### Post by cashmank on 2012-09-04
Yep, I was using my username in place of user/username.

Sorry that was unclear.

---

### Post by bogan on 2012-09-04
Hi!, **cashmank**,

Assuming you did not make a typo & get an upper case error:

Try from 'Crtl+Alt+F1' TTY, not when logged in as Guest:```
cd
cd /home
ls 
ls <user>
# to check if your user folder is there unaltered
```If it seems OK try again after pressing 'Crtl+h' to see if the .*authority files show.

Chao!, **bogan.**

---

### Post by steeldriver on 2012-09-04
> **cashmank said:**
> Entering

```
cd /home/username
``` yields ```
[COLOR=Red]**-bash:**[/COLOR] cd: /home/username: No such file or directory
```

As well as the 'cd' command not finding /home/username, the '-bash: 'prompt also suggest that the system is NOT able to find your .profile / .bashrc - so it seems very likely your username does not have a matching /home/username dir - did you try to change your username?

---

### Post by cashmank on 2012-10-12
> **bogan said:**
> Hi!, **cashmank**,

Assuming you did not make a typo & get an upper case error:

Try from 'Crtl+Alt+F1' TTY, not when logged in as Guest:```
cd
cd /home
ls 
ls <user>
# to check if your user folder is there unaltered
```If it seems OK try again after pressing 'Crtl+h' to see if the .*authority files show.

Chao!, **bogan.**

I still get "No such file or directory".

---

### Post by cashmank on 2012-10-12
> **steeldriver said:**
> As well as the 'cd' command not finding /home/username, the '-bash: 'prompt also suggest that the system is NOT able to find your .profile / .bashrc - so it seems very likely your username does not have a matching /home/username dir - did you try to change your username?


I haven't tried to change my username. I can still see both the guest account and my user account at the graphical log-in screen after booting up, but I get the output I listed about when trying to log into my account. 

Again, this an encrypted installation on a USB drive, but I don't think that has anything to do with it.

---

