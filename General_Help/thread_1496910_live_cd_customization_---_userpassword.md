---
title: "live cd customization --- user/password"
date: 2010-05-29
forum: General Help
---

### Post by plutoniumpenguin on 2010-05-29
Hello.

For customizing the live cd, I was following this guide: [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization) .  The part I'm having trouble with is it "Boot Init" section.  Basically, I want to have the live cd autologin as "exusr" with password "expass1" and to have the root password be "expass2" and the name of the system be "exsys".  I'm not entirely clear on how this is done.  First, in the script "/usr/share/initramfs-tools/scripts/casper", it says the username is "casper", whereas if you actually use the live cd, the username is "ubuntu", so why would editing the username here do anything?  Second, it says that to set the encrypted password, you need a tool called mkpasswd.  But this tools comes with no documentation, and I can't seem to figure out how it's supposed to be used.  I mean, I'll type "mkpasswd badpass" and it will spit out some string, and if I keep reiterating "mkpasswd badpass" it will spit out different strings each time.  I would assume that, in order to recognize the resulting string as representing the unique string "badpass", then you would want the conversion to be one-to-one.  Am I misunderstanding something entirely here?  Oh, also, I am the only one who will probably ever use this live cd, so I don't think that it would be at all necessary to use encryption on the password, is there maybe a way I can use an unencrypted password instead?

Thanks!

---

### Post by bildr on 2010-05-29
unencrypted password, no not for a really long time.  passwords are generated with random salts to make reversing hashes more difficult.  there is a mathematical property that allows these hashes to be correlated.

that guide is brutal, try the turnkey linux tool. google is your friend.

---

