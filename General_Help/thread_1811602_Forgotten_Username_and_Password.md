---
title: "Forgotten Username and Password"
date: 2011-07-25
forum: General Help
---

### Post by Ocea on 2011-07-25
Hi. Firstly, I'm completely computer illiterate so bear that in mind if you should be so nice to try and help me c:

Haven't used my laptop with Ubuntu 9.04 in months, completely forgotten my username and password. I've read up other peoples advice on this but it hasn't helped, tried following this, [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) but once i get to 'Drop to root shell prompt' i get 'Give root password for maintenance (or type Control-D to continue): I don't recall ever having a 'root password'

Pretty much have no idea what to do, but there's some important stuff i need off of it so any help would be absolutely wonderful! 
Thanks.

---

### Post by ~!geek!~ on 2011-07-25
I tried once to reset the password of some linux distro. Don't remember the exact procedure. You need to edit grub before booting. I m sure you will find the article using google (it was just first or second on google search result which helped me.)

About root password, I hope you were using a standard installation of ubuntu with root account disabled by default. So there is not root password associated with it. The only password you need is one belonging to the user capable of using sudo command (by default, the first user that you create while installing ubuntu)

If you just need to get a few important files from ubuntu partition you may use live cd to get it. Although do it only when you get exhausted by trying to reset your password.

---

### Post by raja.genupula on 2011-07-25
[http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/](http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/)






look at this this thing gonna help you

---

### Post by Gyokuro on 2011-07-25
You can access your HD with a Live CD and delete the password hash in /etc/passwd

---

### Post by Ocea on 2011-07-26
Thank you all so much! 
I've had success with using the live cd, much appreciated (:

---

