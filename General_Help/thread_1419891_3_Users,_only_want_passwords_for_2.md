---
title: "3 Users, only want passwords for 2"
date: 2010-03-02
forum: General Help
---

### Post by aceracer24 on 2010-03-02
I am trying to set up Ubuntu like I had on my windows PC. I have my account, my wifes account and my kids account. I want passwords set for both myself and my wife but I don't want the kids to be required to have a password to log in. When setting up Ubuntu, it looks like it was all or none. I have dabbled with Linux off and on for years and am sure there is a way to set this up but I have no idea how. Can anyone help me please?

---

### Post by psusi on 2010-03-02
Just don't enter a password when setting the password for the desired account.

---

### Post by aceracer24 on 2010-03-02
lol don't you think I tried that already? It said that the password wasn't long enough and had to be 6 or more characters or something like that.

---

### Post by gmargo on 2010-03-02
A little googling found a really interesting method here, which I have not tried:
[http://www.psychocats.net/ubuntucat/creating-a-passwordless-account-in-ubuntu/](http://www.psychocats.net/ubuntucat/creating-a-passwordless-account-in-ubuntu/)

---

### Post by aceracer24 on 2010-03-02
> **gmargo said:**
> A little googling found a really interesting method here, which I have not tried:
[http://www.psychocats.net/ubuntucat/creating-a-passwordless-account-in-ubuntu/](http://www.psychocats.net/ubuntucat/creating-a-passwordless-account-in-ubuntu/)

Hey thanks! I'll give this a shot.

---

### Post by SoFl W on 2010-03-02
> **aceracer24 said:**
> lol don't you think I tried that already? It said that the password wasn't long enough and had to be 6 or more characters or something like that.

I have had a similar error when making a dumb password and although it gave the error it took the password.

---

### Post by aceracer24 on 2010-03-02
> **SoFl W said:**
> I have had a similar error when making a dumb password and although it gave the error it took the password.

Maybe true but I wasn't able to continue the install until I provided a good password.

---

### Post by sgosnell on 2010-03-02
I've never seen Ubuntu refuse to install without a good password.  It will complain, but you can click on Continue and it will take the password, no matter how short.  It doesn't like mine, but I'm not that concerned with security, because if someone gets my netbook, they can do whatever they want, no matter how long my password is.  Just go in and change the password to a blank, and it should be fine.

I just tried that, and it won't take a blank password.  It will take one character, but can't process nothing.  You'll have to go in and set that user to automatic login.  The easiest way is to add a new user, via System/Administration/Users and Groups.  Add a new user, and check the box for automatic login.  You may be able to just edit the children's account for that, but I haven't tried that.

---

### Post by aceracer24 on 2010-03-03
> **sgosnell said:**
> You'll have to go in and set that user to automatic login.  

That may be the easiest way but it's not an option I want. The switch user doesn't work (based on the amount of posts concerning the issue it seems to be ATI related). However, I tried the method that gmargo posted to and it works like a charm. Thanks gmargo!

---

