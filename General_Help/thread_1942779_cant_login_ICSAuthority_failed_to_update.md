---
title: "cant login ICSAuthority failed to update???????"
date: 2012-03-18
forum: General Help
---

### Post by aliaksei135 on 2012-03-18
hi i can seem to login to my account and im posting this from the guest account on my pc i cant login through tty either and i have no idea what to do now?:confused::confused::confused::confused:

---

### Post by winh8r on 2012-03-18
Could you be a little more specific in order that someone might be able to help you?

What version of Ubuntu are you running?

Is it dual booting with another OS?

What have you tried in order to remedy the situation?

What is the exact wording of the error messge you receive and at what stage in the login process do you receive it?

Thanks.

---

### Post by aliaksei135 on 2012-03-18
im running ubuntu 11.10 and no dual-boot and it says "Could not update ICEAuthority File /home/aliaksei/.ICEAuthority"

---

### Post by aliaksei135 on 2012-03-18
i get it when i login it hangs for 5 seconds and gives this with the ubuntu background in the back ive tried going through tty1, tty2 and it says login details incorrect i know its right ive checked caps lock num lock etc. and its written in a notebook where i keep my passwords and it still says its wrong

---

### Post by WorMzy on 2012-03-18
Sounds to me like you've been running graphical applications with "sudo", this can happen if you do that. Although a problem with ICEAuthoritory shouldn't prevent you from logging in at a tty.. :/

Boot into recovery mode, drop to a root shell, and run
```
chown -R aliaksei:aliaksei /home/aliaksei
```

---

### Post by winh8r on 2012-03-18
If you boot into recovery mode by holding down the shift key before the machine boots, then navigate to a root shell prompt using the arrow keys on your keyboard.

Then enter the following lines at the prompt:

```
chown -R username:username /home/username/.ICEauthority
```

remembering to replace with your own username in the command

then 
```
chmod 644 /home/username/.ICEauthority
```


again remembering to replace your username in the command.

When you have done this

enter 

```
shutdown -r now
```

And you should be able to login as normal.

Hope this helps.

---

### Post by aliaksei135 on 2012-03-18
how do you get to recovery?

---

### Post by WorMzy on 2012-03-18
> **winh8r said:**
> If you boot into recovery mode ... Then enter the following lines at the prompt:

```
chown $USER:$USER /home/username/.ICEauthority
```

remembering to replace with your own username in the command

Not a good idea to use $USER there, as it will be "root". ;)

---

### Post by winh8r on 2012-03-18
As above:


> If you boot into recovery mode by holding down the shift key before the machine boots, then navigate to a root shell prompt using the arrow keys on your keyboard.

---

### Post by winh8r on 2012-03-18
> **WorMzy said:**
> Not a good idea to use $USER there, as it will be "root". ;)
Thanks for spotting that, I hadn't really made it very clear!

edited now.

---

### Post by aliaksei135 on 2012-03-18
cant get recovery just shows a black screen and press ctrl+alt+del and it reboots and does the same

---

### Post by aliaksei135 on 2012-03-18
ive managed to get into tty1 and tty2 but still cant get to recovery and also i have my livecd if that could be used

---

### Post by winh8r on 2012-03-18
Try holding the right hand shift key down , **before** you turn the machine on and **keep it pressed down** until the Grub menu screen shows up.
Then select the Linux kernel nearest the top of the list with (Recovery Mode) beside it. And proceed as above.

---

