---
title: "Help with getting wireless internet working"
date: 2010-11-30
forum: General Help
---

### Post by wyndham29 on 2010-11-30
Now, lets make this clear: I am a COMPLETE linux noob. I only installed ubuntu today (dual booting with Windows 7).

The thing is, my wireless is working perfectly in windows. However, I can't get it to work in Ubuntu. It detects my internet, but refuses to connect. I'm 100% sure that I have used the right password. I have an Atheros AR5007 wifi adapter. I'm liking the look of Ubuntu, but if I can't solve this it's pretty much useless to me. 

Any help would be greatly appreciated, as I really want to perservere with it. Thanks

---

### Post by tajiknomi on 2010-11-30
[SIZE=2]Right-Click on the Network manger icon > Connection Information > Copy your IP address and then go to terminal....

$ ping (your IP)

then you will see the output....Check it out whether it is sending/Receiving your packets or not...use Ctrl+C to stop it then........

Also **ping** your *default-route* the same way....
[/SIZE]

---

### Post by wyndham29 on 2010-11-30
"Connection Information" is greyed out. To clarify what happens, I start ubuntu, it finds my signal and attempts to connect. It tries for a fair while, but eventually comes up with a message saying "Wireless disconnnected".

---

### Post by tajiknomi on 2010-11-30
[SIZE=2]have you tried Right-clicking on that icon > enable-networking..?[/SIZE]

---

### Post by sepo on 2010-11-30
Do you have a portable (as my Dell) with a key to turn on / off the wireless adapter?
Is the adapter on? :)

---

### Post by wyndham29 on 2010-11-30
Hi all thanks for the help. Network is enabled. In relation to turning the adapter on, it is automatically on when I start the computer. However, every now and then while using ubuntu it flicks off then on again (this doesn't happen while using windows).

---

