---
title: "Can't login into Ubuntu after an upgrade to Precise Pangolin(12.04)"
date: 2012-04-27
forum: General Help
---

### Post by eMKi on 2012-04-27
Hello everybody!

After 4 years it has happened for the first time that googling my problem got me nowhere. 
The thing is that yesterday I upgraded from Ubuntu 11.10 to 12.04. The upgrade went smoothly. I did a restart and then strange things started to happen.
After each upgrade I set my Ubuntu to automatic login(been upgrading from 10.04 until now without a fresh installation, always 64-bit). As expected yesterday the login window appeared. The first thing that caught my eye were the lines below my user name. They say "No value has been set". I think to my self OK, that is strange but nothing special.
Then I type in my password as usual. And then the big one: "Invalid password, please try again"! :shock: :shock: :shock:

From that time on I tried a couple of things:
1. Tried my different passwords. I always use the same password for Ubuntu but still a gave it a shot.
2. My default language in Ubuntu is English. That is different from my keyboard layout that has a Slovenian layout(I come from Slovenia so that why). It has been a problem before that our Slovenian layout keyboard and English OS don't always cooperate as they should. That is the reason my Ubuntu password has only numbers and English letters. So I tried the on screen keyboard in Ubuntu to click my way through the login. No succes.
3. Than I go and think that the upgrade perhaps messed up my password. The first thing to do would be to change it. I followed these instructions ([https://help.ubuntu.com/11.04/ubuntu-help/user-forgottenpassword.html)]("https://help.ubuntu.com/11.04/ubuntu-help/user-forgottenpassword.html") to do that. First through GRUB. After typing in "passwd *myusername*" I got a puzzling response. The terminal said: 
"passwd: Authentication token manipulation error 
 passwd: password unchanged"
The filesystem state was read/write because I used *fsck *option before going into root. Then I tried the second option with the LiveCD. Erased the password from *shadow* but still no success logging in Ubuntu.

Then there is the thing with the Guest session account. No matter which option I choose (Ubuntu, Ubuntu 2D....) and click Log in nothing happens. The screen goes blank for 3 seconds, the hard disk makes some noise and the login screen comes back on.

Now I don't know what to do next. I have a dual-boot system and Win7 boots up without problems. Ubuntu 11.04 runs great from LiveCD. I did a memtest just to be sure and there were no errors. So I am kind of certain it is not a hardware problem.

If you require any further information or if I was unclear please let me know! 
What else can I do? Any suggestions and help would be greatly appreciated!!

---

### Post by subbs on 2012-04-29
Please take a look into this post. See if it helps, especially the "**UPDATE 2"** suggested in the post.

[http://askubuntu.com/questions/127387/cant-login-through-gui-after-upgrade-from-11-10-to-12-04](http://askubuntu.com/questions/127387/cant-login-through-gui-after-upgrade-from-11-10-to-12-04)


> **eMKi said:**
> Hello everybody!

After 4 years it has happened for the first time that googling my problem got me nowhere. 
The thing is that yesterday I upgraded from Ubuntu 11.10 to 12.04. The upgrade went smoothly. I did a restart and then strange things started to happen.
After each upgrade I set my Ubuntu to automatic login(been upgrading from 10.04 until now without a fresh installation, always 64-bit). As expected yesterday the login window appeared. The first thing that caught my eye were the lines below my user name. They say "No value has been set". I think to my self OK, that is strange but nothing special.
Then I type in my password as usual. And then the big one: "Invalid password, please try again"! :shock: :shock: :shock:

From that time on I tried a couple of things:
1. Tried my different passwords. I always use the same password for Ubuntu but still a gave it a shot.
2. My default language in Ubuntu is English. That is different from my keyboard layout that has a Slovenian layout(I come from Slovenia so that why). It has been a problem before that our Slovenian layout keyboard and English OS don't always cooperate as they should. That is the reason my Ubuntu password has only numbers and English letters. So I tried the on screen keyboard in Ubuntu to click my way through the login. No succes.
3. Than I go and think that the upgrade perhaps messed up my password. The first thing to do would be to change it. I followed these instructions ([https://help.ubuntu.com/11.04/ubuntu-help/user-forgottenpassword.html)]("https://help.ubuntu.com/11.04/ubuntu-help/user-forgottenpassword.html") to do that. First through GRUB. After typing in "passwd *myusername*" I got a puzzling response. The terminal said: 
"passwd: Authentication token manipulation error 
 passwd: password unchanged"
The filesystem state was read/write because I used *fsck *option before going into root. Then I tried the second option with the LiveCD. Erased the password from *shadow* but still no success logging in Ubuntu.

Then there is the thing with the Guest session account. No matter which option I choose (Ubuntu, Ubuntu 2D....) and click Log in nothing happens. The screen goes blank for 3 seconds, the hard disk makes some noise and the login screen comes back on.

Now I don't know what to do next. I have a dual-boot system and Win7 boots up without problems. Ubuntu 11.04 runs great from LiveCD. I did a memtest just to be sure and there were no errors. So I am kind of certain it is not a hardware problem.

If you require any further information or if I was unclear please let me know! 
What else can I do? Any suggestions and help would be greatly appreciated!!

---

### Post by eMKi on 2012-04-29
Not sure if that is the same issue. My screen doesn't freeze it is just that no matter what password I provide they are all invalid.

---

