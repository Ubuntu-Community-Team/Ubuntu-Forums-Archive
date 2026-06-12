---
title: "Killing X server"
date: 2011-09-30
forum: General Help
---

### Post by cmfrtblynmb on 2011-09-30
Hello all

I am looking for a way to kill X server both on 11.10 (and also 11.04)

Nvidia drivers are not working properly for me, so that I decided to install it from Nvidia's site. I downloaded the driver, but I have to kill X first, then install driver.

I have looked for the proper command line, I could not find

Recovery mode does not work at all for some reason.So I have to kill X server from command line

I remember looking for a command that also worked for 11.04 and I remember that I could not find one back then as well. But back then, recovery mode did work, so I did not need the command as a result

ANd no, "sudo stop /etc/init.d/gdm stop" or any similar command does not work. Any solution you can find from google does not work. I spent one day on google.

Is there anyone that can help ? I am really going crazy here. It is just killing X-server. I don't know why canonical made it that hard.

PS: There is no gdm in 11.10. That might be the reason why all these commands on gdm did not work. But the same commands did not also work for 11.04 for some reason. And there is a process called lightdm in /etc/init.d, which governs the log in screen as far as I guess, but killing it only reboots x-server (same as pushing ctrl+alt+bkspace)

SOmebody, please help. This should be a trivial thing to do in any linux installation.

---

### Post by dave01945 on 2011-09-30
i would sugest

```
sudo /etc/init.d/gdm stop
```
for 11.04 and

```
sudo /etc/init.d/lightdm stop
```
for 11.11

but you said you tried that and it didn't work so i would suggest trying to get grub to do. it when you at the grub screen press the **e** key on your normal boot to edit commands before booting and on the line that ends in *quiet splash* add **text** after that and see if that works if you do it by using **e** at the grub command line it will be back to normal next time you boot

---

### Post by cmfrtblynmb on 2011-10-01
Thank you very much Dave

That did the trick. Also your advice on boot sequence has been very helpful considering that I have no recovery now

---

