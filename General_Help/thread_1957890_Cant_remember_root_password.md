---
title: "Cant remember root password"
date: 2012-04-13
forum: General Help
---

### Post by typos1 on 2012-04-13
MY mum's pc wouldnt take the update from 9.10 to 10.04 because there was a bug effecting the processor her pc uses. Before I found out about this bug I created a Root account on her pc to try and sort things. I successfully upgraded her to 11.04 yesterday, but it was 18 months ago I created the root account and now I cant remember the password, so I cant do install anything on it -  Help !!

---

### Post by haqking on 2012-04-13
> **typos1 said:**
> MY mum's pc wouldnt take the update from 9.10 to 10.04 because there was a bug effecting the processor her pc uses. Before I found out about this bug I created a Root account on her pc to try and sort things. I successfully upgraded her to 11.04 yesterday, but it was 18 months ago I created the root account and now I cant remember the password, so I cant do install anything on it -  Help !!

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

And in future root account is not needed and locked by default, in Ubuntu use sudo/gksudo

Read more here [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by typos1 on 2012-04-13
Maybe I m using the wrong terminology then, but if I go into a terminal it wont accept the password that the upgrade asked me to create and it doesnt ask for a password when you login, despite it being set to do so. Maybe the root account I created isnt the problem ? In a terminal it just wont accept any password.

I used my harddrive to backup her files and now its changed to a read only system and I cant get it back to normal.

---

### Post by haqking on 2012-04-13
> **typos1 said:**
> Maybe I m using the wrong terminology then, but if I go into a terminal it wont accept the password that the upgrade asked me to create and it doesnt ask for a password when you login, despite it being set to do so. Maybe the root account I created isnt the problem ? In a terminal it just wont accept any password.

I used my harddrive to backup her files and now its changed to a read only system and I cant get it back to normal.

follow the link in my first post.

When it wants admin password supply your own accounts password not the root account.

Peace

---

### Post by typos1 on 2012-04-13
I have tried ALL passwords and none work !

---

### Post by haqking on 2012-04-13
> **typos1 said:**
> I have tried ALL passwords and none work !

have you followed the link in my first post and then mentioned again in my second post ?

you need to give feedback for more assistance.

Peace

---

### Post by typos1 on 2012-04-13
Yeah, thanks, I have, didnt realise you could change it by going into the boot menu.

I will try that when I go and see her next, but not at her house at the  mo.

Any idea how I can get my hard drive to behave normally on my pc now-its turned into write only and I cant find disc manager app ?

---

### Post by zero2xiii on 2012-04-13
> **typos1 said:**
> Yeah, thanks, I have, didnt realise you could change it by going into the boot menu.

I will try that when I go and see her next, but not at her house at the  mo.

Any idea how I can get my hard drive to behave normally on my pc now-its turned into write only and I cant find disc manager app ?

Common error,

You need to chown everything again. **Unless your ubuntu install is on here** (in other words, if this is where you installed ubuntu DONT DO THIS):

```
sudo chown -R $(whoami) <Path_to_drive>
```

If however this is the drive you installed to, running the following should work:

```
sudo chown -R $(whoami) /home/$(whoami)
```

Cherz

---

### Post by typos1 on 2012-04-13
Thanks, I didnt say, but I was talking about my removable 600Gb usb hard drive, not one inside a pc.

(Assuming your answer was reffering to my hard drive prob)

---

### Post by haqking on 2012-04-13
> **typos1 said:**
> Thanks, I didnt say, but I was talking about my removable 600Gb usb hard drive, not one inside a pc.

(Assuming your answer was reffering to my hard drive prob)

yes i think he was.

You need to do the first command to take ownerhsip back

---

### Post by zero2xiii on 2012-04-13
Hahaha

Yea sorry haha I asumed it will be aparent from the qoute lolz.. My bad.

If it is an external drive you can use the first command, pointing it to the drive. For example /dev/sdb1 or such. If that doesn't work. point it to where the drive is mounted eg /media/external

Cherz

---

### Post by typos1 on 2012-04-23
Tried to change password.

I type ls /home, there is only one user listed. It also lists the password. I resumed boot and tried this password and it does not work.

Logged into recovery mode again and tried to change the password. I type the new password and every time I re-type the new password it says "authentication token manipulation error". I have tried this about 10 times, carefully making sure I do not mis-type and trying different passwords, but it always give the same error. 

It doesnt accept new passwords and I nothing can be installed cos it doesnt accept the original password either. It only prompts for password if the screen locks when the pc is on, but it doesnt accept that password for anything else, including when youre trying to install something. Very strange.

It was also set to ask for password before Ubuntu boots, but it doesnt, it justs boots without a password.

HELP !!

---

