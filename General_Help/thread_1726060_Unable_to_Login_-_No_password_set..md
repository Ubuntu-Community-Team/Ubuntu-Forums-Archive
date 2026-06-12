---
title: "Unable to Login - No password set."
date: 2011-04-10
forum: General Help
---

### Post by terobin on 2011-04-10
Just installed Ubuntu 10.10 as a dual boot on a Windows Vista laptop. Usually when I've installed Ubuntu on other machines it's asked me to set a user name and password. In this instance, it's automatically taken the same user name as is used to login on Windows.

When I try and log in on Ubuntu, it comes up with th user name from Windows, but asks for a password. On Windows, there's no password set, so I don't know what to put.

I've tried things like 'password' and 'Password' and the likes. I also tried going on Windows and adding a password there to see if Ubuntu would find it, but no such luck.

I don't know how to log in?

---

### Post by Timmer1240 on 2011-04-10
try leaving the password field blank and press login

---

### Post by jerome1232 on 2011-04-10
You can always boot into recover mode, select root prompt and change the password from there

ie to change timmer's pw (adjust to your real username)
Root won't need to know the existing password, you'll just be able to set a new one.

```
root@host:~#passwd timmer
```

---

### Post by Timmer1240 on 2011-04-10
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by terobin on 2011-04-10
When I go on recovery mode, I don't get that option to drop to shell prompt, instead it just asks me to install some firmware, and then asks me for my login details.

After hitting the power button on the laptop, it skips past the login and goes to the image from the psychocats link, of the list with the root shell prompt option... But then the laptop turns off.

---

### Post by jerome1232 on 2011-04-10
I have no idea, are you sure your not accidentally getting into some bios feature by mistake? Like raid setup, or possibly the cmos setup?

Maybe you could even snap a picture with your phone and upload it here so we can see what the screen looks like.

edit due to your edit: I'm stumped!

---

### Post by terobin on 2011-04-10
Based on information found [http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-username-and-password-459353/](http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-username-and-password-459353/) and [http://www.computing.net/answers/linux/forgot-usernamepasswordlocked-out/28131.html](http://www.computing.net/answers/linux/forgot-usernamepasswordlocked-out/28131.html)

I edited one of the boot options by adding "init=/bin/bash" to the end of it, then booted from that. It's come up like a terminal with me as "root@(none):/#"

Then I entered "passwd Admin" (the login on the splash screen is called Admin)

but it returned "passwd: user 'Admin' does not exist."

I tried just "passwd" and was asked to "Enter new UNIX password" and after I did, "Retype new UNIX password", but after that I got...

"passwd: Authentication token manipulation error
passwd: password unchanged"

So I'm still at a loss.

---

### Post by jerome1232 on 2011-04-10
Easiest way to see the user's name is to ls /home

it's probably admin (no capital 'a')

---

### Post by terobin on 2011-04-10
I reread from that second link, and I'd missed a step.

Had to enter "mount -o remount,rw /" to set it to write rather than read only.

I've used "passwd" to change the password, and it says it's updated successfully, but "passwd Admin" still returns "passwd: user Admin does not exist"

Just tried logging in from the splash screen, still getting Authentication Failure.

Trying ls /home as suggested. It returned "emily"
passwd emily

Back to normal, splash screen...
Admin with new password, authentication failure.

Other...
username: emily, new password, authentication failure.

---

### Post by jerome1232 on 2011-04-10
passwd by itself will unlock roots account, which is a "bad" thing for a desktop in general.

I would get back into recovery mode, ls /home, then change the users account that shows up there.

Also I would relock roots account. 
[https://help.ubuntu.com/community/RootSudo#Re-disabling%20your%20root%20account](https://help.ubuntu.com/community/RootSudo#Re-disabling%20your%20root%20account)

--------------------------------------------------

All this being said I've never had Ubuntu "pick-up" the Windows username and password, I remember during one release where they were working on importing settings from Windows, did you somehow check some option by accident to do that?

---

### Post by terobin on 2011-04-10
Ok, so I can sort out that root password issue if I ever manage to log in.

ls /home only returns 'emily', so I use passwd emily to change that password.

What's the proper way to leave the recovery mode? One of those other links says to use "reboot" but that doesn't do anything for me. Maybe I need to leave it properly for the password change to take effect?

Edit: Also, in answer to your question: I don't remember doing anything different to normal, and I just did my brothers laptop last weekend after he managed to somehow delete Windows.

---

### Post by jerome1232 on 2011-04-10
all of the following should work, maybe even try typing the full paths (maybe your $PATH isn't setup correctly) I think these are all in /bin so /bin/shutdown -r now

```
exit
shutdown -r now
reboot
```

---

### Post by terobin on 2011-04-10
SUCCESS!

Logging in with the 'Admin' and the new reset password has finally worked!

Thanks for all your help, jerome, couldn't've done it without you!

---

### Post by patric_thysell on 2011-10-29
Hey,

I had a similar issue with 11.10 today, which nearly made me throw my laptop out the window.

My wife kept nagging me about the fact that I had to login all the time so I said, fine - no problem, Ill just inactivate that.

So I went in to the user account setup and chose Automatic Logn, and password : None.

After shutting down, I didnt have to login - great, though I still had to unlock my keyring :(. NOW, when I wanted to change system stuff, I had to login, but now it didnt recognize my old password anymore, and a blank input field wasnt accepted. DANG :mad:

Reading this thread made me try the following in the Terminal

patric@computer: passwd

then I could reenter my password and Im back on track again.

I must say its a really sketchy thing that it is possible to lock yourself out like that. It takes some googling to get the system back up again, if you dont know this up front.

Enough bitching, now Ill just enjoy the rest of the day.
cheers

---

