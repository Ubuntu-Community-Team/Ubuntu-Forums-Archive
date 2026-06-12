---
title: "Booting problem"
date: 2009-11-28
forum: General Help
---

### Post by Skyturnred on 2009-11-28
Hello, I am new to Ubuntu. I tried it once about a year ago but I never got the hang of it. Then yesterday I decided to give it another try. I downloaded Ubuntu 9.10 and installed it as a dual boot with windows. It installed nicely and I even used it for an hour or two last night. The last thing I did last night was update it. It was a package about 100 mb large and it updated a variety of things. I let it update overnight. This morning I tried booting ubuntu. It said something to the effect of "mount file system failed" and would not boot. I looked up the problem online and found that a few other people were having the same problem. They said that typing in "fsck" usually fixes it. I typed that in and said yes to everything it asked me so it would fix the file system. When it finished, I rebooted. Now instead of saying "mount file system failed", it says "jack-laptop password:" I enter the password. The next line that comes up is "password:". I have no idea why it asks me for the password twice, but it's wierd. But no matter what I try, it always says "incorrect password" I know it is the correct password. Just to be sure I booted into recovery mode, accessed the root and typed passwd. I changed the password to something very simple and even wrote it down to be sure. I reboot into normal Ubuntu and I get the exact same problem ! When it says "jack-laptop password:" it doesn't matter if i type in the right or wrong password, the next line is ALWAYS "password". Can anyone please help me? I am new to ubuntu and I have no idea what to do. Thanks for the help in advance.

---

### Post by mechro on 2009-11-28
It may sound strange and may not work but when it says "jack-laptop password" try entering your username and when it says "password" enter your password.

---

### Post by Skyturnred on 2009-11-28
OK thanks, I will try that. I will return to tell whether it worked or not.

---

### Post by Skyturnred on 2009-11-28
Ok, I am back. What you told me worked. Thanks, it was a very stupid mistake on my part. It actually said "jack-laptop login", not "jack-laptop password". So anyways, it worked but now I have a new problem. I think that I somehow set ubuntu to not boot up normally. It logs in properly, and normally it would show the orange background, with the white bars at the top and the bottom, but instead it stays like a terminal with a black screen and white writting on the screen. I don't know what to do now, I tried typing b thinking that it would boot ubuntu properly but it says the b command doesn't exist. I am an ubuntu noob and I was sort of caught off guard by how much different it is to windows. Thanks in advance for the help. and thanks for the help before too.

---

### Post by mechro on 2009-11-28
Try this command after your login and password...

```
/etc/init.d/gdm start
```

If it says fail type...

```
exit
```

If that doesn't work, can you try the fsck again from recovery mode?

---

### Post by Skyturnred on 2009-11-28
Thanks for the reply again. I tried that code you gave me with no luck. I also tried fsck again, that didn't work either. Through my research I've learned that many others are having the exact same problem as I am after updating 9.10. So my solution is to re-format the partition and re-install ubuntu 9.10 completely, and to stick with it without updating until 9.11 is released. Oh well. Thanks anyways.

---

### Post by mechro on 2009-11-28
You can pick and choose which updates to install. It's always worth installing the Security Updates and they shouldn't break your system (famous last words!! 8-[ )

I'm still using 9.04 and I'm sticking with that for a while. When I do upgrade I'll do a clean install of 9.10 and dual boot 9.04 and 9.10 until I'm happy with 9.10... just something for you to think about for the future if you stick with Linux and Ubuntu. :)

---

### Post by SuaSwe on 2009-11-28
I might suggest going with 9.04 instead of 9.10 as the latter still has some issues that need ironing out (in my bitter experience anyway!).

---

