---
title: "Can't Enable Password Login 11.10"
date: 2012-02-23
forum: General Help
---

### Post by twaddlac on 2012-02-23
Hi All,

     I can't enable a password login on boot up. When I log out/switch users it prompts me for a password but never on boot up. I don't even have the option to login with password when changing my password from the "User Accounts" menu. Please let me know if you have any ideas, thanks!

---

### Post by raja.genupula on 2012-02-23
> **twaddlac said:**
> Hi All,

     I can't enable a password login on boot up. When I log out/switch users it prompts me for a password but never on boot up. I don't even have the option to login with password when changing my password from the "User Accounts" menu. Please let me know if you have any ideas, thanks!

open user accounts , click at unlock at right top of user accounts . then click your account and then disable automatic login(switch it to OFF) .

---

### Post by twaddlac on 2012-02-23
Hi Raja,

     Thanks for the info but unfortunately that switch is turned off. When I go to change my password I have three options from the dropdown box:

1) Set a Password Now
2) Login Without a Password
3) Disable this Account

Currently I have "Set a Password Now" selected (and has been for the entirety of my account). 

I'm also dual-booting with Windows 7 in case that can have an effect.

---

### Post by raja.genupula on 2012-02-23
> **twaddlac said:**
> Hi Raja,

     Thanks for the info but unfortunately that switch is turned off. When I go to change my password I have three options from the dropdown box:

1) Set a Password Now
2) Login Without a Password
3) Disable this Account

Currently I have "Set a Password Now" selected (and has been for the entirety of my account). 

I'm also dual-booting with Windows 7 in case that can have an effect.

whats the status of 2nd option ? say no to it .

---

### Post by twaddlac on 2012-02-23
I have deselected that; it's a drop-down box so you can only choose one, and selecting it does not give way to any other options.

---

### Post by raja.genupula on 2012-02-23
could you give me the output of this command , do it in terminal . 
```
cat /etc/lightdm/lightdm.conf
```

thank you .

---

### Post by twaddlac on 2012-02-24
```
[SeatDefaults]
greeter-session=unity-greeter
user-session=ubuntu
```

---

### Post by twaddlac on 2012-02-26
Does that help or do you need more information?

---

### Post by Runoono on 2013-02-02
Hope I'm not too late
I had the same problem and here's how to fix it 
first: make a another admin account and yes you want it to an admin so that you can edit your account in the later processes
then then you login to your new admin account upon that go to the account settings
afterwards pick the "Disable this Account" option for your own (primary) account. don't worry account will intact
then re-enable your own account pick a password of your choice
and you're done
also for the 12.04 password restrictions try this:
```
sudo passwd (youraccountname)
```like resetting a password but no root-user reboot remount action
be wary that you will not get any visual feedback while entering your new password
have a nice Ubuntu

---

