---
title: "Login screen"
date: 2011-09-09
forum: General Help
---

### Post by thunderbirdje on 2011-09-09
Hi everyone,

There is some delay when I press a key, but only at my login screen.

When I type in my password, I have to hold each key for a while and then release it very quick when the dot appears, otherwise I would input the key several times.

So instead of pressing the key and input the character directly there seems to be a slight delay, but irritating.

Once I am logged in, I can type normally! It is just at the login screen.

Anyone any idea what in a name could be wrong or happening? Can I reinstall gnome-desktop to fix it?

---

### Post by blueridgedog on 2011-09-09
Are "slow keys" turned on?

[http://www.abilitynet.org.uk/myway/Changing%20keyboard%20settings%20in%20Gnome.php#keyboard](http://www.abilitynet.org.uk/myway/Changing%20keyboard%20settings%20in%20Gnome.php#keyboard)

See post 26 here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/59616](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/59616)

---

### Post by sum1nil on 2011-09-09
If you wanted to be wild and you are using natty, you could follow these instructions: [https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

See if another Display Manager works better.

---

### Post by thunderbirdje on 2011-09-10
> **blueridgedog said:**
> Are "slow keys" turned on?

[http://www.abilitynet.org.uk/myway/Changing%20keyboard%20settings%20in%20Gnome.php#keyboard](http://www.abilitynet.org.uk/myway/Changing%20keyboard%20settings%20in%20Gnome.php#keyboard)

See post 26 here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/59616](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/59616)

YES! It solved my problem! At first I checked it after log in, which was showing that the 'slow keys' were not enabled.

Then I discovered that there seems to be an [Universal Access Icon at the login screen]("http://www.clickonf5.org/wp-content/uploads/2010/05/ubuntu_uap_option.jpg") and there the option was **enabled**. I am not sure how this happened, but I read that by pressing certain keys longer then 6 seconds it will enable this option.

You have to know that I had to replace my last keyboard because the CTRL key hung most of the time... So that probably enabled the option.

So happy now! Finally no torture anymore at the login screen, haha.

THANKS AGAIN!:D

---

### Post by thunderbirdje on 2011-09-10
> **sum1nil said:**
> If you wanted to be wild and you are using natty, you could follow these instructions: [https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

See if another Display Manager works better.

Hehe, seems interesting! My problem is solved, but maybe just for fun! Thank you

---

