---
title: "How to execute startup script in Live cd and ubuntu installed usb drive"
date: 2010-04-15
forum: General Help
---

### Post by venkivoice on 2010-04-15
Hi All,


I am trying to run a script which would execute once the system start's up. I placed my script in /etc/init.d and made it chmod +x my-script and placed my script path in /etc/rc.local . It works fine in installed environment and its not working in live cd and USB.

Please help me, how to achieve this. by the way I am using Ubuntu 9.10

Thanks & Regards,
Venkat

---

### Post by prodigy_ on 2010-04-15
When you boot into live CD, it uses its own **/etc/init.d**. The same goes for USB installation.

---

### Post by venkivoice on 2010-04-15
> **prodigy_ said:**
> When you boot into live CD, it uses its own **/etc/init.d**. The same goes for USB installation.
Thanks for your reply,

But its not working in livecd too. the script gets not executed. I have created ubuntu live cd with certain changes including this script in it.

---

### Post by prodigy_ on 2010-04-15
Can you run it manually when you're using Live CD? Try: ```
sudo /etc/init.d/<your_script_name> start
```

---

### Post by venkivoice on 2010-04-15
yes, it works fine when I run it manually.DO I have to update-rc.d scriptname defaults. I did not give that.

---

### Post by prodigy_ on 2010-04-15
Yeah. Init scripts are executed by rc.

---

### Post by venkivoice on 2010-04-15
Ok, thank you, lemme check it now.

---

### Post by venkivoice on 2010-04-15
> **prodigy_ said:**
> Yeah. Init scripts are executed by rc.


Hi,

It did not work in live cd I have executed update-rc.d script-name defaults. but while i did that i got an warning like this

update-rc.d: warning: /etc/init.d/myscript.sh missing LSB information

How to solve this.but it works nice with the puppy live cd.

---

### Post by prodigy_ on 2010-04-15
You can create rc symlinks manually. For example: ```

for I in 2 3 4 5; do ln -sT /etc/init.d/<your_script_name> /etc/rc.d/rc${I}.d/S80<your_script_name>; done
```
(Ofc, the priority doesn't have to be 80. Substitute whatever number you normally use.)

---

### Post by venkivoice on 2010-04-15
ok, Thank you for your reply. I shall execute this in rc.ocal and try with live cd.

Thanks
Venkat

---

