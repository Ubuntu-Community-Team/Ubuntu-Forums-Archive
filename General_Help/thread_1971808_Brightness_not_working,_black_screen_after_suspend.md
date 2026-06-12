---
title: "Brightness not working, black screen after suspending"
date: 2012-05-02
forum: General Help
---

### Post by higashi on 2012-05-02
I'm running ubuntu 12.04 on a Gateway Nv7915u laptop. I've been having brightness problems ever since I got this laptop and was running 11.04.

When running 11.04, [this patched kernel]("https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight") fixed the problem. I tried adding the same ppa to 12.04 and it helped a bit. Now,when i start the computer, I'm greeted by an ubuntu screen that is stuck at 100% brightness (before adding the ppa, the brightness was stuck at 0% unless i folded and unfolded the laptop). If I suspend my computer, the screen goes back to 0% brightness and I can't get it back unless I restart it. 

Does anyone know a workaround to this bug? Perhaps another patched kernel i can try?

EDIT: I removed the ppa for the previously mentioned patched kernel and nothing has changed.

---

### Post by higashi on 2012-05-06
bump

---

### Post by cmcanulty on 2012-05-06
same here screen reverts to 0 dark every boot. The 11.10 patch not working in 12.04

---

### Post by higashi on 2012-05-20
bump

---

### Post by Toz on 2012-05-20
Out of curiosity, _without_ the linux-kamal-mjgbacklight kernel installed, does adding the kernel parameter **acpi_backlight=vendor** help?

---

### Post by higashi on 2012-05-24
> **Toz said:**
> Out of curiosity, _without_ the linux-kamal-mjgbacklight kernel installed, does adding the kernel parameter **acpi_backlight=vendor** help?

Yes, that did the trick! Thanks!

---

### Post by Toz on 2012-05-24
Glad to hear. Can you mark this thread solved using the Thread Tools link above so that others can more easily find the solution?

---

### Post by coffeequant on 2012-07-09
> **Toz said:**
> Glad to hear. Can you mark this thread solved using the Thread Tools link above so that others can more easily find the solution?

Please don't mark it solved. It is not working in apple macbook pro. Many websites have reported this cheesy solution, but it doesn't work.

---

### Post by Toz on 2012-07-09
@coffeequant,
First, welcome to the forums.

Secondly the solution worked for the Gateway Nv7915u laptop. Since your laptop is different, there is not guarantee it will work. Please create a new thread for the problem with your specific notebook so that it can be addressed.

---

### Post by cmcanulty on 2012-08-26
exactly where do I put the acpi_backlight=vendor

---

### Post by Toz on 2012-08-26
Edit the file /etc/default/grub:
```
gksu gedit /etc/default/grub
```

Change:
> GRUB_CMDLINE_LINUX=""
...to read:
```
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```

Save the file.

Run:
```
sudo update-grub
```

Reboot.

---

### Post by cmcanulty on 2012-08-27
OK thanks, I reinstalled yesterday and couldn't remember the correct fix. All OK now, should be a kernel patch though

---

