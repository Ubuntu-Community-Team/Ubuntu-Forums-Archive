---
title: "Problem with apache password"
date: 2012-01-05
forum: General Help
---

### Post by Margaret Dumont on 2012-01-05
Hello everyone,

I would like to know how to reset the Apache 2.2 password in Lucid. I've been searching for it but I feel I'm missing something cause I'm not being successful.

----------

Two days ago I upgraded from Karmic to Lucid (which was kind of a nightmare for a not-so-expert-user like me because of the fact that Karmic repositories are gone from the servers). 

During one of the update approaches that I tried (I think it happened booting from the Alternate installer CD), the installation program promped me for "the" Apache password to go on. I was rather puzzled because I don't remember having installed Apache in my computer (I thought it was installed by default but I don't remember intentionally doing it), so I had no idea which would be the password. But finally I found an alternative way to upgrade and didn't give any more thought to it.

----------

Today I was trying to change the background of the login screen following the instructions found on this [this video]("http://www.youtube.com/watch?v=4ZY-DKkfFrg&feature=related") (they are also described on [this web]("http://lionlix.wordpress.com/2009/10/23/hack-ubuntu-9-10-karmic-koala-gdm-login-screen/")). The instructions are to change to a text terminal before login and type:
```
export DISPLAY=:0.0
sudo -u gdm gnome-control-center
```Then, when you return to the graphic terminal, you're supposed to find a gnome-control-center window there to change the background conveniently. But what I found when I changed back to CTRL+ALT+F7 was that my graphic terminal was gone and instead I had a text prompting me for the Apache password again.  :?

I rebooted and everything was back to normal. Of course, I couldn't change my background following this method, but now what it really annoys me is this Apache password thing and I would like to fix it so I'm not stuck with it every now and then.

----------

I tried googleing "reset Apache password" and stuff like that but everything seems to point out to change the mysql root password. So I assumed that was the password I had to change and tried to follow the instructions described [here]("http://www.absolutelytech.com/2010/07/01/howto-reset-mysql-root-password-on-ubuntu-when-youve-forgotten-it/").

I couldn't follow the first instruction of shutting down mysql (sudo /etc/init.d/mysql stop) because "mysql" can not be found in my "init.d" folder. So, as described in the same place, I tried to confirm it through the command "ps -A | grep mysql" which yielded nothing. I thought it was a good thing it was not running by default since, as far as I know, I was not using it. Then, I typed the following instruction ("sudo mysqld_safe --skip-grant-tables &"), which yielded "[1] 2986". And then I only had to run "mysql" to start the client, but it seems that the mysql client is not installed so, whenever I tried that, ubuntu complained and suggested me to run apt-get.

Honestly, I ran out of ideas so I would be very grateful if you could give me any hint on how to solve this issue.

Thank you!

M

PD: At the package manager I can see that apache (2.2) and related packages are installed, as well as a package called mysql-common (5.1.41).

---

